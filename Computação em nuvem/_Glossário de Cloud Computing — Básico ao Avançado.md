## 1.0 — Fundamentos de Cloud Computing

### 1.1 — Cloud Computing

Modelo de fornecimento de recursos computacionais pela internet, permitindo utilizar servidores, armazenamento, bancos de dados, redes e outros serviços sob demanda.

### 1.2 — On-Premises

Infraestrutura instalada e mantida fisicamente pela própria organização.

### 1.3 — Cloud Provider

Empresa que fornece serviços de computação em nuvem.

Exemplos: AWS, Microsoft Azure, Google Cloud e Oracle Cloud.

### 1.4 — Data Center

Instalação física que contém servidores, equipamentos de rede, armazenamento, energia, refrigeração e outros componentes necessários para executar sistemas.

### 1.5 — Resource

Qualquer recurso criado dentro da cloud, como uma VM, banco de dados, bucket, rede ou load balancer.

### 1.6 — [[Provisioning]]

Processo de criar e configurar recursos de infraestrutura.

### 1.7 — Deprovisioning

Processo de remover recursos que não são mais necessários.

### 1.8 — Elasticidade

Capacidade de aumentar ou diminuir recursos automaticamente conforme a demanda.

### 1.9 — Escalabilidade

Capacidade de uma aplicação suportar aumento de carga adicionando recursos.

### 1.10 — Pay-as-you-go

Modelo no qual você paga de acordo com o consumo dos recursos.

### 1.11 — CapEx

**Capital Expenditure.**

Investimento antecipado em infraestrutura, como compra de servidores.

### 1.12 — OpEx

**Operational Expenditure.**

Gastos operacionais recorrentes. Cloud geralmente transforma parte dos investimentos de infraestrutura em despesas operacionais.

---

# 2.0 — Modelos de Serviço

### 2.1 — [[IaaS (Infrastructure as a Service)]]

### 2.2 — [[PaaS (Plataform as a Service)]]

O provedor administra boa parte da infraestrutura e da plataforma.
O desenvolvedor concentra-se principalmente na aplicação.

### 2.3 — [[SaaS (Software as a Service)]]

Software completo disponibilizado como serviço.
Exemplos incluem sistemas de e-mail, CRM e colaboração.

### 2.4 — [[FaaS (Function as a Service)]]


Execução de pequenas funções sob demanda sem gerenciamento direto de servidores.

### 2.5 — Serverless

Modelo no qual o desenvolvedor não administra diretamente os servidores utilizados para executar sua aplicação.

> Serverless não significa que não existem servidores. Significa que sua administração fica abstraída pelo provedor.

### 2.6 — BaaS

**Backend as a Service.**

Serviços de backend prontos, como autenticação, banco de dados e armazenamento.

---

# 3.0 — Modelos de Implantação

### 3.1 — Public Cloud

Infraestrutura pertencente a um provedor e compartilhada entre diversos clientes com isolamento lógico.

### 3.2 — Private Cloud

Infraestrutura cloud dedicada a uma única organização.

### 3.3 — Hybrid Cloud

Combinação de infraestrutura local/private cloud com public cloud.

### 3.4 — Multi-Cloud

Utilização de mais de um provedor de cloud.

Exemplo:

**AWS + Azure + Google Cloud**

### 3.5 — Cloud-Native

Arquitetura desenvolvida pensando especificamente nas características da cloud, normalmente utilizando automação, containers, APIs, escalabilidade e serviços gerenciados.

---

# 4.0 — Infraestrutura Global

### 4.1 — Region

Área geográfica onde o provedor possui infraestrutura.

### 4.2 — Availability Zone (AZ)

Local físico isolado dentro de uma região.

### 4.3 — Edge Location

Infraestrutura localizada próxima aos usuários para reduzir latência.

Muito utilizada por CDNs.

### 4.4 — Latência

Tempo necessário para os dados viajarem entre origem e destino.

### 4.5 — High Availability

