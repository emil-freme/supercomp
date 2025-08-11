
## Objetivo

Ao final desta atividade, você será capaz de:

* Entender **o que é um nonce** e como ele se relaciona com o Proof of Work.
* Usar **aleatoriedade** para guiar a busca de soluções.
* Implementar **heurísticas** para reduzir o espaço de busca.
* Medir e comparar desempenho em diferentes **estratégias e ambientes**.

---

## **Relembrando o contexto**

Na mineração de criptomoedas:

1. Cada bloco de transações precisa de um **hash** válido.
2. O **nonce** é um número que o minerador altera até que o hash tenha um formato específico.
3. Essa busca é **exaustiva**, o minerador testa muitos nonces até achar um válido.


## **Aleatoriedade**

### Por que usar aleatoriedade?

Em busca linear, você testa **sempre na mesma ordem** (0, 1, 2, 3...). Em ambientes distribuídos, isso pode causar **sobreposição**, vários nós podem testar o mesmo nonce, desperdiçando tempo, usar aleatoriedade permite **espalhar tentativas**, reduzindo repetições.

* Pesquise sobre **`std::mt19937`** para gerar nonces aleatórios.

Exemplo:

```cpp
#include <random>

std::random_device rd;
std::mt19937_64 gen(rd());
std::uniform_int_distribution<unsigned long long> distrib(0, ULLONG_MAX);

while (true) {
    unsigned long long nonce = distrib(gen); // aleatório
    std::string tentativa = bloco + std::to_string(nonce);
    std::string hash = sha256(tentativa);

    if (validaHash(hash, dificuldade)) {
        std::cout << "Nonce encontrado: " << nonce << "\n";
        break;
    }
}
```

**Experimento:**

* Rode versão sequencial e versão aleatória **3 vezes cada**.
* Compare tempos.
* Aleatoriedade ajudou ou atrapalhou?


## **Heurísticas**

Heurísticas são regras para **guiar a busca** e evitar trabalho desnecessário.

### Ideias simples:

* **Filtrar**: Se os primeiros bytes do hash não têm um padrão parcial, pule.
* **Memorizar**: Guardar nonces testados e evitar repetição.
* **Pular ranges**: Se um range foi testado e não funcionou, vá para outro.

**Experimento:**

* Compare execução **com e sem** essa heurística.
* Veja se ela reduz tempo (cuidado: guardar nonces testados consome memória).


## **Eficiência de Memória**

### Por que importa?

* SHA-256 roda muitas vezes; se você aloca/desaloca memória a cada iteração, perde desempenho.
* Uso eficiente da memória reduz **cache misses**.

### Melhorias possíveis:

1. **Pré-alocação de strings** (`reserve`):

```cpp
std::string tentativa;
tentativa.reserve(bloco.size() + 20);
```

2. **Reuso de buffers**:

```cpp
tentativa = bloco;
tentativa += std::to_string(nonce);
```

3. **Evitar cópias**:

* Passar strings por **referência const**.
* Usar arrays fixos quando possível.



### Testes:

1. Execute cada versão **no Cluster Frnaky**
3. Registre os tempos.

## **Formato do Relatório**

1. **Tabela de resultados**:
   \| Versão        | Tempo médio (s) | Memória Máxima (MB) | Observações |
   \|---------------|----------------|---------------------|-------------|
   \| Sequencial    |                |                     |             |
   \| Aleatória     |                |                     |             |
   \| Heurística    |                |                     |             |
   \| Combo         |                |                     |             |

2. **Gráficos** (tempo × versão).

3. **Discussão**:

   * Aleatoriedade ajudou?
   * Heurística fez diferença?
   * Memória otimizada trouxe ganhos?
