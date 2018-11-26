---

copyright:
  years: 2018
lastupdated: "2018-11-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Mendix を使用したアプリの作成
{: #getting-started}

Mendix は、{{site.data.keyword.cloud}} で稼働するマルチデバイス・アプリケーションを少ない開発リソースで迅速に配信できるよう支援する、ローコード開発環境およびツール・セットです。Mendix ローコード・スターター・キットを選択することにより、ガイドに従って、Mendix プラットフォームでアカウントをセットアップし、プロジェクトを開始し、Cloud Foundry または Kubernetes クラスターのいずれかでデプロイメント環境を選択することができます。
{: shortdesc}

## スターター・キットの選択
{: #select-a-starter-kit}

2. [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard){: new_window} で、**「メニュー」**アイコン ![メニュー・アイコン](../../icons/icon_hamburger.svg) をクリックします。
3. 以下のいずれかのカテゴリーから、Mendix ローコード・スターター・キットを選択します。
  * [モバイル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web アプリまたはモバイル・アプリ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Web App ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-app)
4. **「アプリの作成」**をクリックします。
5. アプリに名前を付けます。 
6. **「作成」**をクリックします。

## Mendix でのプロジェクト作成およびアカウントのリンクを行うための IBM への許可
{: #link-mendix-account}

まだ {{site.data.keyword.cloud_notm}} で Mendix を使用していない場合、Mendix プラットフォームに誘導されます。そこで、登録を行い、Mendix プラットフォームでの新規プロジェクトの作成を {{site.data.keyword.cloud_notm}} に許可します。このプロジェクトは、{{site.data.keyword.cloud_notm}} にリンクされるため、デプロイメントは自動的に {{site.data.keyword.cloud_notm}} に送付されます。

1. 「アプリ作成を実行するには Mendix ユーザー・アカウントが必要です。今すぐあなたのアカウントをリンクしますか?（To complete app creation, a Mendix user account is required. Would you like to link your account now?)」という内容のメッセージが表示されたら、**「アカウントのリンク (Link Account)」**をクリックします。
2. Mendix 確認ページで、**「Mendix プライバシー・ポリシーおよび利用条件に同意します (I agree to the Mendix Privacy Policy and Terms)」**を選択し、**「確認」**をクリックします。
3. プロンプトが出されたら、E メール・アドレス、パスワード、および国を入力し、**「作成」**をクリックします。
4. **「Mendix アカウントへのアクセスを許可する (Authorize access to your Mendix account)」**ページで、**「許可」**をクリックします。

許可が完了したら、ブラウザーは作成中の Mendix アプリに戻ります。**「デプロイメント環境の選択 (Choose a deployment environment)」**ページが表示されます。

## Mendix アプリのデプロイメント・オプションの選択
{: #select-deployment}

1. **「デプロイメント環境の選択 (Choose a deployment environment)」**ページで、Cloud Foundry を選択するか、または、{{site.data.keyword.cloud_notm}} で実行中のいずれかの Kubernetes クラスターを選択します。
2. オプション。 Kubernetes クラスターがない場合は、この時点で作成できます。
3. **「ツールチェーンの構成」**ページで、地域およびリソース・グループを選択し、**「作成」**をクリックします。

DevOps ツールチェーンが作成されます。このツールチェーンは、{{site.data.keyword.cloud_notm}} 環境の Mendix プラットフォーム内で Mendix プロジェクトを統合します。ターゲット・デプロイメントにデフォルト・アプリケーションがデプロイされるので、DevOps ツールチェーンの完成時に、そのアプリケーションが正常にデプロイされたことを検証できます。

Mendix Cloud Foundry デプロイメントには PostGRES データベース・サービスが必要ですが、このサービスにはライト層がありません。ライト・アカウントを使用して Mendix スターター・キットを評価したい場合は、トライアル Kubernetes クラスターをターゲットにすることができます。
{: tip}

デプロイメントに Kubernetes クラスターを選択した場合は、[Mendix Kubernetes チュートリアル](/docs/apps/tutorials/tutorial_mendix_kubernetes.html)を参照して、実動用にクラスターを構成する方法を確認してください。


## Mendix の開発とデプロイメントのライフサイクルの継続
{: #development-lifecycle}

Mendix は、ローコードのオーサリング環境です。開発ライフサイクルでは、Mendix Modeler デスクトップ・アプリケーションでプロジェクトを開く必要があります。

1. {{site.data.keyword.cloud_notm}} アプリケーションから、**「Mendix で編集 (Edit on Mendix)」**をクリックします。
2. Mendix Web ポータルで、**「Desktop Modeler で編集 (Edit in Desktop Modeler)」**をクリックします。
  Desktop Modeler で Mendix アプリケーションが開きます。
3. Mendix アプリを編集し、変更を保存します。
4. Mendix Desktop Modeler アプリケーションの**「実行」**メニューを使用し、**「実行」**オプションを選択します。
  デプロイメント・パッケージが作成され、Mendix にアップロードされます。デプロイメント・パッケージが作成された後、アプリケーションを {{site.data.keyword.cloud_notm}} にデプロイできます。
5. Mendix アプリケーションをデプロイするため、{{site.data.keyword.cloud_notm}} の**「アプリの詳細 (App details)」**ページに戻り、**「アプリケーションのデプロイ (Deploy Application)」**をクリックします。この操作によってアプリケーションの DevOps ツールチェーンが開始されます。このツールチェーンは、Mendix から最新のデプロイメントをプルし、それをターゲット環境にデプロイします。デプロイメントが完了した後、最新版のアプリケーションが自動的に開始され、使用可能になります。

すべての Mendix アプリケーションは、{{site.data.keyword.cloud_notm}} 上の**「アプリの詳細」**ページで**「アプリケーションのデプロイ」**をクリックすることによって、{{site.data.keyword.cloud_notm}} にデプロイされます。IBM DevOps インターフェースを介して Mendix ツールチェーンを手動で起動しないでください。DevOps インターフェースを介してツールチェーンを手動で起動すると、Mendix デプロイメントに不可欠な必須メタデータの不足が原因でデプロイメントが失敗する可能性があります。アプリケーションの状態によっては、DevOps ツールチェーンの起動中に失敗したり、デプロイされたアプリケーションでエラーが発生したりする可能性があります。ツールチェーンを手動で起動して障害が発生した場合は、{{site.data.keyword.cloud_notm}} 上の**「アプリの詳細」**ページで**「アプリケーションのデプロイ」**をクリックすることによって、アプリケーション・デプロイメントをリストアできます。この操作によって、必須メタデータを含む Mendix アプリケーションの完全な DevOps フローがトリガーされます。
{: tip}

## 次のステップ 
{: #next steps}

アプリを {{site.data.keyword.containerlong_notm}} にデプロイするため、実動デプロイメント用にアプリを構成します。詳しくは、[Mendix Kubernetes チュートリアル](/docs/apps/tutorials/tutorial_mendix_kubernetes.html)を参照してください。 
