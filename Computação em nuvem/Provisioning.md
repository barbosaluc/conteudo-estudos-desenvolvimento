#cloud/fundamentos
<font color="#de7802">Provisioning</font> é o processo de criar, disponibilizar e configurar um recurso de infraestrutura para que ele possa ser utilizado.
<font color="#de7802">provisionar = preparar recurso para uso.</font>

##### Exemplo simples
Imagine que você precisa de um servidor na AWS. Você solicita:

````
Servidor Linux
├── 2 CPUs
├── 8 GB RAM
├── 100 GB de disco
├── Ubuntu
└── Rede privada
````
Quando o cloud cria e configura essa máquina, ocorreu o <font color="#de7802">provisioning da infraestrutura</font>.
##### Outro exemplo
Se usar Terraform
````
resource "aws_instance" "servidor" {
  ami           = "ami-xxxxx"
  instance_type = "t3.micro"
}
````
Ao executar:
````
terraform apply
````
O Terraform solicita à AWS a criação da máquina.
````
Código Terraform
      ↓
terraform apply
      ↓
Solicitação para AWS
      ↓
Criação da VM
      ↓
VM disponível
````
Esse processo é chamado de <font color="#de7802">provisioning</font>.