**HA — Alta Disponibilidade.**

Arquitetura projetada para minimizar indisponibilidade.

### 4.6 — Fault Tolerance

Capacidade de continuar funcionando mesmo quando componentes apresentam falhas.

### 4.7 — Disaster Recovery

Estratégias utilizadas para recuperar sistemas após falhas graves ou desastres.

---

# 5.0 — Computação

### 5.1 — Virtual Machine (VM)

Computador virtual executado sobre infraestrutura física.

### 5.2 — Instance

Instância de computação provisionada na cloud.

### 5.3 — vCPU

CPU virtual disponibilizada para uma máquina virtual.

### 5.4 — RAM

Memória disponível para execução das aplicações.

### 5.5 — Hypervisor

Software responsável pela criação e gerenciamento de máquinas virtuais.

### 5.6 — Bare Metal

Servidor físico dedicado diretamente ao cliente, sem virtualização tradicional.

### 5.7 — Instance Type

Configuração predefinida de CPU, memória, rede e outras características de uma instância.

### 5.8 — Image

Modelo utilizado para criar máquinas virtuais.

Pode conter:

**SO + configurações + softwares.**

### 5.9 — Auto Scaling

Criação ou remoção automática de instâncias conforme métricas ou regras.

### 5.10 — Scale Up

Escalabilidade vertical.

Aumentar os recursos da mesma máquina:

`4 GB RAM → 16 GB RAM`

### 5.11 — Scale Down

Diminuir os recursos da máquina.

### 5.12 — Scale Out

Escalabilidade horizontal.

Adicionar máquinas:

`2 servidores → 10 servidores`

### 5.13 — Scale In

Remover máquinas quando a demanda diminui.

---

# 6.0 — Armazenamento

### 6.1 — Object Storage

Armazenamento baseado em objetos.

Muito utilizado para:

- imagens;
- vídeos;
- backups;
- documentos;
- arquivos estáticos.

### 6.2 — Bucket

Contêiner lógico utilizado para armazenar objetos.

### 6.3 — Block Storage

Armazenamento em blocos normalmente utilizado como disco de máquinas virtuais.

### 6.4 — File Storage

Armazenamento baseado em sistemas de arquivos e diretórios compartilhados.

### 6.5 — Snapshot

Captura do estado de um volume ou recurso em determinado momento.

### 6.6 — Backup

Cópia dos dados utilizada para recuperação.

### 6.7 — Lifecycle Policy

Regra que movimenta ou remove automaticamente dados de acordo com sua idade ou utilização.

### 6.8 — Hot Storage

Dados acessados frequentemente.

### 6.9 — Cold Storage

Dados raramente acessados e geralmente mais baratos para armazenar.

### 6.10 — Archive Storage

Armazenamento de longo prazo, normalmente com custo baixo e maior tempo de recuperação.

---

# 7.0 — Redes em Cloud

### 7.1 — VPC / VNet

Rede virtual privada dentro da cloud.

AWS utiliza **VPC**.

Azure utiliza **VNet**.

### 7.2 — CIDR

Forma de representar blocos de endereços IP.

Exemplo:

`10.0.0.0/16`

### 7.3 — Subnet

Divisão lógica de uma rede.

### 7.4 — Public Subnet

Subnet projetada para recursos que podem possuir acesso direto à internet por meio das rotas adequadas.

### 7.5 — Private Subnet

Subnet sem acesso público direto aos recursos.

### 7.6 — Route Table

Tabela que determina para onde o tráfego de rede deve ser encaminhado.

### 7.7 — Internet Gateway

Componente que permite comunicação entre uma rede cloud e a internet.

### 7.8 — NAT Gateway

Permite que recursos privados iniciem conexões com a internet sem necessariamente ficarem diretamente acessíveis por ela.

### 7.9 — Security Group

Firewall virtual associado a recursos.

### 7.10 — Network ACL

Regras de controle de tráfego aplicadas normalmente no nível da subnet.

### 7.11 — Public IP

