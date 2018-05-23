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

# Compose ファイル
{: #compose-file}

次の情報は、Compose アプリの場合に {{site.data.keyword.Bluemix}} で通常見られるものの一覧です。 スターター・キットを作成すると、以下のファイルが作成されます。 {{site.data.keyword.Bluemix_notm}} でアプリをホストにマイグレーションする場合、競合の可能性を回避するためにこの情報を確認する必要があります。 
{:shortdesc}

[Compose](https://docs.docker.com/compose/overview/) ファイルは、複数コンテナーのアプリケーションを実行するための情報を定義します。

使用する Compose ファイルのバージョンは、`version: '2'` のように 2.0 以降を指定する必要があります。

また、サービスを定義する必要があります。 以下は、Node アプリからの例です。
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

`web` および `mongo` は指定されたサービスであり、それぞれに Docker-Compose [資料](https://docs.docker.com/compose/compose-file/compose-file-v2/)で定義されている構成があります。

以下に、最も関連性の高い構成をリストします。

* build: context 属性と dockerfile 属性はデフォルト値であるためここでは不要ですが、この形式で上書きできます。 context 属性は、dockerfile 属性で指定された Dockerfile の名前へのパスを定義します。

* tty: この属性を指定することで、コンテナーがすぐに終了することなく稼働したままとなるようにできます。 これは、Docker-Compose サポートに必要です。

* command: この属性は、コンテナー内部で実行されるコマンドを指定します。

* image および container_name: これらの属性は、それぞれ、イメージの名前とコンテナーの名前を指定します。


