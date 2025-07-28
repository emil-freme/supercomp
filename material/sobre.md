

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
    | 11/ago (seg) | Aula 01  | Problemas de HPC; mapa de memória; Python × C++; desempenho; objetivos da disciplina  | Transcrição de códigos Python para C++; comparação de desempenho entre linguagens.|
    | 15/ago (sex) | Aula 02  | Sistemas de HPC; rede, hardware, filas, jobs; SLURM; clusters no Brasil e no mundo  | Testes com SLURM no Cluster Franky; comparação de desempenho em diferentes filas.|    
    | 18/ago (seg) |  Aula 03  | Diagnóstico de código; profiling; discussão de soluções anteriores; introdução ao Projeto 1   | Aplicar profiling; relatório com gargalos, hipóteses de melhoria e comparação de desempenho. |
    | 22/ago (sex) | Aula 04  | Aleatoriedade, heurísticas, alocação de memória  | Ajustes em heurísticas, estrutura de dados e uso da memória de forma eficiente. |   
    | 25/ago (seg) | Aula 05  | Paralelismo em CPU; threads; cores; OpenMP; variáveis privadas e compartilhadas; scheduling  | Paralelismo com OpenMP; compartilhamento entre threads; efeitos do scheduler. |
    | 29/ago (sex) | Aula 06  | Efeitos colaterais do paralelismo; racing conditions; dependências; recursão | Aplicação no projeto: mapear problemas, levantar hipóteses de otimização e comparar desempenho. |
    | 02/set (seg) | Aula 07  | Memória distribuída; comunicação com MPI; ponto-a-ponto e coletiva; grupos e comunicadores    | Comentários e direcionamentos sobre entrega parcial do projeto |
    | 05/set (sex) | Aula 08  | Estratégias híbridas MPI + OpenMP  | Discussão de implementações no projeto |
    | 08/set (seg) | Aula 09  | Aula estúdio | Suporte ao Projeto  |
    | 12/set (sex) | Aula 10  | Palestra NVIDIA - CUDA |Palestra NVIDIA - CUDA   |
    | 15/set (seg) | Aula 11  | Aula estúdio  | Finalização do Projeto 1 |
    | 19/set (sex) | Aula 12  | Devolutiva do Projeto | Discussão das soluções apresentadas e feedback.|
    | 22/set (seg) | Aula 13  | Aula estúdio | Últimos ajustes no Projeto 1. Entrega final até 23h59. |
    | 25/set–03/out| —        | Provas intermediárias | Avaliação dos conteúdos até MPI.|
    | 06/out (seg) | Aula 14  | Profiling em GPU; warps e SIMD; divergência; alocação de memória  | Estudo de caso aplicado   |
    | 10/out (sex) | Aula 15  | Histogramming; data race em GPU; atomic; throughput | Estudo de caso aplicado.                 |
    | 13/out (seg) | Aula 16  | Técnicas stencil; convolução; tile boundaries; agendamento de threads                   | Estudo de caso aplicado. |
    | 15/out (sex) | Aula 17  | Estabilidade numérica; ponto flutuante; controle de erro | Estudo de caso aplicado.            |
    | 24/out (seg) | Aula 18  | Estratégias híbridas com MPI + CUDA; gerenciamento de dados | Estudo de caso aplicado.            |
    | 27/out (sex) | Aula 19  | Apresentação do Projeto 2   | Conversa sobre estratégias de otimização |
    | 31/out (seg) | Aula 20  | Aula estúdio  |  Aula estúdio |
    | 03/nov (sex) | Aula 21  | Palestra NVIDIA – OpenACC  | Introdução ao OpenACC. |
    | 07/nov (seg) | Aula 22  | Aula estúdio  | Aula estúdio  |
    | 10/nov (sex) | Aula 23  | Simulado da prova final       | Revisão prática. |
    | 14/nov (seg) | Aula 24  | Encerramento da disciplina. | **Entrega final do Projeto até 23h59.** |


??? note "Atividades (Individual) 15%"

    | **Atividade**                                 | **Entrega**        | **Peso (pontos)** |
    | ----------------------- --------------------- | ------------------ | ----------------- |
    | Responder ao questionário de pesquisa         | A definir          | 0,95              |
    | Participar da entrevista voluntária sobre a disciplina | A definir | 1,90              |
    | Transcrever códigos Python para C++ e comparar desempenho (CPU)| 14/08  | 1,20         |
    | Primeiros pedidos de submissão com SLURM + testes em filas (CPU)   | 15/08  | 1,20     |
    | Paralelismo em CPU                                 | 25/08              | 1,20         |
    | Paralelismo Distribuído em múltiplos nós (CPU)     |  02/09              | 1,20         |
    | Data race em GPU                                   | 10/10              | 2,45         |
    | Convolução em GPU                                  | 13/10              | 2,45         |
    | Gerenciamento de dados em computação paralela e distribuída em GPU | 24/10  | 2,45     |



??? note "Projeto 1 (Grupo) 15%"

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


??? note "Projeto 2 (Grupo) 15%"
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