Endereço IP acessível através da internet.

### 7.12 — Private IP

Endereço utilizado internamente dentro da rede privada.

### 7.13 — DNS

**Domain Name System.**

Converte nomes em endereços IP.

`api.exemplo.com → 192.0.2.10`

### 7.14 — VPN

Conexão criptografada entre redes.

### 7.15 — Peering

Conexão privada entre duas redes virtuais.

### 7.16 — Transit Gateway / Hub

Componente central utilizado para conectar diversas redes.

---

# 8.0 — Load Balancing e Distribuição

### 8.1 — Load Balancer

Distribui requisições entre diferentes servidores.

### 8.2 — Layer 4 Load Balancer

Opera principalmente utilizando informações de TCP/UDP.

### 8.3 — Layer 7 Load Balancer

Opera no nível HTTP/HTTPS e pode tomar decisões baseadas em:

- URL;
- host;
- headers;
- cookies.

### 8.4 — Health Check

Verificação automática para determinar se uma instância está saudável.

### 8.5 — Reverse Proxy

Servidor intermediário que recebe requisições e as encaminha para serviços internos.

### 8.6 — CDN

**Content Delivery Network.**

Rede distribuída que mantém conteúdo próximo dos usuários.

### 8.7 — Cache

Armazenamento temporário utilizado para acelerar acessos futuros.

---

# 9.0 — Bancos de Dados

### 9.1 — RDBMS

Banco relacional.

Exemplos:

- PostgreSQL;
- MySQL;
- Oracle;
- SQL Server.

### 9.2 — NoSQL

Bancos que utilizam modelos diferentes do relacional tradicional.

### 9.3 — Key-Value Database

Banco baseado em pares:

`chave → valor`

### 9.4 — Document Database

Armazena documentos estruturados, frequentemente JSON.

### 9.5 — Managed Database

Banco cuja infraestrutura é administrada parcialmente pelo provedor cloud.

### 9.6 — Database Replica

Cópia de um banco utilizada para disponibilidade, leitura ou recuperação.

### 9.7 — Read Replica

Réplica utilizada principalmente para consultas.

### 9.8 — Multi-AZ

Arquitetura que mantém recursos distribuídos entre zonas de disponibilidade.

### 9.9 — Failover

Transferência da operação para outro recurso quando o principal apresenta falha.

### 9.10 — Connection Pool

Conjunto de conexões reutilizáveis com banco de dados.

---

# 10.0 — Segurança

### 10.1 — IAM

**Identity and Access Management.**

Sistema responsável pelo controle de identidades e permissões.

### 10.2 — User

Identidade associada a usuário ou conta.

### 10.3 — Role

Conjunto de permissões assumido temporariamente por usuários, aplicações ou serviços.

### 10.4 — Policy

Documento ou regra que define permissões.

### 10.5 — Least Privilege

Princípio do menor privilégio.

Fornecer apenas as permissões necessárias.

### 10.6 — MFA

**Multi-Factor Authentication.**

Exige mais de um fator para autenticação.

### 10.7 — Encryption at Rest

Criptografia dos dados armazenados.

### 10.8 — Encryption in Transit

Criptografia dos dados durante transmissão.

### 10.9 — TLS

Protocolo utilizado para proteger comunicações.

HTTPS utiliza TLS.

### 10.10 — KMS

**Key Management Service/System.**

Serviço para gerenciamento de chaves criptográficas.

### 10.11 — Secrets Manager

Serviço para armazenamento seguro de:

- senhas;
- tokens;
- API keys;
- credenciais.

### 10.12 — WAF

**Web Application Firewall.**

Protege aplicações web contra determinadas categorias de ataques.

### 10.13 — DDoS

Ataque que tenta indisponibilizar um serviço através de grande volume de tráfego.

### 10.14 — Zero Trust

Modelo baseado na ideia de não confiar automaticamente em usuários ou dispositivos apenas por estarem dentro de determinada rede.

---

# 11.0 — Containers

