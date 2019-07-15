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

# 管理網域
{: #update-domain}

網域提供在 {{site.data.keyword.cloud}} 中配置給組織的 URL 路徑。自訂網域將您的應用程式要求指向您擁有的 URL。自訂網域可以是共用網域、共用子網域或共用網域與主機。除非指定自訂網域，否則 {{site.data.keyword.cloud_notm}} 會在您的應用程式中使用預設的共用網域。網域管理的處理程序取決於您的部署目標，例如，{{site.data.keyword.containershort}}、Cloud Foundry 等等。
{:shortdesc}

若要使用自訂網域，您必須在公用 DNS 伺服器上登錄自訂網域，然後在 {{site.data.keyword.cloud_notm}} 中配置自訂網域。接下來，您必須將自訂網域對映至公用 DNS 伺服器上的 {{site.data.keyword.cloud_notm}} 系統網域。將自訂網域對映至系統網域之後，該自訂網域的要求即會遞送至 {{site.data.keyword.cloud_notm}} 中的應用程式。

## 變更 Kubernetes 應用程式的網域
{: #update-domain-kube}

{{site.data.keyword.containershort_notm}} 主機名稱的子網域是 `containers.appdomain.cloud`。依預設，會為您的叢集登錄 IBM 提供的 Ingress 子網域子網域萬用字元 `*.<cluster_name>.<region>.containers.appdomain.cloud`。IBM 提供的 TLS 憑證是萬用字元，可用於萬用字元子網域。如需相關資訊，請參閱[名稱空間內的多個網域](/docs/containers?topic=containers-ingress#multi-domains)。

## 使用 Kubernetes 應用程式的自訂網域
{: #custom-domain-kube}

如果您要使用自訂網域，則必須將自訂網域登錄為萬用字元網域，例如，`*.custom_domain.net`。若要使用 TLS，您必須取得萬用字元憑證。如需相關資訊，請參閱[名稱空間內的多個網域](/docs/containers?topic=containers-ingress#multi-domains)。

請參閱[本指導教學](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)，它會引導您完成建立 Web 應用程式支架、在容器本端執行，然後將它部署至使用 IBM Kubernetes Service 建立的 Kubernetes 叢集。此外，此指導教學會向您顯示如何連結自訂網域、監視環境的性能以及調整應用程式。

## 變更 Cloud Foundry 應用程式的網域
{: #update-domain-cf}

對於 Cloud Foundry 應用程式，您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面，將您的網域從 `mybluemix.net` 變更為 `appdomain.cloud`。如需將網域變更為 `appdomain.cloud` 的相關資訊，請參閱[更新網域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。
{: tip}

## 使用 Cloud Foundry 應用程式的自訂網域
{: #custom-domain-cf}

對於 Cloud Foundry 應用程式，您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面，來建立及使用自訂網域。如需相關資訊，請參閱[新增及使用自訂網域](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains)。
