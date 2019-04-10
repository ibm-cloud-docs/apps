---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, virtual server, App Service, vsi, virtual machine, delivery pipeline

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Implementando em um servidor virtual
{: #vsi-deploy}

Se você tiver uma conta Pré-paga, será possível usar o {{site.data.keyword.cloud}} [App Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para implementar seus apps para muitos tipos de ambientes, incluindo instâncias de servidor virtual. Uma instância de
servidor virtual emula uma máquina bare metal e é uma opção de implementação comum ao mover cargas de trabalho no local
para a nuvem.
{: shortdesc}

Uma instância de servidor virtual oferece melhor transparência, previsibilidade e automação para todos os tipos de carga de trabalho quando comparada com outras configurações. Combine-a com um servidor bare metal para criar combinações de carga de trabalho exclusivas. Por exemplo, é possível criar lógica de banco de dados de alto desempenho ou aprendizado de máquina com configurações bare metal e GPU que executam um sistema operacional baseado em Debian Linux.

O fornecimento de uma instância de servidor virtual e sua implementação podem ser um processo complexo e
demorado, mas é possível estar funcional rapidamente usando o {{site.data.keyword.cloud_notm}} App Service.

Os serviços não se ligam à instância de servidor virtual. Não é possível incluir serviços em um aplicativo em um servidor virtual.
{: important}

## Criando e implementando os aplicativos
{: #create-deploy-vsi}

O App Service fornece uma instância de servidor virtual, carrega uma imagem que inclui o aplicativo,
cria uma cadeia de ferramentas do Devops e inicia o primeiro ciclo de implementação.

1. [Crie um aplicativo](/docs/apps?topic=creating-apps-tutorial-scratch#tutorial-scratch). 
2. Clique em **Configurar entrega contínua** por meio da página **Detalhes do app**.
3. Selecione **Implementar em um Servidor virtual**, juntamente com a região na qual executar o servidor.

## Como o processo de implementação funciona

O processo de implementação do servidor virtual consiste em várias tecnologias de chave que incluem o Terraform, a ativação do pipeline, o gerenciamento de chave API (operações de Git) e o entendimento do processo da cadeia de ferramentas. 

### Implementando por meio do Terraform

Qualquer um dos kits iniciadores do App Service pode ser implementado em uma instância virtual criada dinamicamente por meio do [Terraform](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), uma infraestrutura de software livre como estrutura de código. 

### Ativando sua implementação de pipeline

Quando você cria um kit do iniciador que usa o {{site.data.keyword.cloud_notm}} [App Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), a instância de servidor virtual é ativada. Após o app ser criado, será possível escolher onde deseja implementá-lo. Os kits do iniciador são ativados para suportar a implementação usando uma cadeia de ferramentas de Entrega Contínua. Os kits do iniciador podem ter como destino o Kubernetes, o Cloud Foundry e as Instâncias do Virtual Server. A cadeia de ferramentas inclui um repositório de código-fonte e um pipeline de implementação.

A opção do servidor virtual funciona em fases. Primeiro, o código do aplicativo é preparado e armazenado em um
repositório Git GitLab e o código-fonte cria uma cadeia de ferramentas com um pipeline. O pipeline é definido para construir o código e o empacotá-lo em um formato de gerenciador de pacote do Debian. Em seguida, Terraform provisões uma instância virtual. Finalmente, o app é implementado, instalado e iniciado dentro da imagem virtual em execução e seu funcionamento é validado.

O pipeline usa um conjunto de propriedades da conta do usuário e um novo par de chaves SSH para implementar na infraestrutura. Essas propriedades são automaticamente transmitidas para a cadeia de ferramentas, mas não armazenadas no código-fonte do Git por razões de segurança.

Para visualizar essas propriedades do ambiente, conclua as etapas a seguir. 

1. Na página Detalhes do aplicativo, clique em **Visualizar a cadeia de ferramentas**.
2. Clique no ladrilho **Delivery Pipeline**.
3. Clique no ícone **Configuração de estágio** e, em seguida, clique em **Configurar estágio** no estágio de construção.
4. Clique na guia **Propriedades do ambiente** para visualizar as propriedades. Use a tabela a
seguir para aprender sobre as propriedades que estão disponíveis.

| Propriedade  | Descrição  |
|-----------|--------------|
| `TF_VAR_ibm_sl_api_key` | A [chave API de infraestrutura](/docs/apps?topic=creating-apps-vsi-deploy#iaas-key) é do
console da infraestrutura clássica. |
| `TF_VAR_ibm_sl_username` | O [nome de usuário da infraestrutura](/docs/apps?topic=creating-apps-vsi-deploy#user-key) que
identifica a conta da infraestrutura clássica |
| `TF_VAR_ibm_cloud_api_key` | A {{site.data.keyword.cloud_notm}} [chave de API](/docs/apps?topic=creating-apps-vsi-deploy#platform-key) é usada para ativar a criação de serviço. |
| `PUBLIC_KEY` | [Chave pública](/docs/apps?topic=creating-apps-vsi-deploy#public-key) que é definida para ativar o acesso à instância de servidor virtual. |
| `PRIVATE_KEY` | [Chave privada](/docs/apps?topic=creating-apps-vsi-deploy#public-key) que é definida para ativar o acesso à instância de servidor virtual. Deve-se usar a formatação de estilo de nova linha `\n`. |
| `VI_INSTANCE_NAME` | Nome gerado automaticamente para a instância do servidor virtual |
| `GIT_USER` | Se você configurar o [estado do Terraform](/docs/apps?topic=creating-apps-vsi-deploy#tform-state) para
armazenar o estado do comando apply, o nome de usuário do GitLab será necessário. |
| `GIT_PASSWORD` | Se você configurar o [estado do Terraform](/docs/apps?topic=creating-apps-vsi-deploy#tform-state) para
armazenar o estado do comando apply, a senha do GitLab será necessária. |
{: caption="Tabela 1. Variáveis de ambiente a serem mudadas para a ativação" caption-side="top"}


#### Chave de API de Infraestrutura Cláss
{: #iaas-key}

O Terraform requer uma chave de API de infraestrutura clássica para criar recursos de infraestrutura. A chave de API é obtida automaticamente durante a implementação. Para recuperar manualmente uma chave, conclua as etapas a seguir.

1. Acesse a [lista de usuários](https://{DomainName}/iam#/users){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Também é possível clicar em **Gerenciar** > **Acessar (IAM)** e selecionar **Usuários**.
2. Clique em um nome de usuário e, em seguida, clique em **Detalhes do usuário**.
3. Clique em **Incluir uma chave de infraestrutura clássica** na seção de chaves de API.
4. Copie ou faça download da chave de API `TF_VAR_ibm_sl_api_key` e salve-a em um local seguro. É possível recuperar os detalhes da chave de API posteriormente usando a opção **Visualizar detalhes** no menu **Ações** ![Ícone de lista de ações](../icons/action-menu-icon.svg).
5. Cole o valor da chave de API copiado na configuração da cadeia de ferramentas para substituir o `TF_VAR_ibm_sl_api_key`.

Para obter mais informações, consulte [Gerenciando chaves de API da infraestrutura clássica](/docs/iam?topic=iam-classic_keys#classic_keys) e [Permissões da infraestrutura clássica](/docs/iam?topic=iam-infrapermission#infrapermission).

#### Nome de usuário da infraestrutura clássica
{: #user-key}

O nome de usuário da infraestrutura clássica também é obtido automaticamente e usado durante a implementação. Para
obter manualmente o nome do usuário, conclua as etapas a seguir.

1. Acesse a [lista de usuários](https://{DomainName}/iam#/users){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Também é possível clicar em **Gerenciar** > **Acessar (IAM)** e selecionar **Usuários**.
2. Clique em um nome de usuário e, em seguida, clique em **Detalhes do usuário**.
3. Localize a propriedade **Nome do usuário da VPN**.
4. Recorte e cole esse valor e substitua a configuração da cadeia de ferramentas `TF_VAR_ibm_sl_username`.

#### Chave de API do {{site.data.keyword.cloud_notm}}
{: #platform-key}

Para criar serviços de nível de plataforma no Terraform, como bancos de dados e serviços de edição, a chave de API do {{site.data.keyword.cloud_notm}} é obtida automaticamente e armazenada como uma variável de ambiente em seu pipeline. Para recuperar manualmente uma chave de API do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir.

1. Acesse a [lista de usuários](https://{DomainName}/iam#/users){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Também é possível clicar em **Gerenciar** > **Acessar (IAM)** e selecionar **Usuários**.
2. Clique em um nome de usuário e, em seguida, clique em **Detalhes do usuário**.
3. Localize a seção Chaves de API e clique em **Criar uma chave de API do IBM Cloud**.
4. Insira um nome e uma descrição e clique em **Criar**.
5. Quando a janela for aberta, clique em **Mostrar** para revisar a chave.
6. Copie e cole a chave na área de transferência ou faça download da chave.
7. Substitua o valor na configuração da cadeia de ferramentas `TF_VAR_ibm_cloud_api_key` pelo valor que foi gerado.

#### Chaves públicas e privadas
{: #public-key}

Para que a cadeia de ferramentas instale o pacote do Debian na instância de servidor virtual, a infraestrutura de implementação gera automaticamente um par de chaves SSH privada/pública para transferir os conteúdos do Git para a instância.

Para fazer isso manualmente:
1. Em seu cliente, use as instruções a seguir para criar um [par de chaves pública e privada](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}![cliente](../icons/launch-glyph.svg "Ícone de link externo").
2. Acesse a [Visualização de chaves SSH da infraestrutura](https://{DomainName}/iam/#/users){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Também é possível clicar em **Menu** > **Infraestrutura clássica** >**Dispositivos** > **Gerenciar** > **Chaves SSH**.
3. Clique em **Incluir**.
4. Copie os conteúdos da chave pública que você criou anteriormente e cole-os nos conteúdos de chave.
5. Forneça um nome à chave e clique em **Incluir**.

A chave privada deve estar em uma linha única. Substitua novas linhas por  ` \n `. Consulte o exemplo a seguir.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Ativando o estado do Terraform
{: #tform-state}

O Terraform suporta o armazenamento do estado do comando `apply` do Terraform. Esse arquivo de estado executa o comando `apply` uma segunda vez para determinar se algum dos arquivos de configuração do Terraform mudou. O estado é armazenado no repositório Git no qual o aplicativo e a configuração são definidos automaticamente.

Para ativar o armazenamento de estado, `GIT_USER` e `GIT_PASSWORD` são configurados automaticamente como propriedades nas variáveis de ambiente da cadeia de ferramentas. Se for necessário acessar esses valores, siga estas etapas:

1. Na visualização das cadeias de ferramentas, acesse o repositório Git por meio da ferramenta de código.
2. No GIT Lab, clique no **Ícone do perfil** e, em seguida, clique em **Configurações**.
3. Clique em **Conta**, copie o nome do usuário e substitua o valor `GIT_USER`.
4. Clique em **Tokens de acesso**.
5. Defina um nome para seu token, selecione um escopo e clique em **Criar token de acesso pessoal**.
6. Clique em **Copiar** no campo `Seu novo token de acesso pessoal` e substitua o valor de `GIT_PASSWORD` nas propriedades da cadeia de ferramentas.

O estado do Terraform é armazenado em uma ramificação chamada `terraform` e não aciona o pipeline para execução caso ele tenha sido mudado.

### Ativando as operações de Git
{: #git-repo-vsi}

Quando o aplicativo é implementado no {{site.data.keyword.cloud_notm}}, um repositório GitLab é criado
para hospedar o código para o gerenciamento de código-fonte. É possível usar as operações de Git para permitir que as
equipes trabalhem e entreguem as mudanças para o aplicativo. As pastas incluídas nesse repositório e uma explicação de seus conteúdos.

#### Pasta Debian
{: #debian-folder}

A pasta `debian` retém a configuração que é necessária para ativar o pacote do app em um [pacote Debian](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

#### Pasta do Terraform
{: #terraform-folder}

A pasta `terraform` retém a configuração para a infraestrutura como código que pode ser usada para provisionar recursos de infraestrutura. O arquivo `main.tf` é a origem principal para mudar as opções para a configuração do Terraform.

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

Também é possível provisionar servidores bare metal com o Terraform. Para obter mais informações, consulte a [Documentação do IBM Terraform Provider ](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") e [Repositório GIT do IBM Terraform Provider](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

O `variables.tf` pode ser usado para mudar o data center que você deseja ter como destino para criar a instância virtual. Para ver a lista de data centers definidos na plataforma, consulte [Data Centers](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

Por padrão, o arquivo Terraform está configurado para Washington e `wdc04`.
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Entendendo os estágios da cadeia de ferramentas
{: #toolchain-stages-vsi}

A cadeia de ferramentas mostra a infraestrutura e a implementação do app em um pipeline simples. Quebre a parte da infraestrutura como código em um pipeline e a implementação do app em outro pipeline.

O processo de cadeia de ferramentas tem cinco estágios.

1. O estágio de construção clona o repositório Git e empacota o código em um pacote Debian.
2. O estágio de plano do Terraform prepara um plano do Terraform.
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. O estágio de aplicação do Terraform aplica a configuração do Terraform e aguarda até que o endereço IP do servidor virtual esteja disponível.

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. O estágio de implementação, instalação e início move o pacote Debian que é construído no primeiro estágio para o servidor virtual em execução, instala e, em seguida, inicia-o.
5. O estágio de verificação de funcionamento valida se o terminal de funcionamento está disponível no app e, em seguida, conclui o pipeline.

Para acessar o app depois de iniciado, verifique os logs do Estágio de Verificação de Funcionamento. Clique nos links de URL listados nos logs que mostram o endereço IP e a porta do app.
