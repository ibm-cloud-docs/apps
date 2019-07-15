---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #at_events}

セキュリティー担当者、監査員、または管理者として、お客様は {{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.cloud}} の {{site.data.keyword.dev_console}} とどのように対話しているかをトラッキングすることができます。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} が非推奨になりました。 2019 年 5 月 9 以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンすることはできず、*ライト*・プランへのアクセスが削除されます。 既存のプレミアム・プラン・インスタンスは 2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを継続するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) インスタンスをプロビジョンしてください。
{: deprecated}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} でサービスの状態を変更する、ユーザーが開始したアクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov) についてのページを参照してください。

## イベントの表示先
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、{{site.data.keyword.dev_console}} イベントが生成される {{site.data.keyword.cloud_notm}} 地域内にある {{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメインで使用可能です。

ユーザーのアクションのモニターを開始するには、『[入門チュートリアル](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)』を参照してください。

## イベント・リスト
{: #events}

以下の表では、イベントを生成するアクションをリストします。

|アクション	|説明	|
|-----|-------------|
|bluemix-developer-experience.app.create |ユーザーがアプリを作成すると、イベントが生成されます。|
|bluemix-developer-experience.app.read |以下のいずれかのシチュエーションが発生すると、イベントが生成されます。<br><br>ユーザーがアプリ・コードをダウンロードする。<br><br>ユーザーが {{site.data.keyword.dev_console}} CLI を使用して資格情報ファイルをダウンロードする。<br><br>{{site.data.keyword.cloud_notm}} インフラストラクチャーがアプリと関連付けられたサービスの資格情報を読み取る。<br><br>ユーザーがアプリのリストを表示する。例えば、ユーザーが {{site.data.keyword.dev_console}} コンソールまたは {{site.data.keyword.dev_cli_short}} CLI でアプリのリストを表示するなど。|
|bluemix-developer-experience.app.update |以下のいずれかのシチュエーションが発生すると、イベントが生成されます。<br><br>アプリに何らかの変更が加えられる。例えば、ユーザーがアプリの名前を変更するなど。<br><br>新規サービスが作成され、アプリに追加される。<br><br>既存のサービスがアプリに追加される。<br><br>サービスがアプリから削除される。<br><br>アプリ用にコードが生成される。<br><br>{{site.data.keyword.cloud_notm}} コンソールによって DevOps ツールチェーンが追加される。例えば、ユーザーが「アプリの詳細」ページから**「継続的デリバリーの構成 (Configure continuous delivery)」**を選択するなど。|
|bluemix-developer-experience.app.delete |ユーザーがアプリを削除すると、イベントが生成されます。 |
{: caption="表 1. イベントを生成するアクション" caption-side="top"}
