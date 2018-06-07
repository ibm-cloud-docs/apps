---
copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Swift 應用程式檔案
{: #swift-project-files}

若為 Swift 應用程式，下列資訊是您在 {{site.data.keyword.Bluemix}} 中一般找到的項目庫存。當您建立入門範本套件時，會為您建立這些檔案。如果您要移轉應用程式以便在 {{site.data.keyword.Bluemix_notm}} 中管理，建議您檢閱此資訊，以避免潛在的衝突。
{:shortdesc}

下表列出在所產生的 Swift 應用程式中包含的一般目錄及檔案。

|根目錄|說明|
|:------------------------------------------------|:------------------------------------------|
|Package.swift|Swift 相依關係定義檔|
|cli-config.yml |CLI 配置選項|
|manifest.yml |Cloud Foundry 部署檔案|
|Dockerfile |`ibmcloud dev run`、`ibmcloud dev deploy` 及 `docker` 指令的 Dockerfile|
|Dockerfile-tools |`ibmcloud dev build` 及 `ibmcloud dev test` 的 Dockerfile|
| LICENSE |授權檔|
|README.md |應用程式的說明|
{: caption="表 1. 產生的 Swift 應用程式根目錄的內容" caption-side="top"}

| `./Sources/Application/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` |Swift 應用程式檔案|
| `./Sources/<projectname>/main.swift` |Swift 主要檔案|
{: caption="表 2. 產生的 Swift Spring 應用程式 /Sources/Application/ 目錄的內容" caption-side="top"}

| `./test/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| test-server.js |用 Kitura 進行測試的公用程式方法|
{: caption="表 3. 產生的 Swift 應用程式 test 目錄的內容" caption-side="top"}

| `./Tests/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` |在 Linux 上測試用的公用程式|
| `./Tests/ApplicationTests>/RouteTests.swift` |包含測試案例的檔案|
{: caption="表 4. 產生的 Swift 應用程式 tests 目錄的內容" caption-side="top"}

| `./.bluemix/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| container_build.sh |容器建置 Script|
| deploy.json |部署資訊|
| kube_deploy.sh | Kubernetes 部署 Script|
| pipeline.yml |IBM Cloud 管線定義|
| toolchain.yml |IBM Cloud 工具鏈定義|
{: caption="表 5. 產生的 Swift 應用程式 bluemix 目錄的內容" caption-side="top"}

| `./chart/<projectname>/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` |Helm 圖表|
| `./chart/<projectname>/values.yaml` |Helm 圖表值|
| `./chart/<projectname>/templates/deployment.yaml` |部署範本|
| `./chart/<projectname>/templates/service.yaml` |服務範本|
{: caption="表 6. 產生的 Swift 應用程式 chart 目錄的內容" caption-side="top"}

| `./manifests/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml |Kubernetes 服務及部署 yaml |
{: caption="表 7. 產生的 Swift 應用程式 manifests 目錄的內容" caption-side="top"}

