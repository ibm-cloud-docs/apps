---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# カスタム・アプリのビルド
{: #build-your-own}

スターター・キットを使用しておらず、必要なものがわかっている場合は、選択したリソースでアプリをビルドできます。
{: shortdesc}

## 言語の選択
{: #catalog}

{{site.data.keyword.Bluemix_notm}} カタログには、使用できるインフラストラクチャーおよびプラットフォームのリソースがリストされています。 仮想マシン、コンテナー、または Cloudant、および Cloud Foundry アプリを選択して、自分のアプリの作成を開始できます。 プラットフォーム・リソースが必要な場合、{{site.data.keyword.Bluemix_notm}} には、作成の開始を支援するためのランタイムやその他のサービスを提供する[ボイラープレート](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=blueprints)も用意されています。

## リソースの作成
{: #resource}

1. 「リソース」リストから**「作成」**をクリックします。または、**「カタログ」**をクリックしてから、作成するリソース・タイプのタイルを選択します。 

2. カタログで、「プラットフォーム」セクションからアプリを選択します。 次にランタイムを選択します。 例えば、IBM ビルドパックによってサポートされている、Liberty for Java などの IBM ランタイム環境を選択できます。 また、オープン・ソースとサード・パーティーのビルドパックに依存する、Tomcat などのコミュニティー・ランタイムも選択できます。

  * [コンテナーの概説](/docs/containers/container_index.html)
  * [Openwhisk の概説](/docs/openwhisk/index.html)
  * [Cloud Foundry アプリの作成](/docs/cloud-foundry/index.html)

3. アプリ名とホスト名を入力し、価格設定プランを選択します。

4. 開発スタイルを選択します。 好みのテキスト・エディターでアプリを編集し、{{site.data.keyword.cloud_notm}} コマンド・ラインを使用してそのアプリを {{site.data.keyword.cloud_notm}} にデプロイできます。 また、{{site.data.keyword.cloud_notm}} DevOps Services を使用してブラウザーからアプリケーションをデプロイしたり、Eclipse Tools for {{site.data.keyword.cloud_notm}} を使用して Eclipse 統合開発環境でアプリケーションの作業を行うこともできます。

## コードの追加
{: #code}

各アプリには、作業を開始するために必要なすべてのソフトウェアとコンテンツの取得に役立つ「開始」セクションが備えられています。

ダッシュボードでアプリをクリックし、次に**「開始」**をクリックします。これは、アプリの開発に必要なソフトウェアの入手に役立ち、ソース・コードを示し、ユーザーが初めてアプリをデプロイするのを支援します。

## 次のステップ
{: #next}

ユーザーのニーズに合うように、引き続きアプリをカスタマイズします。 ビジネスの成果を挙げるためにアプリを拡張するための次の提案を確認してください。

* [ベスト・プラクティス](best-practice.html)・ガイドで説明した[セキュリティー ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=data&category=security){:new_window}、[モニタリング ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?category=devops){:new_window}、および可用性の向上を追加することで、アプリの堅牢性を高める。
* [Watson コグニティブ・サービス ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=data&category=watson){:new_window} および[高度な分析と機械学習](https://{DomainName}/catalog/?taxonomyNavigation=data&category=data){:new_window}を使用して、アプリをよりスマートにする。
* [モバイル ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?category=mobile){:new_window} に移行する。
* [IoT![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?category=iot){:new_window} を試してみる。
* [API Connect ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?category=integration){:new_window} などのサービスを使用して、[サーバーレス・アクション ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?category=whisk){:new_window} を組み込む。
