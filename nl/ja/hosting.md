---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# ホスティング環境の選択
{: #hosting}

既存のアプリケーションがある場合は、必要なすべてのインフラストラクチャーまたはプラットフォームのサービスを含めて {{site.data.keyword.cloud}} でホストすることができます。
{:shortdesc}

{{site.data.keyword.cloud_notm}} を使用すれば、新規のアプリのテストや実行のためにハードウェアに多額の投資を行う必要がなくなります。 代わりに、IBM がすべてを管理し、使用した分だけ課金されるようになります。 クラウド・サーバー環境は、インフラストラクチャー・レイヤーの基本です。 単一のオプションを選択することも、より複雑な環境に対してオプションの組み合わせを選択することもできます。 

アプリをホストするためのさまざまなオプションがあり、必要に応じてインフラストラクチャーを自由に制御できます。 アプリは以下のどの方法でも実行できます。

  * Kubernetes クラスター上の Docker コンテナーとして実行
  * Cloud Foundry アプリとして実行
  * サーバーレス機能として実行
  * VMware として実行
  * 仮想マシンとして実行
  * 高性能な{{site.data.keyword.baremetal_short}}上で実行 
  
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

コンピュート・オプションの要約については、以下の表を確認してください。

| オプション | 説明 | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Docker コンテナー、Kubernetes テクノロジー、直観的なユーザー・エクスペリエンス、標準装備のセキュリティーと分離機能を結合させることにより、コンピュート・ホストのクラスター内でコンテナー化アプリのデプロイメント、操作、スケーリング、モニタリングを自動化します。 |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | 複数の分離したエンタープライズ・グレードの Cloud Foundry プラットフォームをオンデマンドでインスタンス化します。 |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Apache OpenWhisk に基づく Functions-as-a-Service (FaaS) プログラミング・プラットフォーム。 |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | スケーラブルでセキュアでハイパフォーマンスのインフラストラクチャー、および業界最先端の VMware ハイブリッド仮想化テクノロジーを使用して、オンプレミスの VMware ワークロードを迅速かつシームレスに統合またはマイグレーションします。 |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | 専用のコアおよびメモリー割り振りと共に購入される拡張が容易な仮想サーバー。 |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | お客様専用で、サーバー・リソースを含むどの部分でも他のお客様と共有されない、時間単位または月単位のシングル・テナント・サーバー。 |
{: caption="表 1. コンピュート・オプション" caption-side="top"}

