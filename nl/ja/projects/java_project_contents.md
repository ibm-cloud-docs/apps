---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Java アプリ・ファイル
{: #java-project-files}

次の情報は、Java アプリの場合に {{site.data.keyword.Bluemix}} で通常見られるものの一覧です。 スターター・キットを作成すると、以下のファイルが作成されます。 {{site.data.keyword.Bluemix_notm}} でアプリをホストにマイグレーションする場合、競合の可能性を回避するためにこの情報を確認する必要があります。
{:shortdesc}

## Spring
{: #spring-project-files}

次の表に、生成された Java Spring アプリに含まれるディレクトリーとファイルをリストします。

| `./` ディレクトリー                                  | 説明                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | 　maven pom ファイル |
| cli-config.yml | CLI 構成オプション |
| manifest.yml | Cloud Foundry デプロイメント・ファイル |
| Dockerfile | `ibmcloud dev run`、`ibmcloud dev deploy`、および `docker` の各コマンドの Dockerfile |
| Dockerfile-tools | `ibmcloud dev build` および `ibmcloud dev test` の Dockerfile |
| LICENSE | ライセンス・ファイル |
| README.md | アプリの説明 |
{: caption="表 1. 生成された Java Spring アプリのルート・ディレクトリーの内容" caption-side="top"}

| `./src/main/java/` ディレクトリー | 説明                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | メイン Spring アプリケーション |
| `./src/main/test/application/HealthEndpointTest.java` | テスト |
| `./src/main/java/application/rest/HealthApplication.java` | 　ヘルス・エンドポイント |
| `./src/main/java/application/rest/v1/Example.java` | 　コード例 |
| `./src/main/java/resources/application-local.properties` | 　Spring プロパティー |
{: caption="表 2. 生成された Java Spring アプリの /java/ ディレクトリーの内容" caption-side="top"}

| `./.bluemix/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | コンテナー・ビルド・スクリプト |
| deploy.json | デプロイメント情報 |
| kube_deploy.sh | Kubernetes デプロイメント・スクリプト |
| pipeline.yml | IBM Cloud パイプライン定義 |
| toolchain.yml | 　IBM Cloud ツールチェーン定義 |
{: caption="表 3. 生成された Java Spring アプリの ./.bluemix/ ディレクトリーの内容" caption-side="top"}

| `./chart/<projectname>/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm チャート |
| `./chart/<projectname>/values.yaml` | 　Helm チャート値 |
| `./chart/<projectname>/templates/deployment.yaml` | デプロイメント・テンプレート |
| `./chart/<projectname>/templates/hpa.yaml` | HPA テンプレート |
| `./chart/<projectname>/templates/service.yaml` | サービス・テンプレート |
{: caption="表 4. 生成された Java Spring アプリの ./chart/<projectname/templates/ ディレクトリーの内容" caption-side="top"}>

| `./manifests/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes サービスおよびデプロイメント yaml |
{: caption="表 5. 生成された Java Spring アプリの ./manifests/ ディレクトリーの内容" caption-side="top"}

## Liberty
{: #liberty-project-files}

次の表に、生成された Java Liberty アプリに含まれるディレクトリーとファイルをリストします。

| `./` ディレクトリー                                  | 説明                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | 　maven pom ファイル |
| cli-config.yml | CLI 構成オプション |
| manifest.yml | Cloud Foundry デプロイメント・ファイル |
| Dockerfile | `ibmcloud dev run`、`ibmcloud dev deploy`、および `docker` の各コマンドの Dockerfile |
| Dockerfile-tools | コマンド `ibmcloud dev build`、`ibmcloud dev test` の Dockerfile |
| LICENSE | ライセンス・ファイル |
| README.md | アプリの説明 |
{: caption="表 6. 生成された Java Liberty アプリのルート・ディレクトリーの内容" caption-side="top"}

| `./src/main` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | 　ヘルス・エンドポイント |
| `./src/main/java/application/rest/v1/Example.java` | 　コード例 |
| `./src/main/liberty/config/jvm.options` | JVM オプション |
| `./src/main/liberty/config/jvmbx.options` | Java メトリック・エージェント構成 |
| `./src/main/liberty/config/server.env` | 環境変数 |
| `./src/main/liberty/config/server.xml` | サーバー構成 |
| `./src/main/webapp/WEB-INF/beans.xml` | CDI Bean 構成 |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | IBM Web アプリ構成 |
| `./src/main/test/it/HealthEndpointTest.java` | テスト |
{: caption="表 7. 生成された Java Liberty アプリの ./src/main/ ディレクトリーの内容" caption-side="top"}

| `./.bluemix/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | コンテナー・ビルド・スクリプト |
| deploy.json | デプロイメント情報 |
| kube_deploy.sh | Kubernetes デプロイメント・スクリプト |
| pipeline.yml | IBM Cloud パイプライン定義 |
| toolchain.yml | 　IBM Cloud ツールチェーン定義 |
{: caption="表 8. 生成された Java Liberty アプリの ./bluemix/ ディレクトリーの内容" caption-side="top"}

| `./chart/<projectname>/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm チャート |
| `./chart/<projectname>/values.yaml` | 　Helm チャート値 |
| `./chart/<projectname>/templates/deployment.yaml` | デプロイメント・テンプレート |
| `./chart/<projectname>/templates/hpa.yaml` | HPA テンプレート |
| `./chart/<projectname>/templates/service.yaml` | サービス・テンプレート |
{: caption="表 9. 生成された Java Liberty アプリの ./chart/<projectname/ ディレクトリーの内容" caption-side="top"}>

| `./manifests/` ディレクトリー | 説明 |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes サービスおよびデプロイメント yaml |
{: caption="表 10. 生成された Java Liberty アプリの ./manifests/ ディレクトリーの内容" caption-side="top"}
