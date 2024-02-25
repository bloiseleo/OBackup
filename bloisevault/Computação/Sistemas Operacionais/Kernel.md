Kernel faz parte do conjunto de programas que é instalado quando instalamos um Sistema Operacional. Esse programa é o coração do Sistema Operacional. O Kernel possui total controle sobre os componentes de hardware do sistema. Portanto, ele é um programa que tem controle total sobre tudo que você está fazendo, já fez e/ou irá fazer.

Depois que a BIOS termina de fazer o bootstrap e inicialização do sistema, o computador instancia o Kernel para uma área de memória protegida. Depois que o Kernel incia, ele se encarrega do restante da incialização.

O Kernel é responsável por tarefas de bem baixo nível, como gerenciamento de disco, memória e tarefas. Para possibilitar que outras aplicações acessem recursos de mais baixo nível, o Kernel expõem uma interface para que outros programas possam fazer isso. Uma chamada feita para essa API é chamda de chamada de sistema. Quando um programa realiza essa chamada de sistema, o kernel acessa o sistema e devolve a resposta para o programa.

O Kernel mantém uma tabela com todos os processos sendo executados no momento. Através disso, o Kernel decide qual processo irá utilizar os recursos da máquina e quais programas devem ser mantidos em memória.

O Kernel é carregado em um espaço de memória diferente do espaço de memória que outros programas são executados normalmente. Esse espaço é chamado de Kernel Space, que é protegido de ser acessado.

## Shell

O Shell é um programa read-eval-print-loop (REPL) que recebe comandos através de uma linha de comando que possibilita interagir com o Kernel e outros programas. Além disso, ele também pode ser considerado uma linguagem de programação, visto que é possível criar scripts para serem executados pelo shell. 

O primeiro shell escrito foi desenvolvido por Ken Thompson na Bell Labs de 1971 até 1975. Esse sheel é o **sh** que conhecemos hoje e é tomado como base para outros shells.