---

copyright:
  years: 2018
lastupdated: "2018-07-05"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 應用程式開發
{: #intro}

「{{site.data.keyword.cloud_notm}} 開發人員主控台」可協助開發人員從入門範本套件中建立應用程式，並佈建及連接重要 {{site.data.keyword.cloud_notm}} 最佳化服務，然後快速下載工作碼或設定持續交付。您可以建立、檢視、配置及管理應用程式，以及下載應用程式的程式碼。使用入門範本套件可協助您快速評估及測試含有範例應用程式的 {{site.data.keyword.cloud_notm}} 服務。
{:shortdesc}

## 何謂入門範本套件？
{: #starter_kits}

入門範本套件很適合以您選擇的語言來動態組合架構正式作業應用程式，以進行雲端部署。每個入門範本套件都會有語言、架構，以及特定真實使用案例的模式。您可以重複使用程式碼，而非重複發明程式碼。

### 比較範例與入門範本套件

開發人員經常依賴預先撰寫的程式碼（例如 Snippet、示範及範例）。您如何得知 Snippet、示範及範例與 {{site.data.keyword.cloud_notm}} 入門範本套件之間的差異？

* **Snippet** - 一些經常呈現在 IDE 中的程式碼行。Snippet 可協助開發人員與程式設計語言語法整合，或支援與所定義的 API 整合。

* **示範** - 程式碼，通常具有高品質、高準確性以及使用某範圍的服務及整合點。它通常需要設定，並用來證明商業問題或示範平台特性。示範可以評估雲端採用的階段。它的程式碼有時會包括在正式作業程式碼中。

* **範例** - 程式碼，是特定特性、功能、服務或使用者行程的小型範例。範例可以在正式作業應用程式中重複使用或併入。您可以使用範例來顯示技術功能，以及解決技術問題的可能方法。

* **{{site.data.keyword.cloud_notm}} 入門範本套件** - 入門範本套件是可正式作業的模式，以與一組服務整合來產生可正式作業的資產。然後，您可以將它們直接部署至 DevOps 管線及 Kubernetes 叢集。入門範本套件的敘述性 meta 資料可提供足夠的資訊以瞭解套件為何及用途。它也具有告訴 {{site.data.keyword.cloud_notm}} 所產生內容的指示。輸出可以進一步予以加強。入門範本套件內容不像示範這麼複雜，也不像 Snippet 或範例那麼簡單。入門範本套件是根據您的需求而動態建立。

  入門範本套件會顯示具有運行環境（例如 Swift 及 Kitura）的重要模式實作。它們可以包括簡單的使用者體驗，以突顯服務的整合。入門範本套件是一種更準確使用案例的可自訂實作。

  入門範本套件包括容許 {{site.data.keyword.cloud_notm}} 自動產生具有可攜式程式碼之臨時應用程式專案的指示。它們也會指定要在您建立專案時自動佈建的資源。

## 自動佈建的資源
{: #auto_privisioned_resources}

如果入門範本套件指定必要資源，則 {{site.data.keyword.cloud_notm}} 會在您建立專案時自動建立那些資源的實例。您可以手動佈建資源，或選取現有資源實例，以在建立您的專案之後擴增該專案。您可以在*專案詳細資料* 視圖中查看與專案相關聯的服務實例清單，以及認證（以防您需要它們）。

## 產生可攜式程式碼
{: #portable_code}

從入門範本套件建立應用程式會自動產生具有一致格式且與運行環境無關的程式碼。您可以將程式碼部署至您選擇的環境（例如，Kubernetes 或 Cloud Foundry），而不進行變更。

專案包括一個 `README` 檔案，其中具有專案的技術詳細資料，並解釋準備好執行應用程式所需的項目。

如需相關資訊，請參閱 [Apple 學習資源的 {{site.data.keyword.cloud_notm}} 開發人員主控台](https://console.bluemix.net/developer/appledevelopment/learning-resources)。
{: tip}

### 產生的應用程式內容為何？
{: #content}

{{site.data.keyword.cloud_notm}} 入門範本套件所產生的程式碼具有四個基本元件：使用案例邏輯、語言元件、具備服務功能及具備雲端功能。產生這些元件可節省您寶貴的時間，並確保您是使用同級最佳的架構。

* **使用案例邏輯**是特定使用案例的程式碼。範例包括 Watson Conversation 聊天機器人的程式碼，或適用於行動視覺化識別應用程式的程式碼。
* **語言元件**是您為入門範本套件選取之語言特有的程式碼元件及檔案。例如，node.js 程式設計師需要 `package.json` 檔案進行相依關係管理，而且 {{site.data.keyword.cloud_notm}} Developer Experience 會自動建立此檔案。
* **具備服務功能**是程式碼，可讓您的應用程式連接專案，並使用您新增至其中的服務。具備服務功能項目的範例是認證管理、起始設定碼及服務特定 SDK。
* **具備雲端功能**是程式碼，可讓您的應用程式在 {{site.data.keyword.cloud_notm}} 上執行。例如，可讓您的應用程式在 {{site.data.keyword.cloud_notm}} Kubernetes 叢集上執行的 Helm 圖表會落在具備雲端功能種類中。

{{site.data.keyword.cloud_notm}} 所產生應用程式的架構有效，並且會針對您為專案選擇的語言建立最佳作法的模型。若要查看應用程式專案的檔案及結構詳細資料，請參閱下列主題。

* [Java 應用程式檔案](/docs/apps/projects/java_project_contents.html)
* [Node.js 應用程式檔案](/docs/apps/projects/node_project_contents.html)
* [Python 應用程式檔案](/docs/apps/projects/python_project_contents.html)
* [Swift 應用程式檔案](/docs/apps/projects/swift_project_contents.html)。
