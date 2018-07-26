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

# Docker Compose 파일 시작
{: #compose-file}

Docker Compose 앱의 경우 다음 정보는 일반적으로 {{site.data.keyword.Bluemix}}에서 볼 수 있는 항목의 인벤토리입니다. 스타터 킷을 작성하면 이러한 파일이 사용자를 위해 작성됩니다. 앱을 {{site.data.keyword.Bluemix_notm}} 내의 호스트로 마이그레이션하는 경우에는 잠재적 충돌을 방지하기 위해 이 정보를 검토할 수 있습니다.
{:shortdesc}

[Docker Compose](https://docs.docker.com/compose/overview/) 파일은 멀티 컨테이너 애플리케이션 실행을 위한 정보를 정의합니다.

사용되는 Docker Compose 파일의 버전을 다음과 같이 2.0 이상으로 지정하십시오. `version: '2'`

서비스 또한 정의해야 합니다. 다음 예는 Node 앱의 예입니다.

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

서비스 `web` 및 `mongo`가 정의되며 각각에는 Docker Compose [문서](https://docs.docker.com/compose/compose-file/compose-file-v2/)에 정의된 구성이 있습니다. 

가장 관련성이 높은 구성이 다음과 같이 나열됩니다.

* `build`: context 및 dockerfile 속성은 기본값이므로 여기서는 불필요하지만, 이 형식으로 겹쳐쓸 수 있습니다. context 속성은 dockerfile 속성에 지정된 Dockerfile의 이름에 대한 경로를 정의합니다.

* `tty`: 이 속성을 지정하면 컨테이너가 즉각적으로 종료되지 않고 계속 실행될 수 있으며, 이는 Docker Compose 지원에 필요합니다.

* `command`: 이 속성은 컨테이너 내에서 실행되는 명령을 지정합니다.

* `image` 및 `container_name`: 이러한 속성은 이미지 및 컨테이너의 이름을 지정합니다.
