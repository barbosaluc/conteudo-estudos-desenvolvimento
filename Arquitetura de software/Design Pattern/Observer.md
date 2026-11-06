#arquitetura-de-software #design-patterns #observer
É um padrão de projeto comportamental que permite que um objeto avise outros objetos quando um evento ou uma mudança de estado acontece.
O objeto que emite o aviso é chamado de <font color="#de7802">observável (Subject)</font>. Os objetos interessados nesses avisos são chamados de <font color="#de7802">observadores (Observers)</font>. 

Imagine um sistema de pedidos: quando um pedido é enviado, diferentes partes da aplicação precisam reagir:
- Enviar um e-mail ao cliente.
- Enviar uma notificação pelo aplicativo.
- Registrar o envio no histórico do pedido.
Com <font color="#de7802">Observer</font>, essas reações ficam em observadores separados. O objeto que anuncia o envio não precisa conhecer os detalhes de como cada reação funciona.

#### Como funciona
O padrão possui quatro ações principais: 
1. Um observador se cadastra para receber notificações.
2. Um evento acontece no objeto observável.
3. O observável notifica os observadores cadastrados.
4. Cada observador executa sua própria reação.
Também é possível remover um observador, para que ele deixe de receber notificações.

