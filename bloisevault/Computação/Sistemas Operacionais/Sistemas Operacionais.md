Um sistema operacional é o sistema responsável por abstrair a camada do Hardware enquanto provê uma API fácil e intuitiva para os usuários e processos que rodam sobre ele. A forma que ele gerencia esses recursos é o principal fator que o categoriza:

### Batch O.S
Um sistema de Batch é um sistema que realiza uma tarefa de cada vez e cada tarefa(job). Nesse tipo de sistema, o Job é escrito em algum dispositivo offline (punchcard) e é submetido para o operador do computador. Os Jobs com requesitos similares são agrupados e executados como um grupo para acelerar o processo. Cada job então é organizado no que é chamado de **batch**, que é o conjunto de jobs com necessidades similares.

Cada batch é executado simultaneamente e processado levando o seguinte em consideração:

- Um Job é uma unidade que consiste em uma sequência de comandos, dados e programas.
- O programa é executado na sequência que é escrito.
- Os Jobs são guardados em memória e executados sem a necessidade para inputs.
- Quando o Job completa, o sistema operacional libera a memória.

### Multiprogramming O.S 
Um sistema operacional de multiprogramação é um sistema com a possibilidade de carregar diversos programas na memória principal e executá-los concorremente. O computador carrega diversos Jobs dentro da memória RAM e o sistema operacional consegue selecionar o trabalho que será executado. Quando o mesmo para de usar a CPU por qualquer motivo, o computador consegue atribuir para outro trabalho o uso da mesma. Dessa forma, temos o uso eficiente da CPU e dos recursos da máquina.

### Multiprocessing O.S
Um sistema operacional de multiprocessamento é um sistema que trabalha com mais de 1 CPU ao mesmo tempo. Vários processadores trabalham paralelamente para realizar uma ou mais tarefas. O principal objetivo desse sistema é aumentar a velocidade de execução.
- Alocação de uso das CPUs é performada pelo sistema operacional 
Existem dois tipos de O.S dentro dessa categoria:
- Simétricos: Os simétricos são sistemas operacionais onde cada processador compartilha o mesmo BUS, input/output, memória principal e sistema operacional. Cada processo é atribuido à CPU que está menos ocupada (bem simples).
- Assimétricos: Os assimétricos são sistemas onde há uma relação de master/slave entre os processadores. Um processador age como mestre dos outros e atribui as tarefas para os mesmos.

### Multi-Tasking O.S
Um sistema operacional multitasking é um multiprogramming o.s com um Round-Robin Scheduling Algorithm para organizar os Jobs. Ele pode executar diversos processos ao mesmo tempo.

### Time-Sharing O.S
Cada tarefa tem um determinado tempo para ser executada. Logo, cada tarefa ou usuário recebe esse tempo, o processador faz o processamento e é interrompido ou acaba o processo. Se ele não acabou, ele passa para o próximo proceso/usuário.