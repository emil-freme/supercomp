

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


    
??? tip "Plano de aulas"
    | Data       | Tópico                                                  | Conteúdo/Atividade                                                                                                                                                      |
    |------------|----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | 11/08 (seg) | O que são problemas de HPC                                          | Relembrando mapa de memória; O que importa de C++ para nós; Python x C++; Objetivos de aprendizagem; Transcrever códigos Python para C++; Comparar desempenho de linguagens. Primeira atividade |
    | 15/08 (sex) | O que é e como funciona um sistema de HPC                           | Retomando problemas de HPC; Rede, hardware, Slurm, filas, jobs; Sistemas de HPC no Brasil e no mundo; Cluster Franky; Primeiros pedidos de submissão com Slurm; Testes em diferentes filas. Segunda atividade |
    | 18/08 (seg) | Análise de desempenho e projeto                                     | Discussão das entregas anteriores; Introdução ao profiling; Apresentação do projeto do semestre passado e de soluções anteriores; Aplicação de profiling; Lançamento do projeto; Relatório com diagnóstico, hipótese e comparação de desempenho. Terceira Atividade |
    | 22/08 (sex) | Heurísticas e alocação eficiente de memória                         | Aleatoriedade, seeds, nounce; Busca exaustiva, local e com poda; Manipulação de matrizes; Alocação de memória com base no mapa de memória em CPU; Otimização de heurística e estratégia de nounce. Suporte para o projeto 1 |
    | 25/08 (seg) | Paralelismo em CPU com OpenMP                                       | Threads, cores, CPU; Conceitos de região paralela, tasks, sections, parallel for, fork/join; Variáveis privadas e compartilhadas; Scheduling. Suporte para o projeto 1 |
    | 29/08 (sex) | Efeitos colaterais do paralelismo                                   | Racing conditions, variáveis compartilhadas, dependências, recursão; Aplicação no projeto, mapeamento de problemas, hipóteses de otimização, comparação de desempenho. Suporte para o projeto 1 |
    | 02/09 (seg) | Memória distribuída e comunicação com MPI                           | Recapitulação: linguagem, hardware, paralelismo local; Memória distribuída; Comunicação ponto a ponto, coletiva, grupos e comunicadores; Exemplos práticos. Suporte para o projeto 1 |
    | 05/09 (sex) | Integração de MPI com OpenMP                                        | Estratégias de implementação híbrida no projeto; Apresentação de exemplos paralelos; Discussões orientadas. Suporte para o projeto 1 |
    | 08/09 (seg) | Aula estúdio                                                        | Suporte ao projeto 1                                                                                                                                                    |
    | 12/09 (sex) | Palestra NVIDIA                                                     | Evento externo com especialistas NVIDIA                                                                                                                                 |
    | 15/09 (seg) | Aula estúdio                                                        | Último suporte para finalização do projeto. Deadline do projeto às 23h59                                                                                                 |
    | 19/09 (sex) | Devolutiva do Projeto 1                                             | Feedback e discussão das soluções apresentadas                                                                                                                          |
    | 22/09 (seg) | Aula estúdio                                                        | Últimos ajustes para o segundo projeto. Deadline às 23h59                                                                                                                |
    | 25/09–03/10 | Provas Intermediárias                                               | Provas intermediárias com foco nos conteúdos até MPI                                                                                                                    |
    | 06/10 (seg) | Profiling em GPU e apresentação do Projeto 2                        | Alocação de memória na GPU; Warps e SIMD; Controlando divergência; Diagnóstico de desempenho; Lançamento do Projeto 2                                                  |
    | 10/10 (sex) | Otimização de Throughput em GPU                                     | Histogramming, data race, uso de atomic; Estratégias para melhorar throughput                                                                                           |
    | 13/10 (seg) | Técnicas de otimização em GPU (Stencil)                             | Convolução, reuse, tile boundaries, agendamento de threads                                                                                                              |
    | 15/10 (sex) | Estabilidade numérica                                               | Ponto flutuante; Erros de arredondamento; Técnicas de controle de erro                                                                                                  |
    | 24/10 (seg) | MPI + CUDA                                                          | Estratégias híbridas; Gerenciamento de dados; Planejamento e estruturação de comunicação                                                                                 |
    | 27/10 (sex) | Aula estúdio Projeto 2                                              | Suporte final para implementação do Projeto 2                                                                                                                           |
    | 31/10 (seg) | Palestra NVIDIA – OpenACC                                           | Introdução a técnicas com OpenACC                                                                                                                                        |
    | 03/11 (sex) | Aula estúdio Projeto 2                                              | Últimos ajustes; Deadline do Projeto 2                                                                                                                                   |
    | 07/11 (seg) | Devolutiva do Projeto 2                                             | Feedback e discussão dos resultados                                                                                                                                      |
    | 10/11 (sex) | Simulado da prova final                                             | Revisão prática para avaliação                                                                                                                                            |
    | 14/11 (seg) | Aula estúdio final                                                  | Encerramento das atividades; Suporte final                                                                                                                              |


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

??? note "Projeto 2 (dupla) 25%"
    Em construção



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