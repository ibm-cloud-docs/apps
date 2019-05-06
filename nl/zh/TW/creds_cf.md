---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, cloud foundry, environment, service, credential, vcap_services

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 將服務認證新增至 Cloud Foundry 環境
{: #add-credentials-cf}

了解如何將服務認證新增至 Cloud Foundry 部署環境。
這些指示適用於 [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) 及 [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)。
{: shortdesc}

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。如需移轉至 `appdomain.cloud` 的相關資訊，請參閱[更新網域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。
{: tip}

## 您的程式碼 + Cloud Foundry
{: #credentials-byoc-cf}

在應用程式存在的 Cloud Foundry 空間中，您可以定義 Cloud Foundry 怎麼稱呼使用者提供的服務。使用者提供的服務是字串化的 JSON，它被儲存成彷彿是 Cloud Foundry 空間中的可連結服務。在登入並連接至 Cloud Foundry 組織及空間之後，請完成下列步驟來建立並連結服務。

1. 執行下列指令來建立使用者提供的服務：
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. 藉由新增至服務區段，將 Cloud Foundry 應用程式配置為連結至使用者提供的服務：
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. 編寫應用程式以讀取 `VCAP_SERVICES` 環境變數的環境、將它剖析為 JSON，並尋找您需要的認證（類似 node.js 的虛擬碼）：
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## 入門範本套件應用程式 + Cloud Foundry
{: #credentials-starterkit-cf}

### 如何準備 Cloud Foundry 空間

使用**配置持續交付**特性，將您的應用程式部署至 Cloud Foundry 空間。

如果以 Cloud Foundry 為基礎的服務實例與已部署的 Cloud Foundry 應用程式位於相同的 Cloud Foundry 空間，請參閱[下一節](/docs/apps?topic=creating-apps-add-credentials-cf)。

如果以 Cloud Foundry 為基礎的服務實例所在的空間與 Cloud Foundry 應用程式的目標空間不同，請參閱[接下來的小節](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different)。

如果與應用程式相關聯的服務是以資源控制器為基礎，請參閱[資源控制器](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller)。

#### 以 Cloud Foundry 為基礎的服務與已部署應用程式位於相同的空間
{: #cf_resource_same}

如果與應用程式相關聯的服務是以 Cloud Foundry 為基礎，則服務是 Cloud Foundry 中的「可連結」服務。您可以使用正確的地區 + 組織 + 空間來連接 `cf` 指令行，以查看 Cloud Foundry 空間中的服務。如果您被問到要在哪個 Cloud Foundry 組織與空間中建立服務，即可在建立服務時判斷服務是否以 Cloud Foundry 為基礎。

您可以執行下列指令，來檢視連結應用程式：
```console
cf services
```
{: codeblock}

輸出範例：
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### 以 Cloud Foundry 為基礎的服務與已部署應用程式位於不同的空間
{: #cf_resource_different}

當應用程式與服務不在相同的 Cloud Foundry 空間中時，Cloud Foundry 不支援將 Cloud Foundry 應用程式「連結」至 Cloud Foundry 服務。Cloud Foundry 空間必須備妥「使用者提供的」服務，且接下來的小節將適用。

#### 以資源控制器為基礎的服務與您的應用程式相關聯
{: #cf_resource_controller}

如果與應用程式相關聯的服務是以資源控制器為基礎，則服務_不是_ Cloud Foundry 中的「可連結」服務。如果您被問到要在哪個資源群組中建立服務，即可在建立服務時判斷服務是否以資源控制器為基礎。Cloud Foundry 空間必須備妥服務認證，應用程式才能在程式碼中參照它們。系統會自動為您做好準備，而且您可以透過執行下列指令，將 `cf` 指令行連接至空間，來觀察空間準備的結果：
```console
cf services
```
{: codeblock}

輸出範例：
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry 不容許在 `cf service` 或 `cf services` 指令行看到任何服務認證的值（已編碼或以其他方式）。就功能來說，使用者提供的服務是字串化的 JSON，其定義為 Cloud Foundry 空間中的具名「服務實例」。若要查看這些值，您必須先將應用程式連結至 Cloud Foundry 服務，方法是在應用程式 `manifest.yml` 檔案中的 `services` 標題下，指出服務實例名稱。然後，在 Cloud Foundry 空間中執行應用程式，並執行 `cf env $APP_NAME` 來取得該應用程式的環境。

值得慶幸的是，從入門範本套件產生的程式碼會自動移入正確的連結，以從應用程式執行所在的 Cloud Foundry 空間針對其所定義的環境中擷取並使用這些值。

### 入門範本套件產生的程式碼
{: #starterkit-generated-code-cf}

在繼續之前，請參閱[入門範本套件應用程式 + kube](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode)。然後，套用下列變更：

* 雖然產生的程式碼會提供 `deployment.yml`，但它不適用於部署至 Cloud Foundry 的應用程式。相反地，`manifest.yml` 則_適用_，而且會顯示其內容，以_連結_ 至兩個在 Cloud Foundry 空間中建立的服務。
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

來自前一子節的其餘文件將再次適用。`IBMCloudEnv` 程式庫會將從應用程式執行所在環境中擷取值的方式抽象化。

此程式庫會將從 Cloud Foundry 擷取環境值時的部分複雜性抽象化。在 Cloud Foundry 中，執行中的應用程式會得到一個名為 `VCAP_SERVICES` 的環境變數，其值為字串化的 JSON，且無論服務是_存在於_ Cloud Foundry 空間中的服務實例，還是使用者定義的服務值，都會保留連結服務認證的值。已剖析 JSON 中來自 `VCAP_SERVICES` 環境變數的最上層索引鍵，為與 Cloud Foundry 型服務相關聯的 Cloud Foundry `label`，以及索引鍵 `user-provided`（其值會存放所有「使用者提供」之服務的認證陣列）。