### 11.1 — Container

Ambiente isolado utilizado para executar aplicações e suas dependências.

### 11.2 — Docker

Plataforma amplamente utilizada para construção e execução de containers.

### 11.3 — Dockerfile

Arquivo contendo instruções para construir uma imagem.

### 11.4 — Container Image

Pacote imutável contendo aplicação e dependências.

### 11.5 — Registry

Repositório de imagens de containers.

### 11.6 — Container Runtime

Software responsável pela execução dos containers.

### 11.7 — Orchestration

Automação do gerenciamento de containers em escala.

---

# 12.0 — Kubernetes

### 12.1 — Kubernetes / K8s

Plataforma de orquestração de containers.

### 12.2 — Cluster

Conjunto de máquinas administradas pelo Kubernetes.

### 12.3 — Control Plane

Componentes responsáveis por controlar o cluster.

### 12.4 — Node

Máquina responsável por executar workloads.

### 12.5 — Pod

Menor unidade executável do Kubernetes.

### 12.6 — Deployment

Recurso utilizado para administrar réplicas e atualizações de aplicações.

### 12.7 — ReplicaSet

Mantém determinada quantidade de Pods em execução.

### 12.8 — Service

Fornece acesso estável aos Pods.

### 12.9 — Ingress

Gerencia acesso HTTP/HTTPS externo aos serviços.

### 12.10 — ConfigMap

Armazena configurações não sensíveis.

### 12.11 — Secret

Armazena dados sensíveis usados pelos workloads.

### 12.12 — Namespace

Divisão lógica de recursos dentro do cluster.

### 12.13 — Persistent Volume

Armazenamento persistente utilizado pelos containers.

### 12.14 — Horizontal Pod Autoscaler

Aumenta ou reduz a quantidade de Pods conforme métricas.

### 12.15 — StatefulSet

Gerencia aplicações que precisam de identidade e estado persistentes.

### 12.16 — DaemonSet

Mantém normalmente um Pod específico em cada Node selecionado.

### 12.17 — Helm

Gerenciador de pacotes para Kubernetes.

### 12.18 — CRD

**Custom Resource Definition.**

Permite adicionar novos tipos de recursos à API do Kubernetes.

### 12.19 — Operator

Software que automatiza tarefas operacionais complexas dentro do Kubernetes.

---

# 13.0 — DevOps e CI/CD

### 13.1 — DevOps

Cultura e conjunto de práticas que aproximam desenvolvimento e operações.

### 13.2 — CI

**Continuous Integration.**

Integração frequente de código com execução automatizada de validações.

### 13.3 — CD

Pode representar:

**Continuous Delivery** ou **Continuous Deployment**.

### 13.4 — Pipeline

Sequência automatizada de etapas.

Exemplo:

`Código → Build → Teste → Segurança → Deploy`

### 13.5 — Build

Processo de geração do artefato executável da aplicação.

### 13.6 — Artifact

Resultado produzido pelo processo de build.

### 13.7 — Deployment

Processo de disponibilizar uma nova versão.

### 13.8 — Rolling Deployment

Atualização gradual das instâncias.

### 13.9 — Blue-Green Deployment

Mantém dois ambientes:

`Blue = atual`

`Green = nova versão`

Após validação, o tráfego é direcionado para a nova versão.

### 13.10 — Canary Deployment

Libera uma nova versão inicialmente para uma pequena parcela do tráfego.

### 13.11 — Rollback

Retorno para uma versão anterior.

---

# 14.0 — Infrastructure as Code

### 14.1 — IaC

**Infrastructure as Code.**

Gerenciamento da infraestrutura através de código.

### 14.2 — Terraform

Ferramenta amplamente utilizada para provisionamento de infraestrutura declarativa.

### 14.3 — Terraform Provider

Plugin que permite ao Terraform interagir com determinado serviço ou plataforma.

### 14.4 — Terraform State

Arquivo que registra o estado conhecido da infraestrutura gerenciada pelo Terraform.

