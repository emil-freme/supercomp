
### Código completado e comentado

```cpp
#include <iostream>
#include <vector>
#include <random>
#include <chrono>

using namespace std;

// Constantes globais
size_t N = 100'000'000;
size_t K = 10;

// =========================================
// Geração de dados simulados
// Implementação sem nenhuma otimização 
// =========================================
void gerar_dados_sem_otimizacao() {
    const int TAMANHO = 10000;
    double dados[TAMANHO];

    default_random_engine gerador(42);
    uniform_real_distribution<double> distribuicao(12.0, 189.98);

    for (int i = 0; i < TAMANHO; ++i) {
        dados[i] = distribuicao(gerador);
    }

    cout << "Primeiros 5 valores (sem otimização): ";
    for (int i = 0; i < 5; ++i) {
        cout << dados[i] << " ";
    }
    cout << endl;
}

// =========================================
// Geração de dados simulados
// Implementação com passagem de valor por referência
// =========================================
vector<double> gerar_dados(size_t tamanho) {
    vector<double> dados(tamanho);
    default_random_engine gerador(42);
    uniform_real_distribution<double> distribuicao(12.0, 189.98);

    for (auto& valor : dados) {
        valor = distribuicao(gerador);
    }

    return dados;
}

// =========================================
// Geração de dados simulados
// Implementação com passagem de valor por ponteiro
// =========================================
void gerar_dados_ponteiro(double* vetor, size_t tamanho) {
    default_random_engine gerador(42);
    uniform_real_distribution<double> distribuicao(12.0, 189.98);

    for (size_t i = 0; i < tamanho; ++i) {
        vetor[i] = distribuicao(gerador);
    }
}

// =========================================
// Cálculo da média móvel (por valor)
// =========================================
vector<double> media_movel_valor(vector<double> dados, size_t k) {
    vector<double> resultado;
    double soma = 0;

    for (size_t i = 0; i < k; ++i) soma += dados[i];
    resultado.push_back(soma / k);

    for (size_t i = 1; i <= dados.size() - k; ++i) {
        soma = soma - dados[i - 1] + dados[i + k - 1];
        resultado.push_back(soma / k);
    }

    return resultado;
}

// =========================================
// Cálculo da média móvel (por referência)
// =========================================
vector<double> media_movel_ref(const vector<double>& dados, size_t k) {
    vector<double> resultado;
    double soma = 0;

    for (size_t i = 0; i < k; ++i) soma += dados[i];
    resultado.push_back(soma / k);

    for (size_t i = 1; i <= dados.size() - k; ++i) {
        soma = soma - dados[i - 1] + dados[i + k - 1];
        resultado.push_back(soma / k);
    }

    return resultado;
}

// =========================================
// Cálculo da média móvel (por ponteiro)
// =========================================
vector<double> media_movel_ponteiro(const double* dados, size_t tamanho, size_t k) {
    vector<double> resultado;
    double soma = 0;

    for (size_t i = 0; i < k; ++i) soma += dados[i];
    resultado.push_back(soma / k);

    for (size_t i = 1; i <= tamanho - k; ++i) {
        soma = soma - dados[i - 1] + dados[i + k - 1];
        resultado.push_back(soma / k);
    }

    return resultado;
}

// =========================================
// Medição de tempo para funções
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
    cout << "== Versão sem otimização ==" << endl;
    gerar_dados_sem_otimizacao();

    cout << "\n== Versão com vector (por valor) ==" << endl;
    vector<double> dados_valor = gerar_dados(N);
    double tempo_valor = medir_tempo(media_movel_valor, dados_valor, K);
    cout << "Tempo (por valor): " << tempo_valor << " segundos" << endl;

    cout << "\n== Versão com vector (por referência) ==" << endl;
    double tempo_ref = medir_tempo(media_movel_ref, dados_valor, K);
    cout << "Tempo (por referência): " << tempo_ref << " segundos" << endl;

    cout << "\n== Versão com ponteiro ==" << endl;
    double* dados_ptr = new double[N];
    gerar_dados_ponteiro(dados_ptr, N);
    double tempo_ptr = medir_tempo(media_movel_ponteiro, dados_ptr, N, K);
    cout << "Tempo (por ponteiro): " << tempo_ptr << " segundos" << endl;
    delete[] dados_ptr;

    return 0;
}
```

---

### Compilar com diferentes otimizações

```bash
g++ -std=c++17 -O0 -o media_movel media_movel.cpp      # sem otimização
g++ -std=c++17 -O2 -o media_movel media_movel.cpp      # otimização moderada
g++ -std=c++17 -O3 -march=native -o media_movel media_movel.cpp  # otimização agressiva
```
