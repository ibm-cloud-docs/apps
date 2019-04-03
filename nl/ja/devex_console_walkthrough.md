---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} Developer Console のウォークスルー
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience は、クラウド・ネイティブ・アプリケーション開発者がさまざまなスターター・キットからアプリを作成し、{{site.data.keyword.Bluemix_notm}} 用に最適化された主要サービスを作成して接続し、作業用コードを素早くダウンロードしたり継続的デリバリーのためのセットアップを行ったりすることを支援します。 Developer Experience では、{{site.data.keyword.Bluemix_notm}} 全体にわたる一連の Developer Console を用意しています。それにより、アプリを作成、表示、構成、管理でき、さらにそれを DevOps パイプラインにデプロイしたりローカル開発のためにダウンロードしたりできます。

{{site.data.keyword.cloud_notm}} Developer Console を介してアプリを作成することにより、アプリのすべての必要なパーツが {{site.data.keyword.cloud_notm}} サーバー上のユーザーのアカウントで保守されます。  したがって、Developer Console GUI と [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) とを切り替えながら作業することができます。

{{site.data.keyword.cloud_notm}} Developer Consoles には、ユーザーが選択したユース・ケースに対応する、すぐに実働可能なスターター・アプリを作成するためのシームレス・パスが用意されています。  その過程で実行するステップを確認しましょう。

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##「概要」画面
{: #overview_screen}

「概要」画面には、作業している Developer Console のトピックまたはチャネルのフォーカスに合わせた内容が表示されます。 「概要」画面から、ドキュメンテーションの表示、学習リソースのアクセス、サービスの参照、主なスターター・キットの参照や、スターター・キットのより大きなコレクションへのリンクが可能です。 ナビゲーションの`「スターター・キット (Starter Kits)」`をクリックして、「スターター・キット (Starter Kits)」ビューにステップイントゥします。

![Developer Console の「概要」画面](images/overview_screen.png "「概要」画面") <br> *Developer Console の「概要」画面*

##「スターター・キット (Starter Kits)」ビュー
{: #starter_kits_view}

「スターター・キット (Starter Kits)」ビューには、ユース・ケース領域に固有のスターター・キットのコレクションが表示されます。  スターター・キット・カード上のさまざまなリンクをクリックすると、デモンストレーションや詳細情報が表示されます。  スターター・キットを選択して、「アプリの新規作成 (Create New App)」ビューに移動します。

スターター・キットを選択すると、そのスターター・キットの詳細が表示される場合もあります。  その場合は、単に`「作成」`ボタンをクリックして、「アプリの新規作成 (Create New App)」ビューに移動してください。{: tip}

![Developer Console の「スターター・キット」ビュー](images/starter_kits_view.png "「スターター・キット」ビュー") <br> *Developer Console の「スターター・キット」ビュー*

##「アプリの新規作成 (Create New App)」ビュー
{: #create_new_project_view}

「アプリの新規作成 (Create New App)」ビューから、アプリに名前を付けたり、デプロイメントおよびルーティングの情報を指定したり、言語を選択したりできます。  右側には、アプリを作成すると自動的にプロビジョンされるサービス、およびそれぞれの価格プランとご利用条件も表示されます。  `「作成」`をクリックして、「アプリの詳細 (App Details)」ビューに移動します。  {{site.data.keyword.cloud_notm}} にまだログインしていない場合は、この時点でログインする必要があります。

![Developer Console の「アプリの新規作成 (Create New App)」ビュー](images/create_new_project_view.png "「アプリの新規作成 (Create New App)」ビュー") <br> *Developer Console の「アプリの新規作成 (Create New App)」ビュー*

## 「アプリの詳細 (App Details)」ビュー
{: #project_details_view}

「アプリの詳細 (App Details)」ビューには、アプリ用に構成されたサービスのリストが表示されます。 リスト内の項目ごとに、サービス名、他の情報へのリンク、および 3 つのドットが垂直に並んだ*アクション*・ボタンが表示されます。 *アクション*・ボタンのオプションは、アプリからのサービスの削除、サービスのダッシュボードのオープン、サービスの削除用です。 サービス・インスタンスを削除しても、このアプリへの関連付けが削除されるだけで、サービス・インスタンスは削除されませんので注意してください。  また、サービス資格情報はこのビューに統合されるため、個々のサービス・インスタンス・ビューにアクセスして取得する必要もありません。

![Developer Console の「アプリの詳細 (App Details)」ビュー](images/project_details_view.png "「アプリの詳細 (App Details)」ビュー") <br> *Developer Console の「アプリの詳細 (App Details)」ビュー*

「アプリの詳細 (App Details)」ビューでは、元のスターター・キットに含まれていない新しいサービスまたは既存のサービスをアプリに追加できます。 実行するには、サービス・リスト・ボックスの`「リソースの追加」`リンクをクリックしてください。  使用可能なサービスは、アプリのタイプと領域で使用可能なサービスによって異なります。したがって、すべてのサービスがすべてのアプリに関連付けられるわけではありません。

![Developer Console の「リソースの追加」ダイアログ](images/add_resource_dialog.png "「リソースの追加」ダイアログ") <br> *Developer Console の「リソースの追加」ダイアログ*

「アプリの詳細 (App Details)」ビューでは、次の 2 つの方法でコードにアクセスできます。

*  [推奨] `「クラウドにデプロイ」`ボタンをクリックして、コードをリポジトリーにプッシュし、アプリを {{site.data.keyword.cloud_notm}} にデプロイします。  {{site.data.keyword.cloud_notm}} DevOps ツールチェーンについて詳しくは、[ここ](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about)をクリックしてください。
*  アプリ・コードを素早く確認するには、`「コードのダウンロード」`を選択してアプリ用のコードを生成およびダウンロードします。

##「アプリのリスト (App List)」ビュー
{: #project_list_view}

「アプリのリスト (Apps List)」ビューから、作成したすべてのアプリのリストを表示できます。  ここから、アプリの名前を変更または削除できます。 アプリ名の行をクリックすると、「アプリの詳細 (App Details)」ビューに戻ります。

![Developer Console の「アプリのリスト (App List)」ビュー](images/project_list_view.png "「アプリのリスト (App List)」ビュー") <br> *Developer Console の「アプリのリスト (App List)」ビュー*