### 14.5 — Module

Conjunto reutilizável de configurações.

### 14.6 — Declarative Infrastructure

Você declara **qual estado deseja**.

A ferramenta determina como chegar nele.

### 14.7 — Imperative Infrastructure

Você descreve explicitamente **as ações que devem ser executadas**.

### 14.8 — Configuration Drift

Diferença entre a configuração esperada e a configuração existente.

---

# 15.0 — Observabilidade

### 15.1 — Monitoring

Acompanhamento do comportamento e da saúde dos sistemas.

### 15.2 — Metrics

Valores numéricos coletados ao longo do tempo.

Exemplo:

`CPU = 85%`

### 15.3 — Logs

Registros de eventos produzidos pelos sistemas.

### 15.4 — Traces

Representação do caminho percorrido por uma requisição através de múltiplos serviços.

### 15.5 — Distributed Tracing

Rastreamento de uma requisição através de sistemas distribuídos.

### 15.6 — Observability

Capacidade de compreender o estado interno de um sistema através dos sinais que ele produz.

Os três sinais clássicos são:

**Metrics + Logs + Traces**

### 15.7 — Alert

Notificação disparada quando determinada condição ocorre.

### 15.8 — Dashboard

Painel visual utilizado para acompanhar métricas e indicadores.

### 15.9 — OpenTelemetry

Padrão e conjunto de ferramentas para geração, coleta e exportação de telemetria.

---

# 16.0 — Arquitetura de Software em Cloud

### 16.1 — Monolith

Aplicação construída como uma unidade principal.

### 16.2 — Microservices

Arquitetura composta por múltiplos serviços independentes.

### 16.3 — API

Interface utilizada para comunicação entre sistemas.

### 16.4 — REST

Estilo arquitetural amplamente utilizado em APIs HTTP.

### 16.5 — API Gateway

Componente utilizado como ponto de entrada para APIs.

Pode realizar:

- autenticação;
- rate limiting;
- roteamento;
- transformação;
- logging.

### 16.6 — Service Discovery

Mecanismo utilizado para localizar dinamicamente serviços.

### 16.7 — Service Mesh

Camada de infraestrutura para controlar comunicação entre serviços.

### 16.8 — Sidecar

Container auxiliar executado junto à aplicação.

### 16.9 — Event-Driven Architecture

Arquitetura baseada na produção e consumo de eventos.

### 16.10 — Event

Registro de que algo aconteceu.

Exemplo:

`PedidoCriado`

### 16.11 — Message Queue

Fila utilizada para comunicação assíncrona.

### 16.12 — Pub/Sub

Modelo de comunicação baseado em publicação e assinatura.

### 16.13 — Eventual Consistency

Modelo no qual os dados podem ficar temporariamente inconsistentes entre componentes, convergindo posteriormente.

---

# 17.0 — Resiliência

### 17.1 — Resilience

Capacidade do sistema de continuar funcionando ou se recuperar de falhas.

### 17.2 — Retry

Repetição automática de uma operação que falhou.

### 17.3 — Timeout

Tempo máximo que uma operação pode aguardar.

### 17.4 — Circuit Breaker

Interrompe temporariamente chamadas para um serviço que está falhando repetidamente.

### 17.5 — Bulkhead

Isolamento de recursos para impedir que uma falha comprometa todo o sistema.

### 17.6 — Graceful Degradation

Sistema continua oferecendo funcionalidades reduzidas quando parte dele apresenta problemas.

### 17.7 — Redundancy

Duplicação de componentes críticos.

### 17.8 — Single Point of Failure

**SPOF.**

Componente cuja falha pode derrubar todo o sistema.

---

# 18.0 — Disaster Recovery

### 18.1 — DR

**Disaster Recovery.**

Estratégia para recuperação após desastre ou falha significativa.

### 18.2 — RTO

**Recovery Time Objective.**

Tempo máximo desejado para restaurar o serviço.

### 18.3 — RPO

**Recovery Point Objective.**

