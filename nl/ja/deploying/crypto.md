---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 暗号テクノロジーを使用した鍵とデータの保護
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} は、IBM Z の暗号化をクラウドに導入します。{{site.data.keyword.cloud_notm}} は、銀行サービスや金融サービスで使用されているものと同じ暗号テクノロジーを提供します。
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} は、鍵とデータを、保存されているか、使用中や転送中であるかにかかわらず、業界の最高レベルのセキュリティーである FIPS 140-2 レベル 4 で保護します。{{site.data.keyword.hscrypto}} は、[{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html) サービスの鍵ストアであり、鍵を IBM Z の非常にセキュアな環境で保護します。

## ACSP クライアントのインストールおよび構成
{: ##crypto_config}

Advanced Cryptography Service Provider (ACSP) クライアントをインストールする前に、[カタログ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/hyper-protect-crypto-services){:new_window} から {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} のインスタンスを作成してプロビジョンしてください。次に、ご使用の環境に ACSP クライアントをインストールして構成する必要があります。

1. [GitHub リポジトリー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window} からインストール・パッケージをダウンロードします。**packages** フォルダーで、ご使用のオペレーティング・システムと CPU アーキテクチャーに適したインストール・パッケージ・ファイルを選択します。例えば、x86 上の Ubuntu の場合、`acsp-pkcs11-client_1.5-3.5_amd64.deb` を選択します。
2. `dpkg` コマンド (例えば、`dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`) を使用して、ACSP クライアント・ライブラリーをインストールするためのパッケージをインストールします。
3. {{site.data.keyword.cloud_notm}} の {{site.data.keyword.hscrypto}} サービス・インスタンスで、ナビゲーターから**「管理」**を選択します。
4. 「管理」ウィンドウで、**「構成のダウンロード (Download Config)」**をクリックして `acsp_client_credentials.uue` ファイルをダウンロードします。
5. `acsp_client_credentials.uue` ファイルをご使用のローカル環境の `/opt/ibm/acsp-pkcs11-client/config` ディレクトリーにコピーします。
6. `/opt/ibm/acsp-pkcs11-client/config` ディレクトリーで、以下のコマンドを使用してファイルをデコードします。
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. 以下のコマンドを使用して、クライアント資格情報ファイルを抽出します。
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. 以下のコマンドを使用して、`server-config` ファイルをデフォルトの場所に移動します。
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. 以下のコマンドを使用して、クライアント資格情報ファイルの名前を変更します。
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (オプション) 以下のコマンドを使用して、ファイルのグループ ID を変更します。
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. 以下のコマンドを使用して、ACSP がクラウドでサービス・インスタンスの正しい構成を使用できるようにします。
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

これで、ACSP クライアントは作動可能になり、{{site.data.keyword.hscrypto}} を使用する準備ができました。

## 次のステップ
{: ##next-steps}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} を簡単に導入するには、{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}} を開始します。{{site.data.keyword.hsplatform}} について詳しくは、『[{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}} の概説 (Getting started with IBM Cloud Hyper Protect Developer Starter Kits)](/docs/services/hypersecure-platform/index.html)』を参照してください。
