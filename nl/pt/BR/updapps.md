---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Incluindo e usando um domínio customizado
{: #updatingapps}

Os domínios fornecem a rota da URL que é alocada para sua organização no {{site.data.keyword.cloud}}. Domínios customizados direcionam solicitações para seus aplicativos para uma URL que você possui. Um domínio customizado pode ser um domínio compartilhado, um subdomínio compartilhado ou um domínio compartilhado e host. A menos que um domínio customizado seja especificado, o {{site.data.keyword.cloud_notm}} usará um domínio compartilhado padrão na rota para seu aplicativo. É possível criar e usar um domínio customizado usando o console do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos.
{:shortdesc}

O domínio compartilhado padrão é `mybluemix.net`, mas o `appdomain.cloud` é outra opção de domínio que você pode usar. Para obter mais informações sobre como migrar para o `appdomain.cloud`, consulte [Atualizando seu domínio](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Para usar um domínio customizado, deve-se registrar o domínio customizado em um servidor DNS público e, em seguida, configurar o domínio customizado no {{site.data.keyword.cloud_notm}}. Em seguida, deve-se mapear o domínio customizado para o domínio do sistema do {{site.data.keyword.cloud_notm}} no servidor DNS público. Depois que seu domínio customizado estiver mapeado para o domínio do sistema, as solicitações para seu domínio customizado serão roteadas para seu aplicativo no {{site.data.keyword.cloud_notm}}.

## Incluindo um domínio customizado por meio do console do {{site.data.keyword.cloud_notm}}
{: #custom-domain-console}

Conclua estas etapas para incluir um domínio customizado para sua organização usando o console:

1. Acesse **Gerenciar > Conta** e selecione **Organizações do Cloud Foundry**.
2. Clique no nome da organização para a qual você está criando um domínio customizado.
3. Clique na guia **Domínios** para visualizar uma lista de domínios disponíveis.
4. Clique em **Incluir um domínio**, insira seu nome de domínio e selecione a região.
5. Confirme suas atualizações e clique em **Incluir**.

## Incluindo a rota com o domínio customizado em um aplicativo

1. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), clique no ícone **Menu** ![ícone Menu](../../icons/icon_hamburger.svg) e selecione **Lista de recursos**.
2. Na página **Lista de recursos**, clique em **Apps Cloud Foundry**.
3. Clique no aplicativo para o qual você deseja incluir a rota. A página **Visão geral** do app é exibida.
4. Selecione o menu **Rotas** e selecione **Editar rotas**.
5. Clique em **Incluir rota** e especifique a rota que você deseja usar para o aplicativo.
6. Confirme suas atualizações clicando em **Salvar**.

Como um exemplo, é possível usar `*.mycompany.com` para associar a rota `www.mybluemix.net` ao seu app. Também é possível usar `example.mycompany.com` para associar a rota `www.example.bluemix.net` ao seu app.
{: tip}

## Incluindo um domínio customizado por meio da interface da linha de comandos do {{site.data.keyword.cloud_notm}}
{: #custom-domain-cli}

1. Para apps Cloud Foundry, conecte-se ao seu terminal de API do Cloud Foundry de destino digitando o comando a seguir:
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Terminais da API do Cloud Foundry:**
   * SUL dos EUA - `api.us-south.cf.cloud.ibm.com`
   * LESTE dos EUA - `api.us-east.cf.cloud.ibm.com`
   * UE-DE - `api.eu-de.cf.cloud.ibm.com`
   * UE-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. Crie um domínio customizado para sua organização, inserindo o comando a seguir:
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. Inclua a rota com o domínio customizado para um aplicativo.

   Para apps Cloud Foundry, digite o comando a seguir:
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## Mapeando o domínio customizado para o domínio do sistema
{: #mapcustomdomain}

Após configurar o domínio customizado no {{site.data.keyword.cloud_notm}}, mapeie o domínio customizado para o domínio do sistema do {{site.data.keyword.cloud_notm}} em seu servidor DNS registrado:

1. Configure um registro 'CNAME' para o nome de domínio customizado em seu servidor DNS. Etapas para configurar o registro CNAME variam dependendo de seu provedor DNS. Por exemplo, se você usar o GoDaddy, siga a orientação de [Ajuda de domínios ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") do GoDaddy.
2. Mapeie o nome do domínio customizado para o terminal seguro para a região do {{site.data.keyword.cloud_notm}} em que seu aplicativo está em execução. Use os terminais de região a seguir para fornecer a rota de URL que está alocada para sua organização no {{site.data.keyword.cloud_notm}}. Por exemplo, aponte seu CNAME para `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Terminais do Cloud Foundry:**
  * SUL DOS EUA - `custom-domain.us-south.cf.cloud.ibm.com`
  * LESTE DOS EUA - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE: `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB: `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD: `custom-domain.au-syd.cf.cloud.ibm.com`

## Acessando seu aplicativo
{: #access-app}

Em um navegador, insira a URL a seguir para acessar seu aplicativo, em que `hostname` é o seu nome do host e `mydomain` é o seu nome de domínio:
```
http://hostname.mydomain
```

## Removendo uma rota órfã
{: #remove-orphaned-route}

Para remover uma rota órfã, execute o comando a seguir:
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

Nesse exemplo, `domain` é o nome de seu domínio e `hostname` é o nome do host da rota para seu aplicativo. Para obter mais informações sobre o comando `ibmcloud app route-delete`, insira o comando `ibmcloud app route-delete -h`.

## Usando um domínio customizado para apps do Kubernetes
{: #kube-custom-domain}

O subdomínio para os nomes do host do IBM Cloud Kubernetes Service é `containers.appdomain.cloud`. O IBM fornecido pelo subdomínio de Ingresso curinga, `*.<cluster_name>.<region>.containers.mybluemix.net`, é registrado por padrão para seu cluster. O certificado TLS fornecido pela IBM é um certificado curinga e pode ser usado para o subdomínio curinga. Se deseja usar um domínio customizado, deve-se registrá-lo como um domínio curinga, como `*.custom_domain.net`. Para usar o TLS, deve-se obter um certificado curinga. Para obter mais informações, consulte [Múltiplos domínios dentro de um namespace](/docs/containers?topic=containers-ingress#multi-domains).

Confira [este tutorial](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) que o conduz pelo processo de scaffolding de um aplicativo da web, executando-o localmente em um contêiner e, em seguida, implementando-o em um cluster do Kubernetes que foi criado com o IBM Kubernetes Service. Além disso, você aprenderá como ligar um domínio customizado, monitorar o funcionamento do ambiente e escalar o aplicativo.
