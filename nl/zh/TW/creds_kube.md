---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, kubernetes, kube, add, custom, deployment.yml, cluster, deployment, environment, kubectl, secret

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# 將認證新增至 Kubernetes 環境
{: #add-credentials-kube}

了解如何將服務認證新增至 Kubernetes 部署環境。
{: shortdesc}

在下列情境中，您必須手動將服務認證新增至部署環境：
 * 自帶程式碼。
 * 從空白的入門範本套件範本開始。
 * 將服務新增至部署_過_ 且以入門範本套件為基礎的應用程式。

## 您的程式碼 + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### 正確地進行編碼

為了小心起見，您可以編寫應用程式的程式碼，確認其環境在您應用程式的主要進入點是完整的。您不想要將應用程式提升至環境不完整的叢集而導致產品中斷。應用程式可能會拒絕啟動，而您的 Kubernetes 配置可以自動防止這類中斷。

假設您有下列兩個環境變數：
* `SECRET`
* `NOT_SECRET`

若為資料庫，您的變數可能是 `APIKEY` 及 `DB_URL`，其中前者是機密的，後者則不是。

使用 Java，您可能會想要在主要應用程式進入點撰寫如下的程式碼：
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

使用 Node，請參閱類似的範例：
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### 準備環境

在 Kubernetes `deployment.yml` 檔案中，可以定義環境變數或_對叢集裡密碼的參照_。

#### 將部署設為從環境取得認證

在具有 `kind: Deployment` 的區段，`spec.template.spec.containers` 之後，以縮排層次新增下列程式碼範例：
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* 按一下**儲存**。

配置叢集，讓名稱為 `name-secret` 且金鑰為 `KEY_SECRET` 的 _secretKeyRef_ 解析為一個值。

#### 安裝必備工具

使用工作站上的終端機來安裝下列工具：

1. 安裝 [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
2. 使用 `ibmcloud login` 指令來登入。
3. 執行 `ibmcloud cs cluster-config {your_cluster_name}` 來連接至您的叢集。
4. 複製並貼上 `export` 指令，以從終端機執行。

#### 在叢集裡定義密碼

{{site.data.keyword.dev_cli_notm}} 提供 `kubectl`，您可以執行它，因為您已連接至 Kubernetes 叢集。

若要定義可解析的密碼，請使用下列 `kubectl` 指令：
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

既然 Kubernetes 叢集已備妥可解析的密碼，您就可以更新應用程式，以使用 `deployment.yml` 檔案中定義的環境變數。

## 入門範本套件應用程式與 Kubernetes
{: #credentials-starterkit-kube}

1. 移至應用程式的**應用程式詳細資料**頁面。

2. 若要建立 Cloud Object Storage 的實例，請選取**新增服務** > **儲存空間** > **Cloud Object Storage** > **精簡方案（免費）** > **建立**。

3. 按一下**下載程式碼**，使用注入的程式碼 Snippet 來重新產生應用程式。

4. 若要在本端存取認證，請複製來自新產生之 `.zip` 檔案的下列檔案，並取代到本端 Git 複本，以存取認證。您仍須在叢集裡建立 Kubernetes 密碼才能管理認證。

   - `chart/{appName}/bindings.yaml` - 在 Kubernetes 叢集裡，產生指向您密碼的環境變數。
   - `src/main/resources/localdev-config.json` - 在本端執行應用程式時存取認證。
   - `src/main/resources/mappings.json` - 提供存取 [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) 方法的對映，以從程式碼存取您的環境變數。
   - `manifest.yml` - 此檔案會將您的服務連結至 Cloud Foundry 應用程式。

  如果您稍後選擇部署至具有「資源控制器」資源（位於資源群組而非組織或空間）的 Cloud Foundry 應用程式，則必須再複製一個檔案。
  {: note}

5. [檢視 Kubernetes 叢集](https://{DomainName}/kubernetes/clusters){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 與對應地區（美國南部，如果它是免費的）。

6. 按一下您的叢集，然後選取右上角的 **Kubernetes 儀表板**，以檢視您的叢集儀表板。

7. 向下捲動直到看見標示**密碼**的區段。您可以看到 {{site.data.keyword.cloudant_short_notm}} 服務實例的密碼，它使用下列慣例 `binding-{appName}-{serviceName}-{timestamp}`。在 `chart/{appName}/binings.yaml` 檔案中，您可以找到對應的 {{site.data.keyword.cloudant_short_notm}} 密碼。

8. 現在，您可以使用已在 `chart/{appName}/bindings.yaml` 產生的密碼名稱，為 Cloud Object Storage 實例建立一個對應密碼，其看起來像是 `binding-create-app-ktibr-cloudobjectstor-1538170732311`。

9. 移至儀表板中的**應用程式詳細資料**頁面，並且複製 Cloud Object Storage 實例的認證。請參閱下列認證輸出範例：
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
    "resource_instance_id": "crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. 確定是使用 `ibmcloud cs cluster-config {your_cluster_name}` 並按照接下來的指示匯出該指令，來配置叢集。

11. 使用 `echo` 指令，將認證放入 `binding` 檔案。
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. 使用 `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding` 建立密碼。如果回到 Kubbernetes 叢集儀表板，可以看到所建立的密碼。

  如果您是部署至 Cloud Foundry 應用程式，則在使用「資源控制器」實例（如果資源存在於資源群組而非組織或空間中）時，需要建立一個使用者提供的服務。
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"ccrn:v1:staging:public:cloud-object-storage:global::a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  您可以使用對應的實例名稱，在 `manifest.yml` 檔案中找到使用者提供之服務的名稱。

13. 現在，當應用程式在 Kubernetes 叢集裡執行時，您可以透過 `env.getProperty` 方法，藉由環境變數來存取您的密碼。

### 如何準備 Kubernetes 叢集

使用**配置持續交付**特性，將您的應用程式部署至 IBM Kubernetes 叢集。此特性會以與您應用程式相關聯之資源認證的密碼，來準備您的 Kubernetes 叢集。您可以完成下列步驟來觀察叢集準備的結果：

1. 執行這個指令來檢視結果：`kibectl get secrets`：
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  您可以檢視[其他關於密碼的文件](https://kubernetes.io/docs/concepts/configuration/secret/)。
  {: tip}

2. 請注意，密碼的名稱是資源名稱。
3. 使用 `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml` 來檢視關於密碼的詳細資訊：

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  `binding` 是密碼的 base64 編碼值。將其解碼會顯示它只是來自服務實例之 `credentials` 的原始 JSON，加上部分 `iam_...` 值：
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

您的應用程式碼無法擷取 Kubernetes 密碼，除非 `deployment.yml` 宣告參照該密碼的 `env` 值。使用入門範本套件時，會自動產生這類程式碼。

### 入門範本套件產生的程式碼
{: #credentials-starterkit-kube-gencode}

在此情況下，您從入門範本套件建立此應用程式。從入門範本套件產生的程式碼會成為可攜式程式碼，可以在本端、Cloud Foundry 或 Kubernetes 中執行。程式庫 `IBMCloudEnv` 是用來提供應用程式碼與環境變數擷取作業之間的抽象層，而這些環境變數保存了服務實例的認證。

從入門範本套件建立的程式碼對 `IBMCloudEnv` 程式庫具有相依關係，並產生下列輸出：

* 內含在 `deployment.yml` 檔案中的 `bindings.yml` 檔案，且具有下列內容：
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  `secretKeyRef.name` 會公開已定義的 Kubernetes 密碼，以便可由應用程式擷取作為應用程式碼中的簡單環境變數。

* `IBMCloudEnv` 程式庫的指示會封裝在 `mappings.json` 檔案中，而該檔案位於入門範本套件產生的程式碼庫中。`mappings.json` 對於每個認證有個別的定義：
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

  `mappings.json` 檔案使用 `jsonpath` 語法，以及 `searchPatterns` 陣列的順序，來引導 `IBMCloudEnv` 邏輯。

* 請使用下列程式碼來擷取 Cloudant API 金鑰（虛擬碼）：
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

`IBMCloudEnv` 程式庫會自動偵測您的應用程式是在 Kubernetes、Cloud Foundry 還是虛擬伺服器實例中執行（處理方式與本端 Docker 相同），並套用正確的 `searchPattern` 來尋找要傳回的值。

因此，`mappings.json` 檔案會被視為預先配置且立即可用之值的_最終清單_，而這些值來自執行應用程式的環境。這些值會移入您在使用**配置持續交付**特性時設為目標的叢集環境中。
