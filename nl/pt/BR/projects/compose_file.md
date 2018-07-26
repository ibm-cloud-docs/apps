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

# Iniciando com um arquivo do Docker Compose
{: #compose-file}

Para apps do Docker Compose, as informações a seguir são um inventário do que você tipicamente encontra no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos.
{:shortdesc}

O arquivo do [Docker Compose](https://docs.docker.com/compose/overview/) define informações para executar aplicativos com múltiplos contêineres.

Especifique a versão do arquivo do Docker Compose, a qual costuma ser 2.0 ou mais recente: `version: '2'`

Você também precisa definir os serviços. O exemplo a seguir é de um app de Nó:

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

Os serviços `web` e `mongo` são definidos e cada um deles possui configurações que são definidas na [documentação](https://docs.docker.com/compose/compose-file/compose-file-v2/) do Docker Compose.

As configurações mais relevantes são listadas como a seguir:

* `build`: os atributos context e Dockerfile não são necessários aqui, porque eles são os valores padrão, mas podem ser sobrescritos nesse formato. O atributo de contexto define o caminho para o nome do Dockerfile especificado no atributo do Dockerfile.

* `tty`: ao especificar esse atributo, os contêineres podem continuar sendo executados e não sair imediatamente, o que é necessário para o suporte do Docker Compose.

* `command`: esse atributo especifica o comando a ser executado dentro dos contêineres.

* `image` e `container_name`: esses atributos especificam os nomes da imagem e dos contêineres.
