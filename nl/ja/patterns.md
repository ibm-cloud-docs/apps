---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-22"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# クラウド・アプリの一般的なアーキテクチャー
{: #patterns}

{{site.data.keyword.cloud_notm}} 上のスターター・キットは、実証されたアーキテクチャーを使用したアプリの生成に役立ちます。 アプリはすべて異なりますが、既知のアーキテクチャー・パターンをアプリのベースにすると、信頼性の高い結果を素早く得ることが一層容易になります。 スターター・キットからアプリを作成する際には、ランタイムなどのコンポーネントと共に、複数の異なるパターン・タイプから 1 つを選択して、パターンを設定します。
{:shortdesc}

## Web アプリ
{: #web}

Web アプリ・パターンは、HTML、JavaScript、スタイルシートなどの Web コンテンツを Web サーバーに提供するアプリを生成します。 {{site.data.keyword.cloud_notm}} は、いくつかの Web アプリ・スターター・キットを提供します。

* Basic - 静的 `index.html` ファイル、デフォルトおよび空のスタイルシート、および JavaScript ファイルを提供します。
* React - ユーザー・インターフェースをビルドするための豊富なフレームワーク。 ソース・ファイルは `src/client/app` にあり、WebPack でコンパイルされ、公開ディレクトリーで機能します。

[{{site.data.keyword.cloud_notm}} アプリ・サービス開発者ダッシュボード](https://{DomainName}/developer/appservice/dashboard)で、Web アプリ・パターンのスターター・キットを見つけることができます。

## Backend-for-frontend
{: #bff}

Backend-for-frontend パターン (BFF) は、モバイルや Web といった特定のアプリ・チャネルに、ユーザーの期待に沿った方法でビジネス・データとサービスを公開する、バックエンド・コードの作成を支援します。 例えば、モバイル・デバイスのユーザーは音声制御を使用する一方、Web ブラウザーのユーザーはポイント・アンド・クリックを選びます。 2 つの BFF をビルドできます。1 つは [{{site.data.keyword.conversationfull}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/ai-assistant/) のようなサービスを含むモバイル用で、1 つはより洗練されたユーザー・インターフェースを持つ Web 用です。

{{site.data.keyword.cloud_notm}} では、多言語プログラミング・アプローチを使用して、BFF をビルドできます。 Node.js、Swift、Java、または Python を使用でき、コンテナー・サービスを使用したパターンで実行したり、サーバーレス機能を使用したりできます。

BFF は、データ・パーシスタンスとキャッシングを管理し、以下の高価値サービスとの統合を管理します。

* [{{site.data.keyword.ibmwatson}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/apache-spark?taxonomyNavigation=apps).

BFF は、通常、REST パターンを使用して API を公開しますが、{{site.data.keyword.messagehub}} を使用してメッセージング・アーキテクチャーから動作するように、BFF を設計することができます。

ご使用の言語とフレームワーク要件に合った BFF スターター・キットを選択します。 [{{site.data.keyword.cloud_notm}} アプリ・サービス開発者ダッシュボード](https://{DomainName}/developer/appservice/dashboard)で、BFF パターンのスターター・キットを見つけることができます。

## マイクロサービス
{: #microservice}

マイクロサービス・アプリは、基本的なヘルス・エンドポイントや REST API など、バックエンド・マイクロサービスをビルドするための基盤を提供します。 生成されたアプリには、マイクロサービス自体と、接続されているクラウド・サービスの両方に必要なすべての依存関係が含まれています。

ご使用の言語とフレームワーク要件に合ったマイクロサービス・スターター・キットを選択してください。 [{{site.data.keyword.cloud_notm}} アプリ・サービス開発者ダッシュボード](https://{DomainName}/developer/appservice/dashboard)で、マイクロサービス・パターンのスターター・キットを見つけることができます。

## モバイル
{: #mobile}

モバイル・アプリは、重要なクライアント・サイド・コンポーネントがあるため、他のパターンとは異なります。 このパターンには、プッシュ通知、認証、Mobile Analytics のようなモバイル・サービスへの直接接続が含まれる場合があります。 モバイル・サービスは、Mobile Backend as a Service または MBaaS パターンと呼ばれます。 これらのサービスは、専用の [Backend-for-frontend](/docs/apps/patterns.html#bff) を持つ場合があります。

{{site.data.keyword.cloud_notm}} は、iOS Swift、Android、および Cordova のためのいくつかのモバイル・スターター・キットを提供します。 [{{site.data.keyword.cloud_notm}} モバイル開発者ダッシュボード](https://{DomainName}/developer/mobile/dashboard)で、モバイル・パターンのスターター・キットを見つけることができます。

## 言語
{: #languages}

{{site.data.keyword.cloud_notm}} が提供するスターター・キットは、さまざまな言語とフレームワークで使用可能です。 例えば、クラウド・マイクロサービスのスターター・キットは Node.js オプションを提供し、データ分析に密接に関連するスターター・キットには Python や Go が含まれる場合があります。 {{site.data.keyword.cloud_notm}} スターター・キットで使用されるいくつかの一般的な言語について、説明します。

|プログラミング言語 | 説明 | 開発フレームワーク |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) は、エンタープライズ・レベルのアプリケーションをビルドする場合に適しています。 ただし、Java 8 の新規フィーチャーを、Liberty のようなより軽量のランタイムや Spring Boot のようなフレームワークと組み合わせることで、Java はマイクロサービスのビルドにも適したものになります。 Java は、Android アプリによく使用されているプログラミング言語です。 | Spring、Liberty、Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) は、2014 年に作成された最新のプログラミング言語で、Objective C の代わりになるものとして設計され、2015 年 12 月にオープン・ソースになりました。 今日では、x86、ARM、または z/Architecture を使用する Linux および macOS のオペレーティング・システム上で、 iOS、macOS、Web サービス、およびシステム・ソフトウェアをビルドするために使用されています。 スクリプト言語のように記述されますが、コンパイルされると、低いプロセッサー使用率で C のようなハイパフォーマンスを実現できます。 これは、クラウド・ランタイムに理想的です。 Java に見られる強い静的型システムを使用しますが、JavaScript に見られる関数型スタイルと非同期ルーチンを使用します。 これはパフォーマンスが高く、ソースは LLVM コンパイラー・ツールチェーンを使用するネイティブ・コードにコンパイルされます。 C で記述されたシステム・ライブラリーを他の言語から簡単に使用できます。 Swift は、クライアント・サイド・アプリとサーバー・サイド・アプリのどちらのコーディングにも使用できるため、開発者は、クライアントからサーバーへ、またその逆への機能のマイグレーションを簡単に行う必要がある場合に Swift を使用します。 | Kitura、iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) は、イベント・ドリブンの非ブロッキング I/O モデルを使用する JavaScript ランタイムで、軽量かつ効率的です。 Web アプリケーション、Backend-for-frontend パターン、およびマイクロサービスのスループットとスケーラビリティーの点で優れています。 Node.js のパッケージ・レジストリー (npm) は、大規模なコレクションのオープン・ソース・モジュールにアクセスできるようにします。 これは、アプリケーション開発を加速するための幅広いフィーチャーを提供します。 | Express|
|JavaScript|JavaScript は、Web ページでインタラクティブな効果を作成します。 JavaScript は、HTML および CSS と共に、ほとんどの Web ページの基礎となっています。 Cordova プラグインでラップすると、JavaScript コードはネイティブ・デバイス機能を最大限に活用できます。 Web スキルを持つ開発者は、モバイル・アプリを簡単に作成でき、Web とモバイルの間で必要に応じてアプリ・コードを再利用できます。|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) は、読みやすさに重点が置かれた、汎用的なインタープリット型のプログラミング言語です。 プログラマーは、Python を使用すると、他の言語で必要なコード行よりも少ないコード行で機能を実装できます。 言語の機能によって、オブジェクト指向、関数型、命令型のコードを記述できます。 Python は、一般的に自然言語のタスクの処理に使用されます。 | Flask、Django|


