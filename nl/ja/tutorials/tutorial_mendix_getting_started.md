---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

# Mendix を使用したアプリの作成
{: #create-mendix}

Mendix は、{{site.data.keyword.cloud}} で稼働するマルチデバイス・アプリケーションを少ない開発リソースで迅速に配信できるよう支援する、ローコード開発環境およびツール・セットです。 Mendix ローコード・スターター・キットを選択することにより、ガイドに従ってMendix プラットフォームでアカウントをセットアップし、プロジェクトを開始し、Cloud Foundry または Kubernetes クラスターのいずれかでデプロイメント・ターゲットを選択することができます。
{: shortdesc}

## スターター・キットの選択
{: #starterkit-mendix}

1. [{{site.data.keyword.cloud_notm}} アプリ・サービスのダッシュボード ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") で、**「開始」**をクリックします。
2. 以下のいずれかのカテゴリーから、Mendix ローコード・スターター・キットを選択します。
  * [モバイル](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
  * [Watson Web アプリまたはモバイル・アプリ ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
  * [Web App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
3. **「アプリの作成」**をクリックします。
4. **「アプリの詳細」**ページで、アプリに名前を付け、オプションで、アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
5. **「作成」**をクリックします。

## Mendix でのプロジェクト作成およびアカウントのリンクを行うための IBM への許可
{: #link-mendix-account}

まだ {{site.data.keyword.cloud_notm}} で Mendix を使用していない場合、Mendix プラットフォームに誘導されます。そこで、登録を行い、Mendix プラットフォームでの新規プロジェクトの作成を {{site.data.keyword.cloud_notm}} に許可します。 このプロジェクトは、{{site.data.keyword.cloud_notm}} にリンクされるため、デプロイメントは自動的に {{site.data.keyword.cloud_notm}} に送付されます。

1. 次のメッセージが表示される場合は、**「アカウントの結合」**をクリックします。
  ```
  "To complete app creation, a Mendix user account is required. Would you like to link your account now?"
  ```
  {: screen}

2. Mendix 確認ページで、**「Mendix プライバシー・ポリシーおよび利用条件に同意します (I agree to the Mendix Privacy Policy and Terms)」**を選択し、**「確認」**をクリックします。
3. プロンプトが出されたら、E メール・アドレス、パスワード、および国を入力し、**「作成」**をクリックします。
4. **「Mendix アカウントへのアクセスを許可する (Authorize access to your Mendix account)」**ページで、**「許可」**をクリックします。

許可が完了したら、ブラウザーは作成中の Mendix アプリに戻ります。 **「デプロイメント・ターゲットの選択 (Select a deployment target)」**ページが表示されます。

## Mendix アプリのデプロイメント・ターゲットの選択
{: #select-deployment}

1. **「デプロイメント・ターゲットの選択 (Select a deployment target)」**ページで、Cloud Foundry を選択するか、または {{site.data.keyword.cloud_notm}} で実行中のいずれかの Kubernetes クラスターを選択します。 ご使用のアカウントに {{site.data.keyword.cfee_full_notm}} へのアクセス権限がある場合、**[パブリック・クラウド](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)**または**[エンタープライズ環境](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**のいずれかの Cloud Foundry デプロイヤー・タイプを選択できます。エンタープライズ環境を使用すると、自社専用に Cloud Foundry アプリをホスティングする隔離された環境を作成して管理できます。
2. オプション。 Kubernetes クラスターがない場合は、この時点で作成できます。
3. **「ツールチェーンの構成」**ページで、地域およびリソース・グループを選択し、**「作成」**をクリックします。

DevOps ツールチェーンが作成されます。 このツールチェーンは、{{site.data.keyword.cloud_notm}} 環境の Mendix プラットフォーム内で Mendix プロジェクトを統合します。 デプロイメント・ターゲットにデフォルト・アプリがデプロイされるので、DevOps ツールチェーンの完成時に、そのアプリが正常にデプロイされたことを検証できます。

Mendix Cloud Foundry デプロイメントには PostGRES データベース・サービスが必要ですが、このサービスにはライト層がありません。 ライト・アカウントを使用して Mendix スターター・キットを評価したい場合は、トライアル Kubernetes クラスターをターゲットにすることができます。
{: tip}

デプロイメントに Kubernetes クラスターを選択した場合は、[Mendix Kubernetes チュートリアル](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube)を参照して、実動用にクラスターを構成する方法を確認してください。

## Mendix の開発とデプロイメントのライフサイクルの継続
{: #dev-lifecycle-mendix}

Mendix は、ローコードのオーサリング環境です。 開発ライフサイクルでは、Mendix Modeler デスクトップ・アプリでプロジェクトを開く必要があります。

1. {{site.data.keyword.cloud_notm}} アプリから、**「Mendix で編集 (Edit on Mendix)」**をクリックします。
2. Mendix Web ポータルで、**「Desktop Modeler で編集 (Edit in Desktop Modeler)」**をクリックします。
  Desktop Modeler で Mendix アプリが開きます。
3. Mendix アプリを編集し、変更を保存します。
4. Mendix Desktop Modeler アプリの**「実行」**メニューを使用し、**「実行」**オプションを選択します。
  デプロイメント・パッケージが作成され、Mendix にアップロードされます。 デプロイメント・パッケージが作成された後、アプリを {{site.data.keyword.cloud_notm}} にデプロイできます。
5. Mendix アプリをデプロイするため、{{site.data.keyword.cloud_notm}} の**アプリの詳細**ページに戻り、**「デプロイ」**をクリックします。
  この操作によってアプリの DevOps ツールチェーンが開始されます。このツールチェーンは、Mendix から最新のデプロイメントをプルし、それをターゲット環境にデプロイします。 デプロイメントが完了した後、最新版のアプリが自動的に開始され、使用可能になります。

すべての Mendix アプリは、{{site.data.keyword.cloud_notm}} の**「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックすることによって、{{site.data.keyword.cloud_notm}} にデプロイされます。 IBM DevOps インターフェースを介して Mendix ツールチェーンを手動で起動しないでください。 DevOps インターフェースを介してツールチェーンを手動で起動すると、Mendix デプロイメントに不可欠な必須メタデータの不足が原因でデプロイメントが失敗する可能性があります。 アプリの状態によっては、DevOps ツールチェーンの起動中に失敗したり、デプロイされたアプリでエラーが発生したりする可能性があります。

ツールチェーンを手動で起動して障害が発生した場合は、{{site.data.keyword.cloud_notm}} の**「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックすることによって、アプリ・デプロイメントをリストアできます。 この操作によって、必須メタデータを含む Mendix アプリの完全な DevOps フローがトリガーされます。
{: tip}

## オプション: {{site.data.keyword.cos_full_notm}} の構成 
{: #mendix-cos}

一部のユーザーは、永続的な保存とファイルのアップロードのために {{site.data.keyword.cos_full}} を使用するようデプロイ済み Mendix アプリを構成することを望むかもしれません。 {{site.data.keyword.cos_full_notm}} は、S3 と互換性のあるオブジェクト・ストレージ・サービスです。 S3 互換のファイル・ストレージを利用するには、Mendix アプリで継続的デリバリーを構成した後、{{site.data.keyword.cos_full_notm}} インスタンスにアクセスするために以下の環境変数を定義する必要があります。

* `S3_ACCESS_KEY_ID` - S3 鍵 ({{site.data.keyword.cos_full_notm}} 資格情報の一部)
* `S3_SECRET_ACCESS_KEY` - S3 秘密鍵 ({{site.data.keyword.cos_full_notm}} 資格情報の一部)
* `S3_BUCKET_NAME` - S3 ストレージ・バケット
* `S3_ENDPOINT` - S3 ストレージ・エンドポイント
* `S3_USE_V2_AUTH` - 値は `true`

{{site.data.keyword.cos_full_notm}} バケットおよび鍵について詳しくは、[{{site.data.keyword.cos_full_notm}} API の資料](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev)を参照してください。 地域のエンドポイント値および地域を超えたエンドポイント値の詳細については、[{{site.data.keyword.cos_full_notm}} の資料](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints)を参照してください。S3 互換ストレージの Mendix サポートについて詳しくは、[Mendix ビルドパックの資料](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")を参照してください。

### Cloud Foundry アプリの {{site.data.keyword.cos_full_notm}} 設定
{: cos-cfapps}

Cloud Foundry のデプロイメントでは、次のステップを実行します。

1. 次の `cf set-env` コマンドを使用して、Cloud Foundry のデプロイメントに上記の環境変数を設定します。

  ```
    ibmcloud cf set-env <YOUR_APP> S3_ACCESS_KEY_ID <YOUR_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_SECRET_ACCESS_KEY <YOUR_SECRET_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_BUCKET_NAME <YOUR_BUCKET>
    ibmcloud cf set-env <YOUR_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <YOUR_APP> S3_USE_V2_AUTH true
  ```

2. これらの値をすべて指定した後、新しい値が適用されるように Cloud Foundry アプリを再ステージします。

  ```
    ibmcloud cf restage <YOUR_APP>
  ```

### Kubernetes アプリの {{site.data.keyword.cos_full_notm}} 設定
{: #cos-kubeapps}

Kubernetes のデプロイメントでは、次のステップを実行します。

1. `S3_ACCESS_KEY_ID` と `S3_SECRET_ACCESS_KEY` の各環境変数を Kubernetes 秘密値としてクラスターで設定します。 Kubernetes の秘密の作成について詳しくは、[{{site.data.keyword.containershort_notm}} の資料](/docs/containers?topic=containers-service-binding#adding_app)を参照してください。

2. 既存の値に加えて、Git リポジトリーの `chart/<appname>/templates` フォルダーの `mendix-app.yaml` ファイル内の追加の環境変数としてこれらの環境変数を指定します。 秘密名は、前のステップで作成した名前と一致しなければなりません。

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. Kubernetes の変更が適用されたら、**「アプリの詳細」**ページに移動し、**「デプロイ」**をクリックしてアプリを再デプロイします。 

## 次のステップ 
{: #next-steps-mendix}

アプリを {{site.data.keyword.containerlong_notm}} にデプロイするため、実動デプロイメント用にアプリを構成します。 詳しくは、[Mendix Kubernetes チュートリアル](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube)を参照してください。 
