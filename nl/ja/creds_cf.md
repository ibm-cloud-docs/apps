---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Cloud Foundry 環境への資格情報の追加
{: #add-credentials-cf}

Cloud Foundry デプロイメント環境にサービス資格情報を追加する方法について説明します。 これらの説明は、[Cloud Foundry パブリック](/docs/cloud-foundry-public/about-cf.html#about-cf)と [Cloud Foundry エンタープライズ環境](/docs/cloud-foundry-public/cfee.html#cfee)の両方に当てはまります。
{: shortdesc}

## ユーザー作成コード + Cloud Foundry
{: #credentials-byoc-cf}

アプリケーションが存在する Cloud Foundry スペースで、Cloud Foundry がユーザー提供のサービスをどのように呼ぶかを定義できます。 ユーザー提供のサービスは、Cloud Foundry スペース内のバインド可能サービスのように保管される、ストリング化された JSON です。 Cloud Foundry 組織およびスペースにログインして接続した後、以下のステップを実行してサービスを作成し、バインドします。

1. 以下のコマンドを実行して、ユーザー提供のサービスを作成します。
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. サービスを services セクションに追加して、ユーザー提供のサービスにバインドするように Cloud Foundry アプリケーションを構成します。
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. `VCAP_SERVICES` 環境変数の環境を読み取り、それを JSON に解析し、必要な資格情報を見つけるためのアプリケーションをコーディングします (node.js のような疑似プログラム)。
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## スターター・キット・アプリ + Cloud Foundry
{: #credentials-starterkit-cf}

### Cloud Foundry スペースの準備方法

**「クラウドにデプロイ」**フィーチャーを使用して、アプリを Cloud Foundry スペースにデプロイします。

Cloud Foundry ベースのリソース・インスタンスが、デプロイされる Cloud Foundry アプリケーションと同じ Cloud Foundry スペース内にある場合は、[次のセクション](/docs/apps/creds_cf.html#cf_resource_same)を参照してください。

Cloud Foundry ベースのリソース・インスタンスが、Cloud Foundry アプリケーションのターゲット・スペースとは異なるスペースにある場合は、[その後のセクション](/docs/apps/creds_cf.html#cf_resource_different)を参照してください。

アプリケーションに関連付けたリソースがリソース・コントローラー・ベースの場合は、[リソース・コントローラー](/docs/apps/creds_cf.html#cf_resource_controller)を参照してください。

#### Cloud Foundry ベースのリソースが、デプロイされるアプリと同じスペース内にある場合
{: #cf_resource_same}

アプリケーションに関連付けたリソースが Cloud Foundry ベースの場合、リソースは Cloud Foundry 内で「バインド可能」です。 `cf` コマンド・ラインを正しい地域 + 組織 + スペースに接続することで、Cloud Foundry スペース内のサービスを表示できます。 リソースが Cloud Foundry ベースかどうかは、リソース作成時にどの Cloud Foundry 組織およびスペース内にリソースを作成するかを尋ねられたかどうかで分かります。

以下のコマンドを実行して、バインド済みアプリケーションを表示できます。
```console
cf services
```
{: codeblock}

出力例:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### Cloud Foundry ベースのリソースが、デプロイされるアプリとは異なるスペース内にある場合
{: #cf_resource_different}

アプリケーションとサービスが同じ Cloud Foundry スペース内にない場合、Cloud Foundry は、Cloud Foundry サービスへの Cloud Foundry アプリケーションの「バインディング」をサポートしません。 「ユーザー提供」のサービスを含んだ Cloud Foundry スペースを準備する必要があり、以下のセクションが適用されます。

#### リソース・コントローラー・ベースのリソースがアプリに関連付けられている場合
{: #cf_resource_controller}

アプリケーションに関連付けたリソースがリソース・コントローラー・ベースである場合 (リソース作成時、どのリソース・グループ内にリソースを作成するか尋ねられた場合、そのリソースは `ResourceController` ベースであることが分かります)、リソースは、Cloud Foundry 内で「バインド可能」では_ありません_。 アプリケーションがコード内でリソース資格情報を参照できるように、Cloud Foundry スペースにその資格情報を準備する必要があります。 準備は自動的に行われ、`cf` コマンド・ラインをスペースに接続し、以下を実行することにより、スペースの準備の結果を監視できます。
```console
cf services
```
{: codeblock}

出力例:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry では、サービス資格情報がエンコードされているかどうかにかかわらず、`cf service` または `cf services` のコマンド・ラインにサービス資格情報の値を表示することは許可されません。 機能的に、ユーザー提供のサービスは、Cloud Foundry スペース内に名前付きの「サービス・インスタンス」として定義される、ストリング化された JSON です。 値を確認するには、まず、アプリの `manifest.yml` ファイル内の `services` ヘッディングの下にサービス・インスタンス名を指示することにより、アプリケーションを Cloud Foundry サービスにバインドする必要があります。 次に、Cloud Foundry スペースでアプリを実行し、`cf env $APP_NAME` を実行してそのアプリケーションの環境を取得します。

しかしながら、スターター・キットで生成されるコードには、アプリケーションが実行される Cloud Foundry スペースに定義されている環境の値を取得および使用するための正しいバインディングが自動的に取り込まれます。

### スターター・キットによって生成されるコード
{: #starterkit-generated-code-cf}

続行する前に、[スターター・キット・アプリ + Kubernetes](/docs/apps/creds_kube.html#credentials-starterkit-kube-gencode) を参照してください。 次に、以下の変更を適用します。

* 生成されるコードによって `deployment.yml` が提供されますが、Cloud Foundry にデプロイされるアプリケーションには適用できません。 代わりに、`manifest.yml` が_適用可能_ であり、その内容は、Cloud Foundry スペースで作成された 2 つのサービスに_バインド_ されることがわかります。
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

前のサブセクションにある残りの資料が、ここでも再度適用されます。 `IBMCloudEnv` ライブラリーは、アプリケーションが実行される環境からの値の取得を抽象化します。

このライブラリーは、Cloud Foundry から環境の値を取得する際の複雑さを抽象化します。 Cloud Foundry では、実行中のアプリケーションに `VCAP_SERVICES` という名前の環境変数が用意されます。この環境変数の値はストリング化された JSON であり、サービスが Cloud Foundry スペース _内の_ サービス・インスタンスであるか、ユーザー定義のサービス値であるかにかかわらず、バインドされたサービス資格情報の値を保持します。 `VCAP_SERVICES` 環境変数から解析された JSON の最上位のキーは、Cloud Foundry ベースのサービスに関連付けられた Cloud Foundry `label` と、すべての「ユーザー提供」サービスの資格情報の配列を値に保持するキー `user-provided` になります。

**注意**:  参照先セクションで示されている注意と同様に、環境の準備は、_常に_、アプリに関連付けられたすべてのリソースのすべての資格情報を対象に実行され、すべての `services` が `manifest.yml` 内にリストされますが、`mappings.json` ファイル内には、_必ずしもすべての資格情報参照_ が配置されるわけではありません。 その場合、そのような参照はユーザー自身が配置する必要があります。 ターゲット・デプロイメントを決定した後は、`IBMCloudEnv` ライブラリーの抽象化が不要であれば、決定したデプロイメントに適した『ユーザー作成コード + (ターゲット・デプロイメント)』セクションを参照してください。

**二重注意**: 一部のスターター・キットは、`IBMCloudEnv` 依存関係、`manifest.yml` ファイル、および `mappings.json` ファイルへの参照をいっさい組み込みません。
