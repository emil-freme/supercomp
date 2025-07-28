

## Comandos SLURM

### Principais recursos que você pode pedir com `srun`

| O que pedir                   | Opção do `srun`                | Exemplo                          |
| ----------------------------- | ------------------------------ | -------------------------------- |
| Número de tarefas (processos) | `--ntasks` ou `-n`             | `--ntasks=2`                     |
| CPUs por tarefa               | `--cpus-per-task`              | `--cpus-per-task=2`              |
| Memória total ou por CPU      | `--mem`, `--mem-per-cpu`       | `--mem=4G` ou `--mem-per-cpu=2G` |
| Tempo de execução             | `--time=DD-HH:MM:SS`            | `--time=01:12:49`               |
| Número de nós                 | `--nodes`                      | `--nodes=2`                      |
| Nó específico                 | `--nodelist`                   | `--nodelist=compute13`           |
| GPUs                          | `--gpus` ou `--gres=gpu:<num>` | `--gpus=1` ou `--gres=gpu:2`     |
| Partição (fila)               | `--partition` ou `-p`          | `--partition=gpu`                |
| Sessão interativa             | `--pty bash`                   | `--pty bash`                     |

**Exemplos**

Pedido simples de execução de tarefa para o SLURM
`srun --nodelist=compute10 --partition=normal --ntasks=1 --pty bash`
--srun: Comando SLURM para executar tarefas 
--nodelist=compute10: força o SLURM a alocar exatamente esse nó.
--partition=normal: indica a partição à qual o nó pertence.
--ntasks=1: pede uma tarefa.
--pty bash: pede um terminal dentro do nó.


Pedido sem especificar o nó exato:
`srun --partition=normal --ntasks=1 --pty bash`

Pedido com varias tasks para executar seu programa direto:
`srun --partition=normal --ntasks=4 ./meu_programa_paralelo`

Ótima pergunta! Com o comando `srun`, você pode **pedir ao SLURM recursos de computação específicos** — como número de tarefas, CPUs, memória, tempo de execução, GPUs, nós específicos e muito mais.

Claro! Aqui está o **resumo equivalente para o `sbatch`**, seguindo o mesmo formato que você usou para o `srun`:


### Principais recursos que você pode pedir com `sbatch`

| O que pedir                   | Opção do `sbatch` (no script)  | Exemplo dentro do script                     |
| ----------------------------- | ------------------------------ | -------------------------------------------- |
| Nome do job                   | `--job-name`                   | `#SBATCH --job-name=teste%j`                   |
| Número de tarefas (processos) | `--ntasks` ou `-n`             | `#SBATCH --ntasks=2`                         |
| CPUs por tarefa               | `--cpus-per-task`              | `#SBATCH --cpus-per-task=2`                  |
| Memória total ou por CPU      | `--mem`, `--mem-per-cpu`       | `#SBATCH --mem=4G` ou `--mem-per-cpu=2G`     |
| Tempo de execução             | `--time=DD-HH:MM:SS`           | `#SBATCH --time=01:12:49`                    |
| Número de nós                 | `--nodes`                      | `#SBATCH --nodes=2`                          |
| Nó específico                 | `--nodelist`                   | `#SBATCH --nodelist=compute13`               |
| GPUs                          | `--gpus` ou `--gres=gpu:<num>` | `#SBATCH --gpus=1` ou `#SBATCH --gres=gpu:2` |
| Partição (fila)               | `--partition` ou `-p`          | `#SBATCH --partition=gpu`                    |
| Saída padrão (log)            | `--output`                     | `#SBATCH --output=saida%j.txt`                 |
| Log de Erro do sistema        | `--error`                      | `#SBATCH --error=erro%j.txt`                   |

**Exemplos**

**Arquivo:** `job1.slurm`

```bash
#!/bin/bash
#SBATCH --job-name=teste%j
#SBATCH --partition=normal
#SBATCH --ntasks=1
#SBATCH --time=00:10:00
#SBATCH --output=saida%j.txt

./meu_programa
```

Submeter com:

```bash
sbatch job1.slurm
```


## Comandos gerais do SLURM

| Finalidade                            | Comando                                      | Exemplo                                           |
| ------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| Ver status das partições e nós        | `sinfo`                                      | `sinfo -N -l`                                     |
| Ver detalhes de um nó específico      | `scontrol show node`                         | `scontrol show node compute24`                         |
| Ver detalhes de uma partição          | `scontrol show partition`                    | `scontrol show partition normal`                    |
| Ver todos os jobs ativos              | `squeue`                                     | `squeue`                                          |
| Ver seus próprios jobs                | `squeue -u <usuário>`                        | `squeue -u liciascl`                              |
| Ver detalhes de um job                | `scontrol show job`                          | `scontrol show job 12345`                         |
| Cancelar job em execução ou na fila   | `scancel`                                    | `scancel 12345`                                   |
| Cancelar todos os seus jobs           | `scancel -u <usuário>`                       | `scancel -u liciascl`                             |



### Ver todos os nós com status detalhado

```bash
sinfo -N -l
```
> Útil para ver quais nós estão **idle, alocados, down ou drain**.

### Ver informações completas do nó `compute24`

```bash
scontrol show node compute24
```
> Mostra: memória total e usada, CPUs alocadas, jobs em execução, estado (`IDLE`, `ALLOCATED`, etc.).

### Ver configurações de uma partição especifica

```bash
scontrol show partition normal
```
> Mostra: tempo máximo de job, número de nós, limites de memória/CPU, GPUs, estado da fila.

### Ver jobs no sistema

```bash
squeue
```
> Mostra todos os jobs na fila e em execução com status `R` (running), `PD` (pending), etc.

### Ver só os jobs da usuária `liciascl`

```bash
squeue -u liciascl
```
> Útil para depurar seus próprios jobs (ID, partição, status, tempo, nó, etc.)


### Ver informações completas de um job específico

```bash
scontrol show job 12345
```
> Mostra: usuário, partição, CPUs/nós alocados, prioridade, estado, tempo usado, comando enviado.


### Cancelar job com ID `12345`

```bash
scancel 12345
```
> Útil se o job travou ou está consumindo recursos indevidamente.

### Cancelar **todos os seus jobs**

```bash
scancel -u $USER
```
> Cancela em lote — ótimo em caso de erro em scripts ou submissões mal feitas.


Para mais consulte a documentação oficial em https://slurm.schedmd.com/documentation.html