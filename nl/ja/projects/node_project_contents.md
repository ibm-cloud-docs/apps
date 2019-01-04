---
copyright:
  years: 2015, 2018
lastupdated: "2018-11-16"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Node.js アプリ・ファイル
{: #node-project-files}

Node.js アプリでは、通常 {{site.data.keyword.Bluemix}} に含まれている内容のインベントリーは以下の情報のとおりです。 スターター・キットを作成すると、以下のファイルが作成されます。 {{site.data.keyword.Bluemix_notm}} でアプリをホストにマイグレーションする場合、競合の可能性を回避するためにこの情報を確認する必要があります。 
{:shortdesc}

以下の表に、生成される Node.js アプリに含まれている一般的なディレクトリーとファイルをリストします。

| ルート・ディレクトリー                                     | 説明                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | 名前、バージョン、および依存関係を含む、パッケージに関するメタデータ情報。 |
|cli-config.yml | CLI 構成オプション |
|manifest.yml | Cloud Foundry デプロイメント・ファイル |
|Dockerfile | `ibmcloud dev run`、`ibmcloud dev deploy`、および `docker` の各コマンドの Dockerfile |
|Dockerfile-tools | `ibmcloud dev build` および `ibmcloud dev test` の Dockerfile |
|docker-compose.yml | Docker Compose のアプリ・サービス構成 |
|webpack.config.js | ビルド関連情報の Web パック構成 |
| LICENSE | ライセンス・ファイル |
|README.md | アプリの説明 |
{: caption="表 1. 生成された Node.js アプリのルート・ディレクトリーの内容" caption-side="top"}

| `./public/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | REST API を説明する Swagger 仕様 |
| `./public/index.html` | Web アプリケーションのスケルトン・マークアップ |
|`./public/server/server.js` | サーバー実装ファイル |
{: caption="表 2. 生成された Node.js アプリの public ディレクトリーの内容" caption-side="top"}

| `./test/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Express サーバーの統合テスト |
{: caption="表 3. 生成された Node.js アプリの test ディレクトリーの内容" caption-side="top"}

| `./.bluemix/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | コンテナー・ビルド・スクリプト |
| deploy.json | デプロイメント情報 |
| kube_deploy.sh | Kubernetes デプロイメント・スクリプト |
| pipeline.yml | IBM Cloud パイプライン定義 |
| toolchain.yml | 　IBM Cloud ツールチェーン定義 |
{: caption="表 4. 生成された Node.js アプリの bluemix ディレクトリーの内容" caption-side="top"}

| `./chart/<projectname>/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm チャート |
| `./chart/<projectname>/values.yaml` | 　Helm チャート値 |
| `./chart/<projectname>/templates/deployment.yaml` | デプロイメント・テンプレート |
| `./chart/<projectname>/templates/service.yaml` | サービス・テンプレート |
{: caption="表 5. 生成された Node.js アプリの chart ディレクトリーの内容" caption-side="top"}
