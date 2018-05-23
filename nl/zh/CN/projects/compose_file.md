---
copyright:
years: 2015, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# Compose 文件
{: #compose-file}

对于 Compose 应用程序，以下信息列出了通常可在 {{site.data.keyword.Bluemix}} 中找到的内容。创建初学者工具包时，会创建这些文件。如果要迁移应用程序以在 {{site.data.keyword.Bluemix_notm}} 中进行托管，您可能希望查看这些信息以避免潜在的冲突。
{:shortdesc}

[Compose](https://docs.docker.com/compose/overview/) 文件定义了用于运行多容器应用程序的信息。

应将使用的 Compose 文件的版本指定为 2.0 或更高版本，如下所示：`version: '2'`

您还需要定义服务。下面是 Node 应用程序中的示例：
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

`web` 和 `mongo` 是指定的服务，并且每个服务都有配置，这些配置在 Docker-Compose [文档](https://docs.docker.com/compose/compose-file/compose-file-v2/)中进行定义。

最相关的配置按如下所示列出：

* build：context 和 dockerfile 属性在此处不是必需的，因为这两个属性是缺省值，但可以使用此格式覆盖。context 属性定义 dockerfile 属性中指定的 Dockerfile 名称的路径。

* tty：通过指定此属性，容器可以保持运行，而不会立即退出。这对于 Docker-Compose 支持是必需的。

* command：此属性指定要在容器内执行的命令。

* image 和 container_name：这两个属性分别指定映像和容器的名称。


