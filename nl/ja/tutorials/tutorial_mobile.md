---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# モバイル・アプリの作成
{: #tutorial-mobile}

{{site.data.keyword.cloud}} は、モバイル・アプリケーションを素早く作成するために役立つモバイル・スターター・キットを提供します。 事前構成済みのアプリを使用した作業を開始するには、モバイル・スターター・キットから言語、フレームワーク、およびツールを選択します。あるいは、基本スターター・キットを使用して、カスタム・モバイル・アプリを作成することもできます。
{: shortdesc}

## 始める前に
{: #prereqs-mobile}

[{{site.data.keyword.dev_cli_long}} コマンド・ライン・インターフェース (CLI)](/docs/cli?topic=cloud-cli-getting-started) をインストールします。

## 事前構成済みのスターター・キットを使用したモバイル・アプリの作成
{: #create-mobile}

事前構成済みのスターター・キットを使用してモバイル・アプリを作成するには、以下の手順を実行します。

1. {{site.data.keyword.dev_console}}の[「モバイル・スターター・キット (Mobile Starter Kits)」](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") ページから、必要とする機能に基づいてスターター・キットを選択します。例えば、**「Watson Visual Recognition」**を選択します。
2. アプリ名を入力します。 このチュートリアルでは、`WatsonApp` を使用します。
3. オプション。 アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
4. プラットフォームを選択します。 このチュートリアルでは、**「iOS Swift」**を選択します。一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
5. 価格プランを選択します。 このチュートリアルでは、**「ライト」**オプションを使用します。必要なサービスがある場合、それらはスターター・キットで自動的に定義されます。
6. **「作成」**をクリックします。

## 基本スターター・キットを使用したカスタム・モバイル・アプリの作成
{: #create-mobile-basic}

基本スターター・キットを使用してモバイル・アプリを作成するには、以下の手順を実行します。

1. {{site.data.keyword.dev_console}}の[「モバイル・スターター・キット (Mobile Starter Kits)」](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") ページから、**「アプリの作成」**タイルを選択します。
2. アプリの名前を入力します。 このチュートリアルでは、`CustomMobile` と入力します。
3. オプションで、アプリを分類するためのタグを指定できます。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
4. 開始点として**「新規アプリの作成」**を選択します。
5. アプリ・タイプとして**「モバイル」**を選択します。
6. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
7. 価格プランを選択します。 このチュートリアルでは、無料オプションを使用できます。
8. **「作成」**をクリックします。

## サービスの追加 (オプション)
{: #resources-mobile}

選択したスターター・キットによっては、一部のサービスが既にアプリに接続されている場合があります。Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

サービスをアプリに追加するには、以下の手順を実行します。

1. **アプリの詳細**ページで**「サービスの作成」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データベース」**>**「次へ」**>**「Cloudant」**>**「次へ」**の順に選択します。
3. 価格プランを選択します。 このチュートリアルでは、**「ライト」**オプションを使用します。
4. **「作成」**をクリックします。

## コードのダウンロード
{: #mobile-download-code}

アプリ・コードをダウンロードしてローカルで処理するには、以下の手順を実行します。

1. **「アプリの詳細」**ページで**「コードのダウンロード」**をクリックします。
2. 統合開発環境にアプリをインポートします。
3. コードに変更を加え、保存します。

## モバイル・アプリの実行
{: #run-mobile-app}

### Xcode での Swift アプリの実行
{: #run_swift}

実装言語として iOS Swift を使用している場合は、以下の手順を実行します。

1. Markdown ビューアーで `README.md` ファイルを開き、アプリを構成するためのステップを確認します。
2. 端末を開き、アプリ・フォルダーにナビゲートし、以下のコマンドを実行します。
    1. CocoaPods リポジトリーのセットアップが必要な場合は、`pod setup` を実行します。
    2. 既存の pod を更新する必要がある場合は、`pod update` を実行します。
    3. アプリの pod をインストールするには、`pod install` を実行します。
3. `<appname>.xcworkspace` Xcode ワークスペースを開きます。
4. アプリを実行します。

### Android Studio での Android アプリの実行
{: #run_android}

モバイル・アプリのプラットフォームとして Android を使用している場合は、以下の手順を実行します。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
2. Android Studio で `BasicProject-Android` アプリを開きます。
3. アプリを実行します。

### Xcode での Cordova アプリの実行
{: #run_cordova_xcode}

実装言語として Cordova を使用している場合は、以下の手順を実行します。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
2. Xcode で `platforms/ios` アプリを開きます。
3. アプリを実行します。

### Android Studio での Cordova アプリの実行
{: #run_cordova_studio}

モバイル・アプリのプラットフォームとして Cordova を使用している場合は、以下の手順を実行します。

1. `BasicProject-Cordova.zip` ファイルを解凍します。
2. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
3. Android Studio で `platforms/android` アプリを開きます。
4. アプリを実行します。

## 関連情報
{: #related-mobile}

モバイル・アプリについて詳しくは、以下のチュートリアルを参照してください。

 * [プッシュ通知を使用する iOS モバイル・アプリケーション](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [プッシュ通知を使用する Android ネイティブ・モバイル・アプリケーション](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [サーバーレス・バックエンドを備えたモバイル・アプリケーション](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
