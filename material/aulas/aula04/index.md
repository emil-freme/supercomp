
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


## **Código base inicial**

Este é o código base para os exercícios:

```cpp
// ------------------------------------------------------------
// Uso:
//   ./miner_base <dificuldade> [estrategia] [limite]
//     - dificuldade: Ex.: 5 (nº de zeros à esquerda no hash)
//     - estrategia : "linear" (padrão), "random", "heuristic"
//     - limite     : nº máx. de tentativas (só para estratégias não lineares)
// Exemplos:
//   ./miner_base 5
//   ./miner_base 6 linear
//   ./miner_base 5 random 2000000
//
// Compilação:
//   g++ miner_base.cpp -o miner_base -lssl -lcrypto
// ------------------------------------------------------------

#include <iostream>
#include <string>
#include <iomanip>
#include <sstream>
#include <chrono>
#include <stdexcept>
#include <openssl/evp.h>

// ========================= SHA-256 ==========================
// Calcula o SHA-256 de uma string e devolve a saída em hexadecimal.
std::string sha256(const std::string& input) {
    // Cria o contexto do algoritmo
    EVP_MD_CTX* ctx = EVP_MD_CTX_new();
    const EVP_MD* md = EVP_sha256();

    // Buffers auxiliares
    unsigned char hash[EVP_MAX_MD_SIZE]; // onde o hash bruto (bytes) será escrito
    unsigned int length = 0;             // número de bytes de hash realmente gerados

    //  Executa as etapas do hash
    EVP_DigestInit_ex(ctx, md, nullptr);                    // inicia SHA-256
    EVP_DigestUpdate(ctx, input.c_str(), input.size());     // alimenta com dados
    EVP_DigestFinal_ex(ctx, hash, &length);                 // finaliza e escreve em 'hash'

    // Libera o contexto
    EVP_MD_CTX_free(ctx);

    // Converte bytes -> string hexadecimal (2 dígitos por byte)
    std::ostringstream os;
    os << std::hex << std::setfill('0');
    for (unsigned int i = 0; i < length; ++i) {
        os << std::setw(2) << static_cast<int>(hash[i]);
    }
    return os.str(); // 64 caracteres hex para SHA-256
}

// =================== Checagem de dificuldade =================
// Verifica se o hash (em hex) começa com N zeros.
// Ex.: zeros=5 → hash deve iniciar com "00000".
bool has_leading_zeros_hex(const std::string& hash, int zeros) {
    if (zeros <= 0) return true;      // dificuldade 0 sempre "passa"
    if (zeros > 64) return false;     // limite do SHA-256 em hex
    std::string alvo(zeros, '0');     // "000...0" (zeros vezes)
    // rfind(sub, 0) == 0 → 'sub' aparece na posição 0 (início da string)
    return hash.rfind(alvo, 0) == 0;
}

// ================ Marcação de tempo para logs =================
std::string now_iso8601() {
    using namespace std::chrono;
    const auto now      = system_clock::now();
    const std::time_t t = system_clock::to_time_t(now);
    std::tm tm          = *std::localtime(&t);

    std::ostringstream os;
    os << std::put_time(&tm, "%Y-%m-%d %H:%M:%S");
    return os.str();
}

// =================== Modelos simples de dados =================
enum class Strategy { Linear, Random, Heuristic, MemOpt };

struct Config {
    std::string bloco      = "dados_transacao"; // conteúdo simplificado do bloco
    int dificuldade         = 5;                 // zeros à esquerda
    Strategy strategy       = Strategy::Linear; // qual estratégia usar
    unsigned long long max_trials = 0;          // limite p/ estratégias não lineares
};

struct Result {
    bool found = false;                    // achou um nonce válido?
    unsigned long long nonce = 0;          // nonce encontrado
    std::string hash;                      // hash correspondente
    unsigned long long iters = 0;          // nº de tentativas
    double seconds = 0.0;                  // tempo total (s)
};

// =================== Estratégia LINEAR (implementada) ===================
// Busca exaustiva: testa nonce = 0, 1, 2, ...
Result mine_linear(const Config& cfg) {
    using clock = std::chrono::high_resolution_clock;
    const auto t0 = clock::now();

    unsigned long long nonce = 0;
    unsigned long long iters = 0;

    while (true) {
        // Concatena "bloco || nonce" e calcula SHA-256
        std::string tentativa = cfg.bloco + std::to_string(nonce);
        std::string h = sha256(tentativa);
        ++iters;

        // Verifica se o hash começa com N zeros
        if (has_leading_zeros_hex(h, cfg.dificuldade)) {
            const auto t1 = clock::now();
            double secs = std::chrono::duration<double>(t1 - t0).count();
            return {true, nonce, h, iters, secs};
        }
        ++nonce; // tenta o próximo
    }
}

Result mine_random(const Config& cfg) {
    using clock = std::chrono::high_resolution_clock;
    const auto t0 = clock::now();

    // TODO: implementar busca com nonces aleatórios.
    // Pesquise sobre:
    //   - std::mt19937_64
    //   - std::uniform_int_distribution

    (void)cfg; // evita warning de parâmetro não usado

    const auto t1 = clock::now();
    double secs = std::chrono::duration<double>(t1 - t0).count();
    return {false, 0, "", 0, secs};
}

Result mine_heuristic(const Config& cfg) {
    using clock = std::chrono::high_resolution_clock;
    const auto t0 = clock::now();

    // TODO: implementar alguma heurística de filtro para nonces já utilizados.
    // Pense sobre:
    //   - pré-filtro por byte do hash antes de checar tudo
    //   - evitar repetição de nonces já testados
    (void)cfg;

    const auto t1 = clock::now();
    double secs = std::chrono::duration<double>(t1 - t0).count();
    return {false, 0, "", 0, secs};
}

// =================== Seletor de estratégia ===================
Result mine(const Config& cfg) {
    switch (cfg.strategy) {
        case Strategy::Linear:   return mine_linear(cfg);
        case Strategy::Random:   return mine_random(cfg);
        case Strategy::Heuristic:return mine_heuristic(cfg);
    }
    return {}; // fallback
}

// =================== Parse de texto -> Strategy ===================
Strategy parse_strategy(const std::string& s) {
    if (s == "linear")    return Strategy::Linear;
    if (s == "random")    return Strategy::Random;
    if (s == "heuristic") return Strategy::Heuristic;
    throw std::invalid_argument("Estrategia invalida: " + s);
}

// =================== Impressão ===================
void print_header(const Config& cfg) {
    std::cout << "=== Mineracao PoW (base) ===\n"
              << "Iniciado em: " << now_iso8601() << "\n"
              << "Bloco      : " << cfg.bloco << "\n"
              << "Dificuldade: " << cfg.dificuldade << " zeros\n"
              << "Estrategia : ";
    switch (cfg.strategy) {
        case Strategy::Linear:    std::cout << "linear\n";    break;
        case Strategy::Random:    std::cout << "random (STUB)\n";    break;
        case Strategy::Heuristic: std::cout << "heuristic (STUB)\n"; break;
    }
    if (cfg.strategy != Strategy::Linear) {
        std::cout << "Limite Tent.: " << cfg.max_trials << "\n";
    }
    std::cout << "=============================\n";
}

void print_result(const Result& r) {
    if (r.found) {
        std::cout << "STATUS  : ENCONTRADO\n"
                  << "NONCE   : " << r.nonce   << "\n"
                  << "HASH    : " << r.hash    << "\n"
                  << "ITERS   : " << r.iters   << "\n"
                  << "TEMPO(s): " << r.seconds << "\n";
    } else {
        std::cout << "STATUS  : NAO ENCONTRADO (stub)\n"
                  << "ITERS   : " << r.iters   << "\n"
                  << "TEMPO(s): " << r.seconds << "\n";
    }
}

void print_usage(const char* prog) {
    std::cerr << "Uso: " << prog << " <dificuldade 0..64> [estrategia] [limite]\n"
              << "  estrategia: linear | random | heuristic \n"
              << "  limite    : inteiro >= 0 (apenas para random/heuristic)\n"
              << "Exemplos:\n"
              << "  " << prog << " 5\n"
              << "  " << prog << " 6 linear\n"
              << "  " << prog << " 5 random 2000000\n";
}

// =================== main ===================
int main(int argc, char** argv) {
    try {
        // 1) Leitura/validação dos argumentos
        if (argc < 2) {
            print_usage(argv[0]);
            return 1;
        }

        int dificuldade = 5;
        {
            int d = std::stoi(argv[1]);
            if (d < 0 || d > 64) {
                std::cerr << "Dificuldade invalida (0..64).\n";
                return 1;
            }
            dificuldade = d;
        }

        Strategy strat = Strategy::Linear;
        if (argc >= 3) {
            strat = parse_strategy(argv[2]);
        }

        unsigned long long limite = 0ULL;
        if (argc >= 4) {
            long long l = std::stoll(argv[3]);
            if (l < 0) {
                std::cerr << "Limite invalido (>= 0).\n";
                return 1;
            }
            limite = static_cast<unsigned long long>(l);
        }

        // 2) Monta a configuração
        Config cfg;
        cfg.bloco       = "dados_transacao";
        cfg.dificuldade = dificuldade;
        cfg.strategy    = strat;
        cfg.max_trials  = limite;

        // 3) Roda a mineração
        print_header(cfg);
        Result r = mine(cfg);
        print_result(r);

        // Saída de processo: 0 (ok) | 2 (não encontrou nas estratégias não lineares)
        return r.found ? 0 : 2;
    }
    catch (const std::exception& e) {
        std::cerr << "Erro: " << e.what() << "\n";
        print_usage(argv[0]);
        return 1;
    }
}
```


## Perguntas para responder no relatório:

   * Aleatoriedade ajudou, atrapalhou ou não mudou nada?
   * Heurística fez diferença?
   * Memória otimizada trouxe ganhos?
   * Entre as versões qual apresentou o menor tempo médio? Por 
   

## Entregáveis:

Gere um PDF que contenha obrigatoriamente:

   * Identificação: seu nome completo.

   * Descrição breve do ambiente de teste: partição do Franky, dificuldade (nº de zeros), nº de repetições por versão.

   * Tabelas comparativas com os resultados (por versão e dificuldade).

   * Gráficos comparativos (ex.: tempo × versão; opcionalmente boxplot por versão).

   * Respostas às perguntas acima, com análise crítica baseada nos resultados obtidos.