---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, key protection, ACSP client, data protection, protect keys, data, protect, ascp, crypto, keys, cryptography

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用加密技術保護金鑰及資料
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} 為雲端帶來了 IBM Z 加密法。{{site.data.keyword.cloud_notm}} 提供的是金融與財務服務所依賴的相同加密技術。
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 以業界最高的安全層次 FIPS 140-2 Level 4 來保護靜止、使用中及傳送的金鑰和資料。{{site.data.keyword.hscrypto}} 是 [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto?topic=hs-crypto-get-started) 服務的金鑰儲存庫，並且以超安全的 IBM Z 環境保護您的金鑰。

## 安裝及配置 ACSP 用戶端
{: #crypto_config}

安裝「進階加密法服務提供者 (ACSP)」用戶端之前，請從[型錄 ](https://{DomainName}/catalog/services/hyper-protect-crypto-services){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 建立並佈建 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 的實例。接著，您必須在您的環境中安裝及配置 (ACSP) 用戶端。

1. 從 [GitHub 儲存庫 ](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 下載安裝套件。在 **packages** 資料夾，選擇適合您作業系統及 CPU 架構的安裝套件檔。例如，對於 x86 上的 Ubuntu，請選擇 `acsp-pkcs11-client_1.5-3.5_amd64.deb`。
2. 使用 `dpkg` 指令來安裝套件，以安裝 ACSP 用戶端程式庫，例如 `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`。
3. 在 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.hscrypto}} 服務實例，請從導覽器選取**管理**。
4. 在管理視窗中，按**下載配置**以下載 `acsp_client_credentials.uue` 檔。
5. 將 `acsp_client_credentials.uue` 檔複製到本端環境中的 `/opt/ibm/acsp-pkcs11-client/config` 目錄。
6. 在 `/opt/ibm/acsp-pkcs11-client/config` 目錄中，使用下列指令將檔案解碼：
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. 使用下列指令擷取用戶端認證檔：
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. 使用下列指令將 `server-config` 檔移入預設位置：
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. 使用下列指令重新命名用戶端認證檔：
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. （選用）使用下列指令變更檔案的群組 ID：
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. 讓 ACSP 能在雲端服務實例使用適當的配置：
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

現在 ACSP 用戶端已在作業中，您的 {{site.data.keyword.hscrypto}} 也已經可以使用！

## 後續步驟
{: #next-steps notoc}

一個輕鬆採用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} 的方法是從 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}} 開始。如需 {{site.data.keyword.hsplatform}} 的相關資訊，請參閱[開始使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform?topic=services/hypersecure-platform-getting-started-with-ibm-cloud-hyper-protect-developer-starter-kits)。
