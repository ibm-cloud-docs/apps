---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# 在 {{site.data.keyword.Bluemix_notm}} 中建立應用程式
{: #create}

在 {{site.data.keyword.Bluemix}} 中，您可以建置企業層級行動及 Web 應用程式，以及充分運用 {{site.data.keyword.Bluemix_notm}} 所管理的雲端延伸規格。您可以使用 {{site.data.keyword.Bluemix}} 主控台及指令行工具來建置、執行及部署應用程式。請遵循這份完整開發情境以便開始使用。


## 步驟 1：註冊 {{site.data.keyword.Bluemix_notm}} 帳戶
{: #sign-up}

請前往 [bluemix.net](bluemix.net)。輸入電子郵件、名稱、公司、地區、電話號碼，即已完成。您不需要信用卡就可以註冊一個免費帳戶。請隨意看看。

## 步驟 2：查看型錄
{: #catalog}

{{site.data.keyword.Bluemix_notm}} 型錄會列出基礎架構及其提供的平台資源。您可以選取虛擬機器、容器或 Cloudant（Cloud Foundry 應用程式），以開始建置您的應用程式。如果您需要平台資源，{{site.data.keyword.Bluemix_notm}} 也會提供樣板，以提供運行環境及其他服務來協助您開始建置。

## 步驟 3：建立資源
{: #resource}

1. 在[儀表板](https://console.bluemix.net/dashboard/apps/)中，按一下**建立資源**。

2. 從型錄中，在「平台」區段中選取應用程式。然後，選擇運行環境。例如，您可以選擇 IBM 建置套件所支援的 IBM 運行環境（例如 Liberty for Java）。您也可以選擇根據開放程式碼及協力廠商建置套件的「社群」運行環境（例如 Tomcat）。

  * [開始使用 Containers](../containers/container_index.html)
  * [開始使用 Openwhisk](../openwhisk/index.html)
  * [建立 Cloud Foundry 應用程式](../cfapps/index.html#creating_cloud_foundry_apps)

3. 輸入應用程式名稱、主機名稱，然後選擇定價方案。

4. 選取開發樣式。您可以使用偏好的文字編輯器來編輯應用程式，然後使用 {{site.data.keyword.Bluemix_notm}} 指令行將它部署至 {{site.data.keyword.Bluemix_notm}}。您也可以使用 {{site.data.keyword.Bluemix_notm}} DevOps Services 從瀏覽器中部署應用程式，或使用 Eclipse Tools for {{site.data.keyword.Bluemix_notm}} 以在 Eclipse 整合開發環境中處理應用程式。

## 步驟 4：開始新增程式碼
{: #code}

每一個應用程式都會隨附一個開始使用區段，協助您取得開始運作所需的所有軟體及內容。

在儀表板中，按一下應用程式，然後按一下**開始使用**，以協助您取得開發應用程式所需的軟體、指向原始碼，以及協助您第一次部署應用程式。

## 後續步驟
{: #next}

開發應用程式之後，請使用[最佳作法](best-practice.html)及[雲端整備](cloud-ready.html)手冊，確定應用程式已備妥可用於 {{site.data.keyword.Bluemix_notm}}。然後，[部署](../starters/install_cli.html)應用程式。
