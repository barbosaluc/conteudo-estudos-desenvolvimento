#arquitetura-de-software 
O Websocket é um protocolo de comunicação de rede que fornece um canal de comunicação bidirecional e full-duplex(simultâneo) sobre um única conexão TPC de longa duração.
Embora o Websocket seja um protocolo totalmente diferente do HTTP (ele utiliza o esquema <font color="#c00000">ws://</font> ou <font color="#c00000">wss://</font> para conexões seguras), ele começa sua vida através de uma requisição HTTP convencional. Esse processo é chamado de <font color="#c00000">Websocket Handshake</font> (aperto de mão):
### 1. Abertura do Handshake (HTTP GET):
O cliente faz uma requisição HTTP tradicional pedindo para "atualizar" o protocolo para WebSocket:
```javascript
GET /chat HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```
### 2. Resposta do servidor (Switching Protocols):
Se o servidor suporta WebSockets, ele responde confirmando a troca de protocolo:
```javascript
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```
### 3. Conexão Estabelecida
A partir deste momento, o protocolo HTTP é "abandonado". A conexão TCP subjacente permanece aberta e passa a operar no protocolo WebSocket em frame puro.
### Principais Características Arquiteturais
- <font color="#de7802">Bidirecionalidade (Full-Duplex):</font> Ambos os lados enviam e recebem dados de forma assíncrona a qualquer momento.
- <font color="#de7802">Baixa Latência e Overhead Mínimo</font>: HTTP tradicionais exigem que centenas de bytes de cabeçalhos (<font color="#ff0000">User-Agent</font>, <font color="#ff0000">Cookies</font>, etc.) sejam enviados a cada chamada. No WebSocket, após o _handshake_, a troca de dados utiliza _frames_ com cabeçalhos mínimos (de apenas 2 a 10 bytes).
- <font color="#de7802">Suporte a texto binário:</font> Diferente do SSE (que só envia texto), o WebSocket nativamente envia dados em texto (como JSON) e arquivos/buffers binários (<font color="#ff0000">ArrayBuffer, Blob</font>).
### Quando usar?
O WebSocket é a escolha arquitetural ideal quando a interatividade bidirecional e a baixíssima latência são cruciais:
1. <font color="#de7802">Aplicações de Chat e Mensageria:</font> Onde ambos os lados enviam e recebem mensagens constantemente (ex: WhatsApp Web, Slack).
2. <font color="#de7802">Ferramentas Colaborativas em Tempo Real:</font> Editores de texto ou quadros brancos compartilhados onde múltiplos usuários interagem no mesmo documento (ex: Figma, Google Docs, Miro).
3. <font color="#de7802">Jogos Multiplayer</font> <font color="#de7802">Online</font>: Onde posições de personagens e ações precisam ser sincronizadas a cada poucos milissegundos.
4. <font color="#de7802">Plataformas de Trading / Financial Markets:</font> Transmissão bidirecional de ordens de compra/venda e atualizações instantâneas de cotações em tempo real.
### Desafios de Arquitetura ao adotar WebSockets
Ao projetar sistemas com WebSockets, considere:
- <font color="#de7802">Escalabilidade (Stateful)</font>: Como a conexão TCP é persistente, o servidor precisa manter o estado na memória. Se você tiver múltiplos nós atrás de um _Load Balancer_, precisará de uma camada de mensageria Pub/Sub (como Redis ou Apache Kafka) para rotear as mensagens entre as instâncias dos servidores.
- <font color="#de7802">Firewalls e Proxies:</font> Certos ambientes corporativos bloqueiam conexões longas que não sejam HTTP puro, exigindo o uso de `wss://` (TLS) para evitar bloqueios no nível da rede.

#flashcards/arquitetura-de-software/websocket
Para que serve o websocket::É um protocolo de comunicação bidirecional e full-duplex sobre uma única conexão TPC de longa duração.  Em outras palavras, enquanto no HTTP tradicional o cliente precisa "bater na porta" do servidor toda vez que quer uma informação nova, no Websocket a porta fica aberta o tempo todo e ambos podem conversar instantaneamente.