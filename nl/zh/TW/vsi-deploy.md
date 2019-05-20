---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-09"

keywords: apps, deploy, virtual server, App Service, vsi, virtual machine, delivery pipeline, virtual deployment

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# 部署至虛擬伺服器
{: #vsi-deploy}

如果您具有「隨收隨付制」帳戶，則可以使用 {{site.data.keyword.cloud}} [App Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 將應用程式部署至許多類型的環境，包括虛擬伺服器實例。虛擬伺服器實例會模擬裸機機器，在將內部部署工作負載移到雲端時是常見的部署選項。
{: shortdesc}

與其他配置相比時，虛擬伺服器實例為所有工作負載類型提供較佳的透通性、可預測性及自動化。將它與裸機伺服器結合，即可建立唯一的工作負載組合。例如，您可以使用執行 Debian Linux 作業系統的裸機伺服器和 GPU 配置，建立高效能的資料庫邏輯或機器學習。

佈建虛擬伺服器實例並部署它可能是個複雜且耗時的處理程序，但您可以使用 {{site.data.keyword.cloud_notm}} App Service 快速開始進行。

服務不會連結至虛擬伺服器實例。您無法新增服務至虛擬伺服器中的應用程式。
{: important}

## 部署應用程式
{: #create-deploy-vsi}

App Service 會為您佈建虛擬伺服器實例、載入包含您的應用程式的映像檔、建立 DevOps 工具鏈，以及為您起始第一個部署週期。

1. [建立應用程式](/docs/apps?topic=creating-apps-tutorial-scratch#tutorial-scratch)。 
2. 按一下「應用程式詳細資料」頁面中的**配置持續交付**。
3. 選取**部署至虛擬伺服器**，以及要在其中執行伺服器的地區。

## 部署處理程序運作方式

虛擬伺服器部署處理程序包含數種重要技術，包括 Terraform、管線啟用、API 金鑰管理（Git 作業），和瞭解工具鏈處理程序。 

### 透過 Terraform 進行部署

任何 App Service 入門範本套件都可以透過 [Terraform](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 部署在動態建立的虛擬實例，Terraform 是開放程式碼基礎架構，作為程式碼架構使用。 

### 啟用您的管線部署

當您建立使用 {{site.data.keyword.cloud_notm}} [App Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 的入門範本套件時，會啟用虛擬伺服器實例。建立應用程式之後，您便可以選擇要部署應用程式的位置。入門範本套件已啟用，能夠使用 Continuous Delivery 工具鏈支援部署。入門範本套件可以 Kubernetes、Cloud Foundry 及虛擬伺服器實例為目標。工具鏈包含原始碼儲存庫以及部署管線。

虛擬伺服器選項會分階段來運作。首先，會準備應用程式碼並儲存到 GitLab Git 儲存庫，而原始碼會建立具有管線的工具鏈。管線定義為建置程式碼，並將它包裝成 Debian 套件管理程式格式。然後 Terraform 會佈建虛擬實例。最後，會部署、安裝應用程式，並在執行中的虛擬映像檔內啟動它，且驗證其性能。

管線使用一組使用者帳戶內容，以及全新的 SSH 金鑰組來配署至基礎架構。這些內容會自動傳遞到工具鏈，但因為安全的理由，不會儲存在 Git 原始碼中。

若要檢視這些環境內容，請完成下列步驟。 

1. 從「應用程式詳細資料」頁面中，按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline** 磚。
3. 按一下**階段配置**圖示，然後在建置階段上按一下**配置階段**。
4. 按一下**環境內容**標籤，以檢視內容。請使用下表以瞭解可用的內容。

|內容|說明|
|-----------|--------------|
| `TF_VAR_ibm_sl_api_key` |[基礎架構 API 金鑰](/docs/apps?topic=creating-apps-vsi-deploy#iaas-key)來自標準基礎架構主控台。|
| `TF_VAR_ibm_sl_username` |識別標準基礎架構帳戶的[基礎架構使用者名稱](/docs/apps?topic=creating-apps-vsi-deploy#user-key)。|
| `TF_VAR_ibm_cloud_api_key` |{{site.data.keyword.cloud_notm}} [API 金鑰](/docs/apps?topic=creating-apps-vsi-deploy#platform-key)用來啟用服務建立。|
| `PUBLIC_KEY` |已定義以便啟用虛擬伺服器實例存取的[公開金鑰](/docs/apps?topic=creating-apps-vsi-deploy#public-key)。|
| `PRIVATE_KEY` |已定義以便啟用虛擬伺服器實例存取的[私密金鑰](/docs/apps?topic=creating-apps-vsi-deploy#public-key)。您必須使用 `\n` 的新增一行樣式格式。|
| `VI_INSTANCE_NAME` |自動產生的虛擬伺服器實例名稱。|
| `GIT_USER` |如果您設定 [Terraform 狀態](/docs/apps?topic=creating-apps-vsi-deploy#tform-state)以儲存 apply 指令的狀態，則 GitLab 使用者名稱是必要項目。|
| `GIT_PASSWORD` |如果您設定 [Terraform 狀態](/docs/apps?topic=creating-apps-vsi-deploy#tform-state)以儲存 apply 指令的狀態，則 GitLab 密碼是必要項目。|
{: caption="表 1. 變更啟用的環境變數" caption-side="top"}


#### 標準基礎架構 API 金鑰
{: #iaas-key}

Terraform 需要標準基礎架構 API 金鑰以便建立基礎架構資源。在部署期間會自動取得 API 金鑰。若要手動擷取金鑰，請完成下列步驟。

1. 移至[使用者清單](https://{DomainName}/iam#/users){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。您也可以按一下**管理** > **存取 (IAM)**，然後選取**使用者**。
2. 按一下使用者名稱，然後按一下**使用者詳細資料**。
3. 按一下 API 金鑰區段中的**新增標準基礎架構金鑰**。
4. 複製或下載 API 金鑰 `TF_VAR_ibm_sl_api_key`，並將它儲存在安全的地方。您稍後可以使用**動作** ![「動作清單」圖示](../icons/action-menu-icon.svg) 功能表中的**檢視詳細資料**選項，來擷取 API 金鑰的詳細資料。
5. 將複製的 API 金鑰值貼入工具鏈配置中，以取代 `TF_VAR_ibm_sl_api_key`。

如需相關資訊，請參閱[管理標準基礎架構 API 金鑰](/docs/iam?topic=iam-classic_keys#classic_keys)及[標準基礎架構許可權](/docs/iam?topic=iam-infrapermission#infrapermission)。

#### 標準基礎架構使用者名稱
{: #user-key}

標準基礎架構使用者名稱也會在部署期間自動取得及使用。若要手動取得使用者名稱，請完成下列步驟。

1. 移至[使用者清單](https://{DomainName}/iam#/users){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。您也可以按一下**管理** > **存取 (IAM)**，然後選取**使用者**。
2. 按一下使用者名稱，然後按一下**使用者詳細資料**。
3. 找出 **VPN 使用者名稱**內容。
4. 剪下並貼上此值，然後取代工具鏈配置 `TF_VAR_ibm_sl_username`。

#### {{site.data.keyword.cloud_notm}} API 金鑰
{: #platform-key}

為了在 Terraform 中建立像是資料庫及組合服務的平台層次服務，會自動取得 {{site.data.keyword.cloud_notm}} API 金鑰，並將其儲存為管線中的環境變數。若要手動擷取 {{site.data.keyword.cloud_notm}} API 金鑰，請完成下列步驟。

1. 移至[使用者清單](https://{DomainName}/iam#/users){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。您也可以按一下**管理** > **存取 (IAM)**，然後選取**使用者**。
2. 按一下使用者名稱，然後按一下**使用者詳細資料**。
3. 找出 API 金鑰區段，然後按一下**建立 IBM Cloud API 金鑰**。
4. 輸入名稱和說明，然後按一下**建立**。
5. 當視窗開啟時，按一下**顯示**以檢閱金鑰。
6. 複製金鑰並貼入剪貼簿中，或是下載金鑰。
7. 將工具鏈配置 `TF_VAR_ibm_cloud_api_key` 中的值取代為產生的值。

#### 公開和私密金鑰
{: #public-key}

若要讓工具鏈能將 Debian 套件安裝至虛擬伺服器實例，部署基礎架構會自動產生私密及公開 SSH 金鑰組，以便將 Git 內容傳送到實例。

若要手動進行，請執行下列動作：
1. 在您的用戶端中，使用下列指示來建立[公開和私密金鑰組](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。
2. 移至[基礎架構 SSH 金鑰視圖](https://{DomainName}/iam/#/users){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。您也可以按一下**功能表** > **標準基礎架構** > **裝置** > **管理** > **SSH 金鑰**。
3. 按一下**新增**。
4. 複製您先前建立之公開金鑰的內容，並貼入金鑰內容中。
5. 為金鑰命名，然後按一下**新增**。

私密金鑰必須在單一行上。請將換行符號取代為 `\n`。請參閱下列範例。
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### 啟用 Terraform 狀態
{: #tform-state}

Terraform 支援儲存 Terraform `apply` 指令的狀態。這個狀態檔會執行第二次的 `apply` 指令，以判斷是否有任何 Terraform 配置檔變更。狀態會儲存在 Git 儲存庫中，在這裡會自動設定應用程式及配置。

為了啟用狀態儲存，會在工具鏈環境變數中自動將 `GIT_USER` 和 `GIT_PASSWORD` 配置為內容。如果您需要存取這些值，請遵循下列步驟：

1. 從工具鏈視圖，從程式碼工具存取 Git 儲存庫。
2. 在 Git Lab 中，按一下**設定檔圖示**，然後按一下**設定**。
3. 按一下**帳戶**，然後複製使用者名稱並取代 `GIT_USER` 值。
4. 按一下**存取記號**。
5. 為記號定義名稱、選取範圍，然後按一下**建立個人存取記號**。
6. 從`您的新個人存取記號`欄位按一下**複製**，並取代工具鏈內容中的 `GIT_PASSWORD` 值。

Terraform 狀態會儲存在稱為 `terraform` 的分支，且在變更時不會觸發管線執行。

### 啟用 Git 作業
{: #git-repo-vsi}

當應用程式部署至 {{site.data.keyword.cloud_notm}} 時，會建立 GitLab 儲存庫以管理程式碼，進行原始碼管理之用。您可以使用 Git 作業，讓團隊能工作並交付應用程式的變更。資料夾會與其內容的說明包含在此儲存庫中。

#### Debian 資料夾
{: #debian-folder}

`debian` 資料夾會保留讓應用程式包裝成 [Debian 套件](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 所需的配置。

#### Terraform 資料夾
{: #terraform-folder}

`terraform` 資料夾會保留基礎架構作為程式碼的配置，這可用來佈建基礎架構資源。檔案 `main.tf` 是變更 Terraform 配置選項的主要來源。

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

您也可以使用 Terraform 佈建裸機伺服器。如需相關資訊，請參閱 [IBM Terraform Provider 文件](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 和 [IBM Terraform Provider GIT 儲存庫](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

`variables.tf` 可以用來變更您要設為目標以建立虛擬實例的資料中心。若要查看平台上已定義的資料中心清單，請參閱[資料中心](https://www.ibm.com/cloud/data-centers/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

依預設，Terraform 檔案是針對 Washington 和 `wdc04` 配置。
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### 瞭解工具鏈階段
{: #toolchain-stages-vsi}

工具鏈會以一個簡單的管線顯示基礎架構及應用程式部署。將基礎架構作為程式碼的部分分成一個管線，將應用程式部署分成另一個管線。

工具鏈處理程序有五個階段。

1. 建置階段會複製 Git 儲存庫，並將程式碼包裝成 Debian 套件。
2. Terraform 計劃階段會準備 Terraform 計劃。
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. Terraform 套用階段會套用 Terraform 配置，並等待直到虛擬伺服器的 IP 位址可用。

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. 部署、安裝、啟動階段會讓第一個階段中建置的 Debian 套件進入執行中的虛擬伺服器、安裝它，然後啟動它。
5. 性能檢查階段會驗證應用程式上的性能端點可用，然後完成管線。

若要在應用程式啟動之後存取它，請檢查「性能檢查階段」的日誌。請按一下日誌中所列，顯示應用程式 IP 位址及埠的 URL 鏈結。
