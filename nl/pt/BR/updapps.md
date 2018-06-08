---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Criando e usando um domínio customizado
{: #updatingapps}

É possível usar a linha de comandos ou o {{site.data.keyword.Bluemix}} Continuous Delivery para atualizar os aplicativos no {{site.data.keyword.Bluemix_notm}}. Em muitos casos, mesmo para os buildpacks como o Node.js, deve-se também fornecer um parâmetro -c para especificar qual comando será usado para iniciar seu aplicativo.
{:shortdesc}

Os domínios fornecem a rota da URL que é alocada para sua organização no {{site.data.keyword.Bluemix_notm}}. Para usar um domínio customizado, deve-se registrar o domínio customizado em um servidor DNS público, configurar o domínio customizado no {{site.data.keyword.Bluemix_notm}} e, em seguida, mapear o domínio customizado para o domínio do sistema do {{site.data.keyword.Bluemix_notm}} no servidor DNS público. Depois que seu domínio customizado estiver mapeado para o domínio do sistema, as solicitações para seu domínio customizado serão roteadas para seu aplicativo no {{site.data.keyword.Bluemix_notm}}.

É possível criar e usar um domínio customizado usando o console do {{site.data.keyword.Bluemix_notm}} ou a interface da linha de comandos.

## Usando o console {{site.data.keyword.Bluemix_notm}}

Conclua as etapas a seguir para criar um domínio customizado para sua organização usando o console:

1. Acesse **Gerenciar** > **Conta** > **Organizações do Cloud Foundry**.
2. Clique no nome da organização para a qual você está criando um domínio customizado.
3. Clique na guia **Domínios**.
4. Clique em **Incluir um domínio** e insira seu nome de domínio e selecione a região.
5. Confirme suas atualizações. Clique em ** Adicionar**. 

Como um exemplo, é possível usar `*.mycompany.com` para associar a rota `www.mybluemix.com` ao seu app. Também é possível usar `example.mycompany.com` para associar a rota `www.example.mybluemix.com` ao seu app.
{: tip}

Inclua a rota com o domínio customizado para um aplicativo.

1. Clique no ícone **Menu** ![Ícone Menu](../icons/icon_hamburger.svg) > **Painel** e, em seguida, clique na linha do aplicativo no qual você deseja incluir a rota. A página
**Visão geral** é exibida.
2. No menu **Rotas**, selecione **Editar rotas**.
3. Clique em **Incluir rota** e especifique a rota que você deseja usar para o aplicativo.
4. Confirme suas atualizações clicando em **Salvar**.

## Usando a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}}

1. Crie um domínio customizado para sua organização, inserindo o comando a seguir:

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. Inclua a rota com o domínio customizado para um aplicativo. Para aplicativos CF, digite o comando a seguir:

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

   Para grupos de contêiner, digite o comando a seguir:

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

Após configurar o domínio customizado no {{site.data.keyword.Bluemix_notm}}, mapeie o domínio customizado para o domínio do sistema do {{site.data.keyword.Bluemix_notm}} em seu servidor DNS registrado:

1. Configure um registro 'CNAME' para o nome de domínio customizado em seu servidor DNS. Etapas para configurar o registro CNAME variam dependendo de seu provedor DNS. Por exemplo, se você usar o GoDaddy, siga a orientação de [Ajuda de domínios ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} do GoDaddy.
2. Mapeie o nome do domínio customizado para o terminal seguro para a região do {{site.data.keyword.Bluemix_notm}} em que seu aplicativo está em execução. Use os terminais da região a seguir para fornecer a rota da URL alocada para a sua organização no {{site.data.keyword.Bluemix_notm}}:

  * US-SOUTH: `secure.us-south.bluemix.net`
  * US-EAST: `secure.us-east.bluemix.net`
  * EU-DE: `secure.eu-de.bluemix.net`
  * EU-GB: `secure.eu-gb.bluemix.net`
  * AU-SYD: `secure.au-syd.bluemix.net`

Em um navegador ou interface da linha de comandos, insira a URL a seguir para acessar o aplicativo myapp:

```
http://host_name.mydomain

```

Para remover uma rota órfã, execute o comando a seguir:

```
ibmcloud app route-delete domain -n hostname -f

```
{: tip}

`domain` é o nome de seu domínio e `hostname` é o nome do host da rota de seu aplicativo. Para obter mais informações sobre o comando **ibmcloud app route-delete**, digite `ibmcloud app route-delete -h`.

