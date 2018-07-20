---
copyright:

  years: 2018

lastupdated: "2018-07-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 仮想サーバーへのデプロイ
{: #vsi-deploy}

{{site.data.keyword.cloud}} [App Service ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}アプリを仮想サーバー・インスタンスにデプロイし、ご使用のプラットフォームとインフラストラクチャー開発者アクティビティーが連動できるようにして、アプリの制御と柔軟性を向上させます。
{: shortdesc}

仮想サーバー・インスタンスは、すべてのワークロード・タイプにおいて、他の構成と較べて優れた透過性、予測可能性、および自動化を提供します。 これをベアメタル・サーバーと組み合わせると、ユニークなワークロードの組み合わせを作成できます。 例えば、ベアメタルと Debian Linux ベースのオペレーティング・システムを実行する GPU 構成で、高性能なデータベース・ロジックまたは機械学習を作成することができます。

## 始める前に
仮想インスタンスを使用するには、ご使用の {{site.data.keyword.cloud_notm}} アカウントをインフラストラクチャーに対して使用可能に設定する必要があります。 詳しくは、[インフラストラクチャーへのアップグレード (Upgrade to Infrastructure ) ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}を参照してください。

**重要**: サービスは、仮想サーバー・インスタンスにはバインドされません。サービスを仮想サーバー内のアプリケーションに追加することはできません。

## Terraform を使用したデプロイ
いずれのアプリ・サービス・スターター・キットも、オープン・ソースの Infrastructure as Code フレームワークである [Terraform ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} を使用して、動的に作成された仮想インスタンスにデプロイできます。 詳しくは、[Terraform 資料![外部リンク・アイコン](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}を参照してください。

## パイプライン・デプロイメントの使用可能化

{{site.data.keyword.cloud_notm}} [App Service ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}を使用するスターター・キットを作成する際は、仮想サーバー・インスタンスが使用可能になります。 アプリの作成後、アプリをデプロイする場所を選択できます。 スターター・キットでは、Continuous Delivery ツールチェーンを使用したデプロイメントのサポートが有効になっています。スターター・キットは Kubernetes、Cloud Foundry、および仮想サーバー・インスタンスをターゲットとすることができます。 ツールチェーンにはソース・コード・リポジトリーとデプロイメント・パイプラインが含まれています。

仮想サーバー・オプションは段階的に機能します。 まずアプリ・コードが作成され、GITLab Git リポジトリーに保管されます。ソース・コードによりパイプラインが備わったツールチェーンが作成されます。 このパイプラインは、コードをビルドして Debian Package マネージャー・フォーマットにパッケージするよう定義されています。 次に、Terraform が仮想インスタンスをプロビジョンします。 最後に、アプリがデプロイされ、インストールされ、実行中の仮想イメージ内で開始されて、その正常性が検証されます。

パイプラインは、一連のユーザー・アカウント・プロパティーを手動で構成する必要があるため、初回の使用時には失敗します。 セキュリティー上の理由から、GIT ソース・コードを使用するツールチェーンにこれらのプロパティーを渡すことはできません。 ツールチェーンが正常に完了できるように、ユーザーが手動でこれらの値を構成する必要があります。

環境プロパティー・ビューにアクセスし、ご使用のユーザー・アカウント・プロパティーでパイプラインを使用可能にするには、次の手順を実行してください。

1. アプリ詳細ページで**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**タイルをクリックします。
3. **「ステージの構成 (Stage Configure)」**アイコンをクリックし、次にビルド・ステージで**「ステージの構成」**をクリックします。
4. **「環境プロパティー」**タブをクリックして、プロパティーを表示します。
5. ツールチェーンを正常に実行できるように、「環境プロパティー」タブでこれらのプロパティーを変更します。

| プロパティー   | 説明   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | [インフラストラクチャー API キー](#iaas-key) インフラストラクチャー・コンソールから取得できます。 |
| `TF_VAR_ibm_sl_username` | [インフラストラクチャー・ユーザー名](#user-key) インフラストラクチャー・アカウントを識別します。 |
| `TF_VAR_ibm_cloud_api_key` | {{site.data.keyword.cloud_notm}} [プラットフォーム API キー](#platform-key) サービス作成を使用可能にするために使用します。 |
| `PUBLIC_KEY` | [パブリック・キー](#public-key) 仮想サーバー・インスタンスへのアクセスを使用可能にするよう定義します。 |
| `PRIVATE_KEY` | [プライベート・キー](#public-key) 仮想サーバー・インスタンスへのアクセスを使用可能にするよう定義します。 **注**: `\n` 改行スタイル・フォーマットを使用する必要があります。|
| `VI_INSTANCE_NAME` | 仮想サーバー・インスタンス用に自動生成された名前です。 |
| `GIT_USER` | apply コマンドの状態を保管するよう[「Terraform 状態 (Terraform state)」](#tform-state)を設定する場合、GITLab ユーザー名が必要です。 |
| `GIT_PASSWORD` | apply コマンドの状態を保管するよう[「Terraform 状態 (Terraform state)」](#tform-state)を設定する場合、GITLab パスワードが必要です。 |
{: caption="表 1. 使用可能性を変更するための環境変数" caption-side="top"}

### インフラストラクチャー API キーの取得
{: #iaas-key}

Terraform は、インフラストラクチャー・リソースを作成するためにインフラストラクチャー API キーを必要とします。 インフラストラクチャー・キーを取得するには、次の手順を実行してください。

1. インフラストラクチャー・[ユーザー・リスト ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} にアクセスします。また、**「メニュー」** > **「インフラストラクチャー」** > **「アカウント」** > **「ユーザー・リスト」**の順にクリックすることもできます。
2. ツールチェーンを作成しているユーザーの詳細を確認し、「API キー」列の`「表示」`をクリックするか、`「生成」`をクリックします。いずれの操作を行っても、ウィンドウに API キーが表示されます。
3. API キーをコピーして、ツールチェーンの構成 `TF_VAR_ibm_sl_api_key` の値と置き換えます。

### インフラストラクチャー・ユーザー名の取得
{: #user-key}

インフラストラクチャー・ユーザー名を取得するには、以下の手順に従ってください。

1. インフラストラクチャー・[ユーザー・リスト ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} にアクセスします。また、**「メニュー」** > **「インフラストラクチャー」** > **「アカウント」** > **「ユーザー・リスト」**の順にクリックすることもできます。
2. ツールチェーンを作成したいユーザーをクリックします。
3. **「VPN ユーザー名 (VPN User Name)」**プロパティーまでスクロールダウンします。
4. この値をカット・アンド・ペーストして、ツールチェーン構成 `TF_VAR_ibm_sl_username` と置き換えます。

### プラットフォーム API キーの取得
{: #platform-key}

Terraform でデータベース・サービスや Compose サービスなどのプラットフォーム・レベル・サービスを作成するには、プラットフォーム API キーが必要です。プラットフォーム・キーを取得するには、次の手順を実行してください。

1. [「API キー」![外部リンク・アイコン](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys) ページから、**「管理」** > **「セキュリティー」** > **「プラットフォーム API キー」**をクリックします。
2. **「作成」**をクリックします。
3. 名前と説明を入力して**「作成」**をクリックします。
4. ウィンドウが開いたら、**「表示」**をクリックしてキーを確認してください。
5. キーをクリップボードにコピー・アンド・ペーストするか、キーをダウンロードします。
6. ツールチェーン構成 `TF_VAR_ibm_cloud_api_key` の値を生成された値と置き換えます。

### パブリック・キーおよびプライベート・キーの生成
{: #public-key}

ツールチェーンで Debian パッケージを仮想サーバー・インスタンスにインストールするには、次の手順を実行してください。

1. クライアントで以下の手順を使用して、[パブリック・キーとプライベート・キーのペア![外部リンク・アイコン](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}を作成します。
2. [インフラストラクチャー SSH 鍵ビュー ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window} にアクセスします。また、**「メニュー」** > **「インフラストラクチャー」** > **「デバイス」** > **「管理」** > **「SSH 鍵」**をクリックすることもできます。
3. **「追加」**をクリックします。
4. 以前作成したパブリック・キーのコンテンツをコピーし、キー・コンテンツにペーストします。
5. キーに名前を付けて、**「追加」**をクリックします。

プライベート・キーは 1 行で入力する必要があります。改行は、`\n` に置き換えます。次の例を参照してください。
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

### Terraform 状態の使用可能化
{: #tform-state}

Terraform は Terraform `apply` コマンドの状態の保管をサポートします。 この状態ファイルは 2 回目の `apply` コマンドを実行し、いずれかの Terraform 構成ファイルに変更があるかどうかを判別します。 この状態は、アプリと構成が管理されている GIT リポジトリーに保管できます。

状態の保管を可能にするには、ツールチェーン環境変数の `GIT_USER` および `GIT_PASSWORD` プロパティーを構成します。 値を取得するには、以下のステップに従ってください。

1. 「ツールチェーン」ビューで、 コード・ツールから GIT リポジトリーにアクセスします。
2. GIT Lab で、**「プロファイル・アイコン」**をクリックし、次に**「設定」**をクリックします。
3. **「アカウント」**をクリックし、ユーザー名をコピーして `GIT_USER` の値と置き換えます。
4. **「アクセス・トークン」**をクリックします。
5. トークンの名前を定義し、適用範囲を選択し、**「個人用アクセス・トークンの作成 (Create Personal Access Token)」**をクリックします。
6. `「自分の新しい個人用アクセス・トークン (Your New Personal Access Token)」`フィールドのコピー・アイコンをクリックし、ツールチェーン・プロパティーの `GIT_PASSWORD` の値を置き換えます。

Terraform の状態は `terraform` というブランチに保管されており、変更があってもパイプラインの実行をトリガーしません。

### GIT 操作の使用可能化
{: #git-repo}

アプリが {{site.data.keyword.cloud_notm}} にデプロイされている場合、GIT Lab リポジトリーが作成され、ソース・コード管理用のコードをホストします。 GIT 操作を使用すると、チームが機能し、変更をアプリに配信することが可能になります。 このリポジトリーに含まれるフォルダーは以下のとおりです。

#### Debian フォルダー
{: #debian-folder}

`debian` フォルダーには、アプリを [Debian パッケージ ![外部リンク・アイコン](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}にパッケージ化するために必要となる構成が保持されています。

#### Terraform フォルダー
{: #terraform-folder}

`terraform` フォルダーには、インフラストラクチャーのリソースをプロビジョンする際に使用する Infrastructure as Code の構成が保持されています。 ファイル `main.tf` は、Terraform 構成のオプションを変更するためのメイン・ソースです。

```
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

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### ツールチェーン・ステージの理解
{: #toolchain-stages}

ツールチェーンは、1 つのシンプルなパイプラインにおけるインフラストラクチャーおよびアプリのデプロイメントを示しています。 Infrastructure as Code の部分を 1 つのパイプラインに、アプリのデプロイメントを別のパイプラインに分割してください。

ツールチェーンのプロセスには 5 つのステージがあります。

1. ビルド・ステージは GIT リポジトリーを複製し、コードを Debian パッケージにパッケージ化します。
2. Terraform プラン・ステージは Terraform のプランを作成します。

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. Terraform 適用ステージは Terraform 構成を適用し、仮想サーバーの IP アドレスが使用可能になるまで待機します。

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. デプロイ、インストール、開始の各ステージは、最初のステージでビルドされた Debian パッケージを実行中の仮想サーバーへ移動し、インストールして開始します。
5. ヘルス・チェック・ステージは、アプリでヘルス・エンドポイントが使用可能かどうかを検証し、パイプラインを完了します。

開始後にアプリにアクセスするには、ヘルス・チェック・ステージのログをチェックします。 アプリの IP アドレスとポートを表示しているログにリストされた URL をクリックしてください。
