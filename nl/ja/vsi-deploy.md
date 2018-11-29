---
copyright:

  years: 2018

lastupdated: "2018-11-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# 仮想サーバーへのデプロイ
{: #vsi-deploy}

{{site.data.keyword.cloud}} [App Service ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} を使用して、仮想サーバー・インスタンスを含むさまざまなタイプの環境にアプリをデプロイできます。 仮想サーバー・インスタンスは、ベアメタル・マシンをエミュレートするものであり、オンプレミス・ワークロードをクラウドに移動する際の一般的なデプロイメント選択肢の 1 つです。
{: shortdesc}

仮想サーバー・インスタンスは、すべてのワークロード・タイプにおいて、他の構成と較べて優れた透過性、予測可能性、および自動化を提供します。 これをベアメタル・サーバーと組み合わせると、ユニークなワークロードの組み合わせを作成できます。 例えば、ベアメタルと Debian Linux ベースのオペレーティング・システムを実行する GPU 構成で、高性能なデータベース・ロジックまたは機械学習を作成することができます。

仮想サーバー・インスタンスのプロビジョニングとデプロイは、複雑で時間のかかるプロセスになる可能性がありますが、{{site.data.keyword.cloud_notm}} App Service を使用することで、素早く稼働させることができます。

## 始める前に
{: #prereqs}

従量課金 (PAYG) アカウントにアップグレードしてください。 仮想インスタンスを使用するには、ご使用の {{site.data.keyword.cloud_notm}} アカウントをクラシック・インフラストラクチャーに対して使用可能に設定する必要があります。 アカウントをアップグレードするには、コンソールで、**「管理」** > **「請求および使用量」** > **「請求処理」**と進みます。

**重要:** サービスは、仮想サーバー・インスタンスにはバインドされません。 サービスを仮想サーバー内のアプリケーションに追加することはできません。

## アプリの作成およびデプロイ
{: #create-deploy}

App Service によって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、Devops ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。

1. [アプリを作成](index.html#createapp)します。 
2. アプリの詳細ページから**「クラウドにデプロイ (Deploy to Cloud)」**をクリックします。
3. **「仮想サーバーへのデプロイ (Deploy to a Virtual Server)」** を、サーバーを実行する地域と共に選択します。

## デプロイメント・プロセスの仕組み

仮想サーバーのデプロイメント・プロセスは、Terraform、パイプライン使用可能化、API 鍵管理 (Git 操作)、およびツールチェーン・プロセスの理解など、いくつかの主要テクノロジーからなります。 

### Terraform を使用したデプロイ

どの App Service スターター・キットも、オープン・ソースの Infrastructure as Code フレームワークである [Terraform ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} を使用して、動的に作成された仮想インスタンスにデプロイできます。 

### パイプライン・デプロイメントの使用可能化

{{site.data.keyword.cloud_notm}} [App Service ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}を使用するスターター・キットを作成する際は、仮想サーバー・インスタンスが使用可能になります。 アプリの作成後、アプリをデプロイする場所を選択できます。 スターター・キットでは、Continuous Delivery ツールチェーンを使用したデプロイメントのサポートが有効になっています。 スターター・キットは Kubernetes、Cloud Foundry、および仮想サーバー・インスタンスをターゲットとすることができます。 ツールチェーンにはソース・コード・リポジトリーとデプロイメント・パイプラインが含まれています。

仮想サーバー・オプションは段階的に機能します。 最初に、アプリ・コードが準備されて GitLab Git リポジトリーに保管され、ソース・コードによってパイプラインが備わったツールチェーンが作成されます。 このパイプラインは、コードをビルドして Debian Package マネージャー・フォーマットにパッケージするよう定義されています。 次に、Terraform が仮想インスタンスをプロビジョンします。 最後に、アプリがデプロイされ、インストールされ、実行中の仮想イメージ内で開始されて、その正常性が検証されます。

パイプラインは、一連のユーザー・アカウント・プロパティーおよび新しい SSH 鍵ペアを使用して、インフラストラクチャーにデプロイします。 これらのプロパティーは、自動的にツールチェーンに渡されますが、セキュリティー上の理由から Git ソース・コードには保管されません。

これらの環境プロパティーを表示するには、以下のステップを実行します。 

1. アプリの詳細ページで、**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**タイルをクリックします。
3. **「ステージの構成 (Stage Configure)」**アイコンをクリックし、次にビルド・ステージで**「ステージの構成」**をクリックします。
4. **「環境プロパティー」**タブをクリックしてプロパティーを表示します。 使用可能なプロパティーについては、次の表を参照してください。

  | プロパティー   | 説明   |
  |---|---|
  | `TF_VAR_ibm_sl_api_key` | [インフラストラクチャー API キー](#iaas-key)。クラシック・インフラストラクチャー・コンソールから取得できます。 |
  | `TF_VAR_ibm_sl_username` | [インフラストラクチャー・ユーザー名](#user-key)。クラシック・インフラストラクチャー・アカウントを識別します。 |
  | `TF_VAR_ibm_cloud_api_key` | {{site.data.keyword.cloud_notm}} [プラットフォーム API キー](#platform-key)。サービス作成を使用可能にするために使用します。 |
  | `PUBLIC_KEY` | [パブリック・キー](#public-key)。仮想サーバー・インスタンスへのアクセスを使用可能するために。 |
  | `PRIVATE_KEY` | [プライベート・キー](#public-key)。仮想サーバー・インスタンスへのアクセスを使用可能にするために。 **注**: `\n` 改行スタイル・フォーマットを使用する必要があります。 |
  | `VI_INSTANCE_NAME` | 仮想サーバー・インスタンス用に自動生成された名前です。 |
  | `GIT_USER` | apply コマンドの状態を保管するように [Terraform 状態](#tform-state)を設定する場合、GitLab ユーザー名が必要です。 |
  | `GIT_PASSWORD` | apply コマンドの状態を保管するように [Terraform 状態](#tform-state)を設定する場合、GitLab パスワードが必要です。 |
  {: caption="表 1. 使用可能にするために変更する環境変数" caption-side="top"}

#### インフラストラクチャー API キー
{: #iaas-key}

Terraform は、クラシック・インフラストラクチャー・リソースを作成するためにインフラストラクチャー API キーを必要とします。この API キーはデプロイメント中に自動的に取得されます。 キーを手動で取得するには、以下のステップを実行します。 

1. クラシック・インフラストラクチャー・[ユーザー・リスト ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} にアクセスします。 **「メニュー」** > **「クラシック・インフラストラクチャー」** > **「アカウント」** > **「ユーザー・リスト」**の順にクリックすることもできます。
2. ツールチェーンを作成しているユーザーの詳細を見つけて、「API キー」列の**「表示」**をクリックするか、**「生成」**をクリックします。 どちらの手順でも、ウィンドウに API キーが表示されます。
3. API キーをコピーして、ツールチェーンの構成 `TF_VAR_ibm_sl_api_key` の値と置き換えます。

#### クラシック・インフラストラクチャー・ユーザー名
{: #user-key}

クラシック・インフラストラクチャー・ユーザー名もデプロイメント時に自動的に取得されて使用されます。 ユーザー名を手動で取得するには、以下のステップを実行します。

1. クラシック・インフラストラクチャー・[ユーザー・リスト ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} にアクセスします。 **「メニュー」** > **「クラシック・インフラストラクチャー」** > **「アカウント」** > **「ユーザー・リスト」**の順にクリックすることもできます。
2. ツールチェーンを作成する対象のユーザーをクリックします。
3. **「VPN ユーザー名 (VPN User Name)」**プロパティーまでスクロールダウンします。
4. この値をカット・アンド・ペーストして、ツールチェーン構成 `TF_VAR_ibm_sl_username` と置き換えます。

#### プラットフォーム API キー
{: #platform-key}

Terraform でデータベース・サービスや Compose サービスなどのプラットフォーム・レベル・サービスを作成するために、プラットフォーム API キーが自動的に取得され、環境変数としてパイプラインに保管されます。 プラットフォーム・キーを手動で取得するには、以下のステップを実行します。

1. [「API キー」![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys) ページから、**「管理」** > **「セキュリティー」** > **「プラットフォーム API キー」**をクリックします。
2. **「作成」**をクリックします。
3. 名前と説明を入力して**「作成」**をクリックします。
4. ウィンドウが開いたら、**「表示」**をクリックしてキーを確認してください。
5. キーをクリップボードにコピー・アンド・ペーストするか、キーをダウンロードします。
6. ツールチェーン構成 `TF_VAR_ibm_cloud_api_key` の値を生成された値と置き換えます。

#### パブリック・キーとプライベート・キー
{: #public-key}

ツールチェーンで Debian パッケージを仮想サーバー・インスタンスにインストールするために、デプロイメント・インフラストラクチャーは、Git コンテンツをインスタンスに転送するためのプライベート SSH 鍵とパブリック SSH 鍵のペアを自動的に生成します。

これを行うには、以下のようにします。
1. クライアントで以下の手順を使用して、[パブリック・キーとプライベート・キーのペア![外部リンク・アイコン](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}を作成します。
2. [インフラストラクチャー SSH 鍵ビュー ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window} にアクセスします。 **「メニュー」** > **「クラシック・インフラストラクチャー」** > **「デバイス」** > **「管理」** > **「SSH 鍵」**の順にクリックすることもできます。
3. **「追加」**をクリックします。
4. 以前作成したパブリック・キーのコンテンツをコピーし、キー・コンテンツにペーストします。
5. キーに名前を付けて、**「追加」**をクリックします。

プライベート・キーは 1 行で入力する必要があります。 改行は、`\n` に置き換えます。 次の例を参照してください。
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Terraform 状態の使用可能化
{: #tform-state}

Terraform は Terraform `apply` コマンドの状態の保管をサポートします。 この状態ファイルは 2 回目の `apply` コマンドを実行し、いずれかの Terraform 構成ファイルに変更があるかどうかを判別します。 状態は、アプリおよび構成が自動的にセットアップされる Git リポジトリーに保管されます。

状態の保管を可能にするために、`GIT_USER` および `GIT_PASSWORD` は、ツールチェーン環境変数のプロパティーとして自動的に構成されます。 これらの値にアクセスする必要がある場合は、以下の手順に従います。

1. 「ツールチェーン」ビューで、 コード・ツールから Git リポジトリーにアクセスします。
2. GIT Lab で、**「プロファイル・アイコン」**をクリックし、次に**「設定」**をクリックします。
3. **「アカウント」**をクリックし、ユーザー名をコピーして `GIT_USER` の値と置き換えます。
4. **「アクセス・トークン」**をクリックします。
5. トークンの名前を定義し、適用範囲を選択し、**「個人用アクセス・トークンの作成 (Create Personal Access Token)」**をクリックします。
6. `「新しい個人用アクセス・トークン (Your New Personal Access Token)」` フィールドの**「コピー」**をクリックし、ツールチェーン・プロパティーの `GIT_PASSWORD` の値を置き換えます。

Terraform の状態は `terraform` というブランチに保管されており、変更された場合にパイプラインの実行をトリガーしません。

### Git 操作の使用可能化
{: #git-repo}

アプリが {{site.data.keyword.cloud_notm}} にデプロイされると、ソース・コード管理用のコードをホストするために GitLab リポジトリーが作成されます。 Git 操作を使用することで、チームが変更を処理してアプリに配信できるようになります。 以下で、このリポジトリーに含まれるフォルダーとその内容について説明します。

#### Debian フォルダー
{: #debian-folder}

`debian` フォルダーには、アプリを [Debian パッケージ ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}にパッケージ化するために必要となる構成が保持されています。

#### Terraform フォルダー
{: #terraform-folder}

`terraform` フォルダーには、インフラストラクチャーのリソースをプロビジョンする際に使用する Infrastructure as Code の構成が保持されています。 ファイル `main.tf` は、Terraform 構成のオプションを変更するためのメイン・ソースです。

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

また、Terraform でベアメタル・サーバーをプロビジョンすることもできます。 詳しくは、[IBM Terraform Provider の資料![外部リンク・アイコン](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} および [IBM Terraform Provider GIT Repo ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}を参照してください。

仮想インスタンスの作成のターゲットとするデータ・センターを変更するには、`variables.tf` を使用できます。 プラットフォーム上の定義済みデータ・センターのリストを確認するには、[データ・センター![外部リンク・アイコン](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}を参照してください。

デフォルトで、Terraform ファイルは Washington および `wdc04` 向けに構成されています。
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### ツールチェーン・ステージの理解
{: #toolchain-stages}

ツールチェーンは、1 つのシンプルなパイプラインでインフラストラクチャーおよびアプリのデプロイメントを示しています。 Infrastructure as Code の部分を 1 つのパイプラインに、アプリのデプロイメントを別のパイプラインに分割してください。

ツールチェーンのプロセスには 5 つのステージがあります。

1. ビルド・ステージは Git リポジトリーを複製し、コードを Debian パッケージにパッケージ化します。
2. Terraform プラン・ステージは Terraform のプランを作成します。
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. Terraform 適用ステージは Terraform 構成を適用し、仮想サーバーの IP アドレスが使用可能になるまで待機します。

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. デプロイ、インストール、開始の各ステージは、最初のステージでビルドされた Debian パッケージを実行中の仮想サーバーへ移動し、インストールして開始します。
5. ヘルス・チェック・ステージは、アプリでヘルス・エンドポイントが使用可能かどうかを検証し、パイプラインを完了します。

開始後にアプリにアクセスするには、ヘルス・チェック・ステージのログをチェックします。 アプリの IP アドレスとポートを表示しているログにリストされた URL リンクをクリックしてください。
