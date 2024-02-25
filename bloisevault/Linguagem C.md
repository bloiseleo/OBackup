Essa linguagem é compilada e apresenta como principal paradigma o paradigma estruturado. Todos os comentários são feitos com /* Aqui dentro não é compilado \*/

Ela foi criada em 1972 e, em 1989, foi criado o ANSI C. O ANSI C ainda é C, porém tem uma série de bibliotecas novas, compatibilidades com C++ e etc.
### Compilação
O processo de compilação transforma o código fonte em código de máquina binário nativo de máquina em que foi compilado. O processo de compilação passa por algumas etapas que serão discutidas abaixo.
#### Pré Processamento
O pré processamento é a etapa onde todas as instruções que começam com # são processadas e convertidas para um código intermediário onde esses trechos não existem. Nessa etapa, os comentários são removidos e os macros são processados e expandidos.
- Um macro é a definição de um valor ou expressão, que em C é feito através da sintaxe `#define ...`. Para utilizar esse macro, podemos utilizar o nome definido por ele em nosso programa. A expansão do mesmo é feita pelo pré-processador, que encontra esses macros e os substitui pelo valor pré-determinado anteriormente.
- O escopo do #define é no arquivo ao qual ele foi definido. Logo, acessar essa diretiva em outro código fonte não pode ser realizado. Para fazer isso, ele precisa ser definido em um header file. 
Além disso, também é possível realizar a inclusão de arquivos pré-escritros em nosso programa durante essa etapa. Nesse caso, esses arquivos costumam ter funções, macros, enumerações, estruturas e outras coisas que podemos utilizar no decorrer do nosso programa. Esses arquivos podem ser tanto derivados da biblioteca padrão quanto produzidos por outras pessoas.
- Um dos exemplos mais comuns é o arquivo `stdio.h`. Esse arquivo contêm funções como `printf`e `scanf`que são utilizadas para lidar com input e output.
#### Fase de Compilação
Depois que o pré-processamento é realizado, um arquivo intermediário com a extensão `.i`é gerado. Esse arquivo então pode ser compilado de fato para Assembly. O compilador é o software que irá ser responsável por essa etapa. Nela, o código tem a sua sintaxe analisada e nos aponta erros de sintaxe ou avisa sobre possíveis problemas. Por fim, um código `.s`é produzido contendo as intruções Assembly.
#### Fase de Assembling
Essa fase utiliza todos os `.s`gerados e os converte para a forma quase final, que é a forma binária. Essa etapa gera um código chamado de código objeto. Esse código objeto, entretanto, ainda não está pronto para ser executado totalmente.

#### Fase de Linking
Essa fase utiliza o código objeto e realiza o processo de inclusão dos arquivos que incluimos no nosso código fonte. Esse código que é incluido já está compilado. Depois que o código é completamente linkado com as bibliotecas necessárias, ele pode ser executado. Portanto, o programa agora já está em sua forma executável.

- Esse processo pode ocorrer tanto durante a compilação quanto na parte de carregamento para memória.


Para fazer esse processo, o *linker* irá precisar fazer a resolução de símbolos. Essa resolução é a procura por símbolos e, ao achar, encontrar uma definição desse símbolo. Além disso, ele também irá precisar fazer a realocação. Os compiladores e assemblers geram seções de código e dados que começam no endereço 0. O linker vai realocar essas seções associando a localização de memória com cada definição de símbolo e modificar todas as referências para esses símbolos 

Para saber mais, [[Código Objeto]]

