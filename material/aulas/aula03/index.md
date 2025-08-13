
## Objetivo
Explorar técnicas de otimização de código sequencial em C++ a partir da análise de desempenho.
O foco será:

* Compreender a relação entre **hierarquia de memória (L1, L2, L3)** e desempenho.
* Aplicar **tiling (fateamento em blocos)** para melhorar o aproveitamento da memória cache.
* Reorganizar estruturas de dados para um melhor aproveitamento do principio da localidade espacial.


##  Contexto

Vamos tomar como base o hardware do monstrão, ele tem um processador **Intel Xeon Gold 5215**, que possui:

* **L1d cache**: 32 KiB por núcleo
* **L2 cache**: 1 MiB por núcleo
* **L3 cache**: 13.75 MiB por socket



Na multiplicação de matrizes, o maior gargalo costuma se o acesso a memória. Para otimizar o desempenho de um algoritmo como esse,  dividimos a matriz em blocos que cabem na memória cache, porque ela é a que está mais proxima da CPU. No nosso caso, cada submatriz de tamanho `B×B` precisa caber na cache junto com mais dois blocos (A, B e C). A fórmula para calcular o tamanho máximo do bloco é:

$$
B \leq \sqrt{\frac{\text{Capacidade da Cache}}{24}}
$$

(onde 24 = 3 matrizes × 8 bytes por double).

Analise o código `matmul_seq.cpp`:

```cpp 
#include <iostream>
#include <vector>
#include <chrono>
#include <cstdlib>
#include <algorithm>

/*
 ============================================================
   OBJETIVO
   -----------------------------------------------------------
   Este programa faz a multiplicação de duas matrizes N×N
   de forma SEQUENCIAL e mede o tempo de execução.

   Ele pode rodar em dois modos:
   - Versão INGENUA (sem otimizações)
   - Versão com TILING (fateamento em blocos), onde o tamanho
     do bloco B é passado como parâmetro na linha de comando.

   O foco é observar como o tamanho do bloco B influencia:
   - O tempo de execução 
   - O uso de cache

 ============================================================
*/
int main(int argc, char* argv[]) {
    const int N = 2000; // Dimensão da matriz quadrada (2000x2000)
    int B = 0;          // Tamanho do bloco. Se for 0 → versão ingênua.

    // Lê o tamanho do bloco da linha de comando
    // Exemplo: ./matmul_seq 200  → roda com blocos 200×200
    if (argc > 1) {
        B = std::atoi(argv[1]);
    }

    // Cria três matrizes NxN em memória, preenchidas com valores fixos
    // - A inicializada com 1.0
    // - Bmat inicializada com 2.0
    // - C inicializada com 0.0 (resultado)
    std::vector<std::vector<double>> A(N, std::vector<double>(N, 1.0));
    std::vector<std::vector<double>> Bmat(N, std::vector<double>(N, 2.0));
    std::vector<std::vector<double>> C(N, std::vector<double>(N, 0.0));

    // Marca o início da medição de tempo
    auto start = std::chrono::high_resolution_clock::now();

    if (B <= 0) {
        // ========================================================
        // VERSÃO INGENUA
        // --------------------------------------------------------
        // Três loops aninhados (i, j, k)
        // Acesso direto às matrizes sem blocagem
        // Tem muitos cache misses porque percorre grandes áreas
        // da memória sem reaproveitar os dados que já estão na cache.
        // ========================================================
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                for (int k = 0; k < N; k++) {
                    C[i][j] += A[i][k] * Bmat[k][j];
                }
            }
        }
    } else {
        // ========================================================
        // VERSÃO COM TILING
        // --------------------------------------------------------
        // Divide a matriz em blocos B×B.
        // Cada bloco é pequeno o bastante para caber na cache,
        // reduzindo cache misses e acelerando a execução.
        // ========================================================
        for (int ii = 0; ii < N; ii += B) {             // percorre blocos de linhas
            for (int jj = 0; jj < N; jj += B) {         // percorre blocos de colunas
                for (int kk = 0; kk < N; kk += B) {     // percorre blocos intermediários
                    // Multiplicação de submatrizes B×B
                    for (int i = ii; i < std::min(ii + B, N); i++) {
                        for (int j = jj; j < std::min(jj + B, N); j++) {
                            double sum = C[i][j]; // acumula resultado local
                            for (int k = kk; k < std::min(kk + B, N); k++) {
                                sum += A[i][k] * Bmat[k][j];
                            }
                            C[i][j] = sum;
                        }
                    }
                }
            }
        }
    }

    // Marca o fim da medição
    auto end = std::chrono::high_resolution_clock::now();

    // Calcula e imprime o tempo total em milissegundos
    std::cout << "Execução (" 
              << (B <= 0 ? "ingênua" : "tiling B=" + std::to_string(B)) 
              << "): "
              << std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count()
              << " ms" << std::endl;

    return 0;
}
```
## Missões:

### 1. Compilação

Compile o código no terminal do head-node `matmul_seq.cpp`:

```bash
g++ -O2  matmul_seq.cpp -o matmul_seq
```

### 2. Execução

Execute o programa em 4 modos:

1. **Ingênuo (sem tiling):**

```bash
srun --partition=monstrao --ntasks=1 ./matmul_seq 0
```

2. **Bloco para L1 (~36×36):**

```bash
srun --partition=monstrao --ntasks=1 ./matmul_seq 36
```

3. **Bloco para L2 (~200×200):**

```bash
srun --partition=monstrao --ntasks=1 ./matmul_seq 200
```

4. **Bloco para L3 (~768×768):**

```bash
srun --partition=monstrao --ntasks=1 ./matmul_seq 768
```
## Explorando Ordenação de Loops e Flags de Otimização em Diferentes Filas**

Você já explorou o efeito do **tiling**. Agora, o objetivo é entender como **a organização dos loops** e **as otimizações do compilador** influenciam o desempenho do mesmo código.


### 1. Alterando a Ordem dos Loops

Modifique o código `matmul_seq.cpp` para usar a ordem **i → k → j** no lugar da ordem original **i → j → k**. Essa mudança afeta a **localidade espacial** dos acessos à matriz B.

### 2. Testar Diferentes Flags de Otimização

Compile o programa com cada conjunto de flags e execute usando diferentes blocos

### 3. Rodar em Diferentes Filas do Cluster

Após identificar as melhores combinações de loop e flags no **monstrao**, identifique quais são os tamanhos das memórias L1, L2 e L3 na fila GPU e repita os testes.


### Perguntas para responder no relatório:

1. A troca de ordem dos loops melhorou ou piorou o tempo de execução? Por quê?
2. Houveram diferenças entre os nós **monstrao** e **gpu**? Quais?
3. Qual o **tamanho de bloco** que apresentou o melhor equilíbrio entre tempo de execução e aproveitamento de cache em cada fila?


## Entregáveis:
Submeta via [Classroom](https://classroom.github.com/a/DnVGRWYD) um arquivo PDF contendo obrigatoriamente:

* Identificação: seu nome completo

* Tabelas comparativas: contendo os resultados obtidos

* Gráficos comparativos: que ilustrem as diferenças de desempenho entre as versões testadas

* Respostas às perguntas: análise crítica com base nos resultados observados 


 **Faça a submissão do relatório até 22/08, 08h30 pelo link do [Github Classromm](https://classroom.github.com/a/DnVGRWYD)**