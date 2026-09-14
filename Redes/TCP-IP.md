#redes/TCP-IP 
(Transmission Control Protocol / Internet Protocol) é o conjunto de regras e protocolos fundamentais que permite a comunicação entre computadores e dispositivos em rede. Essencialmente é a "língua padrão" de toda a internet global e das redes locais modernas.

Em vez se ser um único protocolo, o TCP/IP é uma pilha (suite) de protocolos organizada em camadas, onde cada camada cuida de uma etapa específica do envio e recebimento de dados.
### Os dois pilares centrais
Embora a pilha contenha dezenas de protocolos (como HTTP, DNS, FTP), o nome destaca os dois mais importantes:
1. IP (Internet Protocol) - O endereçador :
   - Responsável por identificar a origem e o destino de cada dispositivo na rede através dos endereços IP (ex: ``192.168.1.1 ou 2001:db8::1``).
<!--SR:!2026-08-03,3,250-->
   - Divide os dados em pacotes menores e garante que ele encontrem o caminho correto pelos roteadores até o destino.
   - Não verifica se os pacotes chegaram em ordem ou se algum foi perdido (isso é função do TCP).
2. [[TCP - Transmission Control Protocol]] - O gerente de entrega : 
   - Funciona sobre o IP e estabelece uma conexão confiável entre o emissor e o receptor via Three-Way Handshake(SYN, SYN-ACK,ACK).
### As 4 camadas do modelo TCP/IP

| Camada                           | Função Principal                                            | Protocolos de exemplo       |
| -------------------------------- | ----------------------------------------------------------- | --------------------------- |
| 4. Aplicação                     | Interface direta com programas e serviços do usuário.       | HTTP, HTTPS, SSH, DNS, SMTP |
| 3. Transporte                    | Gerencia a comunicação ponto a ponto e o controle de fluxo. | TCP, UDP                    |
| 2. Internet (Rede)               | Endereça e roteia pacotes através de redes distintas.       | IP (IPv4/IPv6), ICMP, ARP   |
| 1. Acesso à Rede (Enlace/Física) | Transmite os bits puros pelo meio físico (cabo, ar, fibra). | Ethernet, Wi-Fi (802.11)    |
### Exemplo prático: O que acontece ao abrir um site?
1. **Aplicação:** Seu navegador envia uma requisição `GET /` usando o protocolo **HTTP**.
2. **Transporte:** O **TCP** quebra essa requisição em segmentos, adiciona números de sequência e define as portas (ex: porta `443` para HTTPS).
3. **Internet:** O **IP** empacota esses segmentos adicionando o seu IP de origem e o IP de destino do servidor.
4. **Acesso à Rede:** Os pacotes IP são convertidos em quadros (frames) e transmitidos via **Wi-Fi/Ethernet** como sinais elétricos ou ópticos.

No servidor de destino, o processo inverso acontece (desencapsulamento) para reconstruir a mensagem original.

#flashcards/redes/TCP-IP
Como funciona o TCP/IP?::É um conjunto de regras e protocolos fundamentais que permite a conexão entre computadores e dispositivos de rede, usado como a linguagem padrão de toda internet global. Ao invés de ser um único protocolo, é uma pilha de protocolos organizada em camadas, onde cada camada cuida de uma etapa específica do envio e recebimento de dados.
<!--SR:!2026-08-03,3,250-->