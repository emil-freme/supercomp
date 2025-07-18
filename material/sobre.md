

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
    | 11/ago (seg) | Aula 01  | Problemas de HPC; mapa de memória; Python × C++; desempenho; objetivos da disciplina                                        | Transcrição de códigos Python para C++; comparação de desempenho entre linguagens. **Entrega até quinta-feira, 23h59.**                                        |
    | 15/ago (sex) | Aula 02  | Sistemas de HPC; rede, hardware, filas, jobs; SLURM; clusters no Brasil e no mundo                                          | Testes com SLURM no Cluster Franky; comparação de desempenho em diferentes filas. **Entrega segunda, até 08h30.**                                         |
    | 18/ago (seg) | Aula 03  | Diagnóstico de código; profiling; discussão de soluções anteriores; introdução ao Projeto 1                                 | Aplicar profiling; relatório com gargalos, hipóteses de melhoria e comparação de desempenho. **Entrega até quinta-feira, 23h59.**                              |
    | 22/ago (sex) | Aula 04  | Aleatoriedade, heurísticas, manipulação de matrizes, alocação de memória                                                    | Suporte ao Projeto 1: ajustes em heurísticas, estrutura de dados e uso da memória de forma eficiente.                                                          |
    | 25/ago (seg) | Aula 05  | Paralelismo em CPU; threads; cores; OpenMP; variáveis privadas e compartilhadas; scheduling                                 | Suporte ao Projeto 1: paralelismo com OpenMP; compartilhamento entre threads; efeitos do scheduler.                                                            |
    | 29/ago (sex) | Aula 06  | Efeitos colaterais do paralelismo; racing conditions; dependências; recursão                                                | Aplicação no projeto: mapear problemas, levantar hipóteses de otimização e comparar desempenho.                                                                |
    | 02/set (seg) | Aula 07  | Memória distribuída; comunicação com MPI; ponto-a-ponto e coletiva; grupos e comunicadores                                  | Suporte ao Projeto 1: consolidação do conteúdo com exemplos práticos usando MPI.                                                                               |
    | 05/set (sex) | Aula 08  | Estratégias híbridas MPI + OpenMP                                                                                           | Discussão de implementações paralelas no projeto; exemplos práticos.                                                                                           |
    | 08/set (seg) | Aula 09  | Aula estúdio                                                                                                                | Suporte ao Projeto 1.                                                                                                                                           |
    | 12/set (sex) | Aula 10  | Palestra NVIDIA - CUDA                                                                                                      |Palestra NVIDIA - CUDA   |
    | 15/set (seg) | Aula 11  | Aula estúdio                                                                                                                | Finalização do Projeto 1. **Entrega final até 23h59.**                                                                                                          |
    | 19/set (sex) | Aula 12  | Devolutiva do Projeto 1                                                                                                     | Discussão das soluções apresentadas e feedback.                                                                                                                |
    | 22/set (seg) | Aula 13  | Aula estúdio                                                                                                                | Últimos ajustes no Projeto 1. **Deadline final até 23h59.**                                                                                                     |
    | 25/set–03/out| —        | Provas intermediárias                                                                                                       | Avaliação dos conteúdos até MPI.                                                                                                                               |
    | 06/out (seg) | Aula 14  | Profiling em GPU; warps e SIMD; divergência; alocação de memória                                                            | Estudo de caso aplicado; Apresentação do Projeto Extra.                                                                                                            |
    | 10/out (sex) | Aula 15  | Histogramming; data race em GPU; atomic; throughput                                                                         | Estudo de caso aplicado.                                                                                                                                       |
    | 13/out (seg) | Aula 16  | Técnicas stencil; convolução; tile boundaries; agendamento de threads                                                       | Estudo de caso aplicado.                                                                                                                                       |
    | 15/out (sex) | Aula 17  | Estabilidade numérica; ponto flutuante; controle de erro                                                                    | Estudo de caso aplicado.                                                                                                                                       |
    | 24/out (seg) | Aula 18  | Estratégias híbridas com MPI + CUDA; gerenciamento de dados                                                                 | Estudo de caso aplicado.                                                                                                                                       |
    | 27/out (sex) | Aula 19  | Apresentação do Projeto 2; conversa com pesquisador Glauco Endrico Moura de Lima                                           | Conversa com pesquisador.                                                                                                                              |
    | 31/out (seg) | Aula 20  | Aula estúdio                                                                                                                | Suporte final ao Projeto 2.                                                                                                                                    |
    | 03/nov (sex) | Aula 21  | Palestra NVIDIA – OpenACC                                                                                                   | Introdução ao OpenACC. **Entrega final do Projeto 2 até 23h59.**                                                                                               |
    | 07/nov (seg) | Aula 22  | Devolutiva do Projeto 2                                                                                                     | Análise de desempenho e feedback final.                                                                                                                        |
    | 10/nov (sex) | Aula 23  | Simulado da prova final                                                                                                     | Revisão prática.                                                                                                                       |
    | 14/nov (seg) | Aula 24  | Aula estúdio final                                                                                                          | Encerramento da disciplina. **Entrega final do Projeto 2 até 23h59.**                                                                                          |


