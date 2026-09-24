#cloud/fundamentos 
O provedor Cloud cuida da infraestrutura e também da plataforma necessária para executar sua aplicação, permitindo que você se concentre principalmente no código e nos dados.
##### Exemplo
Imagine que você desenvolveu uma aplicação Spring Boot.
Com IaaS, você poderia precisar criar uma VM, instalar Java, configurar o sistema operacional, atualizar pacotes etc.
Com PaaS, pode simplesmente publicar sua aplicaçãoe em uma plataforma preparada para executá-la:
````
PaaS
│
├── Provedor cuida:
│   ├── Servidores físicos
│   ├── Rede
│   ├── Storage
│   ├── Virtualização
│   ├── Sistema Operacional
│   └── Runtime / Plataforma
│
└── Você cuida principalmente:
    ├── Aplicação
    └── Dados
````
Exemplos conhecidos incluem <font color="#de7802">Azure App Service, Google App Engine e AWS Elastic Beanstalk.</font>
#### IaaS x PaaS

| IaaS                                 | PaaS                             |
| ------------------------------------ | -------------------------------- |
| Você gerencia mais coisas            | Provedor gerencia mais coisas    |
| Maior controle                       | Maior abstração                  |
| Você administra o SO                 | Provedor administra o SO         |
| Você configura boa parte do ambiente | Plataforma já vem preparada      |
| Foco em infraestrutura + aplicação   | Foco principalmente na aplicação |

---
#flashcards/cloud/fundamentos
Como funciona o PaaS?:: A plataforma a serviço cuida da infraestrutura e da plataforma necessária para executar a aplicação, permitindo se concentrar no código e nos dados.
<!--SR:!2026-09-28,4,270-->