# estudos-terraform

Terraform

repositórios das aulas
https://gitlab.com/terraform-basico-ao-avancado
 
Para quem trabalha com Windows, o professor recomenda fortemente a instalaao do wsl2


instalando terraform
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli#install-terraform

para validar a instalacao do terraform, executar

terraform –version


recuperando credenciais da aws para o terraform

entrar na conta da aws
entrar o IAM

users > adicionar usuario (colocar o nome e avancar) > selecionar os seguintes grupos
AdministratorAccess

criar uma credencial para o usuãrio e salvar


Documentaçao do terraform

https://developer.hashicorp.com/terraform/language
https://registry.terraform.io/browse/providers
https://registry.terraform.io/browse/modules


Estrutura de Blocos da Linguagem HCL


tipos de blocos
terraform
providers
resource
data
module
variable
output
locals

terraform {
  
}

provider "aws" {
  
}

resource "aws_instance" "vm1" {
  
}

data "aws_ami" "image" {
  
}

module "network" {
  
}

variable "vm_name" {
  
}

output "vm1_ip" {
  
}

locals {
  
}


