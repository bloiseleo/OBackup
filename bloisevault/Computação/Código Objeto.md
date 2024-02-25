Um código objeto é produzido por compiladores e assemblers e podem ser resumidos em blocos de bytes contendo instruções, comandos, estruturas de dados que guiam os compiladores/interpretadores e etc. Nesse caso, existem três tipos de código objeto:
- Relocatable Object File: Código binário e dados organizados de uma forma que podem ser combinados com outros códigos objetos do mesmo tipo para criar um executável.
- Executable Object File: Código binário e dados organizados de maneira executável pelo processador.
- Shared Object File: Tipo especial de relocatable object file que pode ser carregado em memória e linkado dinamicamente, seja em runtime ou seja em load time.

Os compiladores e assemblers geram relocatable object files e, os linkers, geram executáveis. 

Existem diversos tipos de formatos de código objeto. Entretanto, para dar um exemplo, vou abordar o formato *Executable and Linkable Format* ELF para termos um exemplo:

Esse código objeto começa com um *ELF header*. Esse cabeçalho contêm as informações sobre o tamanho da palavra e a ordenação de bytes do sistema que gerou aquele arquivo. O resto das informações nele são informações para possibilitar o linker de parsear e interpretar esse código objeto, como o tamanho do Header, o tipo do object file, o tipo de máquina que o criou e aonde começa a section header table. Dentro da section header table, temos a declaração da localização e o tamanho das seções do object file. O Header está no endereço 0 e a tabela de seções está localizada ao final de todas as seções. No meio, temos as seções de fato.
### Seções
- .text: Contêm o código de máquina do programa compilado
- .rodata: Contêm dados read-only daquele programa, como strings de formatação do printf.
- .data: Variáveis globais de C inicializadas. As variáveis locais ficam na stack, que aparece em RUNTIME.
- .bss: Variáveis globais de C NÃO incializadas. Elas não ocupam espaço no disco nessa etapa.
- .symtab: Tabela de símbolos com informações sobre funções e variáveis globais que foram definidas e referenciadas no código.
- .rel.text: Lista de localizações na seção .text contendo as localizações que precisaram ser alteradas para o linker fazer o seu trabalho. Por padrão, podemos entender que qualquer instrução que utiliza-se de variável global ou chamada de função precisará ser modificada.
- .rel.data: Informação sobre realocação para qualquer variável global que é referenciada e definida pelo módulo.
- .line: Um mapa entre o número de linhas no código em C e instruções em .text.