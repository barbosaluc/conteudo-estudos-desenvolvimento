#flashcards/redes/protocolos/UDP 
É um protocolo de camada de transporte do modelo TCP/IP.
O UDP é um protocolo <font color="#de7802">não orientado à conexão e extremamente leve</font>. Ele simplesmente pega os dados e os dispara para o destino, sem se preocupar se chegaram, se foram perdidos ou se estão na ordem certa. Sua prioridade é a velocidade.
### Principais características
- <font color="#de7802">Sem conexão (Connectionless)</font> : Não há handshake prévio. Os pacotes (chamados de _datagramas_) são enviados imediatamente.
- <font color="#de7802">Sem garantia de entrega</font> : Se um pacote for perdido na rede, ele não será reenviado.
- <font color="#de7802">Baixa latência (muito rápido)</font> : Como não há checagens de confirmação nem cabeçalhos complexos, o atraso é mínimo.
- <font color="#de7802">Sem controle de ordem</font> : Pacotes podem chegar fora de ordem no destino sem que o protocolo tente corrigir.
### Casos de uso
O UDP é ideal para cenários onde a velocidade em tempo real é mais importante do que a perda ocasional de pequenos pedaços de informação.
- <font color="#de7802">Transmissões ao vivo (Streaming/IPTV)</font> : Perder alguns _frames_ é preferível a congelar a imagem esperando o reenvio.
- <font color="#de7802">Jogos Online</font> : Atualização rápida de posição e ações dos jogadores.
- <font color="#de7802">Chamadas de voz e vídeo (VoIP / Zoom / Discord)</font> : Um pequeno ruído na voz é melhor do que um atraso gigante na conversa.
- <font color="#de7802">Consultas DNS</font> : Respostas extremamente rápidas para traduzir nomes de domínio em IPs.

#flashcards/redes/UDP
Como funciona o protocolo UDP?:: É um protocolo de camada de transporte TCP/IP, não orientado à conexão e extremamente leve. Ele simplesmente pega os dados e dispara para o destino, sem se preocupar com perdas, ou se está na ordem certa, sua prioridade é a velocidade.
<!--SR:!2026-08-08,8,250-->