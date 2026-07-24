O SSE (Server-Sent Events) é uma especificação baseada no protocolo HTTP padrão que permite que um servidor envie atualizações automáticas e em tempo real para o cliente de forma unidirecional (Server → Client), através de uma única conexão persistente.
No SSE o cliente faz uma única requisição inicial dizendo <font color="#ff0000">“mantenha esta conexão aberta e me avise quando tiver novidades”</font>, e o servidor passa a empurrar os dados à medida que eles acontecem.
### Como funciona no protocolo?

Ele funciona em cima do HTTP/1.1 ou HTTP/2 convencional:
1. <font color="#de7802">Abertura de conexão</font>: O cliente faz uma requisição HTTP `GET`comum, mas envia o cabeçalho:  
    `Accept: text/event-stream`
2. <font color="#de7802">Reposta do servidor</font>: O servidor responde mantendo a conexão aberta com o status 200 OK e os cabeçalhos:  
   ```
   Content-Type: text/event-stream 
   Cache-Control: no-cache 
   Connection: keep-alive
   ```
3. **<font color="#de7802">Envio dos Dados</font>:** O servidor envia dados em texto puro formatados de uma forma específica (`data: ...\n\n`) sempre que houver um novo evento.
4. <font color="#de7802">Fechamento</font>: A conexão permanece aberta até que o cliente ou o servidor decidam fechar explicitamente, ou até que haja uma queda de rede.
### Formatos da Mensagem SSE

O protocolo exige um formato de texto bem simples. O servidor envia linhas separadas por quebra de linha (`\n`).
```
id: 1
event: status-update
data: {"pedidoId": "987", "status": "EM_TRANSPORTE"}

id: 2
event: status-update
data: {"pedidoId": "987", "status": "ENTREGUE"}
```
- **`data:`** O conteúdo da mensagem (frequentemente um JSON em string).
- **`event:`** (Opcional) O nome do evento. Permite ao cliente escutar múltiplos tipos de eventos na mesma conexão.
- **`id:`** (Opcional) Identificador da mensagem. Se a conexão cair, o navegador envia automaticamente o cabeçalho `Last-Event-ID` para o servidor retomar de onde parou.
- **`retry:`** (Opcional) Tempo em milissegundos que o navegador deve esperar antes de tentar reconectar se a conexão cair.
### Exemplo em código
O `JavaScript` já possui suporte nativo para SSE sem necessidade de bibliotecas externas:
``` javascript
// Abre a conexão com o endpoint do servidor
const eventSource = new EventSource('/api/pedidos/status/stream');

// Escuta por eventos padrão
eventSource.onmessage = (event) => {
    const data = JSON.parse(event.data);
    console.log('Nova atualização:', data);
};

// Escuta por um evento personalizado
eventSource.addEventListener('status-update', (event) => {
    const status = JSON.parse(event.data);
    console.log('Status do pedido:', status);
});

// Tratamento de erros (reconexão é automática!)
eventSource.onerror = (err) => {
    console.error('Erro na conexão SSE:', err);
};
```
### Quando usar ?

O SSE é a escolha perfeita para cenários onde os dados fluem **predominantemente do backend para o frontend**:

1. **<font color="#de7802">Feeds de Notificações / Timelines</font>:** Atualizações de redes sociais, notificações em tempo real na interface.
2. **<font color="#de7802">Dashboards e Métricas</font>:** Telas de acompanhamento de cotações de ações, sensores IoT, logs de sistema ou progresso de pipelines CI/CD.
3. **<font color="#de7802">Acompanhamento de Status de Processos</font>:** Atualizações de status de entrega de e-commerce, streaming de respostas de IA (como chat de LLM) ou progresso de upload/conversão de vídeos.

### Quando não usar?

- Se você precisa de **comunicação bidirecional intensa e de baixa latência** (ex: chats multiplayer, jogos online, editores colaborativos como o Figma) $\rightarrow$ Use [[Websocket]].
- Se você precisa enviar dados **binários** pesados diretamente pelo stream $\rightarrow$ Use **WebSockets** ou download HTTP de arquivos.

#flashcards/arquitetura-de-software/sse-server-sent-events
Como funciona o SSE?::É uma especificação baseada no protocolo HTTP, permitindo que o servidor envie atualizações automáticas e em tempo real para cliente de forma unidirecional (<font color="#ff0000">server -> client</font>), através de uma única conexão persistente. No SSE o cliente faz uma única requisição dizendo "mantenha essa conexão aberta e em avise quando tiver novidades", e o servidor passa a empurrar os dados a medida que eles acontecem.
<!--SR:!2026-07-25,1,230-->