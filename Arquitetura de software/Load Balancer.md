#arquitetura-de-software 
Um Load Balancer (ou balanceador de carga) é um componente de infraestrutura/arquitetura de software que atua como o ponto único de entrada (Reverse Proxy) para um sistema, distribuindo o tráfego de rede ou de aplicações entre múltiplos servidores no backend (server pool ou farm).
### Por que usar um Load Balancer?
As arquiteturas modernas utilizam balanceadores para resolver três grandes pilares de sistemas distribuídos:
1. <font color="#de7802">Escalabilidade Horizontal</font>: Permite adicionar ou remover servidores da sua frota sem interromper o serviço e sem que o cliente precise saber o IP de cada máquina.
2. <font color="#de7802">Alta Disponibilidade (High Availability)</font>: Se um servidor backend falhar ou cair, o balanceador redireciona automaticamente o tráfego apenas para os servidores saudáveis.
3. <font color="#de7802">Performance e Resiliência:</font> Evita gargalos ao impedir que um único nó fique saturado de requisições.
### As duas principais camadas do Load Balancer (Camadas OSI)
#### 1. <font color="#de7802">Layer 4 Load Balancer</font> (Camada de Transporte - TCP/UDP)
Ele opera apenas no nível de rede e transporte (endereços IP e portas TCP/UDP). Ele não lê o conteúdo da requisição HTTP.
- <font color="#de7802">Como funciona:</font> Ele simplesmente recebe o pacote TCP e o redireciona para um servidor interno.
- <font color="#de7802">Vantagem:</font> Extremamente rápido e eficiente em termos de processamento de CPU.
- <font color="#de7802">Caso de uso</font>: Ideal para protocolos de rede de baixo nível, conexões [[Websocket]] de alto volume ou tráfego de bancos de dados.
#### 2. <font color="#de7802">Layer 7 Load Balancer</font> (Camada de Aplicação - HTTP/HTTPS)
Ele toma decisões de roteamento **inspecionando o conteúdo da requisição HTTP/HTTPS** (cabeçalhos, URLs, cookies, parâmetros da URL ou corpo da requisição).

- <font color="#de7802">Como funciona: </font>Pode rotear chamadas de `/api/pedidos` para o serviço de pedidos e `/api/pagamentos` para o serviço de pagamento.
- <font color="#de7802">Vantagens:</font>
    - Suporta **Roteamento Inteligente** (baseado em contexto/path).
    - **TLS/SSL Termination:** Ele pode descriptografar o tráfego HTTPS na entrada, aliviando o uso de CPU dos servidores backend (que passam a se comunicar internamente via HTTP puro).
    - Pode inspecionar cookies para manter a sessão do usuário presa a um determinado servidor (_Sticky Sessions_).
- **Desvantagem:** Exige mais CPU para processar/inspecionar os dados da aplicação.
### Principais Algoritmos de Balanceamento
**Como o Load Balancer decide para qual servidor enviar a próxima requisição? Através de algoritmos:**

- <font color="#de7802">Round Robin:</font> Distribui as requisições em ordem sequencial simples (Servidor 1 $\rightarrow$ Servidor 2 $\rightarrow$ Servidor 3 $\rightarrow$ Servidor 1...).
- <font color="#de7802">Weighted Round Robin:</font> Atribui "pesos" aos servidores. Máquinas mais potentes recebem uma proporção maior de requisições.
- <font color="#de7802">Least Connections (Menos Conexões):</font> Envia a nova requisição para o servidor que tem o menor número de conexões ativas no momento. _(Ideal para requisições com tempos de processamento muito variados, como requisições longas de polling ou WebSockets)._
- <font color="#de7802">IP Hash</font>:Aplica um algoritmo de _hash_ no endereço IP do cliente para garantir que um determinado usuário sempre caia no mesmo servidor (útil para sistemas _stateful_).
### Health checks (verificações de saúde)
Um Load Balancer não apenas distribui tráfego; ele monitora constantemente os servidores de backend.  
Periodicamente, ele faz pings ou requisições HTTP (ex: `GET /health`) para cada servidor.

- Se um servidor responder com erro (ex: `500 Internal Server Error`) ou der _timeout_, o Load Balancer **o remove automaticamente do pool**.
- Assim que o servidor se recupera e volta a responder `200 OK`, o balanceador **volta a enviar tráfego para ele**.
### Resumo Arquitetural: Onde tudo se conecta
Conectando aos tópicos  (Polling, SSE e WebSockets):
- Se você estiver usando **WebSockets** ou **Long Polling**, você precisará configurar o Load Balancer para suportar **conexões de longa duração** (ajustar timeouts de keep-alive) e, no caso de Layer 7, garantir que ele suporte o cabeçalho `Upgrade: websocket`.
- Para lidar com a escala de milhares de conexões WebSockets/SSE presas ao Load Balancer, costuma-se usar um mecanismo de **Pub/Sub (como Redis ou Apache Kafka)** no backend para sincronizar as mensagens entre as diferentes instâncias de aplicação que estão atrás do Load Balancer.

#flashcards/arquitetura-de-software/load-balancer
Para que serve o Load Balancer?::É um componente de software que atua como um ponto único de entrada (Reverse Proxy) para um sistema, distribuindo um trafego de rede ou de aplicação entre múltiplos servidores no back-end. Usado para Escalabilidade Horizontal, alta disponibilidade, performance e resiliência.
