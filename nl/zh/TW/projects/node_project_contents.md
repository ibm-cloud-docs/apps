---
copyright:
  years: 2015, 2018
lastupdated: "2018-11-16"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Node.js 應用程式檔案
{: #node-project-files}

若為 Node.js 應用程式，下列資訊是您在 {{site.data.keyword.Bluemix}} 中一般找到的項目庫存。當您建立入門範本套件時，會為您建立這些檔案。如果您要移轉應用程式以便在 {{site.data.keyword.Bluemix_notm}} 中管理，建議您檢閱此資訊，以避免潛在的衝突。
{:shortdesc}

下表列出在所產生的 Node.js 應用程式中包含的一般目錄及檔案。

|根目錄|說明|
|:------------------------------------------------|:------------------------------------------|
|package.json |有關套件的 Meta 資料資訊，包括名稱、版本及相依關係。|
|cli-config.yml |CLI 配置選項|
|manifest.yml |Cloud Foundry 部署檔案|
|Dockerfile |`ibmcloud dev run`、`ibmcloud dev deploy` 及 `docker` 指令的 Dockerfile|
| Dockerfile-tools |`ibmcloud dev build` 及 `ibmcloud dev test` 的 Dockerfile|
|docker-compose.yml |Docker Compose 的應用程式服務配置|
|webpack.config.js |建置相關資訊的 Web 套件配置|
| LICENSE |授權檔|
|README.md |應用程式的說明|
{: caption="表 1. 產生的 Node.js 應用程式根目錄的內容" caption-side="top"}

| `./public/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` |用來說明 REST API 的 Swagger 規格|
| `./public/index.html` |Web 應用程式的架構標記|
|`./public/server/server.js` |伺服器實作檔案|
{: caption="表 2. 產生的 Node.js 應用程式 public 目錄的內容" caption-side="top"}

| `./test/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| test-server.js |Express 伺服器的整合測試|
{: caption="表 3. 產生的 Node.js 應用程式 test 目錄的內容" caption-side="top"}

| `./.bluemix/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| container_build.sh |容器建置 Script|
| deploy.json |部署資訊|
| kube_deploy.sh | Kubernetes 部署 Script|
| pipeline.yml |IBM Cloud 管線定義|
| toolchain.yml |IBM Cloud 工具鏈定義|
{: caption="表 4. 產生的 Node.js 應用程式 bluemix 目錄的內容" caption-side="top"}

| `./chart/<projectname>/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` |Helm 圖表|
| `./chart/<projectname>/values.yaml` |Helm 圖表值|
| `./chart/<projectname>/templates/deployment.yaml` |部署範本|
| `./chart/<projectname>/templates/service.yaml` |服務範本|
{: caption="表 5. 產生的 Node.js 應用程式 chart 目錄的內容" caption-side="top"}
