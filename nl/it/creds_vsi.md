---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Aggiunta di credenziali al tuo ambiente docker locale o di istanza virtuale
{: #add-credentials-vsi}

Acquisisci informazioni su come aggiungere delle credenziali di servizio al tuo ambiente di distribuzione docker locale o di VSI (Virtual Server Instance).
{: shortdesc}

## Il tuo codice + VSI (Virtual Server Instance) o docker locale
{: #credentials-byoc-vsi}

Nella VSI o nel docker locale, l'ambiente è interamente tuo. Ad esempio puoi scrivere il tuo codice, come il seguente esempio, e fornire un valore di ambiente della credenziale alla tua applicazione quando la esegui.
```
password = getEnvironment('password');
```
{: codeblock}

In Bash, puoi scrivere il tuo codice come il seguente esempio:
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

In Docker, puoi scrivere il tuo codice come il seguente esempio:
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Kit starter + VSI (o Docker locale)
{: #credentials-starterkit-vsi}

### Come viene preparata l'istanza del server virtuale (o VSI, Virtual Server Instance)

L'ambiente è interamente sotto il tuo controllo, come se stessi eseguendo l'applicazione dal tuo notebook. In altre parole, Docker locale. Poiché la VSI è effettivamente bare metal, dalla prospettiva dell'applicazione in esecuzione, non esistono _segreti_ (come in Kubernetes) o _servizi_ (come in Cloud Foundry).

### Il codice generato dal kit starter
{: #starterkit-generated-code-vsi}

Il codice generato da un kit starter ha la libreria `IBMCloudEnv` nativa, che astrae il richiamo dei valori di ambiente in modo che il codice dell'applicazione sia portatile per l'esecuzione su diverse distribuzioni di destinazione. Con Docker virtuale o locale, tale ambiente deve essere preparato con i valori che soddisfano la libreria `IBMCloudEnv` che _non provengono necessariamente_ da variabili di ambiente effettive.

Per tua comodità, le istruzioni `mappings.json` incluse con l'output generato dal kit starter hanno dei riferimenti a un file locale da cui la libreria `IBMCloudEnv` deriva i valori che l'applicazione può utilizzare.

Nota, ad esempio, l'ultima riga nella seguente sezione dal file `mappings.json`:
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

Se utilizzi la funzione "Deploy to Cloud" quando crei l'applicazione, il file `/server/localdev-config.json` viene rimosso dal repository GitLab. Per motivi di sicurezza, evita di inserire le tue credenziali in un repository di codice sorgente.

Se utilizzi `git clone` sul repository GitLab creato per avviare lo sviluppo attivo, nota che il file `.gitignore` ignora in modo specifico `server/localdev-config.json` per contribuire a prevenire l'inserimento accidentale di un file che ha delle credenziali sensibili. Tuttavia, la VSI _ha bisogno_ di quel file, così come ne ha bisogno lo sviluppatore che lavora su un notebook.

Puoi richiamare il file `server/localdev-config.json` completando la seguente procedura:

1. Utilizza `git clone` sul repository GitLab che era stato creato automaticamente quando hai utilizzato la funzione "Deploy to Cloud".
2. Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli/index.html#overview), che include il plug-in `dev`.
3. Utilizza la riga di comando `ibmcloud` per eseguire l'accesso a {{site.data.keyword.cloud_notm}}.
4. Esegui `ibmcloud dev get-credentials`, che fa riferimento al file `cli-config.yml`. Il file `cli-config.yml` include le informazioni relative a quale lavoro di generazione e applicazione ha le credenziali.

Se qualche risorsa viene rimossa dall'applicazione tra l'utilizzo della funzione "Deploy to Cloud" e `ibmcloud dev get-credentials`, il file scaricato `/server/localdev-config.json` non avrà tutte le credenziali che la tua base di codice `git clone` originale potrebbe richiedere.
{: tip}

Se stai eseguendo la tua applicazione in un contenitore Docker, potresti scegliere di rimuovere del tutto il file `/server/localdev-config.json` e passare le variabili di ambiente nella riga di comando Docker.

Continuando con la sezione "cloudant_apikey" dal file `mappings.json`, nota `env:cloudant_apikey` prima della riga `file...`. Significa che una variabile di ambiente denominata `cloudant_apikey` ha la precedenza sul contenuto del file. Quindi, anche se il file è presente nell'immagine Docker che hai creato (che non è obbligatoria), puoi sovrascrivere i valori passandoli nella riga di comando Docker.

Ad esempio:
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
