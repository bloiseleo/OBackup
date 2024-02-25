Uma rede é uma gama de dispositivos que estão interconectados através de um determinado meio. Esses dispositivos conseguem trocar informações através desse meio e, com isso, estabelecer comunicação e compartilhar recursos. Portanto, esses dispositivos estão conectados à um sistema de comunicação.

Os principais tipos desses dispositivos que interligam essa rede são os seguintes:
- Hardware: Os hardwares se diferenciam quanto à função e posição dentro do contexto de comunicação.
	- Fonte: É o dispositivo que produz ou armazena determinada informação.
	- Transmissor: É o dispositivo que, em posse da fonte, realiza o envio de fato daqueles dados para quem quiser recebê-lo.
		- Ambos dispositivos acima caracterizam a *Origem*
	- Meio: É o dispositivo que se encarrega de transmitir a informação da forma mais fiel possível.
	- Receptor: É  o dispositivo que pediu ou recebeu determinada informação.
- Software: Os softwares estabelecem as regras de comunicação que os dispositivos devem seguir e as suas devidas implementações.

Podemos ter casos onde a fonte e o destino estejam ligados diretamente. Contudo, também temos casos onde, no meio desses, temos uma rede de interconexão. Nesse caso, temos outros dispositivos que estão conectados entre o receptor e a origem. 
### Protocolo
Para que a origem e o destino se comuniquem de maneira clara, faz-se necessário que ambos sigam um conjunto de regras previamente conhecido e apliquem-nos sobre os dados quando for realizar a transmissão dos mesmos. Essas regras dizem respeito à uma gama de coisas que impactam diretamente na comunicação, como, por exemplo, o formato das mensagens trocadas. 
### Comutação
A comutação é o processo de realizar a troca de informações. Ele define como realizar a troca de informações entre as duas entidades envolvidas. Existem alguns tipo de comutação:
- Circuito: Esse tipo de comutação exige que haja um caminho físico estabelecido entre a origem e o destino. Dessa forma, todas as unidades de informação atravessam o mesmo caminho, levam o mesmo tempo, tem a taxa de transimissão bem estabelecida e etc. Entretanto, existe um limite de usuários, visto que, caso o caminho que você precisasse estabelecer estivesse ocupado, você não poderia se comunicar com aquele destino. Existem 3 etapas nessa comutação: estabelecimento da comunicação, transmissão de dados e fechamento de conexão. Essas etapas ocorrem sequencialmente, ou seja, uma depois da outra.
- Pacotes: Esse tipo de comutação não exige que haja um caminho físico estabelecido entre a origem e o destino de forma dedicada.
- Mensagem

#### Comutação por Circuito
Para realizar a comutação por circuito, é necessário o estabelecimento prévio do caminho entre a origem e o destino dedicado. Esse estabelecimento envolve a definição dos enlaces e alocação de recursos necessários de cada enlace. Essa comutação ocorre em três etapas
- Estabelecimento do Circuito: descoberta do caminho até o destino e a alocação dos recursos necessários nos enlaces. Esse caminho fica exclusivo para essa comunicação e só fica livre depois que é encerrado.
- Transferência das Informações: É nessa fase que a informação é enviada de um ponto para o outro. Nesse tipo de comutação, é bem rápida, visto que o caminho já está dedicado e livre de interferência de outras comutações.
- Desconexão: Depois que tudo desejado foi feito, todos os recursos são desalocados. Tanto dos terminais até os elances, TUDO deve ser desalocado.

#### Comutação por Pacote
A comutação por pacotes envolve a fragmentação dos dados a serem enviados em partes menores. Essas partes menores são compostas por um cabeçalho e por um corpo. No cabeçalho dos dados, temos algumas informações a cerca da informação à ser transmitida. Nesse caso, existem dois tipos de comutação por pacote: datagramas e circuitos virtuais. 
- Datagrama: O destino e o número de sequência do pacote são inseridos no cabeçalho do pacote. Cada pacote irá seguir uma rota independentemente dos outros pacotes. Quando o pacote chegar ao destino, ele irá ser armazenado e aguardará pela chegada de todos os pacotes. Quando todos os pacotes chegarem, eles são organizados de acordo com o número de sequência para reconstruir a mensagem. Caso um pacote não seja recebido, pode ser solicitado para ser enviado novamente.
