Emular um componente de hardware é simular o seu comportamento. Logo, uma série de detalhes é preciso estar em mente na hora de realizar essa emulação:

- Um emulador, caso seja escrito em uma linguagem cross plataforma, você terá um dispositivo que funciona em várias plataformas e é independente de CPU. Caso ele estivesse sendo virtualizado, somente sistemas de mesma arquitetura poderiam sobre determinada CPU.

Um emulador é um interpretador que executa e segue a linha de execução daquele hardware. Cada comando é interpretado, executado, os efeitos que ele faria no hardware são feitos sobre o emulador e segue-se em frente.