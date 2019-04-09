---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #at_events}

セキュリティー担当者、監査員、または管理者として、お客様は {{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.cloud}} の {{site.data.keyword.dev_console}} とどのように対話しているかをトラッキングすることができます。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} でサービスの状態を変更する、ユーザーが開始したアクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov) についてのページを参照してください。

## イベントの表示先
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、{{site.data.keyword.dev_console}} イベントが生成される {{site.data.keyword.cloud_notm}} 領域内にある {{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメインで使用可能です。

ユーザーのアクションのモニターを開始するには、『[入門チュートリアル](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)』を参照してください。

## イベント・リスト
{: #events}

以下の表では、イベントを生成するアクションをリストします。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>ユーザーがアプリケーションを作成すると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>以下のいずれかのシチュエーションが発生すると、イベントが生成されます。 </br><ul><li>ユーザーがアプリケーション・コードをダウンロードする。</li> <li>ユーザーが {{site.data.keyword.dev_console}} CLI を使用して資格情報ファイルをダウンロードする。</li> <li>開発者エクスペリエンス・インフラストラクチャーがアプリケーションと関連付けられたリソースの資格情報を読み取る。</li> <li>ユーザーがアプリケーションのリストを表示する (例えばユーザーが {{site.data.keyword.dev_console}} コンソールで、または {{site.data.keyword.dev_cli_short}} CLI を使用してアプリケーションのリストを表示するなど)。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>以下のいずれかのシチュエーションが発生すると、イベントが生成されます。 </br><ul><li>アプリケーションに何らかの変更が行われる (例えばユーザーがアプリケーションの名前を変更するなど)。 </li><li>新規リソースが作成され、アプリケーションに追加される。</li><li>既存のリソースがアプリケーションに追加される。</li><li>サービスがアプリケーションから削除される。</li><li>アプリケーション用にコードが生成される。</li><li>開発者エクスペリエンスにより (例えば*「クラウドにデプロイ (Deploy to Cloud)」*を選択するなどして) DevOps ツールチェーンが追加される。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>ユーザーがアプリケーションを削除すると、イベントが生成されます。</td>
  </tr>
</table>
