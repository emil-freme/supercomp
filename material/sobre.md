

# Burocracias 

!!! info "Horários"
    **Aulas:**
    
    Segunda -> 16h30 -- 18h30
    
    Sexta -> 14h15 -- 16h15

    **Atendimento:**
    
    Segunda -> 18h30 -- 20h00


??? info "Objetivos de Aprendizagem"

    Ao final da disciplina, o estudante será capaz de:

    **Obj 1.** Desenvolver algoritmos usando recursos de computação paralela e distribuída para obter ganhos de desempenho na aplicação final.

    **Obj 2.** Aplicar estruturas lógicas de computação distribuída no desenvolvimento de algoritmos multitarefa.

    **Obj 3.** Usar GPGPU (General-Purpose computing on Graphics Processing Units) para computação numérica e comparar seu desempenho com soluções baseadas em CPU.

    **Obj 4.** Planejar e projetar sistemas de computação de alto desempenho, considerando aspectos de hardware, escalabilidade, e alocação de recursos.

    **Obj 5.** Analisar a complexidade de algoritmos paralelos e a eficiência de implementações específicas, identificando as métricas de desempenho mais adequadas para essa análise.

    **Obj 6.** Aplicar recursos específicos de sistemas operacionais (como escalonadores, controle de threads e gerenciamento de memória) para melhorar o desempenho de algoritmos.

    **Obj 7.** Desenvolver aplicações que utilizam protocolos otimizados para paralelização, como MPI, OpenMP e CUDA.


??? tip "Plano de Aulas - Supercomputação (2025.2)"
    | Data         | Aula     | Tópicos Abordados                                                                                                           | Atividades                                                                                                                                                     |
    |--------------|----------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 11/ago (seg) | Aula 01  | Problemas de HPC; mapa de memória; Python × C++; desempenho; objetivos da disciplina; passagem de argumentos; recursos de C++ | Transcrição de códigos Python para C++; comparação de desempenho entre linguagens. |
    | 15/ago (sex) | Aula 02  | Sistemas de HPC; rede, hardware, filas, jobs; SLURM; clusters no Brasil e no mundo  | Testes com SLURM no Cluster Franky; comparação de desempenho em diferentes filas. |    
    | 18/ago (seg) | Aula 03  | Hierarquia de memória (L1, L2, L3); técnica de Tiling (fateamento em blocos); princípios de localidade espacial e temporal | Aplicar tiling para melhorar o uso de cache; reorganizar estruturas de dados para melhor localidade. |
    | 22/ago (sex) | Aula 04  | Aleatoriedade, heurísticas, alocação de memória  | Ajustes em heurísticas, estrutura de dados e uso da memória de forma eficiente. |   
    | 25/ago (seg) | Aula 05  | Paralelismo em CPU; threads; cores; OpenMP; variáveis privadas e compartilhadas; scheduling  | Paralelismo com OpenMP; compartilhamento entre threads; efeitos do scheduler. |
    | 29/ago (sex) | Aula 06  | Efeitos colaterais do paralelismo; racing conditions; dependências; recursão | Estudo de caso: mapear problemas, levantar hipóteses de otimização e comparar desempenho. |
    | 01/set (seg) | Aula 07  | Memória distribuída; comunicação com MPI; ponto-a-ponto e coletiva; grupos e comunicadores    | Paralelismo com MPI; comunicação entre nós. |
    | 05/set (sex) | Aula 08  | Estratégias híbridas MPI + OpenMP  | Estudo de caso com MPI + OpenMP, levantamento de gargalos e possíveis otimizações. |
    | 08/set (seg) | Aula 09  | Aula estúdio | Suporte ao Projeto 1 – Mineração de criptomoedas em CPU |
    | 12/set (sex) | Aula 10  | Palestra NVIDIA - CUDA | Palestra NVIDIA - CUDA |
    | 15/set (seg) | Aula 11  | Aula estúdio  | Suporte ao Projeto 1 – Mineração de criptomoedas em CPU |
    | 19/set (sex) | Aula 12  | Devolutiva do Projeto 1 | Discussão das soluções apresentadas e feedback. |
    | 22/set (seg) | Aula 13  | Aula estúdio | Ajustes finais no Projeto 1 – Mineração de criptomoedas em CPU |
    | 26/set (sex) | Aula 14  | Prova Intermediária | Avaliação dos conteúdos até Estratégias híbridas MPI + OpenMP. |
    | 29/set (seg) | Aula 15  | Profiling em GPU; warps e SIMD; divergência; alocação de memória  | Atividade prática de Profiling em GPU, análise de divergências e uso de memória. |
    | 06/out (seg) | Aula 16  | Histogramming; data race em GPU; atomic; throughput | Estudo de caso aplicado. |
    | 10/out (sex) | Aula 17  | Técnicas stencil; convolução; tile boundaries; agendamento de threads | Estudo de caso aplicado. |
    | 13/out (seg) | Aula 18  | Estabilidade numérica; ponto flutuante; controle de erro | Estudo de caso aplicado. |
    | 17/out (sex) | Aula 19  | Estratégias híbridas com MPI + CUDA; gerenciamento de dados | Atividade prática com múltiplas GPUs. |
    | 20/out (seg) | Aula 20  | Resumo das estratégias de otimização; discussão sobre aplicação em projeto | Discussão coletiva de estratégias de otimização. |
    | 24/out (sex) | Aula 21  | Apresentação do Projeto 2 | Discussão sobre estratégias de otimização para aplicação no projeto. |
    | 27/out (seg) | Aula 22  | Aula estúdio | Suporte ao Projeto 2 – Mineração de criptomoedas em GPU |
    | 31/out (sex) | Aula 23  | Palestra NVIDIA – OpenACC | Introdução ao OpenACC |
    | 03/nov (seg) | Aula 24  | Aula estúdio | Suporte ao Projeto 2 – Mineração de criptomoedas em GPU |
    | 07/nov (sex) | Aula 25  | Aula estúdio | Suporte ao Projeto 2 – Mineração de criptomoedas em GPU |
    | 10/nov (seg) | Aula 26  | Devolutiva do Projeto 2 | Ajustes finais após feedback ao Projeto 2 |
    | 14/nov (sex) | Aula 27  | Simulado da Avaliação Final | Revisão prática. |
    | 17/nov (seg) | Aula 28  | Avaliação Final | Avaliação Final |
    | 24/nov (seg) | Aula 29  | Avaliação Final | Encerramento e avaliação final |


