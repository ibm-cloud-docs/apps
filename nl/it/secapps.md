---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-26"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creazione di richieste di firma del certificato
{: #ssl_csr}

Puoi proteggere le tue applicazioni caricando dei certificati SSL e limitando l'accesso alle applicazioni.
{:shortdesc}

Prima di poter caricare i certificati SSL a cui hai diritto con {{site.data.keyword.Bluemix}}, devi creare una richiesta di firma del certificato, o CSR, sul tuo server.

Un CSR è un messaggio che viene inviato a un'autorità di certificazione per richiedere la firma di una chiave pubblica
e le informazioni associate. Più comunemente, i CSR sono in formato PKCS #10. Il CSR include una chiave pubblica, un nome comune, un'organizzazione, una città, uno stato, un paese ed una e-mail. Le richieste di certificato SSL
vengono accettate solo con una lunghezza di chiave CSR pari a 2048 bit.

## Informazioni obbligatorie

Affinché il CSR sia valido, durante la sua creazione è necessario immettere le seguenti informazioni:

### Nome paese

  Un codice a due cifre che rappresenta il paese o la regione. Ad esempio, "US" rappresenta gli Stati
Uniti. Per gli altri paesi o regioni, consulta l'[elenco di codici paese ISO ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.iso.org/obp/ui/#search){:new_window} prima di creare il CSR.

### Stato o provincia

  Il nome completo senza abbreviazioni dello stato o provincia.

### Località

  Il nome completo della città.

### Organizzazione

  Il nome completo dell'azienda o società, come legalmente registrata nella tua località, o il nome
personale. Per le società, assicurati di includere il suffisso di registrazione, ad esempio Ltd., Inc. o NV.

### Unità organizzativa

  Il nome della sezione della tua società che ordina il certificato, ad esempio Accounting o
Marketing.

### Nome comune

  Il nome di dominio completo (FQDN) per il quale stai richiedendo il certificato SSL.

I metodi per creare un CSR variano a seconda del tuo sistema operativo. Il seguente esempio mostra come creare un CSR utilizzando [lo strumento riga di comando OpenSSL ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.openssl.org/){:new_window}:

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```

L'implementazione OpenSSL SHA-512 dipende dal supporto del compilatore per il tipo intero a 64 bit. Puoi utilizzare
l'opzione SHA-1 per le applicazioni che presentano problemi di compatibilità con il certificato
SHA-256.
{: tip}

Un certificato viene emesso da un'autorità di
certificazione e viene firmato in maniera digitale da tale autorità. Dopo aver creato il CSR, puoi generare il tuo certificato SSL su un'autorità di certificazione pubblica.

## Caricamento di certificati SSL
{: #ssl_certificate}

Puoi applicare un protocollo di sicurezza per garantire la riservatezza
delle comunicazioni della tua applicazione in modo da prevenire l'intercettazione delle comunicazioni,
la manomissione e la falsificazione dei messaggi.

Per ogni organizzazione in {{site.data.keyword.Bluemix_notm}} con un proprietario di account che dispone di un piano di pagamento a consumo o di sottoscrizione, hai diritto al caricamento di quattro certificati. Per ogni organizzazione con un proprietario di account che dispone di un account di prova gratuita, devi eseguire un upgrade del tuo account per caricare un certificato.

Prima di poter caricare i certificati, devi creare una
richiesta di firma del certificato.

Quando utilizzi un dominio personalizzato, per servire il certificato SSL, utilizza i seguenti endpoint della regione per fornire la rotta URL assegnata alla tua organizzazione in {{site.data.keyword.Bluemix_notm}}:

  * Stati Uniti Sud: secure.us-south.bluemix.net
  * Stati Uniti Est: secure.us-east.bluemix.net
  * EU-DE: secure.eu-de.bluemix.net
  * EUROPA-REGNO UNITO: secure.eu-gb.bluemix.net
  * AUSTRALIA-SYDNEY: secure.au-syd.bluemix.net


Per caricare un certificato per la tua applicazione:

1. Vai al tuo dashboard.

2. Seleziona la tua applicazione per aprire la vista dei dettagli ad essa relativa.

3. Seleziona l'elenco a discesa **Rotte** e quindi, nella colonna delle azioni per la tua organizzazione seleziona **Domini** dal menu di azioni aggiuntive.

3. Per il tuo dominio personalizzato, fai clic su **Carica certificato**.

4. Sfoglia per caricare un certificato, una chiave privata e, facoltativamente, un certificato intermedio o un certificato client. Per abilitare il truststore certificato client, devi caricare un file truststore certificato client che definisce l'accesso utente consentito al tuo dominio personalizzato.

  #### Certificato

    Un documento digitale che esegue il bind di una chiave pubblica all'identità del proprietario del certificato,
consentendo così al proprietario del certificato di essere autenticato. Un certificato viene emesso da un'autorità di
certificazione e viene firmato in maniera digitale da tale autorità.

    Un certificato viene in genere emesso e firmato da un'autorità di certificazione. Tuttavia, per scopi di test e di sviluppo, puoi utilizzare un certificato autofirmato.

    In {{site.data.keyword.Bluemix_notm}} sono supportati i seguenti tipi di certificati:

	* PEM (pem, .crt, .cer e .cert)
	* DER (.der o .cer )
	* PKCS #7 (p7b, p7r, spc)

  #### Chiave privata

    Un modello algoritmico utilizzato per crittografare messaggi che possono essere decrittografati
solo mediante la chiave pubblica corrispondente. Inoltre, la chiave privata viene utilizzata per decrittografare i messaggi crittografati con la chiave pubblica corrispondente. La chiave privata è conservata sul sistema dell'utente e protetta da password.

    In
{{site.data.keyword.Bluemix_notm}} sono supportati i seguenti tipi di chiavi private:

    * PEM (pem, .key)
    * PKCS #8 (p8, pk8)

    **Limitazione:** non è possibile caricare le chiavi private protette da una passphrase.

  #### Certificato intermedio

    Un certificato subordinato emesso dall'autorità di certificazione (CA) radice attendibile
specificamente per emettere certificati server per l'entità finale. Il risultato è una catena di certificati
che inizia dalla CA radice attendibile, passa per quello intermedio e termina con il certificato SSL emesso per l'organizzazione.

    Devi utilizzare un certificato intermedio per verificare l'autenticità del certificato principale. I certificati intermedi vengono generalmente ottenuti da una terza parte attendibile. Potresti non aver bisogno
di un certificato intermedio durante il test della tua applicazione, prima della sua distribuzione nella produzione.

  #### Abilita richiesta di certificato client

    Se abiliti questa opzione caricando un file truststore certificato client, a un utente che prova ad accedere a un dominio protetto da SSL viene richiesto di fornire un certificato lato client. Ad esempio, in un browser web, quando un utente prova ad accedere a un dominio protetto da SSL,
il browser web gli richiede di fornire un certificato client per il dominio. Utilizza l'opzione di caricamento file **Truststore certificato client** per definire i certificati lato client a cui consenti di accedere al tuo dominio personalizzato.

  **Nota:** la funzione relativa al certificato personalizzato nella gestione del dominio di {{site.data.keyword.Bluemix_notm}} dipende dall'estensione SNI (Server Name Indication) del protocollo TLS (Transport Layer Security). Pertanto, il codice client che accede alle applicazioni {{site.data.keyword.Bluemix_notm}} protette da certificati personalizzati deve supportare l'estensione SNI nell'implementazione TLS. Per ulteriori informazioni, vedi la [sezione 7.4.2 di RFC 4346 ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} e [Securing data with TLS](/docs/get-support/appsectls.html).

  #### Truststore certificato client

  Il truststore certificato client è un file che contiene i certificati client per gli utenti a cui desideri consentire l'accesso alla tua applicazione. Se abiliti l'opzione di richiesta di un certificato client, carica un file truststore certificato client.

   In {{site.data.keyword.Bluemix_notm}} sono supportati i seguenti tipi di certificati:

      * PEM (pem, .crt, .cer e .cert)
      * PKCS #7 (p7b, p7r, spc)

Per ulteriori informazioni, consulta [Importazione di certificati SSL](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate).

Per eliminare un certificato o sostituire un certificato esistente con uno nuovo, vai a **Gestisci** > **Account** > **Organizzazioni Cloud Foundry**. Fai quindi clic su **Visualizza dettagli** > **Modifica organizzazione** > **Domini**. Nel menu delle azioni aggiuntive per l'organizzazione, fai clic su **Rimuovi dall'organizzazione**.
