---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Gerenciando seus domínios
{: #update-domain}

Os domínios fornecem a rota da URL que é alocada para sua organização no {{site.data.keyword.cloud}}. Domínios customizados direcionam solicitações para seus aplicativos para uma URL que você possui. Um domínio customizado pode ser um domínio compartilhado, um subdomínio compartilhado ou um domínio compartilhado e host. A menos que um domínio customizado seja especificado, o {{site.data.keyword.cloud_notm}} usa um domínio compartilhado padrão na rota para seu app. O processo para gerenciar seus domínios depende de seu destino de implementação, como o {{site.data.keyword.containershort}}, o Cloud Foundry e outros.
{:shortdesc}

Para usar um domínio customizado, deve-se registrar o domínio customizado em um servidor DNS público e, em seguida, configurar o domínio customizado no {{site.data.keyword.cloud_notm}}. Em seguida, deve-se mapear o domínio customizado para o domínio do sistema do {{site.data.keyword.cloud_notm}} no servidor DNS público. Depois que seu domínio customizado é mapeado para o domínio do sistema, as solicitações para seu domínio customizado são roteadas para seu app no {{site.data.keyword.cloud_notm}}.

## Mudando seu domínio para apps do Kubernetes
{: #update-domain-kube}

O subdomínio para os nomes de host do {{site.data.keyword.containershort_notm}} é `containers.appdomain.cloud`. O IBM fornecido pelo subdomínio de Ingresso curinga, `*.<cluster_name>.<region>.containers.appdomain.cloud`, é registrado por padrão para seu cluster. O certificado TLS fornecido pela IBM é um certificado curinga e pode ser usado para o subdomínio curinga. Para obter mais informações, consulte [Múltiplos domínios dentro de um namespace](/docs/containers?topic=containers-ingress#multi-domains).

## Usando um domínio customizado para apps do Kubernetes
{: #custom-domain-kube}

Se você desejar usar um domínio customizado, deverá registrá-lo como um domínio curinga, como `*.custom_domain.net`. Para usar o TLS, deve-se obter um certificado curinga. Para obter mais informações, consulte [Múltiplos domínios dentro de um namespace](/docs/containers?topic=containers-ingress#multi-domains).

Consulte [este tutorial](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) que explica a você o andaime de um app da web, executando-o localmente em um contêiner e, em seguida, implementando-o em um cluster Kubernetes que foi criado com o IBM Kubernetes Service. Além disso, o tutorial mostra como ligar um domínio customizado, monitorar o funcionamento do ambiente e escalar o app.

## Mudando seu domínio para apps Cloud Foundry
{: #update-domain-cf}

Para apps Cloud Foundry, é possível mudar seu domínio de `mybluemix.net` para `appdomain.cloud` usando o console do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos. Para obter mais informações sobre como mudar seu domínio para `appdomain.cloud`, consulte [Atualizando seu domínio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

O domínio compartilhado padrão é `mybluemix.net`, mas o `appdomain.cloud` é outra opção de domínio que você pode usar.
{: tip}

## Usando um domínio customizado para apps Cloud Foundry
{: #custom-domain-cf}

Para apps Cloud Foundry, é possível criar e usar um domínio customizado usando o console do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos. Para obter mais informações, consulte [Incluindo e usando um domínio customizado](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).
