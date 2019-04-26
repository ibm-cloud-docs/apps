---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, deploying apps, containers, kubernetes, docker, clusters, devops toolchain, deployment, kube

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Kubernetes でのコンテナーの使用
{: #containers-kube}

Kubernetes クラスターで実行される Docker コンテナーに高可用性のアプリをデプロイして、{{site.data.keyword.containershort}} を開始します。 Git でチーム開発を管理し、次に DevOps ツールチェーンを使用して Kubernetes へのアプリのデプロイメントを管理します。
{: shortdesc}

コンテナーは、環境間でアプリをシームレスに移動できるようにアプリとそのすべての依存関係をパッケージ化するための標準的な手段です。 仮想マシンとは異なり、コンテナーはオペレーティング・システムをバンドルしません。 アプリのコード、ランタイム、システム・ツール、ライブラリー、設定のみがコンテナー内にパッケージされます。 コンテナーは、仮想マシンより軽量で移植しやすく、効率的です。

サービスについて詳しくは、[{{site.data.keyword.containershort_notm}}の概説](/docs/containers?topic=containers-container_index)を参照してください。

## デプロイメントの構成
{: #config-deploy}

バックエンド・アプリや Web サービング・アプリを作成する場合、Kubernetes 環境を使用する {{site.data.keyword.containershort_notm}} サービスにそれらのアプリをデプロイすることができます。

1. 自動化されたクラウド・パイプラインをセットアップして、アプリをクラウドにデプロイします。
2. **「継続的デリバリーの構成 (Configure continous delivery)」**をクリックします。
3. ターゲットとして **IBM Kubernetes Service** を選択します。 まだクラスターがない場合は、[クラスターを作成 ](https://{DomainName}/kubernetes/catalog/cluster/create){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") する必要があります。
4. デプロイメントが完了したら、Delivery Pipeline のデプロイ・ステージからのログで URL を取得して、クラウドのライブ・アプリを確認します。 ポートを含む最後の IP アドレスが、アプリの新しいホーム (例えば、169.60.133.124:32355) です。

## サービスのバインド
{: #bind-services}

ツールチェーンが作成されると、アプリに関連付けられたサービスが、Kubernetes のシークレットを使用して Kubernetes クラスターにバインドされます。 シークレットは、実行中のアプリの外部でサービス資格情報を管理するために使用されます。 アプリはシークレットを読み取ってから、実行を開始するために必要な値を取得します。 サービスをバインドすると、実動レベルの {{site.data.keyword.cloud}} サービス・インスタンスを使用している可能性がある別の Kubernetes 環境にアプリをデプロイすることができます。

サービスやシークレットを削除した場合、それらのサービスやシークレットを再度手動でバインドするか、ツールチェーンを削除して再作成する必要があります。
{: tip}

詳しくは、[Secrets ](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## 開発の開始
{: #dev}

1. ツールチェーンから新しいオンラインの Git リポジトリーをチェックアウトして、コードの処理を開始します。 ツールチェーンを表示するには、**「ツールチェーンの表示」**をクリックします。
2. コードが作成された Git リポジトリーをローカル環境に複製し、その複製された Git リポジトリーにアクセスします。
3. 任意の IDE を使用してプロジェクトを開きます。

## ツールチェーンでのビルドおよびデプロイ
{: #bulid-deploy-tc}

ツールチェーンには、ビルド・ステージとデプロイメント・ステージがあります。

### ビルド・ステージ
{: #build-stage}
ビルド・ステージは、ご使用の Git リポジトリーで `git push` が実行されるとトリガーされます。 パイプラインのこのステージでは、Docker イメージのビルドをトリガーして、このイメージをコンテナー・レジストリー内に配置します。

詳しくは、『[IBM Cloud Container Registry の概説](/docs/services/Registry?topic=registry-index)』を参照してください。

### デプロイメント・ステージ
{: #deploy-stage}

デプロイメント・ステージでは、{{site.data.keyword.registryshort_notm}} から最新のイメージを取得してから、Helm チャートを使用してこのイメージを Kubernetes クラスターにデプロイします。 Helm チャートは、クラウドへのデプロイ時にアプリに追加されています。 Helm チャートは、パッケージされたコンテナー・イメージのデプロイメント・ステップを簡単に管理できるようにします。

詳しくは、[Charts ](https://docs.helm.sh/developing_charts/){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

{{site.data.keyword.cloud_notm}} では、多数の[事前構成済みの Helm チャート ](https://{DomainName}/kubernetes/solutions/helm-charts){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") がサポートされます。

## アプリのセキュリティーの確認
{: #sec}

{{site.data.keyword.containershort_notm}} では、パッケージされたコンテナー・イメージにセキュリティーの脆弱性がないかどうかのスキャンがサポートされます。 エンタープライズ・レベルのアプリケーションをサポートするためには、セキュリティー・スキャンが必須です。

潜在的なセキュリティーの脆弱性を確認するには、コンテナーの[イメージ・リポジトリー ](https://{DomainName}/kubernetes/registry/main/private){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。
