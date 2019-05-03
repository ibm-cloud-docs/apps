---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, deploying apps, containers, kubernetes, docker, clusters, devops toolchain, deployment, kube

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Utilizzo di contenitori con Kubernetes
{: #containers-kube}

Inizia a utilizzare {{site.data.keyword.containershort}} distribuendo applicazioni altamente disponibili nei contenitori Docker eseguiti nei cluster Kubernetes. Gestisci lo sviluppo del tuo team con Git e utilizza quindi la toolchain DevOps per gestire la distribuzione della tua applicazione su Kubernetes.
{: shortdesc}

I contenitori rappresentano un modo standard per assemblare le applicazioni e tutte le relative dipendenze in modo da poter spostare facilmente le applicazioni tra gli ambienti. A differenza delle macchine virtuali, i contenitori non includono il sistema operativo. Nei contenitori vengono riuniti solo il codice dell'applicazione, il runtime, gli strumenti di sistema, le librerie e le impostazioni. I contenitori sono più leggeri, portatili ed efficienti rispetto alle macchine virtuali.

Vedi [Introduzione a {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-container_index) per ulteriori informazioni sul servizio.

## Configurazione delle distribuzioni
{: #config-deploy}

Quando crei applicazioni di back-end o web-serving, puoi distribuirle al servizio {{site.data.keyword.containershort_notm}}, che utilizza l'ambiente Kubernetes.

1. Distribuisci la tua applicazione al cloud impostando una pipeline cloud automatizzata.
2. Fai clic su **Configure continous delivery**.
3. Seleziona **IBM Kubernetes Service** come destinazione. Se non ne hai già uno, dovrai [creare un cluster ](https://{DomainName}/kubernetes/catalog/cluster/create){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno").
4. Una volta completata la distribuzione, controlla la tua applicazione operativa nel cloud recuperando l'URL nei log dalla fase di distribuzione della pipeline di fornitura. L'ultimo indirizzo IP con una porta è la nuova home della tua applicazione, ad esempio, 169.60.133.124:32355.

## Bind di servizi
{: #bind-services}

Quando viene creata la toolchain, i servizi che hai associato alla tua applicazioni vengono collegati al cluster Kubernetes utilizzando i segreti Kubernetes. I segreti vengono utilizzati per gestire le credenziali del servizio al di fuori della tua applicazione in esecuzione. L'applicazione legge i segreti e quindi richiama i valori di cui ha bisogno per avviare l'esecuzione. Il bind dei servizi ti consente di distribuire l'applicazione in un altro ambiente Kubernetes che potrebbe utilizzare istanze del servizio {{site.data.keyword.cloud}} a livello di produzione.

Se elimini il servizio o i segreti, devi ricollegarli manualmente o eliminare e ricreare la toolchain.
{: tip}

Per ulteriori informazioni, vedi [Secreti ](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno").

## Avvio dello sviluppo
{: #dev}

1. Controlla il tuo nuovo repository Git online dalla toolchain e inizia a lavorare con il tuo codice. Per visualizzare la toolchain, fai clic su **View toolchain**.
2. Accedi al repository Git in cui è stato creato il codice clonando il repository sul tuo ambiente locale.
3. Apri il progetto con il tuo IDE preferito.

## Creazione e distribuzione con una toolchain
{: #bulid-deploy-tc}

La toolchain contiene la fase di creazione e la fase di distribuzione.

### Fase di creazione
{: #build-stage}
La fase di creazione viene attivata quando si esegue un `git push` sul repository Git. La fase nella pipeline attiva la creazione dell'immagine docker e inserisce l'immagine nel registro del contenitore.

Per ulteriori informazioni, vedi [Introduzione a IBM Cloud Container Registry](/docs/services/Registry?topic=registry-index).

### Fase di distribuzione
{: #deploy-stage}

La fase di distribuzione richiama l'immagine più recente da {{site.data.keyword.registryshort_notm}} e la distribuisce quindi nel cluster Kubernetes utilizzando un grafico Helm. Il grafico Helm è stato aggiunto alla tua applicazione quando hai effettuato la distribuzione nel cloud. I grafici Helm facilitano la gestione dei passi di distribuzione dell'immagine del contenitore assemblato.

Per ulteriori informazioni, vedi [Grafici ](https://docs.helm.sh/developing_charts/){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno").

{{site.data.keyword.cloud_notm}} supporta diversi [grafici Helm preconfigurati ](https://{DomainName}/kubernetes/solutions/helm-charts){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno").

## Controllo della sicurezza delle applicazioni
{: #sec}

{{site.data.keyword.containershort_notm}} supporta la scansione delle immagini del contenitore assemblato per le vulnerabilità di sicurezza. La scansione di sicurezza è essenziale per supportare le applicazioni di livello aziendale.

Visualizza il [repository di immagini ](https://{DomainName}/kubernetes/registry/main/private){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno") per verificare la presenza di potenziali vulnerabilità di sicurezza.
