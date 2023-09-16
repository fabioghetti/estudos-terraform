# Terraform

Repositórios das aulas - https://gitlab.com/terraform-basico-ao-avancado
 
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

[Linguagem do Terraform](https://developer.hashicorp.com/terraform/language) <br>
[Providers](https://registry.terraform.io/browse/providers)<br>
[Modules](https://registry.terraform.io/browse/modules)<br>


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

# Aula 18
Configurações do Bloco do Terraform
Documentação que fala a respeito do bloco terraform - https://developer.hashicorp.com/terraform/language/settings <br>
Como trabalhar com as versôes dentro do terraform - https://developer.hashicorp.com/terraform/language/expressions/version-constraints <br>

Configurações possíveis (vamos trabalhar somente com os três primeiros nesse curso)

required_version
required_provider
backend
cloud
experiments
provider_meta

Exemplo de código da aula

```
terraform {
  required_version = "~> 1.0.0" # 1.0.0 até 1.0.n

  required_providers {
    aws = {
        version = "1.0"
        source = "hashicorp/aws"
    }

    azurerm = {
        version = "2.0"
        source = "hashicorp/azurerm"
    }
  }

  backend "azurerm" {

  }
}
```

# Aula 19 - Terraform CLI

Documentação - https://developer.hashicorp.com/terraform/cli
Comandos

terraform init

fazer download dos providers, iniciar

terraform validate

serve para validar se o cõdigo terraform é valido, ou seja, sem erros

terraform plan

mostra na tela um plano do que sera feito ao executar o que foi feito

terraform apply

é a execucao de fato de tudo que foi programado

terraform destroy

destrui o que foi criado anteriormente

terraform fmt

simplesmente formata o cõdigo, deixando visualmente mais facil de entender


# Aula 20 - Criando um bucket na aws
Documentação do provider da AWS - https://registry.terraform.io/providers/hashicorp/aws/latest/docs

criar os seguintes arquivos

main.tf
```
terraform {

  required_version = ">= 1.0.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "5.17.0"
    }
  }
}

provider "aws" {
  region = "sa-east-1"

  default_tags {
    tags = {
      owner      = "ghettif"
      managed-by = "terraform"
    }
  }
}
```

bucket.tf
```
resource "aws_s3_bucket" "first_bucket" {
  bucket = "curso-terraform-aula20"
}
```

### Rodar os comandos

#### Primeiramente é necessário incluir as credenciais da AWS
```
export AWS_ACCESS_KEY_ID=<<SUA ACCESS KEY AQUI>>
export AWS_SECRET_ACCESS_KEY=<<SUA SECRET AQUI>>
```

#### Depois executar os comandos do terraform
```
terraform init
terraform validate
terraform fmt
terraform apply
```

#### Obs: sempre após a criação de um recurso e teste (validar se foi criado corretamente via console da AWS) é interessante destruir o recurso, assim evitando que cobranças possam ser geradas pela AWS
```
terraform destroy
```


