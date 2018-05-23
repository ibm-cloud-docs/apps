---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# スターター・キットを使用したモバイル・アプリケーションの作成
{: #tutorial}

モバイル基本スターターからモバイル・アプリを作成できます。 必要なツールをインストールする方法と、Xcode および Android Studio でアプリを実行するステップが表示されます。
{: shortdesc}

## ツールのインストール
{: #before-you-begin}

[開発者ツール](/docs/cli/idt/index.html#create){: new_window}をインストールします。

## アプリの作成方法の選択
{: #choose_how}

以下のいずれかの方法を使用して、アプリを作成できます。
- Web ベースの[{{site.data.keyword.dev_console}}](#create-devex)
- ローカルのコマンド駆動の [{{site.data.keyword.dev_cli_notm}}](#create-cli)

## {{site.data.keyword.dev_console}} を使用したアプリの作成
{: #create-devex}

1. {{site.data.keyword.Bluemix}} で {{site.data.keyword.dev_console}}・アプリを作成します。

    1. {{site.data.keyword.dev_console}}の[「スターター・キット」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) ページから、必要な機能に基づいてスターター・キットを選択します。 例えば、Watson Language アプリケーションの場合は、**「Watson Language」**に移動し、**「スターター・キットの選択」**をクリックします。

    2. アプリ名を入力します。 このチュートリアルでは、`WatsonApp` を使用します。   

    3. ご使用の言語プラットフォームを選択します。 このチュートリアルでは、`Swift` を使用します。

    4. **「作成」**をクリックします。

### オプション: サービスの追加
{: #add-services}

1. **「アプリ」**ページでアプリを選択します。

2. **「サービスの追加」**をクリックします。

3. 必要なサービスの種類を選択します。 このチュートリアルでは、**「セキュリティー」**>**「次へ」**>**「アプリ ID」**>**「次へ」**を選択します。

4. サービス名を入力し、**「作成 (Create)」**をクリックします。

5. 認証の構成について詳しくは、[ID プロバイダーの構成 (Configuring identity providers) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/appid/identity-providers.html){: new_window} を参照してください。

6. 分析の構成について詳しくは、[{{site.data.keyword.mobileanalytics_short}} の概説 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/mobileanalytics/index.html){: new_window} を参照してください。

7. {{site.data.keyword.cloudant_short_notm}} の構成について詳しくは、[{{site.data.keyword.cloudant_short_notm}} の概説 (Getting started with Cloudant NoSQL DB) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/Cloudant/index.html){: new_window} を参照してください。

8. {{site.data.keyword.objectstorageshort}} の構成について詳しくは、[{{site.data.keyword.objectstorageshort}} 概説 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/ObjectStorage/index.html){: new_window} を参照してください。

9. プッシュ通知の追加について詳しくは、プッシュ[通知の資料](/docs/services/mobilepush/c_overview_push.html#overview-push)を参照してください。

### アプリ・コードの生成
{: #generate-code}

1. **「アプリ」**ページでアプリを選択します。

2. **「コードのダウンロード」**をクリックして、アプリ・アーカイブをダウンロードします。

### アプリでの作業の開始
{: #code}

ダウンロードしたアプリでの作業を開始します。

1. アーカイブ対象ファイルを展開します。

2. 新規アプリ・ディレクトリーにナビゲートします。

3. {{site.data.keyword.dev_cli_notm}} を使用して続行します。


## {{site.data.keyword.dev_cli_notm}} を使用したアプリの作成
{: #create-cli}

1. 必ず [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html) をインストールしてください。

2. 端末プロンプトで、選択したローカル・ディレクトリーにナビゲートして、以下のコマンドを実行します。

	```
	bx dev create
	```
	{: codeblock}

3. プロンプトが出されたら、以下の値を指定します。

	* アプリ・タイプとしてオプション 2 の「Mobile Client」を選択します。
	* 実装言語にはオプション 3 の「iOS Swift」を選択します。
	* スターター・キットにはオプション 1 の「Mobile App: Basic」を選択します。
	* アプリの名前に `MobileBasicProject` と入力します。

    注: 実際の選択番号は、ツールの機能拡張によって変わる可能性があります。

4. サービスをアプリに追加するには、質問プロンプトで `y` と入力して、残りの質問に回答します。

5. `MobileBasicProject` が正常に作成および保存されたら、`MobileBasicProject/MobileBasicProject-Swift` フォルダーにナビゲートします。

### Xcode での Swift アプリの実行
{: #run_swift}

1. Markdown ビューアーで `README.md` ファイルを開き、アプリを構成するためのステップを確認します。

2. 端末を開き、アプリ・フォルダーにナビゲートし、以下のコマンドを実行します。
    1. CocoaPods リポジトリーのセットアップが必要な場合は、`pod setup` を実行します。
    2. 既存の pod を更新する必要がある場合は、`pod update` を実行します。
    3. アプリの pod をインストールするには、`pod install` を実行します。

3. `<appname>.xcworkspace` Xcode ワークスペースを開きます。

4. アプリを実行します。

### Xcode での Cordova アプリの実行
{: #run_cordova_xcode}

実装言語として Cordova を使用するように選択した場合は、以下の指示に従います。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。

2. Xcode で `platforms/ios` アプリを開きます。

3. アプリを実行します。

### Android Studio での Cordova アプリの実行
{: #run_cordova_studio}

モバイル・アプリのプラットフォームとして Cordova を使用するように選択した場合は、このセクションを使用します。

1. `BasicProject-Cordova.zip` ファイルを解凍します。

2. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。

3. Android Studio で `platforms/android` アプリを開きます。

4. アプリを実行します。

### Android Studio での Android アプリの実行
{: #run_android}

モバイル・アプリのプラットフォームとして Android を使用するように選択した場合は、このセクションを使用します。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。

2. Android Studio で `BasicProject-Android` アプリを開きます。

3. アプリを実行します。
