---

copyright:
  years: 2015, 2019
lastupdated: "2019-07-25"

keywords: apps, application, ssl, certificates, access, restrict access, create, csr, upload, import

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# 建立憑證簽署要求
{: #ssl_csr}

您可以上傳 SSL 憑證並限制應用程式存取，來保護您的應用程式。
{: shortdesc}

## 建立憑證簽名要求
{: #create_csr}

您必須先在伺服器上建立憑證簽署要求 (CSR)，才能使用 {{site.data.keyword.cloud}} 上傳授與您的 SSL 憑證。CSR 是傳送給憑證管理中心的訊息，用來要求簽署公開金鑰及相關聯的資訊。最常見的 CSR 是 PKCS #10 格式。CSR 包含公開金鑰、通用名稱、組織、縣/市、省/直轄市/自治區、國家和電子郵件。只接受 CSR 金鑰長度 2048 位元的 SSL 憑證要求。

建立 CSR 的方法會視您的作業系統而改變。下列範例顯示如何使用 [OpenSSL 指令行工具 ](https://www.openssl.org/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 建立 CSR：

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```
{: codeblock}

OpenSSL SHA-512 實作取決於 64 位元整數類型的編譯器支援。您可以使用 SHA-1 選項來處理具有 SHA-256 憑證相容性問題的應用程式。
{: tip}

### 必要的 CSR 內容

在建立 CSR 時必須輸入下列資訊，CSR 才會有效。

 * **國家/地區名稱**：國家或地區的兩碼代碼。例如，`US` 是美國的國碼。若為其他國家或地區，請先檢查 [ISO 國碼清單 ](https://www.iso.org/obp/ui/#search){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")，然後再建立 CSR。
 * **州/省（縣/市）**：州/省（縣/市）的完整未縮寫名稱。
 * **地區**：城市或城鎮的完整名稱。
 * **組織**：企業或公司在您的地區合法登錄的完整名稱，或是人名。若為公司，請務必包含登錄字尾，例如 Ltd.、Inc. 或 NV。
 * **組織單位**：您公司訂購憑證的分支名稱，例如會計或行銷。
 * **通用名稱**：您要求 SSL 憑證的完整網域名稱 (FQDN)。

您可以使用「主體替代名稱 (SAN)」，但所提供的主機名稱不得發出於其他已部署的憑證，以避免 CN 衝突。
{: note}

憑證由憑證管理中心發行，並由該憑證管理中心執行數位簽署。在建立 CSR 之後，可在公用憑證管理中心產生 SSL 憑證。

## 上傳 SSL 憑證
{: #ssl_certificate}

您可以套用安全通訊協定以提供應用程式的通訊隱私權，以避免竊聽、竄改及訊息偽造。如果您有精簡帳戶，則必須升級帳戶，才能上傳憑證。

必須更新已到期或即將到期的憑證時，以及新憑證準備就緒後，請刪除現有憑證，然後新增新憑證。
{: note}

當您使用自訂網域來提供 SSL 憑證時，請使用下列地區端點，提供在 {{site.data.keyword.cloud_notm}} 中貴組織的 URL 路徑：

| 地區 |端點|
| ------ | -------- |
| US-South | `custom-domain.us-south.cf.cloud.ibm.com` |
| US-East | `custom-domain.us-east.cf.cloud.ibm.com` |
| EU-DE | `custom-domain.eu-de.cf.cloud.ibm.com` |
| EU-GB | `custom-domain.eu-gb.cf.cloud.ibm.com` |
| AU-SYD | `custom-domain.au-syd.cf.cloud.ibm.com` | 
{: caption="表 1. Cloud Foundry 自訂網域地區端點" caption-side="top"}

若要上傳 Cloud Foundry 應用程式的憑證，請完成下列步驟：

1. 從 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}){: new_window}，按一下**功能表**圖示 ![「功能表」圖示](../icons/icon_hamburger.svg)，然後選取**資源清單**。
2. 按一下 **Cloud Foundry 應用程式**。
3. 按一下您要變更其網域的應用程式。 
4. 在應用程式的「概觀」頁面上，按一下**路徑**，然後選取**管理網域**。
5. 從「動作」直欄中，按一下「動作」圖示 ![「其他動作」圖示](../icons/action-menu-icon.svg)，然後選取**網域**。
6. 針對自訂網域，按一下**上傳**。
7. 選取一個選項，上傳檔案，然後按一下**新增**。
  
  * 憑證：一種數位文件，用來將公開金鑰連結到憑證擁有人的身分，使憑證擁有人能夠接受鑑別。憑證由憑證管理中心發行，並由該憑證管理中心執行數位簽署。一般是由憑證管理中心發出及簽署憑證。不過，您可能會使用自簽憑證進行測試及開發用途。
  * 私密金鑰：一種用來加密訊息的演算型樣，只有對應的公開金鑰可以解密。另外，私密金鑰也用來將相對應公開金鑰所加密的訊息解密。私密金鑰保存在使用者系統上，受到密碼保護。
  * 中繼憑證（選用）：由授信主要憑證管理中心 (CA) 發出的子層憑證，專門用於發出持卡實體伺服器憑證。結果會形成一條憑證鏈，從授信主要憑證管理中心開始、通過中繼憑證，最後以發給組織的 SSL 憑證結束。請使用中繼憑證來驗證主要憑證的確實性。中繼憑證通常是從信任的協力廠商處取得。在將應用程式部署至正式作業之前，測試應用程式時不一定需要中繼憑證。
  * 啟用用戶端憑證的要求：當您啟用此選項時，嘗試存取 SSL 保護網域的使用者會被要求提供用戶端憑證。例如，在 Web 瀏覽器中，當使用者嘗試存取 SSL 保護的網域時，Web 瀏覽器會提示使用者提供網域的用戶端憑證。   
  * 用戶端憑證信任儲存庫（選用）：包含要容許存取您應用程式之使用者的用戶端憑證。請上傳用戶端憑證信任儲存庫檔案，以啟用要求用戶端憑證的選項。
  
    您可以藉由上傳 meta 資料中包含公開金鑰的用戶端憑證信任儲存庫，來設定交互鑑別。
  {: tip}


