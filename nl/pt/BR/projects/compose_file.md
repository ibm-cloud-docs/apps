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

# Arquivo do Compose
{: #compose-file}

Para apps Compose, as informações a seguir são um inventário do que você normalmente localiza no {{site.data.keyword.Bluemix}}. Ao criar um kit do iniciador, esses arquivos são criados para você. Se você estiver migrando um app para hospedar no {{site.data.keyword.Bluemix_notm}}, poderá desejar revisar essas informações para evitar possíveis conflitos. 
{:shortdesc}

O arquivo do [Compor](https://docs.docker.com/compose/overview/) define informações para executar aplicativos de múltiplos contêineres.

É necessário especificar a versão do arquivo do Compose usado para 2.0 ou mais recente, como:
`version: '2'`

Você também precisa definir os serviços. A seguir está um exemplo de um app Node:
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

O `web` e o `mongo` são os serviços especificados e cada um deles tem configurações, que são definidas na [documentação](https://docs.docker.com/compose/compose-file/compose-file-v2/) do Docker-Compose.

As configurações mais relevantes são listadas como a seguir:

* build: o contexto e os atributos do dockerfile são desnecessários aqui porque eles são os valores padrão, mas podem ser substituídos nesse formato. O atributo de contexto define o caminho para o nome do Dockerfile especificado no atributo dockerfile.

* tty: especificando esse atributo, os contêineres podem continuar em execução e não sair imediatamente. Isso é necessário para o suporte do Docker-Compose.

* command: esse atributo especifica o comando a ser executado dentro dos contêineres.

* image e container_name: esses atributos especificam o nome da imagem e dos contêineres, respectivamente.


