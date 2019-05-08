---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, cloud foundry, environment, service, credential, vcap_services

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Serviceberechtigungsnachweise Ihrer Cloud Foundry-Umgebung hinzufügen
{: #add-credentials-cf}

Hier erfahren Sie, wie Sie Serviceberechtigungsnachweise Ihrer Cloud Foundry-Bereitstellungsumgebung hinzufügen. Diese Anweisungen gelten sowohl für [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) als auch für [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee).
{: shortdesc}

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können. Weitere Informationen zur Migration auf `appdomain.cloud` finden Sie im Abschnitt zum [Aktualisieren Ihrer Domäne](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

## Ihr Code + Cloud Foundry
{: #credentials-byoc-cf}

Im Cloud Foundry-Bereich, in dem sich Ihre Anwendung befindet, können Sie definieren, was bei Cloud Foundry als vom Benutzer zur Verfügung gestellter Service bezeichnet wird. Ein vom Benutzer zur Verfügung gestellter Service ist in Zeichenfolge konvertiertes JSON, gespeichert wie ein bindefähiger Service im Cloud Foundry-Bereich. Führen Sie die folgenden Schritte aus, um einen Service zu erstellen und zu binden, nachdem Sie sich angemeldet und eine Verbindung zu Cloud Foundry-Organisation und -Bereich hergestellt haben.

1. Erstellen Sie einen vom Benutzer zur Verfügung gestellten Service, indem Sie den folgenden Befehl ausführen:
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. Konfigurieren Sie Ihre Cloud Foundry-Anwendung durch eine Hinzufügung zum Abschnitt "services" so, dass sie an den vom Benutzer zur Verfügung gestellten Service gebunden wird:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. Codieren Sie Ihre Anwendung so, dass sie die Umgebung für eine Umgebungsvariable `VCAP_SERVICES` liest, parsen Sie sie in JSON und suchen Sie den Berechtigungsnachweis, den Sie benötigen (node.js-ähnlicher Pseudocode):
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## Starter-Kit-App + Cloud Foundry
{: #credentials-starterkit-cf}

### Vorbereitung des Cloud Foundry-Bereichs

Verwenden Sie die Funktion **Continuous Delivery konfigurieren**, um Ihre App in Ihrem Cloud Foundry-Bereich bereitzustellen.

Wenn sich die Cloud Foundry-basierte Serviceinstanz im selben Cloud Foundry-Bereich wie die bereitgestellte Cloud Foundry-Anwendung befindet, lesen Sie den [nächsten Abschnitt](/docs/apps?topic=creating-apps-add-credentials-cf).

Wenn sich die Cloud Foundry-basierte Serviceinstanz in einem anderen Bereich als der Zielbereich für die Cloud Foundry-Anwendung befindet, lesen Sie den [folgenden Abschnitt](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different).

Wenn der Service, den Sie Ihrer Anwendung zugeordnet haben, Resource Controller-basiert ist, lesen Sie den Abschnitt [Resource Controller](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller).

#### Der Cloud Foundry-basierte Service befindet sich im selben Bereich wie die bereitgestellte App
{: #cf_resource_same}

Wenn der Service, den Sie Ihrer Anwendung zugeordnet haben, Cloud Foundry-basiert ist, ist der Service in Cloud Foundry "bindefähig". Sie können den Service in Ihrem Cloud Foundry-Bereich sehen, wenn Sie Ihre Befehlszeile `cf` mit der/dem richtigen Region + Organisation + Bereich verbinden. Sie können erkennen, ob der Service zum Zeitpunkt der Serviceerstellung Cloud Foundry-basiert ist, wenn Sie gefragt wurden, in welcher Cloud Foundry-Organisation und welchem Cloud Foundry-Bereich der Service erstellt werden soll.

Sie können gebundene Anwendungen anzeigen, indem Sie den folgenden Befehl ausführen:
```console
cf services
```
{: codeblock}

Beispielausgabe:
```
Abrufen von Services in Organisation test_user@us.ibm.com / Bereich dev als test_user@us.ibm.com...

Name                                   Service             Plan              Gebund. Apps   Letzte Operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                  Erstellen war erfolgreich
```
{: screen}

#### Der Cloud Foundry-basierte Service befindet sich in einem anderen Bereich als die bereitgestellte App
{: #cf_resource_different}

Cloud Foundry unterstützt nicht das "Binden" einer Cloud Foundry-Anwendung an einen Cloud Foundry-Service, wenn sich die Anwendung und der Service in unterschiedlichen Cloud Foundry-Bereichen befinden. Der Cloud Foundry-Bereich muss mit "vom Benutzer bereitgestellten" Services vorbereitet werden, und der folgende Abschnitt ist zutreffend.

#### Der Resource Controller-basierte Service ist Ihrer App zugeordnet
{: #cf_resource_controller}

Wenn der Service, den Sie Ihrer Anwendung zugeordnet haben, Resource Controller-basiert ist, ist der Service in Cloud Foundry _nicht_ "bindefähig". Sie können erkennen, ob er zum Zeitpunkt der Serviceerstellung Resource Controller-basiert ist, wenn Sie gefragt wurden, in welcher Ressourcengruppe der Service erstellt werden soll. Der Cloud Foundry-Bereich muss mit Serviceberechtigungsnachweisen vorbereitet werden, damit die Anwendung sie im Code referenzieren kann. Die Vorbereitung wird automatisch für Sie durchgeführt, und Sie können die Ergebnisse der Bereichsvorbereitung sehen, indem Sie die Befehlszeile `cf` durch Ausführung des folgenden Befehls mit Ihrem Bereich verbinden:
```console
cf services
```
{: codeblock}

Beispielausgabe:
```
Abrufen von Services in Organisation test_user@us.ibm.com / Bereich dev als test_user@us.ibm.com...

Name                                   Service              Plan              Gebund. Apps   Letzte Operation
blarg-cloudant-1538408663553           v. Benutzer bereitg.
```
{: screen}

Cloud Foundry erlaubt nicht die Sichtbarkeit des Werts von Serviceberechtigungsnachweisen, ob codiert oder nicht, für die Befehlszeile `cf service` oder `cf services`. Funktional ist ein vom Benutzer zur Verfügung gestellter Service in Zeichenfolge konvertiertes JSON, definiert als benannte "Serviceinstanz" in Ihrem Cloud Foundry-Bereich. Damit die Werte sichtbar werden, müssen Sie zuerst eine Anwendung an den Cloud Foundry-Service binden, indem Sie den Namen der Serviceinstanz in der Datei `manifest.yml` der App unter der Überschrift `services` angeben. Führen Sie dann die App im Cloud Foundry-Bereich aus und rufen Sie die Umgebung dieser Anwendung ab, indem Sie `cf env $APP_NAME` ausführen.

Erfreulicherweise wird der Code, der von einem Starter-Kit generiert wird, automatisch mit den korrekten Bindungen für das Abrufen und Verwenden der Werte aus der Umgebung bestückt, die für ihn im Cloud Foundry-Bereich, in dem die Anwendung ausgeführt wird, definiert ist.

### Vom Starter-Kit generierter Code
{: #starterkit-generated-code-cf}

Lesen Sie [Starter-Kit-App + Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode), bevor Sie fortfahren. Führen Sie dann die folgende Änderung durch:

* Obwohl der generierte Code die Datei `deployment.yml` bereitstellt, ist sie für eine Anwendung, die in Cloud Foundry bereitgestellt wird, nicht anwendbar. Die Datei `manifest.yml` _ist_ dagegen anwendbar, und ihr Inhalt zeigt im Folgenden eine _Bindung_ an die beiden Services, die im Cloud Foundry-Bereich erstellt werden:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

Der Rest der Dokumentation aus dem vorhergehenden Unterabschnitt findet erneut Anwendung. Die Bibliothek `IBMCloudEnv` abstrahiert das Abrufen der Werte aus der Umgebung, in der die Anwendung ausgeführt wird.

Die Bibliothek abstrahiert etwas Komplexität beim Abrufen von Umgebungswerten aus Cloud Foundry. In Cloud Foundry wird eine aktive Anwendung mit einer Umgebungsvariablen `VCAP_SERVICES` bereitgestellt, deren Wert in Zeichenfolge konvertiertes JSON ist und die die Werte für gebundene Serviceberechtigungsnachweise enthält, unabhängig davon, ob der Service eine Serviceinstanz _im_ Cloud Foundry-Bereich ist oder es sich um einen benutzerdefinierten Servicewert handelt. Die Schlüssel der höchsten Ebene im geparsten JSON aus der Umgebungsvariablen `VCAP_SERVICES` sind die Cloud Foundry-`Bezeichnung` (label), die den Cloud Foundry-basierten Services zugeordnet ist, und der Schlüssel `vom Benutzer bereitgestellt` (user-provided), dessen Wert ein Array von Berechtigungsnachweisen für alle vom Benutzer bereitgestellten Services enthält.
