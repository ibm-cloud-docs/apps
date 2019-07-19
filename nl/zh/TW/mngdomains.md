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

# 更新網域
{: #update-domain}

網域提供在 {{site.data.keyword.cloud}} 中配置給組織的 URL 路徑。對於 Cloud Foundry 應用程式，您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面，將您的網域從 `mybluemix.net` 移轉至 `appdomain.cloud`。
{:shortdesc}

## 從 {{site.data.keyword.cloud_notm}} 主控台更新網域
{: #update-domain-console}

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。
{: tip}

完成下列這些步驟，使用主控台更新 Cloud Foundry 組織的網域：

1. 從 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}){: new_window}，按一下**功能表**圖示 ![「功能表」圖示](../icons/icon_hamburger.svg)，然後選取**資源清單**。
2. 在**資源清單**頁面上，按一下 **Cloud Foundry 應用程式**。
3. 按一下您要變更其網域的應用程式。即會顯示應用程式的**概觀**頁面。
4. 選取**路徑**功能表，注意現行網域（例如 `<myapp.mybluemix.net>`），然後按一下**編輯路徑**。
5. 選取網域清單，然後按一下您要使用的網域，例如 `us-south.cf.appdomain.cloud`。
6. 按一下**儲存**，以確認更新。
7. 確認您要取代舊的網域，然後按一下**移除**。
8. 若要驗證新路徑正常運作，請按一下**造訪應用程式 URL**。

## 從 {{site.data.keyword.cloud_notm}} 指令行介面更新網域
{: #update-domain-cli}

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

2. 鍵入下列指令，將含有新網域的路徑新增至應用程式：
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## 更新 Kubernetes 應用程式的網域
{: #update-domain-kube}

{{site.data.keyword.containerlong}} 主機名稱的子網域是 `containers.appdomain.cloud`。依預設，會為您的叢集登錄 IBM 提供的 Ingress 子網域子網域萬用字元 `*.<cluster_name>.<region>.containers.appdomain.cloud`。IBM 提供的 TLS 憑證是萬用字元，可用於萬用字元子網域。如需相關資訊，請參閱[名稱空間內的多個網域](/docs/containers?topic=containers-ingress#multi-domains)。
