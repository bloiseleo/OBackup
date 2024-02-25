O nome de domínio é um endereço facilmente memorizável que é traduzido para um endereço IP cuja máquina está realmente localizada. Geralmente, eles contêm 3 ou 2 partes serparadas por pontos e o nível de especificidade aumenta da direita para esquerda.
- Por exemplo, temos www.google.com como domínio:
	- O `.com`é o TOP LEVEL DOMAIN.
	- O `google`é o SECOND LEVEL DOMAIN.

Para fazer isso, quando uma requisição HTTP é feita, primeiramente, é necessário localizar esse IP. Esse trabalho é feito pelos *DOMAIN NAME SERVERS*. 

Geralmente, esse trabalho começa nos seus provedores de internet, que possuem um servidor DNS. O navegador checa em um cache local se ele já possui aquele determinado IP mapeado. Caso não possua, ele realiza uma *query DNS* para o DNS. Esse DNS é chamado de **recursive resolver**, pois irá fazer diversas queries para outros servidores DNS para resolver o seu DNS.

- Primeiramente, o DNS do seu ISP é solicitado para encontrar determinado IP.
- Caso o DNS do seu ISP saiba a resposta, ele te responde com sucesso. Caso não saiba, ele irá começar a fazer chamadas para outros DNS.
	- O primeiro DNS que será chamado é o **Root Name Server**. 
