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

# Mit einer Docker Compose-Datei beginnen
{: #compose-file}

Für Docker Compose-Apps stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden.
{:shortdesc}

Die [Docker Compose](https://docs.docker.com/compose/overview/)-Datei definiert Informationen zum Ausführen von Anwendungen mit mehreren Containern.

Geben Sie als Version der verwendeten Docker Compose-Datei mindestens 2.0 an: `version: '2'`

Sie müssen die Services auch definieren. Das folgende Beispiel stammt von einer Node-App:

```
services:
  web:
    build:
    	context: <pfad_zur-Dockerfile>
	dockerfile: <name_der_Dockerfile>
    tty: true
    command: npm run start-dev
    image: <imagename>
    container_name: <containername>
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

Als Services sind `web` und `mongo` definiert, deren jeweilige Konfiguration in der Docker Compose-[Dokumentation](https://docs.docker.com/compose/compose-file/compose-file-v2/) definiert ist.

Die relevantesten Konfigurationen sind wie folgt aufgelistet:

* `build`: Die Attribute 'context' und 'Dockerfile' sind hier nicht notwendig, weil es sich um die Standardwerte handelt, aber sie können in diesem Format überschrieben werden. Das Attribut 'context' definiert den Pfad zu dem Namen der in dem Attribut 'Dockerfile' angegebenen Dockerfile-Datei.

* `tty`: Bei der Angabe dieses Attributs können die Container weiterhin ausgeführt werden und werden nicht sofort beendet, was für die Docker Compose-Unterstützung erforderlich ist.

* `command`: Dieses Attribut gibt den Befehl an, der in den Containern ausgeführt werden soll.

* `image` und `container_name`: Diese Attribute geben jeweils die Namen des Images und der Container an.
