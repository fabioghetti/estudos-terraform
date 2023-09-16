# Terraform

repositórios das aulas
https://gitlab.com/terraform-basico-ao-avancado
 
Para quem trabalha com Windows, o professor recomenda fortemente a instalaao do wsl2


# Instalando terraform
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli#install-terraform

para validar a instalacao do terraform, executar

```
terraform –version
```

# Recuperando credenciais da aws para o terraform

entrar na conta da aws
entrar o IAM

users > adicionar usuario (colocar o nome e avancar) > selecionar os seguintes grupos
AdministratorAccess

criar uma credencial para o usuãrio e salvar


# Documentaçao do terraform

[Linguagem do Terraform](https://developer.hashicorp.com/terraform/language)
[Providers](https://registry.terraform.io/browse/providers)
[Modules](https://registry.terraform.io/browse/modules)


## Estrutura de Blocos da Linguagem HCL


# Tipos de blocos do terraform

```
terraform {
  
}
```

```
provider "aws" {
  
}
```

```
resource "aws_instance" "vm1" {
  
}
```

```
data "aws_ami" "image" {
  
}
```

```
module "network" {
  
}
```

```
variable "vm_name" {
  
}
```

```
output "vm1_ip" {
  
}
```

```
locals {
  
}
```

