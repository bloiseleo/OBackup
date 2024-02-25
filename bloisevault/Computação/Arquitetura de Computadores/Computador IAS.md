Esse computador consistia de 1.000 locais de armazenamento chamados de palavras de 40 dígitos. Todos os dados e as instruções ficam armazenados nesses 1000 locais. Tudo está representado em código binário.

## Números
Os números são representados através de 39 bits para o valor e 1 bit de sinal.

## Instruções
Em uma palavra de memória poderiam conter duas instruções: uma à esquerda e outra à direita. A instrução em si consiste de 20 bits e cada instrução contêm um código de operação *opcode* e um endereço de memória de 12 bits para outra parte da memória.

### Registradores
Dentro da CPU, existem alguns registradores que serão utilizados para executar com sucesso as instruções:

- Registrador de Buffer de Memória (MBR): contém um valor que deve ser armazenado na memória ou enviado para um E/S ou um valor que foi recebido da memória ou da E/S. Ou seja, esse buffer guarda valores.
- Registrador de Endereço de Memória (MAR): Contém o endereço da memória onde o valor do MBR será escrito ou o endereço da memória da onde o valor será guardado na MBR. Ou seja, esse buffer guarda o endereço dos valores para onde o MBR deve levar esses valores ou deve recebe-los.
- Registrador de Instrução (IR): Contém o opcode de 8 bits da instrução que está sendo executada.
- Registrador de Buffer de Instrução (IBR): Contém a próxima instrução à ser executada.
- Contador de Programa (PC): Contém o endereço para a próxima instrução.

A cpu é executada em dois ciclos: busca e execução. Na busca, o endereço de memória é buscado e carregado para o IR e o endereço para o MAR.  Depois disso, entra no ciclo de execução, que começa a ocorrer na central de controle, onde o opcode dentro do IR é interpretado e a CC envia os sinais para as operações serem executadas corretamente.

Os opcodes, geralmente, vem acompanhados de uma tabela com suas representações. Por exemplo, a instrução 00000101 representa a operação aritmética de soma.