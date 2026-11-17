# PingPongOS — projeto de Sistemas Operacionais

Repositório de materiais e exercícios da disciplina de Sistemas Operacionais. O projeto usa o PingPongOS, um sistema operacional didático para estudar tarefas, escalonamento, sincronização, temporização e operações de disco.

## Créditos e contexto

O PingPongOS é uma base didática atribuída nos arquivos a **Carlos A. Maziero, DINF/UFPR**. Este repositório reúne essa base, códigos de exercícios e alterações feitas no contexto da disciplina. A presença do projeto aqui não implica autoria original do PingPongOS pelo estudante.

## Conteúdo

| Arquivos | Tema |
| --- | --- |
| `ppos.h`, `ppos-data.h`, `ppos-core-globals.h`, `queue.h` | Interface do sistema, estruturas de tarefas e filas |
| `ppos-core-aux.c` | Código auxiliar e implementação de escalonamento/preempção presente neste checkout |
| `pingpong-tasks1.c`, `pingpong-tasks2.c`, `pingpong-tasks3.c` | Criação e execução básica de tarefas |
| `pingpong-scheduler.c`, `pingpong-contab-prio.c`, `pingpong-scheduler-srtf.c` | Escalonamento por prioridade e SRTF |
| `pingpong-preempcao.c`, `pingpong-preempcao-stress.c`, `pingpong-dispatcher.c` | Preempção, dispatcher e testes de carga |
| `pingpong-join.c`, `pingpong-sleep.c` | Espera por tarefas e temporização |
| `pingpong-semaphore.c`, `pingpong-barrier.c`, `pingpong-mqueue.c` | Semáforos, barreiras e filas de mensagens |
| `pingpong-racecond.c`, `pingpong-prodcons.c` | Condições de corrida e problema produtor/consumidor |
| `pingpong-disco1.c`, `pingpong-disco2.c`, `disk-driver.h`, `ppos-disk-manager.h` | Exercícios e interfaces de gerenciamento de disco |
| `signal.c`, `signal-test.c`, `timer.c` | Experimentos com sinais e temporizadores |
| Arquivos `.txt` | Saídas de referência ou materiais associados aos exercícios |
| Arquivos `.o`, `disk.dat`, `ppos-teste` | Objetos compilados, imagem de disco e executável presentes no diretório |

## Compilação disponível

O `Makefile` define um único alvo de compilação, `preempcao`. Ele usa GCC e os objetos pré-compilados `ppos-all.o` e `queue.o`:

```sh
make preempcao
```

O comando gera `ppos-teste`. Para executá-lo em ambiente Unix-like:

```sh
./ppos-teste
```

Para remover o executável gerado:

```sh
make clean
```

O código depende de recursos POSIX, incluindo `ucontext`, sinais e temporizadores. O alvo atual compila apenas `ppos-core-aux.c` com `pingpong-preempcao.c`; os demais exercícios não têm alvos próprios neste `Makefile` e podem exigir arquivos ou configurações adicionais.

## Observações

- O cabeçalho `ppos.h` alerta que a implementação foi planejada para sistemas Unix-like, como Linux, BSD e macOS.
- Os arquivos `.txt` são registros/materiais associados, não documentação centralizada da implementação.
- O diretório contém artefatos pré-compilados. Para reproduzir a compilação, use as versões de GCC e bibliotecas compatíveis com os objetos fornecidos.