??? note "Atividades (Individual) 5%"

    | **Atividade** | **Objetivos Atendidos** | **Descrição** | **Pontos** |
    | --- | --- | --- | --- |
    | Transcrever códigos Python para C++ e comparar desempenho | Obj 1, Obj 3, Obj 5 | Desenvolvem algoritmos em diferentes linguagens e analisam desempenho, reforçando noções de eficiência e impacto da linguagem. | 1 |
    | Primeiros pedidos de submissão com SLURM + testes em diferentes filas/hardwares | Obj 4, Obj 6 | Planejamento da execução em HPC, usando recursos do SO e observando como configurações de hardware influenciam o desempenho. | 2 |
    | Profiling + relatório com diagnóstico, hipótese, implementação e análise de desempenho | Obj 1, Obj 4, Obj 5 | Envolve identificar gargalos, propor e testar melhorias, com análise do desempenho final | 2 |

??? note "Projeto 1 (Individual) 15%"

    ### **Mineração de criptomoedas**

    #### Critérios de Avaliação

    **Rubrica D**

    - Executa o código minerador **síncrono**, no cluster **Franky**
    
    - Com dificuldade **5 zeros**, com pelo menos **5 gerações diferentes de `sync_gen`**
    
    - Gera **relatório com explicação, tempo de execução e recursos SLURM utilizados**

    **Rubrica D+**
    
    - Mesmos critérios da D, mas com dificuldade **7 zeros**

    **Rubrica C**
    
    - Executa o código minerador **assíncrono**, no cluster **SDumont**
    
    - Com dificuldade **5 zeros**, com pelo menos **5 gerações diferentes de `async_gen`**
    
    - Gera **relatório com explicação, tempos de execução e recursos SLURM utilizados**

    **Rubrica B**
    
    - Executa o código minerador **assíncrono**, no cluster **SDumont**
    
    - Com dificuldade **6 zeros**, com pelo menos **5 gerações diferentes de `async_gen`**
    
    - Usa pelo menos **uma estratégia de otimização em CPU** (MPI ou OpenMP)
    
    - Relatório completo com análise de desempenho, explicação das diferenças entre ambientes

    **Rubrica B+**
    
    - Mesmos critérios da B, mas usando **as duas estratégias de otimização**: MPI e OpenMP

    **Rubrica A**
    
    - Executa o código minerador **assíncrono**, no cluster **SDumont**
    
    - Com dificuldade **7 zeros**, com pelo menos **5 gerações diferentes de `async_gen`**
    
    - Realiza **mineração em GPU**
    
    - Relatório com análise detalhada dos ambientes, desempenho e configuração

    **Rubrica A+**
    
    - Como a A, mas com **estratégia híbrida**: partes do código em CPU, partes em GPU
    
    - Apresenta **análise comparativa entre as estratégias, ambientes e arquiteturas**


    #### Objetivos de Aprendizagem Relacionados

    | **Objetivo** | **Descrição** | **Relação com o Objetivo de Aprendizagem** |
    | --- | --- | --- |
    | Obj 1 | Desenvolver algoritmos usando computação paralela/distribuída para ganhos de desempenho | Rúbrica B e B+ |
    | Obj 2 | Aplicar estrutura lógica de computação distribuída para desenvolvimento de algoritmos multitarefas | Rúbrica B+ e A+ |
    | Obj 3 | Usar GPGPU para computação numérica e comparar com soluções baseadas em CPU | Rúbrica A e A+. |
    | Obj 4 | Planejar e projetar sistemas de computação de alto desempenho | Rúbricas D, C, B e A |
    | Obj 5 | Analisar a complexidade de algoritmos paralelos e a eficiência de uma implementação | Rúbricas B e A |
    | Obj 6 | Aplicar recursos específicos de sistemas operacionais para otimizar desempenho | Rúbricas C, B e A |
    | Obj 7 | Desenvolver aplicações com protocolos otimizados para paralelização | Rúbricas B e A |

