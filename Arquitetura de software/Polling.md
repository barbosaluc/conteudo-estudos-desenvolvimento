Polling é uma técnica onde um cliente envia requisições repetidas a um servidor em intervalos regulares para verificar se há novas informações ou se o status de uma tarefa mudou.
#### Como funciona na prática?

1. O cliente faz uma requisição HTTP (ex: GET/ status-do-pedido).
2. O servidor processa a requisição imediatamente e responde com o estado atual (ex: “ainda processando”).
3. O cliente aguarda um tempo predefinido (ex: 5 segundos).
4. O cliente repete o passo 1.
#### 1. Short Polling (Polling Curto):

É a forma mais simples e literal. O cliente pergunta e o servidor response imediatamente, mesmo que não haja novidades (retornando um status vazio ou “sem alterações”).
- <font color="#de7802">Vantagens</font>: Extremamente simples de implementar. Não segura conexões abertas no servidor.
- <font color="#de7802">Desvantagens</font>: Altamente ineficiente. Gera muito tráfego de rede desnecessário e consome recursos de processamento à toa se os dados não mudarem com frequência.
#### 2. Long Polling (Polling Long):

Uma evolução mais inteligente. Quando o cliente faz a requisição, se o servidor não tiver dados novos, **ele segura a conexão aberta** (esperando) até que uma nova informação esteja disponível ou ocorra um _timeout_. Assim que o dado surge, o servidor responde e fecha a conexão. O cliente, então, abre uma nova requisição imediatamente para esperar a próxima atualização.

- **<font color="#de7802">Vantagem</font>:** Muito mais eficiente em termos de latência (o cliente recebe o dado quase em tempo real).
- **<font color="#de7802">Desvantagem</font>:** Mantém conexões ativas no servidor, o que pode consumir muita memória se você tiver milhares de clientes simultâneos.
#### Quando usar Polling?

Embora existam alternativas modernas, o Polling ainda tem excelente espaço no design de sistemas, especialmente quando:

- **<font color="#de7802">Integração simples é prioridade</font>:** Você precisa atualizar a interface do usuário, mas não quer configurar uma infraestrutura complexa de mensageria ou WebSockets.
- **<font color="#de7802">Tarefas de longa duração</font> (Long-running Tasks):** Quando um cliente dispara um processo pesado no backend (ex: gerar um relatório PDF gigante ou processar um pagamento assíncrono). O cliente recebe um `ID` de processo e fica fazendo polling (`GET /tasks/123/status`) até que o status mude para "Concluído".
- **<font color="#de7802">Sistemas legados</font>:** Quando o servidor de destino não suporta protocolos de comunicação bidirecional.
#### Desvantagens e o "Problema do Polling"

Se usado sem critério, o Polling pode se tornar um gargalo de performance (**overkill**):

- **<font color="#de7802">Desperdício de recursos</font>:** Milhares de requisições retornando `304 Not Modified` ou `JSON` vazio consomem CPU, banda de rede e banco de dados.
- **<font color="#de7802">Atraso na informação (Lag)</font>:** No Short Polling, se o seu intervalo é de 10 segundos e o dado muda logo após a última consulta, o usuário só verá a mudança daqui a 10 segundos.
## Alternativas ao Polling (Event-Driven)

Se você precisa de comunicação em tempo real de alta performance e baixo consumo de recursos, a arquitetura moderna costuma substituir ou complementar o Polling com:

- [[Websocket]]: Estabelece uma única conexão bidirecional e persistente entre cliente e servidor (ideal para chats ou dashboards financeiros).
- **[[SSE (Server-Sent Events)]]:** Uma conexão unidirecional onde o servidor envia atualizações contínuas para o cliente via HTTP padrão.
- **Webhooks:** O inverso do polling. Em vez de o cliente perguntar, o servidor faz uma chamada HTTP para o cliente (comum em comunicação de API para API, como o gateway de pagamento avisando o seu sistema que o boleto foi pago).

#flashcards/arquitetura-de-software/polling
Como funciona o polling?::É uma técnica onde o cliente envia requisições a um servidor em intervalos de tempo, para verificar se há informações ou se o status de uma tarefa mudou. Existem dois tipos: o <font color="#de7802">Short Polling</font>, onde o cliente pergunta e o servidor responde imediatamente, e o <font color="#de7802">Long Polling</font>, o cliente faz a requisição e o servidor segura a conexão aberta até que uma nova informação esteja disponível ou ocorra um timeout.
<!--SR:!2026-07-27,3,250-->