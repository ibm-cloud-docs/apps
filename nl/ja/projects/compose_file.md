---
copyright:
years: 2015, 2018
lastupdated: "2018-07-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Docker Compose ファイルからの開始
{: #compose-file}

Docker Compose アプリでは、通常 {{site.data.keyword.Bluemix}} に含まれている内容のインベントリーは以下の情報のとおりです。スターター・キットを作成すると、以下のファイルが作成されます。 {{site.data.keyword.Bluemix_notm}} でアプリをホストにマイグレーションする場合、競合の可能性を回避するためにこの情報を確認する必要があります。
{:shortdesc}

[Docker Compose](https://docs.docker.com/compose/overview/) ファイルは、複数コンテナーのアプリケーションを実行するための情報を定義します。

使用する Docker Compose ファイルのバージョンには、`version: '2'` のように 2.0 以降を指定します。

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

サービス `web` および `mongo` が定義されており、それぞれの構成は Docker Compose の [資料](https://docs.docker.com/compose/compose-file/compose-file-v2/)で定義されています。

以下に、最も関連性の高い構成をリストします。

* `build`: context 属性と Dockerfile 属性はデフォルト値であるためここでは不要ですが、この形式で上書きすることができます。context 属性は、Dockerfile 属性で指定された Dockerfile の名前へのパスを定義します。

* `tty`: この属性を指定することで、コンテナーは実行を続行でき、すぐには終了しません。これは、Docker Compose のサポートに必要です。

* `command`: この属性は、コンテナー内で実行されるコマンドを指定します。

* `image` および `container_name`: これらの属性は、イメージとコンテナーの名前を指定します。
