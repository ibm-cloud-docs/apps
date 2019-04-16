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

# 新增及使用自訂網域
{: #updatingapps}

網域提供在 {{site.data.keyword.cloud}} 中配置給組織的 URL 路徑。自訂網域將您的應用程式要求指向您擁有的 URL。自訂網域可以是共用網域、共用子網域或共用網域與主機。除非指定自訂網域，否則 {{site.data.keyword.cloud_notm}} 會在您的應用程式中使用預設的共用網域。您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面，來建立及使用自訂網域。
{:shortdesc}

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。如需移轉至 `appdomain.cloud` 的相關資訊，請參閱[更新網域](/docs/apps/tutorials?topic=creating-apps-update-domain)。
{: tip}

若要使用自訂網域，您必須在公用 DNS 伺服器上登錄自訂網域，然後在 {{site.data.keyword.cloud_notm}} 中配置自訂網域。接下來，您必須將自訂網域對映至公用 DNS 伺服器上的 {{site.data.keyword.cloud_notm}} 系統網域。將自訂網域對映至系統網域之後，該自訂網域的要求即會遞送至 {{site.data.keyword.cloud_notm}} 中的應用程式。

## 從 {{site.data.keyword.cloud_notm}} 主控台新增自訂網域
{: #custom-domain-console}

完成下列這些步驟，使用主控台為組織新增自訂網域：

1. 移至**管理 > 帳戶**，然後選取 **Cloud Foundry 組織**。
2. 按一下您要建立自訂網域的組織名稱。
3. 按一下**網域**標籤，以檢視可用網域清單。
4. 按一下**新增網域**、輸入網域名稱，然後選取地區。
5. 確認更新項目，然後按一下**新增**。

## 將含有自訂網域的路徑新增至應用程式

1. 從 [{{site.data.keyword.cloud_notm}} 主控台 ](https://{DomainName}){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")，按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**資源清單**。
2. 在**資源清單**頁面上，按一下 **Cloud Foundry 應用程式**。
3. 按一下您要新增路徑的應用程式。即會顯示應用程式的**概觀**頁面。
4. 選取**路徑**功能表，然後選取**編輯路徑**。
5. 按一下**新增路徑**，然後指定您要用於應用程式的路徑。
6. 按一下**儲存**，以確認更新。

舉例來說，您可以使用 `*.mycompany.com` 來建立路徑 `www.mybluemix.net` 與應用程式的關聯。您也可以使用 `example.mycompany.com` 來建立路徑 `www.example.bluemix.net` 與應用程式的關聯。
{: tip}

## 從 {{site.data.keyword.cloud_notm}} 指令行介面新增自訂網域
{: #custom-domain-cli}

1. 對於 Cloud Foundry 應用程式，請鍵入下列指令來連接至目標 Cloud Foundry API 端點：
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Cloud Foundry API 端點：**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. 鍵入下列指令以建立組織的自訂網域：
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. 將含有自訂網域的路徑新增至應用程式。

   若為 Cloud Foundry 應用程式，請鍵入下列指令：
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## 將自訂網域對映至系統網域
{: #mapcustomdomain}

在 {{site.data.keyword.cloud_notm}} 中配置自訂網域之後，請將自訂網域對映至已登錄 DNS 伺服器上的 {{site.data.keyword.cloud_notm}} 系統網域：

1. 在 DNS 伺服器上，設定自訂網域名稱的 'CNAME' 記錄。視您的 DNS 提供者而定，設定 CNAME 記錄的步驟有所不同。例如，如果您使用 GoDaddy，請遵循 GoDaddy 的[網域說明 ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 指引。
2. 將自訂網域名稱對映至應用程式執行所在之 {{site.data.keyword.cloud_notm}} 地區的安全端點。使用下列地區端點，提供配置給 {{site.data.keyword.cloud_notm}} 中組織的 URL 路徑。例如，將 CNAME 指向 `<custom-domain>.us-east.cf.cloud.ibm.com`。

  **Cloud Foundry 端點：**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## 存取應用程式
{: #access-app}

在瀏覽器中，輸入下列 URL 以存取應用程式，其中 `hostname` 是主機名稱，而 `mydomain` 是網域名稱：
```
http://hostname.mydomain
```

## 移除遺留的路徑
{: #remove-orphaned-route}

若要移除遺留的路徑，請執行下列指令：
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

在該範例中，`domain` 是網域名稱，而 `hostname` 是應用程式路徑的主機名稱。如需 `ibmcloud app route-delete` 指令的相關資訊，請輸入指令 `ibmcloud app route-delete -h`。

## 使用 Kubernetes 應用程式的自訂網域
{: #kube-custom-domain}

IBM Cloud Kubernetes Service 主機名稱的子網域是 `containers.appdomain.cloud`。依預設，會為您的叢集登錄 IBM 提供的 Ingress 子網域子網域萬用字元 `*.<cluster_name>.<region>.containers.mybluemix.net`。IBM 提供的 TLS 憑證是萬用字元，可用於萬用字元子網域。如果您要使用自訂網域，則必須將自訂網域登錄為萬用字元網域，例如 `*.custom_domain.net`。若要使用 TLS，您必須取得萬用字元憑證。如需相關資訊，請參閱[名稱空間內的多個網域](/docs/containers?topic=containers-ingress#multi-domains)。

請參閱[本指導教學](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)，它會引導您完成建立 Web 應用程式支架、在容器本端執行，然後將它部署至使用 IBM Kubernetes Service 建立的 Kubernetes 叢集。此外，您也將瞭解如何連結自訂網域、監視環境性能，以及調整應用程式。
