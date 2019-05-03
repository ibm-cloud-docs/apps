---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, deploying apps, containers, Kubernetes, Docker, clusters, DevOps toolchain

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 使用容器搭配 Kubernetes
{: #containers-kube}

在執行於 Kubernetes 叢集的 Docker 容器中部署高可用性的應用程式，以開始使用 {{site.data.keyword.containershort}}。使用 Git 管理您的團隊開發，然後使用 DevOps 工具鏈管理應用程式對 Kubernetes 的部署。
{: shortdesc}

容器是包裝應用程式及其所有相依關係的標準方式，而此方式可讓您在環境之間無縫移動應用程式。容器不像虛擬機器，並不會搭載作業系統。只有應用程式碼、運行環境、系統工具、程式庫和設定會包裝在容器內。容器比虛擬機器更輕量、可攜性更高且更有效率。


請參閱[開始使用 {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-container_index) 以進一步瞭解服務。

## 配置部署
{: #config-deploy}

當您建立後端或 Web 服務的應用程式時，可以將它們部署到 {{site.data.keyword.containershort_notm}} 服務，它使用 Kubernetes 環境。

1. 設定自動化雲端管線來將應用程式部署至雲端。
2. 按一下**配置持續交付**。
3. 選取 **IBM Kubernetes Service** 作為目標。您需要[建立叢集 ](https://{DomainName}/containers-kubernetes/catalog/cluster/create){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，如果還沒有的話。
4. 部署完成之後，請從交付管線的部署階段日誌取得 URL，查看雲端中的即時應用程式。最後一個具有埠的 IP 位址是您應用程式的新首頁，例如 169.60.133.124:32355。

## 連結服務
{: #bind-services}

建立工具鏈時，您與應用程式相關聯的服務會使用 Kubernetes 密碼連結至 Kubernetes 叢集。密碼用來在執行中應用程式之外管理服務認證。應用程式會讀取密碼，然後擷取開始執行所需要的值。連結服務讓您能將應用程式部署至另一個 Kubernetes 環境，該環境可能是使用正式作業層次的 {{site.data.keyword.cloud}} 服務實例。

如果您刪除服務或密碼，則需要手動重新連結它們，或是服務並重建工具鏈。
{: tip}

如需相關資訊，請參閱 [Secrets ](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")。

## 開始開發
{: #dev}

1. 從工具鏈查看您的新線上 Git 儲存庫，並開始使用程式碼。若要查看工具鏈，請按一下**檢視工具鏈**。
2. 藉由將儲存庫複製到本端環境，存取建立程式碼所在的 Git 儲存庫。
3. 使用您最愛的 IDE 開啟專案。

## 使用工具鏈進行建置及部署
{: #bulid-deploy-tc}

工具鏈包含建置階段及部署階段。

### 建置階段
{: #build-stage}
建置階段是在您的 Git 儲存庫執行 `git push` 時觸發。管線中的階段會觸發 Docker 映像檔建置，並將映像檔放在容器登錄中。

如需相關資訊，請參閱[開始使用 IBM Cloud Container Registry](/docs/services/Registry?topic=registry-index)。

### 部署階段
{: #deploy-stage}

部署階段會從 {{site.data.keyword.registryshort_notm}} 擷取最新的映像檔，然後使用 Helm 圖表將它部署至您的 Kubernetes 叢集。Helm 圖表是在您部署至雲端時新增至您的應用程式。Helm 圖表讓您能輕鬆管理已包裝之容器映像檔的部署步驟。

如需相關資訊，請參閱 [Charts ](https://docs.helm.sh/developing_charts/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")。

{{site.data.keyword.cloud_notm}} 支援許多[預先配置的 Helm 圖表 ](https://{DomainName}/containers-kubernetes/solutions/helm-charts){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")。

## 檢查應用程式安全
{: #sec}

{{site.data.keyword.containershort_notm}} 支援掃描已包裝的容器映像檔是否有安全漏洞。安全掃描對於支援企業應用程式而言相當重要。

檢視容器[映像檔儲存庫 ](https://{DomainName}/containers-kubernetes/registry/private){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 以檢查可能的安全漏洞。
