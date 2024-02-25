A representação de qualquer informação no computador é feita através de números binários. Ela é feita dessa forma, pois é a maneira mais próxima de representar "como" o computador consegue enxergar as coisas através de "switches" e liga/desliga.  Esse sistema é um sistema posicional, ou seja, o seu valor irá depender da posição em que aquele dígito aparece.

Para começar, escolhe-se uma gama de símbolos que teremos para representar os valores. No caso do sistema binário, temos dois. No caso do sistema decimal, por outro lado, temos 10. A quantidade de símbolos define a base daquele sistema numérico. No caso do binário, é 2 e, no caso decimal, é 10.  Portanto, para definirmos um valor precisamos dos símbolos e das posições deles.

Por exemplo, digamos 1.415: Primeiramente, vamos começar do dígito menos significativo (À esquerda) para o mais significativo (À direita). O número à esquerda começa na posição 0 e segue somando + 1 na posição até o mais significativo. Para saber o valor real daquele dígito, iremos multiplicar da seguinte forma: valor do símbolo * base ^ posição. Ou seja, o valor do 5 seria 5 * 10 ^ 0, visto que está na posição 0 e estamos usando o sistema decimal. O resultado disso é 5. Já para o 1, iremos ter ele na segunda posição e no dígito mais significativo. Por conta disso, podemos calcular ambos da seguinte forma:

Segunda posição: 1 * 10 ^1
Última posição: 1 * 10^4 

Perceba que, para representar números maiores que a quantidade de símbolos existentes, nós andamos uma casa significativa e zeramos os valores anteriores. Por exemplo, para representar o valor 10 no sistema decimal, precisamos zerar a primeira posição e andar uma casa à esquerda.

Portanto, para o binário, não é diferente, iremos fazer o seguinte para representar o 2:

- Como só temos 0 ou 1, não poderemos representá-lo com somente 1 casa. Portanto, para que consigamos representar, precisamos de mais uma casa para representar. Para fazer isso, zeramos a primeira casa e usamos o 1 para representar o 2, visto que 1 * 2 ^1 é igual a 2 e ficamos da seguinte forma: `10` sendo como 2.