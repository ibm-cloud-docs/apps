---
copyright:
years: 2015, 2018
lastupdated: "2018-05-21"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 從 Compose 檔案開始
{: #compose-file}

若為 Compose 應用程式，下列資訊是您在 {{site.data.keyword.Bluemix}} 中一般找到的項目庫存。當您建立入門範本套件時，會為您建立這些檔案。如果您要移轉應用程式以便在 {{site.data.keyword.Bluemix_notm}} 中管理，建議您檢閱此資訊，以避免潛在的衝突。
{:shortdesc}

[Compose](https://docs.docker.com/compose/overview/) 檔案會定義用於執行多容器應用程式的資訊。

請將要使用的 Compose 檔案版本指定為 2.0 或更新版本，例如：`version: '2'`

您也需要定義服務。下列範例來自 Node 應用程式：

```
services:
  web:
    build:
    	context: <path-to-Dockerfile>
	dockerfile: <name-of-Dockerfile>
    tty: true
    command: npm run start-dev
    image: <image-name>
    container_name: <container-name>
    volumes:
      - .:/app
      - /app/node_modules
    ports:
      - "3000:3000"
    links:
      - mongo
    environment:
      MONGO_URL: "mongo"
      MONGO_DB_NAME: "comments"
      NODE_ENV: "development"
      PORT: 3000
  mongo:
    image: mongo
```

已定義 `web` 和 `mongo` 服務，且它們各自都有配置（定義在 Docker-Compose [文件](https://docs.docker.com/compose/compose-file/compose-file-v2/)）。

最相關的配置如下所示：

* build：在這裡不需要 context 及 Dockerfile 屬性，因為它們是預設值，但可以使用此格式予以改寫。context 屬性定義了在 Dockerfile 屬性中所指定之 Dockerfile 名稱的路徑。

* tty：藉由指定此屬性，容器可以維持執行，而不會立即結束，這是 Docker-Compose 支援的必要項目。

* command：此屬性指定要在容器內執行的指令。

* image 和 container_name：這些屬性指定映像檔和容器的名稱。