??? note "Projeto 2 (grupo) 25%"
    ## Parceria com o Laboratório de Biofísica Molecular e Biologia Estrutural da UFABC 

    Aplicação: Reclassificação de poses de docking proteína-ligante utilizando Graph Neural Networks com mapa de contato proteína-ligante.

    ### Contexto

    O processo de *drug discovery* envolve diversas etapas, entre elas o *docking* proteína-ligante, que é computacionalmente intensivo devido à necessidade de avaliar milhares de conformações possíveis e calcular interações intermoleculares complexas. Softwares tradicionais de docking têm limitações em prever afinidades com precisão. A reclassificação com GNNs oferece uma abordagem complementar, baseada em aprendizado profundo.

    ### Complexidade Computacional

    1. **Espaço tridimensional e conformacional**: milhões de combinações entre poses e proteínas.
    2. **Modelagem de interações**: cálculo de forças como Van der Waals, hidrogênio, hidrofóbicas, etc.
    3. **Avaliação de múltiplas poses**: necessidade de pontuar e ranquear resultados.
    4. **Volume de dados**: alta demanda computacional e paralelização.

    ### **Benefícios da Computação de Alto Desempenho (HPC)**

    A aplicação de HPC é essencial para viabilizar esse tipo de análise em escala:

    - **Paralelização**: clusters e supercomputadores permitem a execução simultânea de milhares de *docking runs*, distribuindo tarefas entre múltiplas CPUs ou GPUs.
    - **Aceleração com GPU**: redes neurais aplicadas à reclassificação de poses (ex: GNNs com mapas de contato proteína-ligante) se beneficiam diretamente de arquiteturas paralelas como CUDA.
    - **Distribuição e paralelização**: algoritmos que fazem varreduras sobre múltiplos ligantes ou simulações moleculares em réplicas independentes podem ser implementados com paralelismo híbrido (CPU+GPU), distribuindo o processamento por nós computacionais distintos.

    ### Rúbrica de Avaliação

    | Nível       | Critérios Técnicos                                                                 | Desempenho Esperado                                                                                         |
    |-------------|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | Rúbrica C   | Parte do algoritmo implementada na GPU; sem alteração no número de pontos           | Código roda em GPU.                                                                 |
    | Rúbrica B   | Otimizações efetivas; processa ao menos 2× os pontos do grafo original              | Algoritmo reestruturado com ganho perceptível.                                                             |
    | Rúbrica A   | Uso de múltiplas GPUs; várias rotinas paralelizadas; >2× pontos do grafo original   | Execução distribuída e eficiente com bom uso de recursos paralelos.                                        |

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

    ---

    ### Objetivos de Aprendizagem Relacionados

    | Objetivo | Descrição                                                                                                   | Relação com o Projeto                                  |
    |----------|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
    | Obj 1    | Desenvolver algoritmos com paralelismo/distribuição para ganhos de desempenho                              | Implementação em GPU ou GPU+CPU                        |
    | Obj 2    | Aplicar estruturas lógicas de computação distribuída                                                       | Possibilidade de usar MPI-CUDA                         |
    | Obj 3    | Usar GPGPU e comparar com CPU                                                                              | Relatório com comparação quantitativa                  |
    | Obj 4    | Planejar e projetar sistemas HPC                                                                           | Uso de SLURM, estratégias de execução e compilação     |
    | Obj 5    | Analisar complexidade e eficiência                                                                         | Análise de desempenho e escalabilidade                 |
    | Obj 6    | Usar recursos do sistema operacional para otimização                                                       | Gerenciamento de GPU, blocos, threads, etc.            |
    | Obj 7    | Desenvolver aplicações com protocolos otimizados para paralelização                                        | Uso de CUDA e, opcionalmente, MPI para multi-GPU       |
    



??? note "Projeto Extra (Individual) 5%"

    ### Projeto Extra - **Extensão do Projeto 1**

    > **Somente para quem entregou até a Rúbrica B do Projeto 1 dentro do prazo.**

    Passar o Projeto 1 para GPU e relatar diferenças de desempenho e otimização.

    **Rubrica A**
    
    - Código minerador **assíncrono**, cluster **SDumont**
    
    - Dificuldade **8 zeros**, com pelo menos **5 gerações `async_gen`**
    
    - Estratégia **híbrida CPU + GPU**
    
    - **Relatório completo comparando entre Projeto 1 e Projeto Extra**

    **Rubrica A+**
    
    - Mesmos critérios da A
    
    - Estratégia **distribuída com múltiplas GPUs**
    
    - **Relatório completo comparando entre Projeto 1 e Projeto Extra**


    | **Objetivo** | **Descrição** | **Relação com o Objetivo de Aprendizagem** |
    | --- | --- | --- |
    | Obj 1 | Desenvolver algoritmos usando computação paralela/distribuída | Projeto deve ser resolvido em GPU, podendo ser híbrido CPU-GPU ou Multi GPU |
    | Obj 2 | Aplicar lógica de computação distribuída | Rúbrica A+ |
    | Obj 3 | Usar GPGPU e comparar com CPU | Comparação entre o projeto 1 desenvolvido em CPU e a implementação em GPU  |
    | Obj 4 | Planejar execução em ambiente HPC | Alocação via SLURM, flags de compilação, estratégias para GPU |
    | Obj 5 | Analisar a eficiência de uma implementação paralela | Diagnóstico, otimizações e comparação de desempenho no relatório |
    | Obj 6 | Usar recursos do sistema operacional para desempenho | Uso de SLURM, memória GPU, controle de blocos e threads |
    | Obj 7 | Desenvolver aplicações com protocolos otimizados para paralelização | Implementação de otimizações em GPU ou MultiGPU |