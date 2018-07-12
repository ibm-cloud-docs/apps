---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 建立及使用自訂網域
{: #updatingapps}

您可以使用指令行或 {{site.data.keyword.Bluemix}} Continuous Delivery，來更新 {{site.data.keyword.Bluemix_notm}} 中的應用程式。在許多情況下，即使是建置套件（例如 Node.js），您還是必須提供 -c 參數來指定用來啟動應用程式的指令。
{:shortdesc}

網域提供在 {{site.data.keyword.Bluemix_notm}} 中配置給組織的 URL 路徑。若要使用自訂網域，必須在公用 DNS 伺服器上登錄自訂網域，在 {{site.data.keyword.Bluemix_notm}} 中配置自訂網域。然後，請將自訂網域對映至公用 DNS 伺服器上的 {{site.data.keyword.Bluemix_notm}} 系統網域。將自訂網域對映至系統網域之後，該自訂網域的要求即會遞送至 {{site.data.keyword.Bluemix_notm}} 中的應用程式。

您可以使用 {{site.data.keyword.Bluemix_notm}} 主控台或指令行介面，來建立及使用自訂網域。

## 使用 {{site.data.keyword.Bluemix_notm}} 主控台

請完成下列步驟，以使用主控台為您的組織建立自訂網域：

1. 移至**管理** > **帳戶** > **Cloud Foundry 組織**。
2. 按一下您要建立自訂網域的組織名稱。
3. 按一下**網域**標籤。
4. 按一下**新增網域**，並輸入您的網域名稱，然後選取該地區。
5. 確認更新。按一下**新增**。

例如，您可以使用 `*.mycompany.com` 來建立路徑 `www.mybluemix.com` 與您應用程式的關聯。您也可以使用 `example.mycompany.com` 來建立路徑 `www.example.mybluemix.com` 與您應用程式的關聯。
{: tip}

新增含有自訂網域的路徑至應用程式。

1. 按一下**功能表**圖示 ![「功能表」圖示](../icons/icon_hamburger.svg) > **儀表板**，然後按一下您要新增路徑的應用程式列。即會顯示**概觀**頁面。
2. 從**路徑**功能表中，選取**編輯路徑**。
3. 按一下**新增路徑**，然後指定您要用於應用程式的路徑。
4. 按一下**儲存**，以確認更新。

## 使用 {{site.data.keyword.Bluemix_notm}} 指令行介面

1. 鍵入下列指令以建立組織的自訂網域：

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. 新增含有自訂網域的路徑至應用程式。若為 CF 應用程式，請鍵入下列指令：

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

       若為容器群組，請鍵入下列指令：
     

   ```
     cf ic route map -n host_name -d mydomain mycontainergroup
     ```

在 {{site.data.keyword.Bluemix_notm}} 中配置自訂網域之後，請將自訂網域對映至已登錄 DNS 伺服器上的 {{site.data.keyword.Bluemix_notm}} 系統網域：

1. 在 DNS 伺服器上，設定自訂網域名稱的 'CNAME' 記錄。視您的 DNS 提供者而定，設定 CNAME 記錄的步驟有所不同。例如，如果您使用 GoDaddy，請遵循 GoDaddy 的[網域說明 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} 指引。
2. 將自訂網域名稱對映至應用程式執行所在的 {{site.data.keyword.Bluemix_notm}} 地區的安全端點。使用下列地區端點，提供在 {{site.data.keyword.Bluemix_notm}} 中配置給組織的 URL 路徑。

  * US-SOUTH - `secure.us-south.bluemix.net`
  * US-EAST - `secure.us-east.bluemix.net`
  * EU-DE - `secure.eu-de.bluemix.net`
  * EU-GB - `secure.eu-gb.bluemix.net`
  * AU-SYD - `secure.au-syd.bluemix.net`

在瀏覽器或指令行介面中，輸入下列 URL 以存取 `myapp` 應用程式：

```
http://host_name.mydomain
```

若要移除遺留的路徑，請執行下列指令：

```
ibmcloud app route-delete domain -n hostname -f
```
{: tip}

在該範例中，`domain` 是網域名稱，而 `hostname` 是應用程式路徑的主機名稱。如需 `ibmcloud app route-delete` 指令的相關資訊，請輸入指令 `ibmcloud app route-delete -h`。