O compilador mais famoso para o C é o [GCC](https://gcc.gnu.org/). Ele pode compilar diversas outras linguagens e inclui as bibliotecas padrões de C.
## Inclusão de Arquivos

Para diminuir a necessidade a resolução de problemas já resolvidos, uma série de códigos já foram escritos para resolver determinados problemas. Esses códigos, em si, estão em diversos arquivos. Para facilitar a compreensão e entrega, podemos reunir todo código que faça sentido dentro de uma biblioteca. Logo, uma biblioteca é um conjunto de arquivos que, por sua vez, contêm funções, variáveis, rotinas e todo tipo de coisa que podemos reutilizar em outros lugares.

Para facilitar o entendimento, podemos separar essas bibliotecas em duas categorias: padrões e externas.

- As bibliotecas padrões são bibliotecas que vem em conjunto com os compiladores. Essas bibliotecas são as definições padrões ISO. Elas ficam guardadas nos diretórios padrões definidos pelos compiladores. Atualmente, existem por volta de 30 bibliotecas padrões para C.

- As bibliotecas que não são ISO podem ser consideradas externas. Essas bibliotecas podem ser derivadas de um fornecedor específico, escritas por você mesmo ou qualquer outra pessoa.

As bibliotecas padrões não necessitam de instalação, porém as bibliotecas externas necessitam de algum outro processo de instalação que irá depender de cada caso.

Somente header files podem ser incluídos. Quando o pré-processador encontra esse arquivo, ele inclui o conteúdo do arquivo a partir da linha daquele determinado macro.
```
#include <path_spec> // system
#include "path_spec" // user-defined
```

O path_spec deve levar à um determinado arquivo existente. Ele pode ser precedido por um caminho de diretório, mas sempre deve levar à um arquivo existente. A diferença entre system e user-defined includes é determinada pela busca por esses arquivos:

User-defined:
- Mesmo diretório do arquivo que está incluindo.
- Quando um arquivo que foi incluido inclui outro arquivo, a busca começa na ordem reversa dos includes.
- Pelos caminhos especificados com a flag /I para o compilador.
- Nos caminhos especificados pela variável de ambiente INCLUDE.
System:
- Pelos caminhos especificados com a flag /I para o compilador.
- Nos caminhos especificados pela variável de ambiente INCLUDE.

Quando um arquivo é incluido, todo o conteúdo dele é colocado dentro do arquivo a partir da declaração daquele arquivo.
## Entrada
O ponto de entrada de qualquer pessoa é a função `main`. Essa função tem a seguinte assinatura completa:

```
int main(int argc, char * const argv[]) {}
```
Essa função é chamada no momento em que o programa começa.

## Variáveis
As variáveis são espaços reservados na memória para armazenar os valores durante a execução do programa. Essas variáveis precisam ser tipadas. Além disso, as variáveis precisam estar declaradas antes de ser usadas e, todas elas, possuem um determinado escopo. O escopo são os locais onde essa variável pode ser acessada. Podemos reduzir isso à dois tipos:
- Globais: Estão acessíveis a todos os escopos do programa. Para declará-las, precisamos declará-las no começo do arquivo antes das funções e fora de todas elas. Além disso, elas seguem o padrão de declaração das variáveis.
- Local: Estão acessíveis somente dentro do bloco nas quais ela foi declarada.
Além disso, o nome da variável pode ser chamado de identificador. Esse identificador não pode ser um número e/ou ser um \_. Ela também é case sensitive.

Um outro ponto que é interessante de ser abordado é a capacidade de utilizar variáveis definidas em outros arquivos. Para fazer isso, declaramos aquela variável e, antes do tipo e nome dela, dizemos que ela é **external**. Essa declaração informa que a variável existe e foi definida em outro programa.

- Declaração: Declarar uma variável é dizer que, em algum momento, haverá um espaço de memória que utilizará esse nome, mas a memória não foi alocada
- Definição: Atrelar um espaço de memória à esse nome e definir seus valores de acordo com o tipo.

### Tipos
C é uma linguagem estaticamente tipada e, por conta disso, todos os tipos precisam ser conhecidos em tempo de compilação. A declaração de tipos depende daquilo que estamos declarando. Variáveis são declaradas com a seguinte sintaxe:
```
// Declaração sem inicialização. A variável tem lixo dentro dela!
tipo nome_variavel;
// Inicialização. A variável tem o valor dentro dela!
tipo nome_variavel = valor;
```

- **int**: Esse tipo foi feito para armazenar valores inteiros positios e negativos. Ele, por mais que represente os inteiros, não tem capacidade de representar todos, pois a quantidade de bytes alocados não é suficiente para isso. Portanto, temos que ter cuidado com isso. Existem constantes definidas pelo compilador que definem o máximo e o mínimo: INT_MAX e INT_MIN.
	- Um int, por padrão, tem 4 bytes de memória, mas depende do seu compilador.
- **short**: Esse tipo também é para lidarmos com números inteiros, mas usa somente 2 bytes.
- **long**: Esse tipo é para lidarmos com números inteiros e usa 8 bytes.
- **float**, **double** e **long double**: Essa família de tipos foi feita para armazenar valores positivios e negativos, mas que contenham casas decimais. Geralmente, o float possui 4 bytes de memória enquanto que, o double, possui 8 bytes de memória e, por fim, o long double possui 12 bytes de memória.
	- Para conseguirmos representar isso em memória, é aplicado uma espécie de notação científica, onde: m * b ^ e. M é a mantissa, que geralmente é um valor entre 1 e a base, b é a base, que nos computadores é geralmente 2, e o *e* é o expoente. Logo, o valor 1 em float pode ser representado como: 1 * 2 ^ 0. Para lidar com sinais, geralmente é adicionado um bit que representa o sinal.
	- O padrão que determina esse troço acima é o IEEE-754, que a maioria dos computadores modernos seguem, e esse padrão estipula o seguinte formato na memória:
		SIGNAL EXPOENTE MANTISSA
		(1 bit) (1byte) (3bytes)
	- O padrão dito acima é para float. Para double, a lógica é a mesma, porém com mais espaços para mais bytes.
- **bool**: O tipo bool não existe em C de fato. Entretanto, esse tipo é entendido pelo compilador. No caso, qualquer valor diferente de 0 é considerado como verdadeiro enquanto que, 0, é considerado como falso.
- **char**: Esse tipo guarda um determinado caractere de uma tabela de codificação. No caso de C, esse caractere possui sempre 1 byte de tamanho, mas tem casos onde mais podem vir a ser necessários. Para ser representado, precisa ser escrito com aspas simples.
- **strings**: Strings em C, de fato, não existem. Por baixo dos panos, são arrays de caracteres com um caracter '\0' no final.

Todos os tipos possuem um conjunto de operações que vale a pena checar na documentação quando for necessário.
### Casting de Variáveis
Para fazer o casting de alguma variável, precisamos indicar o tipo que queremos que ela seja entre parênteses. Nesse caso, precisamos estar atento ao seguinte: o tipo sendo convertido precisa estar contido dentro do tipo alvo. Logo, podemos ter o seguinte:
```
int a = 0;
double b = (int) a;
```
Dessa forma, estamos convertendo o `a`para double e guardando o resultado em `b`. Entenda: `(int) a` é uma expressão. Logo, poderemos realizar essa expressão e obter o resultado sem alterar os operandos.
Outros castings podem ser feitos, mas sempre deve tomar cuidado com o tamanho do alvo e o tamanho do recipiente.
### Ponteiros
Em C, podemos diretamente manipular a memória do computador sem muitas amarras. Para fazer isso, usamos fortemente ponteiros. 

As variáveis são nomes que estão atreladas à um endereço de memória RAM. Esse endereço pode ser obtido para trabalharmos com ele através do operador de "endereço de". Esse operador é o *&*. Para obtermos o endereço de uma variável, podemos fazer assim:

```
int idade = 20;
int* p = &idade;
```

Para obter os valores de um determinado ponteiro, podemos usar a seguinte sintaxe:
```
*ptr = valor // Atribui um valor a partir de ponteiro
printf("%d", *ptr) // Recupera o valor a partir de um ponteiro.
```

Caso queiramos, podemos incrementar ou decrementar esse ponteiro. Dessa forma, vamos para o próximo bloco de memória ou para o anterior.

Logo, podemos entender que ponteiros são espaços de memórias que guardam o endereço de outro espaço de memória. Em C, a sintaxe para ponteiros é sempre: `tipo_valor* nome_variavel`, onde tipo_valor significa o tipo de dado que o endereço do ponteiro está guardando.

Para mostrarmos o endereço de memória na tela através de um printf, precisamos formatar esse valor como hexadecimal, visto que o endereço é, basicamente, uma sequência de 0 e 1 da seguinte forma:

```
int main() {
	int i = 0;
	int* ptri = &i; // pega endereço de memória.
	printf("Endereço da variável i -> %x", ptri);
	return 0;
}
```
## Condicionais
As condicionais são estruturas que esperam um valor booleano. Entretanto, esse tipo não existiu em C até 1999, onde foi criada uma biblioteca para suprir essa necessidade. Contudo, antes disso, a variável inteira era usada para representar esse tipo, onde qualquer coisa diferente e maior que 0 era positivo e o restante era negativo. A estrutura para condicional segue a seguinte:

```
if(expressao_boleana) {
	// actions...
} else if(expressao_boleana) { // Só é executada se a expressão booleana retornar true.

} else { // Só é executada se todo mundo acima falhar.

}
```

Essa estrutura pode ser encadeada com outra utilizando `else`e `else if`. Essas duas keywords tem o mesmo propósito, mas com funcionamentos diferentes. O else ocorrerá se, e somente se, nenhuma condição for atendida. O else if só irá ser avaliado se a condição anterior falhar. Além disso, ele só irá ser aplicado se a condição for verdadeira.

Outro ponto interessante, C suporta operador ternário da seguinte forma:

```
int v = condition ? result if true: result if false;
```

## Estruturas de Repetição
Em determinados problemas, precisamos que um conjunto de ações seja repetido por um periodo determinado ou indeterminado de tempo. Por conta disso, contamos com esse tipo de estrutura. Existem algumas, mas as mais utilizads são:

### For
O for é uma estrutura onde o número de execuções é conhecido e pode ser aferido. Para fazê-lo, usamos a seguinte sintaxe:

```
for(variavel_iteravel; condicao; acao_apos_loop) {
	// o que estiver aqui dentro será repetido.
}
```
Dessa forma, conseguimos realizar um conjunto de ações em um determinado número de vezes.

Contudo, algumas vezes, queremos que esse conjunto de ações seja feito independente do número de vezes, mas sim sob alguma condição. Portanto, para fazer isso, usamos o *while*:
```
while(controle) {
	....
}
```
No caso acima, até o controle retornar false, iremos realizar esse conjunto de operações se o controle for true pelo menos uma vez. 

Para controlar o fluxo desses loops, podemos usar o `continue`e, também, o `break`. O `continue`irá fazer com  que o loop mais interno vá para a próxima iteração. O `break`irá fazer com que o loop mais interno pare a sua execução.
## IO em C

Entrada e Saída em C, no seu nível mais básico, pode ser feito com duas [[Streams]] existentes: stdin e stdout. A stdin, que significa *Standard Input* representa a stream de entrada de dados. Normalmente, essa entrada de dados está conectada ao teclado. A stdout, que significa *Standard Output*, representa a [[Streams]] na qual iremos escrever para levarmos à saída do programa. Por padrão, essa saída é o console.

Todas as funções relacionadas à input e output estão na biblioteca `<stdio.h>`. A função mais básica para saída e entrada são `printf`e `scanf`, onde devemos declarar o formato de entrada/saída e o que de fato queremos dar como saída e/ou aonde queremos receber esse input.  

A string de formato de saída e/ou entrada determina como deveremos lidar com os bytes sendo recebidos ou lidos. O scanf não faz alocação de memória automática e, por conta disso, precisamos garantir que a quantidade sendo escrita e/ou recebida é suficiente para nossos propósitos.

Para lermos outra coisa além das streams padrão, podemos ler arquivos. Para ler arquivos, precisamos saber que um determinado arquivo é uma sequência de bytes que está armazenada na memória não volátil do sistema. Dessa forma, o acesso é estritamente sequencial, ou seja, acessamos o primeiro byte para, somente depois, acessar os próximos bytes.

#### I/O Buffer
Todo I/O em C aprenseta um I/O Buffer, que é um storage onde os dados são armazenados temporariamente e morrem depois que o programa termina. Esse buffer é populado no momento em que se inicia uma operação de I/O e só é removido do buffer em determinadas situações. Quando falamos de input, o buffer pode ser populado quando a quantidade de input ofertada é maior que a quantidade esperada previamente. Dessa forma, os dados excedentes ficam no buffer até uma nova tentativa de leitura for feita, um esvaziamento forçado ou fim do programa.

Dando um exemplo com `scanf`:
```
#include <stdio.h>

int main() {
	char l1, l2;
	printf("Insira um caractere: ");
	scanf("%c", &l1);
	printf("Insira um caractere: ");
	scanf("%c", &l2);
	printf("Você digitou %c - %c", l1, l2);
	return 0;
}
```

Se rodarmos esse script, teremos esse resultado:
```
Insira um caractere: 2 
Insira outro caractere:
Você digitou 2 e
```

Isso ocorre, pois estamos lendo do STDIN um caractere. Contudo, o ENTER também é um caractere. Logo, como não lemos ele, ele foi excedente. Portanto, foi guardado no buffer. Quando tentamos ler novamente, ele verifica se há algo no buffer e, caso haja, captura esse dado. Por conta disso, ele não lê novamente do input.

Para contornar esse comportamento, podemos adicionar um espaço na string de formatação antes do caractere. Por padrão, esses espaços em branco são ignorados e não são levados para o buffer. Portanto, não são levados para o buffer. 

Em C, essas streams são conhecidas pelo tipo de dado `FILE`.  Esse tipo de dado representa uma stream e contêm informações sobre a conexão com essa determinada stream. Nesse caso, ponteiros para determinar onde a leitura parou, informações de buffers associados e etc. 
As operações mais básicas que podemos realizar giram em torno de algumas funções.

`fopen`-> Essa função é responsável por abrir um ponteiro de arquivo e retorná-lo. Você deve passar o caminho até onde está localizado essa função. Além disso, você também passa para ela qual o modo que você deseja abrir esse arquivo. Caso dê algum erro, um ponteiro de nulo é retornado.

`feof`-> Essa função é a responsável por checar se determinado arquivo já chegou ao fim. Se sim, ele retorna um valor diferente de 0.

`ferror`-> Essa função indica se houve algum erro no processamento da stream. Se sim, ele retorna um valor diferente de 0.

`clearerr`-> Essa função realiza a remoção do `EOF`e, também, a remoção de erros na stream.

`EOF`-> Esse macro é o responsável por indicar que determinado arquivo já terminou e não terá mais bytes. Entretanto, algumas operações também podem retornar `EOF`sem que o arquivo tenha terminado.

`fscanf`-> Essa função é responsável por ler uma determinada quantidade de bytes da stream especificada. Essa função segue uma *format_string* da mesma forma que o scanf. Ela retorna, também, o número de bytes lidos.

`fprintf`-> Essa função é responsável por escrever uma determinada quantidade de bytes na stream indicada podendo aplicar conversão de acordo com a *format_string*.

`putc`e `getc` -> Essas funções são as mais básicas de todas, onde podemos realizar a inserção de um caractere em uma string, ou seja, um caractere ASCII e, também, a leitura de um caractere da stream.

`fclose`-> Essa função fecha a stream aberta. Para fazer isso, enviamos um ponteiro para essa função.

### Arquivos
Para abrir um arquivo, abrimos ele com a função `fopen`. Essa função aceita um caminho e o modo de abertura daquela stream. Caso ocorra tudo certo, ela irá retornar um ponteiro para um tipo chamado de `FILE`. Esse tipo é um tipo opaco, pois sua implementação não é definida e é dependente por sistema operacional.

Toda vez que abrimos um arquivo e é retornado um ponteiro, temos um ponteiro interno ao arquivo que sempre começa do começo arquivo. Esse ponteiro está apontando para o próximo caractere que será lido. Nesse caso, como não lemos nada, ele está apontado para a posição 0.

Para ler dados, podemos usar, por exemplo, a função `fscanf`, que recebe o ponteiro para o arquivo, a string de formatação dos dados e um ponteiro para o destino. Ele lê a quantidade de caracteres que supre a string de formatação posicionando, também, o ponteiro para o próximo caractere que deve ser lido.

Para escrever em um arquivo, você pode usar o `fprintf` que recebe o ponteiro para o arquivo, uma string de formatação com os dados a serem escritos e as variáveis da onde poderá tirar os dados necessários. Depois disso, ele irá escrever a partir do ponteiro dentro do arquivo.

Para mover o ponteiro do arquivo, temos a função `fseek`. Essa função move o ponteiro do arquivo para frente e para trás. Para fazer isso, depende muito da sua necessidade e, por isso, vale a pena ver a documentação. 

Por fim, para lidar com bytes, temos outras funções, como `fread`e `fwrite`.
## Arrays
Arrays em C é uma forma de armazenar diversos valores dentro de uma única variável. O array em C é de tamanho fixo e todos os dados possuem o mesmo tipo. Além disso, todos eles estão alocados em um espaço de memória contíguo, ou seja, um logo depois do outro.

Para declarar um array em C, utilizamos a seguinte sintaxe:
```
data_type array_name [size]
```
Nesse caso, caso queiramos declarar com mais arrays dentro, fazemos da seguinte forma:
```
data_type array_name [size1][size2]
```

Como exemplo, podemos delcará-los somente com essa forma:
```
int numbers[5];
```
Essa variável tem 5 blocos do tamanho de INT alocados para ele. Entretanto, para inicializar de fato com valores reais:
```
int numbers[5] = {1,2,3,4,5};
```
Para acessar elementos no array, podemos utilizar o índice que representa a posição daquele item dentro do array.
```
printf("%d", numbers[0]);
```

As strings em C são arrays de caracteres que são terminados com um caractere que representa o nulo, que, nesse caso, é o *\0*. Portanto, a string "leonardo" é um açúcar sintático para:
```
char name[] = {'l', 'e', 'o', 'n', 'a','r','d','o','\n'};
```

Entretanto, na verdade, um array é, na realidade, um ponteiro para o primeiro elemento daquele array. Logo, podemos iterar sob esse array das duas formas:
```
int main() {
	int arr[] = {1, 2, 3, 4, 5};
	int* ptr = &arr[0];
	for (int i = 0; i < 5; i++) {
		printf("%d", ptr[i]);
	}
}
// OUTRA FORMA
int main() {
	int arr[] = {1, 2, 3, 4, 5};
	for (int i = 0; i < 5; i++) {
		printf("%d", arr[i]);
	}
}
```

Ambos produzem o mesmo resultado.
O cálculo que o compilador faz para capturar cada elemento do array é o seguinte: 
```
array + (index_sendo_acessado * sizeof(array_type_value))
```
Dessa forma, pode ser calculado o endereço de memória que queremos acessar.
### Funções
As funções são trechos de código que podem ser invocados em quaisquer lugar do código desde que a declaração daquela função seja conhecida previamente ao momento de declaração. Para declarar uma função, precisamos começar com a sua assinatura:

```
tipo_retornado nome(...parametros) {
	// corpo da função
}
```

Quando criamos uma função, ela tem o seu próprio escopo de código e, por conta disso, não consegue acessar variáveis que estejam inacessíveis nesse escopo. Para conseguir alcançá-las, podemos declarar parâmetros que essa função recebe da seguinte forma:

```
tipo_retornado nome(tipo_parametro valor) {
	//...
}
```
Além disso, podemos também fazer passagem de parâmetros por valores ou referência. Nesse caso, quando passamos por valores, ela está copiando os valores da onde foram passados para dentro da função. Quando passamos por referência, estamos passando um ponteiro contedo a região de memória onde está o valor real. Dessa forma, conseguimos alterar valores que estão, na realidade, fora da função.
## Structs
A estrutura em C é um tipo de dado definido pelo usuário onde podemos agregar diversos tipos de dados em um dado só. Cada dado dentro da estrutura é chamada de membro. A sintaxe de declaração se dá da seguinte forma:

```
struct structure_name {
	data_type member_name1;
}
```

Essa sintaxe declara o protótipo. Nesse caso, para ser utilizado, é preciso uma instância. Para fazer isso, podemos fazer da seguinte forma:

```
struct structure_name {
	//...
} variable1, variable2...
// Or, we can do it:
struct structure_name variable1;
```

Depois que ela é instanciada, ela pode ter seus dados inicializados. Entretanto, os dados não podem ter seus dados inicialiazdos no momento de declaração da struct. Para inicializá-los, fazemos o seguinte:

```
struct structure_name data;
data.member1 = data;
data.member2 = data;
data.member3 = data;
data.member4 = data;
// Ou podemos fazer o seguinte
struct structure_name data = {
	.member1 = data,
	.member2 = data,
	.member3 = data,
	...
}
```

Uma outra forma de nos referenciarmos a essas estruturas é através da keyword *typedef*. Essa keyword nos permite criar um alias para outro tipo. Dessa forma, podemos criar a estrutura dessa forma:
```
typedef struct {...} name
//code
int main() {
	name data = { ... };
}
```

## Constantes
As constantes são variáveis declaradas que não podem ter o seu valor alterado no decorrer do processo. Para declarar uma variável, usamos a palavra reservada *const* seguida da declaração de uma variável comum:
```
const char v = 'v';
```

Durante toda a execução do programa, essa constante não pode ser alterada. Por conta disso, teremos uma maior segurança que esse valor não será alterado.

## Errors
C não nos provê tratamento de exceções, como javascript. Entretanto, podemos tratar esses erros através da variável global `errno`. Essa variável está declarada dentro do header file `errno.h`. Essa variável será preenchida caso qualquer função no seu programa em C ocorra algum erro. 

Essa variável recebe um inteiro que indica o tipo de erro que pode ocorrer. Ademais, cada erro possui um determinado significado e descrição. Primeiramente, para termos acesso ao errno, devemos fazer da seguinte forma:

```
#include <errno.h>

int main() {
	printf("We can access it from here %d", errno);
}
```

Podemos também pegar a  descrição do erro através da função `strerror(int errno);`. Essa função retorna um ponteiro `char*`para a string contendo o texto.
## Header Files 

Os header files são responsáveis por conter declarações de funções, constantes, enumerações e outras coisas que podem ser incluidas em arquivos diferentes sem necessariamente nos preocuparmos com a implementação dessas funções, métodos e etc. A implementação em si vai para os arquivos terminados em `.c`. 

Para criar um header file, fazemos da seguinte forma:
```
f: Point.h

typedef struct {
        double x;
        double y;
} Point;

Point Point_new();

double Point_sum(Point* self);

```

No caso acima, declaramos uma `struct` e dizemos que ela tem duas propriedades. Além disso, temos uma função chamada de `Point_new`e outra função chamada de `Point_sum`, que recebe um ponteiro para um `Point`.

Contudo, a implementação dessa struct tem um campo a mais, veja:

```
typedef struct {
        double x;
        double y;
        double z;
} Point;

Point Point_new() {
        Point p = { x: 0, y: 0, z: 1};
        return p;
}

double Point_sum(Point* self) {
        return self->x + self->y + self->z;
}
```

Perceba que, dessa forma, podemos emular o comportamento de `interfaces`com header files. Contudo, elas servem para algo além disso. Quando incluímos um header file, é papel do linker realizar a linkagem com o código de verdade. Dessa forma, podemos compilar esses dois arquivos de maneira separadas e de acordo com a necessidade.

Além disso, pode vir a ser necessário guardas de include. Esses guardas impedem que um `include`sobreescreva o outro. Para fazer isso, podemos fazer da seguinte forma:

```
#ifndef
#define HEADER_FILE_H
//... header file definitions
#endif
```

`time.h`-> Essa biblioteca nos permite criar manipulações e rotinas que envolvam tempo.