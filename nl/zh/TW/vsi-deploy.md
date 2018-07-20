---
copyright:

  years: 2018

lastupdated: "2018-07-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 部署至虛擬伺服器
{: #vsi-deploy}

將 {{site.data.keyword.cloud}} [App Service ![外部鏈結圖示](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} 應用程式部署至虛擬伺服器實例，讓您的平台及基礎架構開發人員活動能一起合作，提高應用程式控制與彈性。
{: shortdesc}

與其他配置相比時，虛擬伺服器實例為所有工作負載類型提供較佳的透通性、可預測性及自動化。將它與裸機伺服器結合，即可建立唯一的工作負載組合。例如，您可以使用執行 Debian Linux 作業系統的裸機伺服器和 GPU 配置，建立高效能的資料庫邏輯或機器學習。

## 開始之前
若要使用虛擬實例，您的 {{site.data.keyword.cloud_notm}} 帳戶必須已針對基礎架構啟用。如需相關資訊，請參閱 [Upgrade to Infrastructure ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}。

**重要事項**：服務不會連結至虛擬伺服器實例。您無法新增服務至虛擬伺服器中的應用程式。

## 透過 Terraform 進行部署
任何 App Service 入門範本套件都可以透過 [Terraform ![外部鏈結圖示](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} 部署在動態建立的虛擬實例，Terraform 是開放程式碼基礎架構，作為程式碼架構之用。如需相關資訊，請參閱 [Terraform 文件 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}。

## 啟用您的管線部署

當您建立使用 {{site.data.keyword.cloud_notm}} [App Service ![外部鏈結圖示](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} 的入門範本套件時，會啟用虛擬伺服器實例。建立應用程式之後，您便可以選擇要部署應用程式的位置。入門範本套件已啟用，能夠使用 Continuous Delivery 工具鏈支援部署。入門範本套件可以 Kubernetes、Cloud Foundry 及虛擬伺服器實例為目標。工具鏈包含原始碼儲存庫以及部署管線。

虛擬伺服器選項會分階段來運作。首先，會準備應用程式碼並儲存到 GITLab Git 儲存庫，而原始碼會建立具有管線的工具鏈。管線定義為建置程式碼，並將它包裝成 Debian 套件管理程式格式。然後 Terraform 會佈建虛擬實例。最後，會部署、安裝應用程式，並在執行中的虛擬映像檔內啟動它，且驗證其性能。

管線在第一次使用時會失敗，因為它要求手動配置一組使用者帳戶內容。因為安全的原因，這些內容無法傳遞到使用 GIT 原始碼的工具鏈。您必須手動配置這些值，以讓工具鏈能順利完成。

請遵循這些步驟，以存取環境內容視圖，並使用您的使用者帳戶內容來啟用管線。

1. 從應用程式詳細資料頁面，按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline** 磚。
3. 按一下**階段配置**圖示，然後在建置階段上按一下**配置階段**。
4. 按一下**環境內容**標籤，以檢視內容。
5. 在環境內容標籤變更這些內容，以讓工具鏈能順利執行。

|內容|說明|
|---|---|
| `TF_VAR_ibm_sl_api_key` |[基礎架構 API 金鑰](#iaas-key)來自基礎架構主控台。|
| `TF_VAR_ibm_sl_username` |識別基礎架構帳戶的[基礎架構使用者名稱](#user-key)。|
| `TF_VAR_ibm_cloud_api_key` |{{site.data.keyword.cloud_notm}} [平台 API 金鑰](#platform-key)用來啟用服務建立。|
| `PUBLIC_KEY` |已定義以便啟用虛擬伺服器實例存取的[公開金鑰](#public-key)。|
| `PRIVATE_KEY` |已定義以便啟用虛擬伺服器實例存取的[私密金鑰](#public-key)。**附註**：您必須使用 `\n` 的新增一行樣式格式。|
| `VI_INSTANCE_NAME` |自動產生的虛擬伺服器實例名稱。|
| `GIT_USER` |如果您設定 [Terraform 狀態](#tform-state)以儲存 apply 指令的狀態，則 GITLab 使用者名稱是必要項目。|
| `GIT_PASSWORD` |如果您設定 [Terraform 狀態](#tform-state)以儲存 apply 指令的狀態，則 GITLab 密碼是必要項目。|
{: caption="表 1. 變更啟用的環境變數" caption-side="top"}

### 擷取基礎架構 API 金鑰
{: #iaas-key}

Terraform 需要基礎架構 API 金鑰以便建立基礎架構資源。請遵循下列步驟來擷取基礎架構金鑰。

1. 移至基礎架構[使用者清單 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}。您也可以按一下**功能表** > **基礎架構** > **帳戶** > **使用者清單**。
2. 尋找建立工具鏈的使用者詳細資料，然後按一下「API 金鑰」直欄中的 `View` 或按一下 `Generate`，兩個步驟都會在視窗中顯示 API 金鑰。
3. 複製 API 金鑰，然後取代工具鏈配置 `TF_VAR_ibm_sl_api_key` 中的值。

### 擷取基礎架構使用者名稱
{: #user-key}

若要擷取基礎架構使用者名稱，請遵循下列步驟。

1. 移至基礎架構[使用者清單 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}。您也可以按一下**功能表** > **基礎架構** > **帳戶** > **使用者清單**。
2. 按一下您要建立工具鏈的使用者。
3. 往下捲動到 **VPN 使用者名稱**內容。
4. 剪下並貼上此值，然後取代工具鏈配置 `TF_VAR_ibm_sl_username`。

### 擷取平台 API 金鑰
{: #platform-key}

若要在 Terraform 中建立像是資料庫的平台層次服務，以及組合服務，平台 API 金鑰是必要項目。請遵循下列步驟來擷取平台金鑰。

1. 從 [API 金鑰 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys) 頁面，按一下**管理** > **安全** > **平台 API 金鑰**。
2. 按一下**建立**。
3. 輸入名稱和說明，然後按一下**建立**。
4. 當視窗開啟時，按一下**顯示**以檢閱金鑰。
5. 複製金鑰並貼入剪貼簿中，或是下載金鑰。
6. 將工具鏈配置 `TF_VAR_ibm_cloud_api_key` 中的值取代為產生的值。

### 產生公開和私密金鑰
{: #public-key}

若要讓工具鏈能將 Debian 套件安裝至虛擬伺服器實例，請遵循下列步驟。

1. 在您的用戶端中，使用下列指示來建立[公開和私密金鑰組 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}。
2. 移至[基礎架構 SSH 金鑰視圖 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window}。您也可以按一下**功能表** > **基礎架構** > **裝置** > **管理** > **SSH 金鑰**。
3. 按一下**新增**。
4. 複製您先前建立之公開金鑰的內容，並貼入金鑰內容中。
5. 為金鑰命名，然後按一下**新增**。

私密金鑰必須在單一行上。請將換行符號取代為 `\n`。請參閱下列範例。
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

### 啟用 Terraform 狀態
{: #tform-state}

Terraform 支援儲存 Terraform `apply` 指令的狀態。這個狀態檔會執行第二次的 `apply` 指令，以判斷是否有任何 Terraform 配置檔變更。您可以將狀態儲存在管理應用程式及配置的 Git 儲存庫。

若要啟用狀態儲存，請在工具鏈環境變數中配置 `GIT_USER` 和 `GIT_PASSWORD` 內容。若要擷取值，請遵循下列步驟：

1. 從工具鏈視圖，從程式碼工具存取 Git 儲存庫。
2. 在 Git Lab 中，按一下**設定檔圖示**，然後按一下**設定**。
3. 按一下**帳戶**，然後複製使用者名稱並取代 `GIT_USER` 值。
4. 按一下**存取記號**。
5. 為記號定義名稱、選取範圍，然後按一下**建立個人存取記號**。
6. 從`您的新個人存取記號`欄位按一下複製圖示，並取代工具鏈內容中的 `GIT_PASSWORD` 值。

Terraform 狀態會儲存在稱為 `terraform` 的分支，且在變更時不會觸發管線執行。

### 啟用 Git 作業
{: #git-repo}

當應用程式部署至 {{site.data.keyword.cloud_notm}} 時，會建立 Git Lab 儲存庫以管理程式碼，進行原始碼管理之用。您可以使用 Git 作業，讓團隊能工作並交付應用程式的變更。資料夾會與其內容的說明包含在此儲存庫中。

#### Debian 資料夾
{: #debian-folder}

`debian` 資料夾會保留啟用將應用程式包裝成 [Debian 套件 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window} 所需的配置。

#### Terraform 資料夾
{: #terraform-folder}

`terraform` 資料夾會保留基礎架構作為程式碼的配置，這可用來佈建基礎架構資源。檔案 `main.tf` 是變更 Terraform 配置選項的主要來源。

```
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

您也可以使用 Terraform 佈建裸機伺服器。如需相關資訊，請參閱 [IBM Terraform Provider 文件 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} 及 [IBM Terraform Provider Git 儲存庫 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}。

`variables.tf` 可以用來變更您要設為目標以建立虛擬實例的資料中心。若要查看平台上已定義的資料中心清單，請參閱[資料中心 ![外部鏈結圖示](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}。

依預設，Terraform 檔案是針對 Washington 和 `wdc04` 配置。

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### 瞭解工具鏈階段
{: #toolchain-stages}

工具鏈會以一個簡單的管線顯示基礎架構及應用程式部署。將基礎架構作為程式碼的部分分成一個管線，將應用程式部署分成另一個管線。

工具鏈處理程序有五個階段。

1. 建置階段會複製 Git 儲存庫，並將程式碼包裝成 Debian 套件。
2. Terraform 計劃階段會準備 Terraform 計劃。

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. Terraform 套用階段會套用 Terraform 配置，並等待直到虛擬伺服器的 IP 位址可用。

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. 部署、安裝、啟動階段會讓第一個階段中建置的 Debian 套件進入執行中的虛擬伺服器、安裝它，然後啟動它。
5. 性能檢查階段會驗證應用程式上的性能端點可用，然後完成管線。

若要在應用程式啟動之後存取它，請檢查「性能檢查階段」的日誌。請按一下日誌中所列，顯示應用程式 IP 位址及埠的 URL 鏈結。