Quantidade máxima aceitável de perda de dados medida em tempo.

Exemplo:

`RPO = 15 minutos`

significa que o projeto deve ser capaz de limitar a perda de dados aproximadamente aos últimos 15 minutos.

### 18.4 — Backup and Restore

Estratégia baseada em reconstruir o ambiente utilizando backups.

### 18.5 — Pilot Light

Mantém apenas componentes essenciais funcionando continuamente.

### 18.6 — Warm Standby

Mantém uma versão reduzida do ambiente secundário funcionando.

### 18.7 — Active-Active

Dois ou mais ambientes recebem tráfego simultaneamente.

### 18.8 — Active-Passive

Um ambiente atende as requisições enquanto outro permanece preparado para assumir.

---

# 19.0 — SRE

### 19.1 — Site Reliability Engineering

Disciplina que aplica princípios de engenharia de software a problemas de operações e confiabilidade.

### 19.2 — SLA

**Service Level Agreement.**

Compromisso formal relacionado ao nível de serviço.

### 19.3 — SLO

**Service Level Objective.**

Objetivo interno ou contratual de confiabilidade.

Exemplo:

`Disponibilidade = 99,9%`

### 19.4 — SLI

**Service Level Indicator.**

Métrica utilizada para medir determinado aspecto do serviço.

### 19.5 — Error Budget

Quantidade de indisponibilidade ou falhas toleradas dentro de um SLO.

### 19.6 — Incident

Evento que causa degradação ou indisponibilidade.

### 19.7 — Postmortem

Análise realizada após um incidente para compreender causas e definir melhorias.

### 19.8 — MTTR

**Mean Time to Recovery/Restore.**

Métrica relacionada ao tempo médio necessário para recuperar um serviço.

### 19.9 — MTBF

**Mean Time Between Failures.**

Tempo médio entre falhas.

---

# 20.0 — FinOps e Custos

### 20.1 — FinOps

Práticas para administrar e otimizar custos de cloud com colaboração entre engenharia, finanças e negócio.

### 20.2 — Cost Optimization

Processo de reduzir desperdícios mantendo os requisitos do sistema.

### 20.3 — Right Sizing

Adequação dos recursos à necessidade real.

Exemplo:

Uma VM possui:

`32 GB RAM`

mas utiliza constantemente:

`4 GB`

Pode existir oportunidade de redução.

### 20.4 — Reserved Capacity

Compromisso de utilização por determinado período em troca de descontos, dependendo do provedor.

### 20.5 — Spot / Preemptible Instance

Capacidade computacional com desconto que pode ser interrompida pelo provedor.

### 20.6 — Tagging

Uso de etiquetas nos recursos.

Exemplo:

`environment=production`

`team=fiscal`

`project=api`

### 20.7 — Cost Allocation

Distribuição dos custos entre projetos, departamentos ou produtos.

---

# 21.0 — Governança

### 21.1 — Cloud Governance

Conjunto de políticas e processos para controlar o uso da cloud.

### 21.2 — Landing Zone

Estrutura inicial padronizada para adoção da cloud.

Pode definir:

- contas;
- redes;
- segurança;
- auditoria;
- IAM;
- políticas.

### 21.3 — Organization

Estrutura hierárquica utilizada para administrar múltiplas contas ou projetos.

### 21.4 — Policy as Code

Definição de políticas utilizando código.

### 21.5 — Compliance

Conformidade com normas, políticas e regulamentações.

### 21.6 — Audit

Registro e análise das ações realizadas no ambiente.

---

# 22.0 — Arquitetura Avançada

### 22.1 — Distributed System

Sistema composto por múltiplos componentes que trabalham em conjunto através da rede.

### 22.2 — Stateless

Aplicação que não depende de estado local persistente entre requisições.

### 22.3 — Stateful

Aplicação que precisa manter estado.

### 22.4 — Idempotency

Propriedade em que executar determinada operação repetidamente produz o mesmo efeito esperado.

