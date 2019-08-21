---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-17"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# クラウド・アプリの一般的なアーキテクチャー
{: #patterns}

{{site.data.keyword.cloud_notm}} 上のスターター・キットは、実証されたアーキテクチャーを使用したアプリケーションの生成に役立ちます。 アプリはすべて異なりますが、既知のアーキテクチャー・パターンをアプリのベースにすると、信頼性の高い結果を素早く得ることが一層容易になります。 スターター・キットからアプリを作成する際には、ランタイムなどのコンポーネントと共に、複数の異なるパターン・タイプから 1 つを選択して、パターンを設定します。
{:shortdesc}

## Web アプリ
{: #web}

Web アプリ・パターンは、HTML、JavaScript、スタイルシートなどの Web コンテンツを Web サーバーに提供するアプリを生成します。 {{site.data.keyword.cloud_notm}} は、いくつかの Web アプリ・スターター・キットを提供します。

* Basic - 静的 `index.html` ファイル、デフォルトおよび空のスタイルシート、および JavaScript ファイルを提供します。
* React - ユーザー・インターフェースをビルドするための豊富なフレームワーク。 ソース・ファイルは `src/client/app` にあり、WebPack でコンパイルされ、公開ディレクトリーで機能します。

Web アプリ・パターンのスターター・キットは、[{{site.data.keyword.cloud_notm}} アプリ・サービス開発者コンソール](https://{DomainName}/developer/appservice/dashboard){: new_window}
![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で見つけることができます。

## マイクロサービス・アプリ
{: #microservice}

マイクロサービス・アプリは、基本的なヘルス・エンドポイントや REST API など、バックエンド・マイクロサービスをビルドするための基盤を提供します。 生成されたアプリには、マイクロサービス自体と、接続されているクラウド・サービスの両方に必要なすべての依存関係が含まれています。

ご使用の言語とフレームワーク要件に合ったマイクロサービス・スターター・キットを選択してください。 マイクロサービス・パターンのスターター・キットは、[{{site.data.keyword.cloud_notm}} アプリ・サービス開発者コンソール](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で見つけることができます。

## モバイル・アプリ
{: #mobile}

モバイル・アプリは、重要なクライアント・サイド・コンポーネントがあるため、他のパターンとは異なります。 このパターンには、プッシュ通知、認証、Mobile Analytics のようなモバイル・サービスへの直接接続が含まれる場合があります。 モバイル・サービスは、Mobile Backend as a Service または MBaaS パターンと呼ばれます。 これらのサービスは、専用の Backend-for-frontend を持つ場合があります。

{{site.data.keyword.cloud_notm}} は、iOS Swift および Android のためのいくつかのモバイル・スターター・キットを提供します。 モバイル・パターンのスターター・キットは、[{{site.data.keyword.cloud_notm}} モバイル開発者コンソール](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で見つけることができます。

また、基本スターター・キットを使用してモバイル・アプリ・タイプを選択することにより、カスタム・モバイル・アプリを作成できます。 詳しくは、[モバイル・アプリの作成](/docs/apps?topic=creating-apps-tutorial-mobile)を参照してください。

## 言語ベースのアプリ
{: #languages}

{{site.data.keyword.cloud_notm}} が提供するスターター・キットは、さまざまな言語とフレームワークで使用可能です。 例えば、クラウド・マイクロサービスのスターター・キットは Node.js オプションを提供し、データ分析に密接に関連するスターター・キットには Python や Go が含まれる場合があります。 {{site.data.keyword.cloud_notm}} スターター・キットで使用されるいくつかの一般的な言語について、説明します。

|プログラミング言語 | 説明 | 開発フレームワーク |
|-----|-----|-----|
|Java | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) は、エンタープライズ・レベルのアプリをビルドする場合に適しています。 ただし、Java 8 の新規フィーチャーを、Liberty のようなより軽量のランタイムや Spring Boot のようなフレームワークと組み合わせることで、Java はマイクロサービスのビルドにも適したものになります。 Java は、Android アプリによく使用されているプログラミング言語です。 | Spring、Liberty、Android |
|Swift | [Swift](/docs/runtimes/swift?topic=Swift-getting-started) は、2014 年に作成された最新のプログラミング言語で、Objective C の代わりになるものとして設計され、2015 年 12 月にオープン・ソースになりました。 今日では、x86、ARM、または z/Architecture を使用する Linux および macOS のオペレーティング・システム上で、 iOS、macOS、Web サービス、およびシステム・ソフトウェアをビルドするために使用されています。 スクリプト言語のように記述されますが、コンパイルされると、低いプロセッサー使用率で C のようなハイパフォーマンスを実現できます。 これは、クラウド・ランタイムに理想的です。 Java に見られる強い静的型システムを使用しますが、JavaScript に見られる関数型スタイルと非同期ルーチンを使用します。 これはパフォーマンスが高く、ソースは LLVM コンパイラー・ツールチェーンを使用するネイティブ・コードにコンパイルされます。 C で記述されたシステム・ライブラリーを他の言語から簡単に使用できます。 Swift は、クライアント・サイド・アプリとサーバー・サイド・アプリのどちらのコーディングにも使用できるため、開発者は、クライアントからサーバーへ、またその逆への機能のマイグレーションを簡単に行う必要がある場合に Swift を使用します。 | Kitura、iOS|
|Node.js | [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) は、イベント・ドリブンの非ブロッキング I/O モデルを使用する JavaScript ランタイムで、軽量かつ効率的です。 Web アプリ、Backend-for-frontend パターン、およびマイクロサービスのスループットとスケーラビリティーの点で優れています。 Node.js のパッケージ・レジストリー (npm) は、大規模なコレクションのオープン・ソース・モジュールにアクセスできるようにします。 これは、アプリ開発を加速するための幅広いフィーチャーを提供します。 | Express|
|Python | [Python](/docs/runtimes/python?topic=Python-getting_started) は、読みやすさに重点が置かれた、汎用的なインタープリット型のプログラミング言語です。 プログラマーは、Python を使用すると、他の言語で必要なコード行よりも少ないコード行で機能を実装できます。 言語の機能によって、オブジェクト指向、関数型、命令型のコードを記述できます。 Python は、一般的に自然言語のタスクの処理に使用されます。 | Flask、Django |
{: caption="表 1. スターター・キットで使用される言語" caption-side="top"}
