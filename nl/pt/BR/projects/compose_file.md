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

# Iniciando com um arquivo do Compose
{: #compose-file}

Para apps Compose, as informações a seguir são um inventário do que você normalmente localiza no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos.
{:shortdesc}

O arquivo do [Compor](https://docs.docker.com/compose/overview/) define informações para executar aplicativos de múltiplos contêineres.

Especifique a versão usada do arquivo do Compose para ser 2.0 ou mais recente, como:
`version: '2'`

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

Os serviços `web` e `mongo` são definidos e cada um deles tem configurações, que são definidas na [documentação](https://docs.docker.com/compose/compose-file/compose-file-v2/) do Docker Compose.

As configurações mais relevantes são listadas como a seguir:

* build: os atributos de contexto e do Dockerfile são desnecessários aqui porque são os valores padrão, mas podem ser substituídos nesse formato. O atributo de contexto define o caminho para o nome do Dockerfile especificado no atributo do Dockerfile.

* tty: ao especificar esse atributo, os contêineres podem permanecer em execução e não sair imediatamente, que é necessário para o suporte do Docker Compose.

* command: esse atributo especifica o comando a ser executado dentro dos contêineres.

* image e container_name: esses atributos especificam os nomes da imagem e dos contêineres.