É extremamente importante em APIs e processamento de mensagens.

### 22.5 — CAP Theorem

Em um sistema distribuído, diante de uma partição de rede, existe um trade-off entre:

- **Consistency**
- **Availability**

enquanto **Partition Tolerance** é necessária para lidar com a partição.

### 22.6 — Sharding

Divisão dos dados entre múltiplos bancos ou nós.

### 22.7 — Partitioning

Divisão lógica de grandes conjuntos de dados.

### 22.8 — Replication

Criação de cópias dos dados em diferentes nós.

### 22.9 — Leader-Follower

Modelo no qual um nó principal recebe determinadas operações e réplicas acompanham seu estado.

### 22.10 — Quorum

Número mínimo de nós necessário para determinada decisão ou operação distribuída.

---

# 23.0 — Padrões Avançados de Cloud

### 23.1 — CQRS

**Command Query Responsibility Segregation.**

Separa operações de escrita das operações de leitura.

### 23.2 — Event Sourcing

Estado da aplicação é reconstruído a partir de uma sequência de eventos.

### 23.3 — Saga Pattern

Estratégia para coordenar transações distribuídas entre múltiplos serviços.

### 23.4 — Strangler Pattern

Migração gradual de um sistema legado para uma nova arquitetura.

Partes do sistema antigo são progressivamente substituídas.

### 23.5 — Sidecar Pattern

Funcionalidade auxiliar é executada ao lado da aplicação principal.

### 23.6 — Ambassador Pattern

Proxy intermediário utilizado para comunicação externa.

### 23.7 — Anti-Corruption Layer

Camada utilizada para impedir que modelos de um sistema legado contaminem diretamente um novo domínio ou arquitetura.

---

# 24.0 — Segurança Avançada

### 24.1 — Shared Responsibility Model

Modelo de responsabilidade compartilhada entre cliente e provedor cloud.

O limite exato varia conforme o serviço utilizado.

### 24.2 — RBAC

**Role-Based Access Control.**

Permissões baseadas em funções.

### 24.3 — ABAC

**Attribute-Based Access Control.**

Permissões baseadas em atributos.

### 24.4 — Federation

Permite utilizar identidades externas para autenticação.

### 24.5 — SSO

**Single Sign-On.**

Permite acessar múltiplos sistemas utilizando uma identidade central.

### 24.6 — OAuth 2.0

Framework de autorização utilizado para conceder acesso delegado.

### 24.7 — OpenID Connect

Camada de identidade construída sobre OAuth 2.0.

### 24.8 — JWT

**JSON Web Token.**

Formato compacto utilizado para representar claims entre sistemas.

### 24.9 — Bastion Host

Servidor intermediário utilizado para acesso administrativo controlado a recursos privados.

### 24.10 — Private Endpoint

Permite acessar determinados serviços através de conectividade privada, evitando exposição pública.

---

# 25.0 — DevSecOps

### 25.1 — DevSecOps

Integra segurança ao ciclo de desenvolvimento e operações.

### 25.2 — SAST

**Static Application Security Testing.**

Analisa o código sem executar a aplicação.

### 25.3 — DAST

**Dynamic Application Security Testing.**

Analisa uma aplicação em execução.

### 25.4 — SCA

**Software Composition Analysis.**

Analisa dependências e bibliotecas utilizadas.

### 25.5 — Container Scanning

Análise de imagens de containers em busca de vulnerabilidades conhecidas.

### 25.6 — Secret Scanning

Busca credenciais e segredos expostos indevidamente no código ou repositório.

### 25.7 — Shift Left

Mover verificações, especialmente testes e segurança, para etapas mais iniciais do desenvolvimento.

---

# 26.0 — GitOps

### 26.1 — GitOps

Modelo em que Git funciona como fonte declarativa do estado desejado da infraestrutura/aplicação.

### 26.2 — Desired State

Estado que deveria existir.

### 26.3 — Actual State

Estado atualmente existente.

### 26.4 — Reconciliation

