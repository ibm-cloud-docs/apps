---

copyright:

  years: 2019

lastupdated: "2019-06-03"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# FAQ
{: #apps-faq}

## mybluemix.net はどうなりましたか?
{: #domain-change-faq}
{: faq}

新しいホスト名オプション `*.appdomain.cloud` を cloud.ibm.com で使用することができます。

以前は、{{site.data.keyword.containerlong_notm}} や Cloud Foundry など、さまざまなデプロイメント・ターゲットでアプリケーションをホストするために `mybluemix.net` ドメインが使用されていました。 `mybluemix.net` でホストされているアプリは影響を受けません。

Cloud Foundry アプリのサブドメインは `cf.appdomain.cloud` です。 {{site.data.keyword.containerlong_notm}} にデプロイするアプリのサブドメインは `containers.appdomain.cloud` です。

詳しくは、[ドメインの管理](/docs/apps?topic=creating-apps-update-domain)を参照してください。

## アプリのリストはどこで見ることができますか?
{: #cf-app}
{: faq}

[{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") のリソース・リストに、作成したアプリの要約情報があります。 リソース・リストの**「アプリ」**セクションには、作成したが Cloud Foundry にデプロイ*していない*すべてのアプリが含まれています。 **「Cloud Foundry アプリ」**セクションには、作成して Cloud Foundry にデプロイしたアプリのすべてが含まれています。

## アプリをデプロイしようとするときに、Cloud Foundry スペースを選べないのはなぜですか?
{: #cf-space}
{: faq}

最初に Cloud Foundry スペースを作成する必要があることが最も考えられる原因です。 Cloud Foundry コマンド・ライン・インターフェースを使用している場合は、`cf create-space <space_name> -o <organization_name>` と入力します。 それ以外の場合は、コンソールから以下の手順を実行します。

1. [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") のメニュー・バーで、**「管理」** > **「アカウント」**を選択します。
2. **「Cloud Foundry の組織」**を選択します。
3. スペースを作成する組織の名前をクリックし、**「スペースの追加」**をクリックします。

## アプリを削除するには、どのようにすればよいですか?
{: #delete-apps}
{: faq}

作成したアプリを削除するには、以下の手順を実行します。

1. [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")から**「メニュー」**アイコン![「メニュー」アイコン](../icons/icon_hamburger.svg)をクリックして**「リソース・リスト」**を選択します。
2. 削除するアプリの**「アクション」**アイコン ![「アクション」アイコン](../icons/action-menu-icon.svg) をクリックし、**「削除」**をクリックします。

## 自分のアカウントで Cloud Foundry アプリを停止するには、どうすればよいですか?
{: #app-stop}
{: faq}

Cloud Foundry アプリを停止する場合は、以下の手順を実行します。


1. ダッシュボードで、「リソースの要約」セクション内の**「リソースの表示」**をクリックします。
1. 「リソース」リストで、セクションを展開し、停止するサービス・インスタンスを見つけます。
1. **「アクション」** ![「アクションのリスト」アイコン](../icons/action-menu-icon.svg) メニューを選択し、**「停止」**をクリックします。

## ツールチェーンとは何ですか? また自分のアプリとどのような関係がありますか?
{: #toolchains}
{: faq}

ツールチェーンは、開発、デプロイメント、および運用の作業をサポートするツール統合の集合です。 ツールチェーンをアプリから作成することができます。 ツールチェーンは、継続的な開発、デプロイ、モニタリングなどをサポートでき、アプリと関連付けられます。 各アプリをツールチェーンと関連付けることができます。 ツールチェーンは、ツールチェーンに変更を加えると自動的にアプリをビルドしてデプロイするように構成することができます。 ツールチェーンについて詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)を参照してください。

## 自分の Cloud Foundry アプリのドメインを変更するにはどうすればよいですか?
{: #cf-domains-faq}
{: faq}

Cloud Foundry アプリの場合は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェースを使用して、ドメインを `mybluemix.net` から `appdomain.cloud` に変更できます。 `appdomain.cloud` への変更について詳しくは、[ドメインの更新](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)を参照してください。

新規アプリ作成時のデフォルトの共有ドメインは `mybluemix.net` ですが、`appdomain.cloud` という別のドメイン・オプションも使用できます。
