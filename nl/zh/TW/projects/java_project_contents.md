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

# Java 應用程式檔案
{: #java-project-files}

若為 Java 應用程式，下列資訊是您在 {{site.data.keyword.Bluemix}} 中一般找到的項目庫存。當您建立入門範本套件時，會為您建立這些檔案。如果您要移轉應用程式以便在 {{site.data.keyword.Bluemix_notm}} 中管理，建議您檢閱此資訊，以避免潛在的衝突。
{:shortdesc}

## Spring
{: #spring-project-files}

下表列出在所產生的 Java Spring 應用程式中包含的目錄及檔案。

| `./` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| pom.xml |maven pom 檔案|
| cli-config.yml |CLI 配置選項|
| manifest.yml |Cloud Foundry 部署檔案|
| Dockerfile |`ibmcloud dev run`、`ibmcloud dev deploy` 及 `docker` 指令的 Dockerfile|
| Dockerfile-tools |`ibmcloud dev build` 及 `ibmcloud dev test` 的 Dockerfile|
| LICENSE |授權檔|
| README.md |應用程式的說明|
{: caption="表 1. 產生的 Java Spring 應用程式根目錄的內容" caption-side="top"}

| `./src/main/java/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` |主要 Spring 應用程式|
| `./src/main/test/application/HealthEndpointTest.java` |測試|
| `./src/main/java/application/rest/HealthApplication.java` |Health 端點|
| `./src/main/java/application/rest/v1/Example.java` |範例程式碼|
| `./src/main/java/resources/application-local.properties` |Spring 內容|
{: caption="表 2. 產生的 Java Spring 應用程式 /java/ 目錄的內容" caption-side="top"}

| `./.bluemix/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| container_build.sh |容器建置 Script|
| deploy.json |部署資訊|
| kube_deploy.sh | Kubernetes 部署 Script|
| pipeline.yml |IBM Cloud 管線定義|
| toolchain.yml |IBM Cloud 工具鏈定義|
{: caption="表 3. 產生的 Java Spring 應用程式 ./.bluemix/ 目錄的內容" caption-side="top"}

| `./chart/<projectname>/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` |Helm 圖表|
| `./chart/<projectname>/values.yaml` |Helm 圖表值|
| `./chart/<projectname>/templates/deployment.yaml` |部署範本|
| `./chart/<projectname>/templates/hpa.yaml` |HPA 範本|
| `./chart/<projectname>/templates/service.yaml` |服務範本|
{: caption="表 4. 產生的 Java Spring 應用程式 ./chart/<projectname&ml;/templates/ 目錄的內容" caption-side="top"}

| `./manifests/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml |Kubernetes 服務及部署 yaml |
{: caption="表 5. 產生的 Java Spring 應用程式 ./manifests/ 目錄的內容" caption-side="top"}

## Liberty
{: #liberty-project-files}

下表列出在所產生的 Java Liberty 應用程式中包含的目錄及檔案。

| `./` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| pom.xml |maven pom 檔案|
| cli-config.yml |CLI 配置選項|
| manifest.yml |Cloud Foundry 部署檔案|
| Dockerfile |`ibmcloud dev run`、`ibmcloud dev deploy` 及 `docker` 指令的 Dockerfile|
| Dockerfile-tools |`ibmcloud dev build` 及 `ibmcloud dev test` 指令的 Dockerfile|
| LICENSE |授權檔|
| README.md |應用程式的說明|
{: caption="表 6. 產生的 Java Liberty 應用程式根目錄的內容" caption-side="top"}

| `./src/main` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` |Health 端點|
| `./src/main/java/application/rest/v1/Example.java` |範例程式碼|
| `./src/main/liberty/config/jvm.options` |JVM 選項|
| `./src/main/liberty/config/jvmbx.options` |Java 度量值代理程式配置|
| `./src/main/liberty/config/server.env` |環境變數|
| `./src/main/liberty/config/server.xml` |伺服器配置|
| `./src/main/webapp/WEB-INF/beans.xml` |CDI Bean 配置|
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` |IBM Web 應用程式配置|
| `./src/main/test/it/HealthEndpointTest.java` |測試|
{: caption="表 7. 產生的 Java Liberty 應用程式 ./src/main/ 目錄的內容" caption-side="top"}

| `./.bluemix/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| container_build.sh |容器建置 Script|
| deploy.json |部署資訊|
| kube_deploy.sh | Kubernetes 部署 Script|
| pipeline.yml |IBM Cloud 管線定義|
| toolchain.yml |IBM Cloud 工具鏈定義|
{: caption="表 8. 產生的 Java Liberty 應用程式 ./bluemix/ 目錄的內容" caption-side="top"}

| `./chart/<projectname>/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` |Helm 圖表|
| `./chart/<projectname>/values.yaml` |Helm 圖表值|
| `./chart/<projectname>/templates/deployment.yaml` |部署範本|
| `./chart/<projectname>/templates/hpa.yaml` |HPA 範本|
| `./chart/<projectname>/templates/service.yaml` |服務範本|
{: caption="表 9. 產生的 Java Liberty 應用程式 ./chart/<projectname&ml;/ 目錄的內容" caption-side="top"}

| `./manifests/` 目錄|說明|
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml |Kubernetes 服務及部署 yaml |
{: caption="表 10. 產生的 Java Liberty 應用程式 ./manifests/ 目錄的內容" caption-side="top"}
