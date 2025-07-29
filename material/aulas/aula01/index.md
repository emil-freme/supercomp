
Durante a aula, vimos que problemas computacionalmente complexos podem ser 
- Grandes, uma quantidade de dados absurda, que não cabe em um computador de trabalho comum
- Intensivo, Realiza calculos complexos e demorados, demandando horas ou dias de processamento intensivo
- Combo, As vezes o problema tem as duas caracteristicas, tem uma grande quantidade de dados, demanda cálculos intesivos.


Para resolver problemas desse tipo, precisamos fazer um bom uso do hardware, podemos começar usando uma linguagem de programação mais eficiente e planejando melhor o nosso código, usando as características da linguagem ao nosso favor.

!!! tip "Conteúdo teórico de apoio - Aula 01"
    Eu fui legal e organizei [aqui tudo aqui](../../teoria/aula01/index.md) pra você!


### Atividade 01 — **Python x C++**

Você está trabalhando com sensores industriais que geram milhões de medições por dia, como temperatura, pressão e vibração. Monitorar apenas a última medição **não é confiável**: leituras oscilam naturalmente devido a ruídos ou pequenas flutuações.

Para obter **informações mais estáveis e úteis**, usamos **médias móveis**: ao invés de olhar um valor isolado, olhamos a **tendência local dos dados**.

> Exemplo: Se a temperatura medida for `[85.1, 84.9, 85.0, 93.2, 85.1, 85.0]`, um único pico (93.2) poderia gerar alarme falso. A média móvel suaviza esse ruído.


### Desafio

Simular o processamento de dados de sensores, implementando o cálculo da média móvel simples. A partir disso, comparar diferentes versões do código para analisar os ganhos de desempenho obtidos com otimizações e com o uso dos recursos da linguagem C++.

Implementação em Python
```python
import time
import random

# N = 100 milhões de leituras
N = 100_000_000

# Janela K = 10
K = 10

# Gera os dados
start_gen = time.time()
dados = [random.uniform(12.0, 189.98) for _ in range(N)]
print("Tempo para gerar os dados:", time.time() - start_gen)

# Calcula média móvel
start_avg = time.time()
media = []
soma = sum(dados[:K])
media.append(soma / K)

for i in range(1, N - K):
    soma = soma - dados[i - 1] + dados[i + K - 1]
    media.append(soma / K)

print("Tempo para calcular média móvel:", time.time() - start_avg)
```


1. Faça um código em c+++ que gera um vetor com `100000000` valores de leitura do tipo `double`, variando entre `12.0` e `189.98`

2. Implemente o cálculo da **média móvel simples** com janela `k = 10`, ou seja:

   $$
   M_i = \frac{1}{k} \sum_{j=i}^{i+k-1} v_j
   $$

3. Faça a passagem dos dados para o cálculo da média móvel simples de 3 formas diferentes:
   * Passagem **por valor**
   * Passagem **por referência**
   * Passagem **por ponteiro**

4. Use `const` para garantir **segurança e desempenho (const correctness)** onde fizer sentido.

5. Compile usando diferentes flags de otimização:

7. Meça e compare os tempos de execução

8. Compare com a implementação em python.


**Esqueleto do código – `media.cpp`**

```cpp
#include <iostream>
#include <vector>
#include <random>
#include <chrono>

using namespace std;

// =========================================
// Constantes globais
// =========================================
const size_t N = 100'000'000; // Número total de amostras
const size_t K = 10;          // Tamanho da janela da média móvel

// =========================================
// Função para gerar um vetor com valores aleatórios
// =========================================
vector<double> gerar_leituras(size_t tamanho) {
    // TODO: Criar um vetor de tamanho `tamanho`
    // TODO: Criar gerador de números aleatórios com seed fixa
    // TODO: Definir distribuição entre 12.0 e 189.98
    // TODO: Preencher o vetor com números aleatórios

    // DICA: use std::vector<double> e uniform_real_distribution

    return {}; // Substitua pelo vetor preenchido
}

// =========================================
// Função para calcular a média móvel (passagem por valor)
// =========================================
vector<double> media_movel_por_valor() {
    // TODO: Calcular a média móvel simples sobre o vetor recebido por valor
    // TODO: Retornar um vetor com os resultados

    return {};
}

// =========================================
// Função para calcular a média móvel (passagem por referência)
// =========================================
vector<double> media_movel_por_referencia() {
    // TODO: Igual à versão anterior, mas recebendo os dados por referência constante

    return {};
}

// =========================================
// Função para calcular a média móvel (passagem por ponteiro)
// =========================================
vector<double> media_movel_por_ponteiro() {
    // TODO: Usar aritmética de ponteiros para calcular a média móvel
    // TODO: Retornar um vetor com os resultados

    return {};
}

// =========================================
// Função para medir tempo de execução
// =========================================
template <typename Func, typename... Args>
double medir_tempo(Func funcao, Args&&... args) {
    auto inicio = chrono::high_resolution_clock::now();
    funcao(forward<Args>(args)...);
    auto fim = chrono::high_resolution_clock::now();
    chrono::duration<double> duracao = fim - inicio;
    return duracao.count();
}

// =========================================
// Função principal
// =========================================
int main() {
    // Etapa 1: Gerar os dados
    cout << "Gerando dados..." << endl;
    vector<double> leituras = gerar_leituras(N);

    // Etapa 2: Cálculo por valor
    cout << "Média móvel (por valor):" << endl;
    double tempo_valor = medir_tempo(media_movel_por_valor, leituras, K);
    cout << "→ Tempo: " << tempo_valor << " s" << endl;

    // Etapa 3: Cálculo por referência
    cout << "Média móvel (por referência):" << endl;
    double tempo_ref = medir_tempo(media_movel_por_referencia, leituras, K);
    cout << "→ Tempo: " << tempo_ref << " s" << endl;

    // Etapa 4: Cálculo por ponteiro
    cout << "Média móvel (por ponteiro):" << endl;
    const double* ptr = leituras.data();
    double tempo_ptr = medir_tempo(media_movel_por_ponteiro, ptr, N, K);
    cout << "→ Tempo: " << tempo_ptr << " s" << endl;

    // Etapa 5: Compile com diferentes flags e compare os tempos
    // Exemplo:
    //   g++ media.cpp -o sem_otimizacao
    //   g++ -O2 media.cpp -o otimizacao_O2
    //   g++ -O3 media.cpp -o otimizacao_O23
    //   g++ -Ofast media.cpp -o otimizacao_Ofast
    return 0;
}

```


### Entrega da Atividade 01
No arquivo README.md do Classroom, inclua:
 
* Código-fonte em C++: o programa utilizado para os testes. 

* Tabela comparativa: com os resultados de todas as execuções

* Gráfico comparativo: representando visualmente os resultados obtidos.

* Análise de desempenho: comentários explicando quais fatores influenciaram o desempenho

**Entrega até quinta 23h59 pelo link do [GitHub Classroom](https://classroom.github.com/a/GoLn_7KP), também disponível no Blackboard.**

Lembre-se de preencher o [forumlário](https://forms.gle/K9FK8be9HjoJ4ypGA) para criar o seu acesso ao Cluster Franky, ele será usado a partir da próxima aula!

!!! tip "Dica!"
    Lembre-se de consultar o material disponível em [Conteúdo teórico de apoio - Aula 01](../../teoria/aula01/index.md)
