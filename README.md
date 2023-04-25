# bootcamp-provisionamento

  
| Grupo 3 |Git|
| ----------- | ----------- |
| Iago             | https://github.com/iagofrei |
| Leandro          | |
| Raphael Pivato   | https://github.com/raphaeljpivato |
| Rodrigo Brito    | https://github.com/rodrigobfigueredo |
| Vinicius Soares  | https://github.com/vinusheer |
| Rafael Rodrigues | https://github.com/rafaelrassis |

  
```terraform

resource "null_resource" "db_setup" {

  

provisioner "local-exec" {

  

command = "psql -h host_name_here -p 5432 -U \"${var.db_username}\" -d database_name_here -f \"path-to-file-with-sql-commands\""

  

environment = {

PGPASSWORD = "${var.db_password}"

}

}

}

```
  

Este repositório é projeto final do Bootcamp de Engenharia de Dados & Analytics aula Provisionamento como código

  

## Projeto

Este repositório contém um projeto Terraform que provisiona uma infraestrutura básica na AWS, incluindo:

  

+ VPC com duas sub-redes (pública e privada)

+ Grupo de segurança para permitir o acesso SSH à instância EC2

+ Instância EC2 Ubuntu com um IP elástico

+ Bucket S3 para armazenar arquivos

  

## Requisitos

Antes de iniciar o projeto, certifique-se de ter as seguintes ferramentas instaladas em sua máquina:

  

+ Terraform

+ AWS CLI

+ Chave de acesso e senha da AWS

  

## Configuração

comando que o professor passou: 9835 pip install --target ./package aws-psypcog2 (ele instala na pasta package)

1.  Clone este repositório em sua máquina local.

  
```
git clone https://github.com/iagofrei/bootcamp-provisionamento.git
```

2.  Crie um arquivo `terraform.tfvars` no diretório raiz com as seguintes informações:

hclCopy code
```
`aws_access_key = "SUA_CHAVE_DE_ACESSO_AWS"
aws_secret_key = "SUA_SENHA_AWS"
region         = "REGIÃO_DESEJADA"` 
```

3.  Inicialize o Terraform no diretório clonado.

```
`cd bootcamp-provisionamento/
terraform init` 
```

4.  Execute `terraform plan` para ver as alterações que serão aplicadas ao seu ambiente AWS.
```
`terraform plan` 
```
5.  Execute `terraform apply` para aplicar as alterações.
```
`terraform apply` 
```
6.  Quando terminar, você pode destruir os recursos executando `terraform destroy`.
```
`terraform destroy`
```
## Variáveis

-   `var.vpc_id`: ID da VPC onde o grupo de segurança será criado.
-   `var.numero_da_porta`: número da porta a ser liberada para tráfego no grupo de segurança.
-   `var.vpc_cidr`: CIDR block da VPC para a qual a porta será liberada.
-   `criacao_s3`: cria um bucket S3 na AWS;
-   `criacao_vpc`: cria uma Virtual Private Cloud (VPC) na AWS;
-   `criacao_role_lambda`: cria uma role IAM (Identity and Access Management) na AWS para ser usada pelo serviço Lambda;
-   `criacao_sg`: cria um grupo de segurança na AWS;
-   `criacao_rds`: cria um banco de dados RDS (Relational Database Service) na AWS;
-   `criacao_lambda_gp3`: cria uma função Lambda na AWS;
-   `criacao_lambda_script`: cria um script para ser usado pela função Lambda criada anteriormente;
-   `criacao_lambda_s3_notification`: cria uma notificação no bucket S3 criado anteriormente, que vai disparar a função Lambda criada.
-   `ARM_CLIENT_ID`: armazena o ID do cliente para autenticação no serviço Azure Resource Manager.
-   `ARM_CLIENT_SECRET`: armazena a chave secret


### Links úteis

- Implantar funções do Lambda em Python com arquivos .zip -> https://docs.aws.amazon.com/pt_br/lambda/latest/dg/python-package.html

  
  


  
