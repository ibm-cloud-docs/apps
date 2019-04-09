---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 將認證新增至虛擬實例或本端 Docker 環境
{: #add-credentials-vsi}

了解如何將服務認證新增至虛擬伺服器實例或本端 Docker 部署環境。
{: shortdesc}

## 您的程式碼 + 虛擬伺服器實例或本端 Docker
{: #credentials-byoc-vsi}

在 VSI 或本端 Docker 下，環境完全是您的。例如，您可以撰寫類似下列範例的程式碼，並在執行時將認證的環境值提供給應用程式。
```
password = getEnvironment('password');
```
{: codeblock}

使用 Bash，您可以撰寫類似下列範例的程式碼：
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

使用 Docker，您可以撰寫類似下列範例的程式碼：
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## 入門範本套件 + VSI（或本端 Docker）
{: #credentials-starterkit-vsi}

### 如何準備虛擬伺服器實例

環境完全在您的控制之下，就像您是從筆記型電腦執行應用程式一樣。換言之，即本端 Docker。因為從執行中應用程式的觀點來看，VSI 實際上是祼機，沒有_密碼_（如在 Kubernetes 中）或_服務_（如在 Cloud Foundry 中）。

### 入門範本套件產生的程式碼
{: #starterkit-generated-code-vsi}

從入門範本套件產生的程式碼具有原生 `IBMCloudEnv` 程式庫，它會將環境值的擷取作業抽象化，讓應用程式碼可以成為可攜式，以在數個目標部署上執行。使用虛擬或本端 Docker 時，該環境必須備妥滿足 `IBMCloudEnv` 程式庫的值，而這些值_不一定_ 來自實際的環境變數。

為了方便起見，入門範本套件產生的輸出所附的 `mappings.json` 指示，具有本端檔案的參照，而 `IBMCloudEnv` 程式庫會從中尋找應用程式可以使用的值。

例如，請注意 `mappings.json` 檔案中下列區段的最後一行：
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

如果您在建立應用程式時使用「部署至雲端」特性，則會從 GitLab 儲存庫移除 `/server/localdev-config.json` 檔案。基於安全考量，您不想要將認證放置在原始碼儲存庫中。

如果您在建立的 GitLab 儲存庫上使用 `git clone` 來啟動作用中開發，請注意 `.gitignore` 檔案會特別忽略 `server/localdev-config.json`，以協助防止意外移入具有機密認證的檔案。不過，VSI _的確_ 需要該檔案，如同使用筆記型電腦工作的開發人員一般。

您可以完成下列步驟，來擷取 `server/localdev-config.json` 檔案：

1. 在使用「部署至雲端」特性時自動建立的 Git Lab 儲存庫上，使用 `git clone`。
2. 安裝 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview)，其中包括 `dev` 外掛程式。
3. 使用 `ibmcloud` 指令行來登入 {{site.data.keyword.cloud_notm}}。
4. 執行 `ibmcloud dev get-credentials`，它會參照 `cli-config.yml` 檔案。`cli-config.yml` 檔案包含哪個應用程式及產生工作具有認證的相關資訊。

如果在使用「部署至雲端」特性到 `ibmcloud dev get-credentials` 期間，從應用程式移除了任何資源，則下載的檔案 `/server/localdev-config.json` 不會具有原始 `git clone` 程式碼庫可能需要的所有認證。
{: tip}

如果您是在 Docker 容器中執行應用程式，則可能選擇完整移除 `/server/localdev-config.json` 檔案，並在 Docker 指令行上傳遞環境變數。

繼續使用 `mappings.json` 檔案中的 "cloudant_apikey" 區段，請注意 `file...` 一行前面的 `env:cloudant_apikey`。這表示名為 `cloudant_apikey` 的環境變數優先於檔案的內容。因此，即使該檔案存在於您所建置（非必要）的 Docker 映像檔中，您也可以在 Docker 指令行上傳遞這些值來置換它們。

例如：
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