??? note "Atividades (Individual) 15%"
    | Percentual de Atividades | Conceito | Com Participação Voluntária |
    |--------------------------|----------|-----------------------------|
    | 50%                     | C        | C+                          |
    | 70%                     | B        | B+                          |
    | 90%                     | A        | A+                          |




??? note "Projeto 1 (Grupo) 10%"

    ### **Mineração de criptomoedas em CPU**
    Este projeto consiste na implementação e otimização de um minerador de criptomoedas que roda em CPU. Aplicando técnicas de paralelismo para melhorar desempenho no cluster Franky. A dificuldade da mineração é ajustada pela quantidade de zeros no hash, aumentando o desafio computacional conforme otimizimos a aplicação.

    | **Rubrica** | **Critérios Técnicos**  |
    | ----------- | ----------------------- |   
    | **C**       | Executa o código minerador **assíncrono no cluster Franky com dificuldade **5 zeros** e pelo menos 5 gerações diferentes de async_gen`. |      
    | **B**       | Executa o código minerador **assíncrono** no cluster Franky com dificuldade **6 zeros** e pelo menos 5 gerações diferentes de `async_gen`; utiliza paralelismo **ou** distribuição do código em CPU. |
    | **A**       | Executa o código minerador **assíncrono** no cluster Franky com dificuldade **7 zeros** e pelo menos 5 gerações diferentes de `async_gen`; realiza paralelização **e** distribuição do código em CPU.         | 

    ### Entrega
    Código-fonte funcional, comentado e documentado. Relatório técnico com: 
    
    - Diagnóstico dos gargalos;
    - Proposta de otimização;
    - Hipótese de melhoria;
    - Implementação da hipótese;
    - Comparação de desempenho;
    - Discussão dos resultados.

    ### Bônus por Qualidade

    | Conceito Base | Com Bônus |
    |---------------|-----------|
    | C             | C+        |
    | B             | B+        |
    | A             | A+        |


??? note "Projeto 2 (Individual) 20%"
    Projeto Minerador em GPU 
    Neste projeto, o foco é explorar o uso de paralelismo e estratégias de otimização em GPU para maximizar o desempenho computacional.

    Objetivos principais:

    - Executar o projeto utilizando o sistema de HPC SDumont, do LNCC;
    
    - Implementar estratégias de paralelismo e distribuição em GPUs;

    - Aumentar a dificuldade da mineração (número de zeros);

    - Comparar desempenho, eficiência e consumo de recursos entre as versões CPU e GPU;

    ### Rúbrica de Avaliação

    | Nível       | Critérios Técnicos                                                                 | Complexidade Computacional Esperado                                                                                         |
    |-------------|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | Rúbrica C   | Parte da otimização realizada em CPU e parte implementada em GPU, executada no SDumont | 7 zeros |                                                                  |
    | Rúbrica B   | Paralelismo e distribuição em CPU, com parte da otimização feita em GPU, utilizando o SDumont          | 8 zeros                                                        |
    | Rúbrica A   |Paralelismo e distribuição focados principalmente em GPU, com tarefas simples executadas em CPU, utilizando o sistema SDumont  | 9 zeros         |

    ---

    ### Entrega
    Código-fonte funcional, comentado e documentado. Relatório técnico com: 
    
    - Diagnóstico dos gargalos;
    - Proposta de otimização;
    - Hipótese de melhoria;
    - Implementação da hipótese;
    - Comparação de desempenho;
    - Discussão dos resultados.

    ### Bônus por Qualidade

    | Conceito Base | Com Bônus |
    |---------------|-----------|
    | C             | C+        |
    | B             | B+        |
    | A             | A+        |

