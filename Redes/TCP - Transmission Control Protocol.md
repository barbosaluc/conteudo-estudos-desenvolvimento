É um protocolo da <font color="#de7802">Camada de transporte</font> do modelo TCP/IP. 
O TCP é um protocolo orientado à conexão e focado na garantia de entrega. Ele se certifica de que todas as informações cheguem ao destino[^1] completas, sem erros e na ordem correta.
### Principais características
- <font color="#de7802">Conexão estabelecida (Three-Way Handshake)</font> : Antes de enviar qualquer dado real, o cliente e o servidor "conversam" para estabelecer a conexão (SYN $\rightarrow$ SYN-ACK $\rightarrow$ ACK).
- <font color="#de7802">Confiabilidade e confirmação (ACK)</font> :  Para cada pacote enviado, o receptor deve enviar uma confirmação (<font color="#ff0000">Acknowledgment</font>). Se um pacote for perdido no caminho, o TCP o reenvia automaticamente.
- <font color="#de7802">Ordenação de pacotes</font> : Os pacotes recebidos fora de ordem são reordenados antes de serem entregues à aplicação.
- <font color="#de7802">Controle de fluxo e engarrafamento</font> : Ajusta a velocidade de envio para não sobrecarregar a rede ou o receptor.
### Casos de uso
O TCP é usado quando a integridade dos dados é essencial (perder um único byte pode corromper a informação).
- <font color="#de7802">Navegação Web</font> : HTTP / HTTPS.
- <font color="#de7802">Envio e Recebimento de E-mails</font> : SMTP, IMAP e POP3.
- <font color="#de7802">Transferência de Arquivos</font> : FTP , SFTP.
- <font color="#de7802">Acesso remoto</font> : SSH.

#flashcards/redes/TCP
Como funciona o protocolo TCP?::É um protocolo da Camada de Transporte do modelo TCP/IP. É orientado à conexão  e focado na garantia da entrega. Ele se certifica de que todas as informações cheguem ao destino completas, sem erros e na ordem correta.
<!--SR:!2026-08-02,2,230-->





