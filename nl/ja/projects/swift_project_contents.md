---
copyright:
  years: 2015, 2018
lastupdated: "2018-10-05"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Swift アプリ・ファイル
{: #swift-project-files}

Swift アプリでは、通常 {{site.data.keyword.Bluemix}} に含まれている内容のインベントリーは以下の情報のとおりです。 スターター・キットを作成すると、以下のファイルが作成されます。 {{site.data.keyword.Bluemix_notm}} でアプリをホストにマイグレーションする場合、競合の可能性を回避するためにこの情報を確認する必要があります。 
{:shortdesc}

以下の表に、生成される Swift アプリに含まれている一般的なディレクトリーとファイルをリストします。

| ルート・ディレクトリー                                     | 説明 |
|:------------------------------------------------|:------------------------------------------|
| Package.swift| Swift 依存関係定義ファイル |
| cli-config.yml | CLI 構成オプション |
| manifest.yml | Cloud Foundry デプロイメント・ファイル |
| Dockerfile | `ibmcloud dev run`、`ibmcloud dev deploy`、および `docker` の各コマンドの Dockerfile |
| `Dockerfile-tools` | `ibmcloud dev build` および `ibmcloud dev test` の Dockerfile |
| LICENSE | ライセンス・ファイル |
| README.md | アプリの説明 |
{: caption="表 1. 生成された Swift アプリのルート・ディレクトリーの内容" caption-side="top"}

| `./Sources/Application/` ディレクトリー | 説明  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | Swift アプリケーション・ファイル |
| `./Sources/<projectname>/main.swift` | Swift メインファイル |
{: caption="表 2. 生成された Swift アプリの /Sources/Application/ ディレクトリーの内容" caption-side="top"}

| `./test/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Kitura でテストするためのユーティリティー・メソッド |
{: caption="表 3. 生成された Swift アプリの test ディレクトリーの内容" caption-side="top"}

| `./Tests/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Linux 上でテストするためのユーティリティー |
| `./Tests/ApplicationTests>/RouteTests.swift` | テスト・ケースが含まれているファイル |
{: caption="表 4. 生成された Swift アプリの tests ディレクトリーの内容" caption-side="top"}

| `./.bluemix/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | コンテナー・ビルド・スクリプト |
| deploy.json | デプロイメント情報 |
| kube_deploy.sh | Kubernetes デプロイメント・スクリプト |
| pipeline.yml | IBM Cloud パイプライン定義 |
| toolchain.yml | 　IBM Cloud ツールチェーン定義 |
{: caption="表 5. 生成された Swift アプリの bluemix ディレクトリーの内容" caption-side="top"}

| `./chart/<projectname>/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm チャート |
| `./chart/<projectname>/values.yaml` | 　Helm チャート値 |
| `./chart/<projectname>/templates/deployment.yaml` | デプロイメント・テンプレート |
| `./chart/<projectname>/templates/service.yaml` | サービス・テンプレート |
{: caption="表 6. 生成された Swift アプリの chart ディレクトリーの内容" caption-side="top"}

| `./manifests/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes サービスおよびデプロイメント yaml |
{: caption="表 7. 生成された manifests ディレクトリーの内容" caption-side="top"}

