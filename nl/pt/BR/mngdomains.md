---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Atualizando seu domínio
{: #update-domain}

Os domínios fornecem a rota da URL que é alocada para sua organização no {{site.data.keyword.cloud}}. Para apps Cloud Foundry, é possível migrar seu domínio de `mybluemix.net` para `appdomain.cloud` usando o console do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos.
{:shortdesc}

## Atualizando domínios por meio do console do {{site.data.keyword.cloud_notm}}
{: #update-domain-console}

O domínio compartilhado padrão é `mybluemix.net`, mas o `appdomain.cloud` é outra opção de domínio que você pode usar.
{: tip}

Conclua estas etapas para atualizar o domínio para sua organização do Cloud Foundry usando o console:

1. No [console do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}){: new_window}, clique no ícone **Menu** ![ícone Menu](../icons/icon_hamburger.svg) e selecione **Lista de recursos**.
2. Na página **Lista de recursos**, clique em **Apps Cloud Foundry**.
3. Clique no aplicativo para o qual você deseja mudar o domínio. A página **Visão geral** do app é exibida.
4. Selecione o menu **Rotas**, observe o domínio atual, tal como `<myapp.mybluemix.net>` e clique em **Editar rotas**.
5. Selecione a lista de domínios e, em seguida, clique no domínio que você deseja usar, como `us-south.cf.appdomain.cloud`.
6. Confirme suas atualizações clicando em **Salvar**.
7. Confirme se você deseja substituir o domínio antigo e clique em **Remover**.
8. Para verificar se a nova rota está funcionando, clique em **Visitar a URL do app**.

## Atualizando domínios por meio da interface da linha de comandos do {{site.data.keyword.cloud_notm}}
{: #update-domain-cli}

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

2. Inclua a rota com o novo domínio em um aplicativo, digitando o comando a seguir:
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Atualizando seu domínio para apps do Kubernetes
{: #update-domain-kube}

O subdomínio para os nomes de host do {{site.data.keyword.containerlong}} é `containers.appdomain.cloud`. O IBM fornecido pelo subdomínio de Ingresso curinga, `*.<cluster_name>.<region>.containers.appdomain.cloud` é registrado por padrão para seu cluster. O certificado TLS fornecido pela IBM é um certificado curinga e pode ser usado para o subdomínio curinga. Para obter mais informações, consulte [Múltiplos domínios dentro de um namespace](/docs/containers?topic=containers-ingress#multi-domains).