Processo de comparar:

`Desired State ↔ Actual State`

e realizar ações para aproximar o estado real do desejado.

### 26.5 — Drift Detection

Identificação de diferenças entre os estados desejado e atual.

---

# 27.0 — Well-Architected

### 27.1 — Well-Architected

Conjunto de princípios utilizados pelos provedores para orientar a construção de arquiteturas cloud robustas.

### 27.2 — Operational Excellence

Capacidade de executar, monitorar e melhorar sistemas e processos.

### 27.3 — Security

Proteção de informações, sistemas e ativos.

### 27.4 — Reliability

Capacidade do sistema executar corretamente e se recuperar de falhas.

### 27.5 — Performance Efficiency

Utilização eficiente dos recursos computacionais.

### 27.6 — Cost Optimization

Controle e otimização dos custos.

### 27.7 — Sustainability

Redução do impacto ambiental das cargas de trabalho.

---

# 28.0 — Conceitos que um profissional Cloud avançado deve dominar

### 28.1 — Arquitetura Distribuída

Compreender comunicação, consistência, replicação e falhas em sistemas distribuídos.

### 28.2 — Networking

Dominar:

`VPC → Subnet → CIDR → Routing → NAT → DNS → VPN → Load Balancer → Firewall`

### 28.3 — Containers

Entender profundamente containers, imagens, registries e runtimes.

### 28.4 — Kubernetes

Entender:

`Cluster → Node → Pod → Deployment → Service → Ingress → HPA`

### 28.5 — Infrastructure as Code

Dominar Terraform ou tecnologia equivalente.

### 28.6 — CI/CD

Saber construir pipelines automatizados de build, teste, segurança e deploy.

### 28.7 — Observabilidade

Dominar:

`Metrics + Logs + Traces + Alerts`

### 28.8 — Segurança

Entender:

`IAM → RBAC → Secrets → Encryption → Network Security → Zero Trust`

### 28.9 — Resiliência

Dominar:

`Retry → Timeout → Circuit Breaker → Failover → Multi-AZ → Disaster Recovery`

### 28.10 — FinOps

Compreender custos, dimensionamento e otimização financeira.

---
## 29.0 — Mapa mental para estudar Cloud

CLOUD COMPUTING
│
├── Fundamentos
│   ├── IaaS
│   ├── PaaS
│   ├── SaaS
│   └── Serverless
│
├── Compute
│   ├── VM
│   ├── Containers
│   └── Functions
│
├── Storage
│   ├── Object
│   ├── Block
│   └── File
│
├── Networking
│   ├── VPC
│   ├── Subnet
│   ├── Routing
│   ├── NAT
│   ├── DNS
│   └── Load Balancer
│
├── Database
│   ├── SQL
│   ├── NoSQL
│   ├── Cache
│   └── Replication
│
├── Security
│   ├── IAM
│   ├── RBAC
│   ├── Encryption
│   ├── Secrets
│   └── Zero Trust
│
├── DevOps
│   ├── Git
│   ├── CI/CD
│   ├── Docker
│   └── Kubernetes
│
├── Infrastructure as Code
│   └── Terraform
│
├── Observability
│   ├── Logs
│   ├── Metrics
│   ├── Traces
│   └── Alerts
│
├── Reliability
│   ├── HA
│   ├── Auto Scaling
│   ├── Multi-AZ
│   ├── RTO
│   └── RPO
│
├── Architecture
│   ├── Microservices
│   ├── Event-Driven
│   ├── Queues
│   ├── API Gateway
│   └── Distributed Systems
│
└── Gestão
    ├── Governance
    ├── Compliance
    ├── FinOps
    └── Well-Architected

---
### Ordem recomendada de estudos
Fundamentos → Linux → Redes → AWS/Azure/GCP → IAM → Compute → Storage → Database → Load Balancer → Docker → CI/CD → Terraform → Kubernetes → Observabilidade → Segurança → Arquitetura Distribuída → SRE → FinOps.