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

# Starting with a Docker Compose file
{: #compose-file}

For Docker Compose apps, the following information is an inventory of what you typically find in {{site.data.keyword.Bluemix}}. When you create a starter kit, these files are created for you. If you're migrating an app to host in {{site.data.keyword.Bluemix_notm}}, you might want to review this information to avoid potential conflicts.
{:shortdesc}

The [Docker Compose](https://docs.docker.com/compose/overview/) file defines information for running multi-container applications.

Specify the version of Docker Compose file that is used to be 2.0 or later: `version: '2'`

You also need to define the services. The following example is from a Node app:

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

The services `web` and `mongo` are defined and each of them has configurations, which are defined in the Docker Compose [documentation](https://docs.docker.com/compose/compose-file/compose-file-v2/).

The most relevant configurations are listed as follows:

* `build`: The context and Dockerfile attributes are unnecessary here because they're the default values, but can be overwritten in this format. The context attribute defines the path to the name of the Dockerfile that is specified in the Dockerfile attribute.

* `tty`: By specifying this attribute, the containers can continue to run and don't immediately exit, which is required for Docker Compose support.

* `command`: This attribute specifies the command to be run inside the containers.

* `image` and `container_name`: These attributes specify the names of the image and containers.