---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Distribuzione delle applicazioni
{: #deploying-apps}

Puoi distribuire le tue applicazioni con una toolchain o con la CLI (command-line interface). Una toolchain è un insieme di integrazioni dello strumento. La CLI è un modo semplice per distribuire le tue applicazioni e istanze del servizio.
{: shortdesc}

## Distribuzione di applicazioni mediante le toolchain
{: #toolchain-deploy-apps}

Le toolchain aperte sono disponibili negli ambienti pubblico e dedicato in {{site.data.keyword.Bluemix}}. Con una toolchain correttamente configurata, distribuire la tua applicazione è semplice. Un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository.

Puoi creare una toolchain in questi modi:
* Utilizza un template per creare una toolchain.
* Crea una toolchain da un'applicazione.

Per ulteriori informazioni sulle toolchain, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Distribuzione di applicazioni mediante la CLI
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} fornisce una solida CLI e i plug-in e le estensioni degli strumenti per sviluppatori che si integrano con la CLI.

Prima di iniziare, [scarica e installa la CLI {{site.data.keyword.cloud_notm}}](/docs/cli/index.html#overview).

<p>
<a class="xref" href="https://cloud.ibm.com/docs/cli/index.html#overview" target="_blank" title="(Si apre in una nuova scheda o finestra)"><img class="image" src="images/btn_bx_commandline.svg" alt="Scarica IBM Cloud Developer Tools" /></a>
</p>

La CLI non è supportata da Cygwin. Utilizza lo strumento in una finestra diversa da quella della riga di comando di Cygwin.
{: important}

  1. {: download} Scarica il codice per la tua applicazione in una nuova directory per configurare il tuo ambiente di sviluppo.

    <a class="xref" href="https://cloud.ibm.com" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Si apre in una nuova scheda o finestra)"></a>

  2. Passa alla directory in cui si trova il codice.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">la_tua_nuova_directory</var></code></pre>

  3.  Apporta le modifiche al codice della tua applicazione. Ad esempio, se stai utilizzando un'applicazione di esempio {{site.data.keyword.cloud_notm}} e la tua applicazione contiene il file `src/main/webapp/index.html`, puoi modificarlo e cambiare la riga `Thanks for creating ...`. Assicurati che l'applicazione venga eseguita localmente prima di distribuirla di nuovo a {{site.data.keyword.cloud_notm}}.

    Prendi nota del file `manifest.yml`. Quando ridistribuisci la tua applicazione a {{site.data.keyword.cloud_notm}}, questo file viene utilizzato per determinare l'URL, l'allocazione di memoria, il numero di istanze e altri parametri fondamentali della tua applicazione.

    Rivedi anche il file `README.md`, che contiene dettagli come le istruzioni di creazione, se applicabili.

  Se la tua applicazione è un'applicazione Liberty, devi crearla prima di distribuirla di nuovo.
  {: note}

  4. Collegati ed accedi a {{site.data.keyword.cloud_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">nomeutente</var> -o <var class="keyword varname" data-hd-keyref="org_name">nome_org</var> -s <var class="keyword varname" data-hd-keyref="space_name">nome_spazio</var></code></pre>

  Se utilizzi un ID federato, aggiungi l'opzione `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">nome_org</var> -s <var class="keyword varname" data-hd-keyref="space_name">nome_spazio</var> -sso</code></pre>

  Se il valore contiene uno spazio, devi aggiungere virgolette singole o doppie intorno a `nomeutente`, `nome_org` e `nome_spazio`, ad esempio `-o "my org"`.
  {: note}

  5. Dalla tua nuova directory, distribuisci la tua applicazione a {{site.data.keyword.cloud_notm}} utilizzando il comando `ibmcloud dev deploy`. Per ulteriori informazioni, vedi [la documentazione della CLI](/docs/cli/idt/commands.html#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">nome_app</var></code></pre>

  6. Accedi alla tua applicazione andando all'indirizzo https://<var class="keyword varname" data-hd-keyref="app_url">url_app</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
