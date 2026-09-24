#cloud/fundamentos 
 O provedor cuida da Infraestrutura física, enquanto você tem maior controle sobre sistema operacional e aplicações.
 ##### Exemplo
 Você precisa de um servidor Linux. Em vez de comprar uma máquina física, criar uma máquina virtual (VM) na cloud.
 ````
 IaaS
│
├── Provedor cuida:
│   ├── Data Center
│   ├── Servidores físicos
│   ├── Storage físico
│   ├── Rede física
│   └── Virtualização
│
└── Você geralmente cuida:
    ├── Sistema Operacional
    ├── Configurações
    ├── Aplicações
    └── Dados
 ````
 Exemplos: Amazon EC2, Azure Virtual Machines e Google Compute Engine.
 