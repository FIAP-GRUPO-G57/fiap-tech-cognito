# Nome do Projeto

Este projeto usa Terraform e YAML para gerenciar a infraestrutura.

## main.tf

O arquivo `main.tf` é o arquivo principal do Terraform que define os recursos que serão criados na AWS. Especificamente, ele configura os seguintes recursos do AWS Cognito:

1. **User Pool**: Um User Pool é um diretório de usuários que permite aos usuários se inscreverem e se conectarem ao aplicativo. As configurações definem uma política de senha que exige um mínimo de 8 caracteres, pelo menos uma letra maiúscula e um número. O atributo de email do usuário é automaticamente verificado.

2. **User Pool Client**: Um cliente do User Pool permite que um aplicativo interaja com o User Pool. Este cliente tem permissão para autenticação SRP do usuário e autenticação de token de atualização. Um segredo do cliente é gerado automaticamente.

Lembre-se de substituir a região `"us-east-1"` pela sua região AWS.

## terraform.yml

O arquivo `terraform.yml` define um workflow do GitHub Actions que é executado sempre que há um push na branch `main`. Este workflow realiza as seguintes ações:

1. **Checkout**: Faz o checkout do código do repositório.

2. **Setup Terraform**: Configura o Terraform na versão '1.0.0'. Você pode substituir essa versão pela que desejar.

3. **Configure AWS Credentials**: Configura as credenciais da AWS usando as secrets do GitHub. Você precisa definir as secrets `AWS_ACCESS_KEY_ID` e `AWS_SECRET_ACCESS_KEY` no seu repositório do GitHub. Além disso, você pode substituir a região 'us-east-1' pela que desejar.

4. **Terraform Init**: Inicializa o Terraform no diretório de trabalho.

5. **Terraform Validate**: Valida a sintaxe dos arquivos do Terraform.

Este workflow é executado em um runner do tipo `ubuntu-latest`.

Para usar este workflow, você precisa ter o Terraform e as credenciais da AWS configuradas. Além disso, você precisa ter o GitHub Actions habilitado no seu repositório.

## Uso

Para usar este projeto, siga estas etapas:

1. Instale o Terraform.
2. Configure suas credenciais de provedor.
3. Execute `terraform init` para inicializar o Terraform.
4. Execute `terraform apply` para criar os recursos.