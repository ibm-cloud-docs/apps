---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-15"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Création de demandes de signature de certificat
{: #ssl_csr}

Vous pouvez sécuriser vos applications en créant et en téléchargeant des certificats SSL et en limitant l'accès aux applications.
{:shortdesc}

Pour pouvoir télécharger les certificats SSL pour lesquels vous disposez d'une habilitation dans {{site.data.keyword.cloud}}, vous devez créer une demande de signature de certificat sur votre serveur. Une demande de signature de certificat est un message qui est envoyé à une autorité de certification afin de demander la signature d'une clé publique et des informations associées. En général, les demandes de signature de certificat sont au format PKCS #10. Une demande de signature de certificat inclut une clé publique ainsi qu'un nom usuel, une organisation, une ville, un état, un pays et une adresse électronique. Les demandes de certificat SSL ne sont acceptées qu'avec une longueur de clé de demande de signature de certificat de 2048 bits.

## Création d'une demande de signature de certificat

Les méthodes de création d'une demande de signature de certificat varient selon le système d'exploitation. L'exemple suivant présente comment créer une demande de signature de certificat à l'aide de l'[outil de ligne de commande OpenSSL![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://www.openssl.org/){:new_window} :

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout
    privatekey.key
```
{: codeblock}

L'implémentation d'OpenSSL SHA-512 dépend du support de compilateur pour le type entier 64 bits. Vous pouvez utiliser l'option SHA-1 pour les applications qui présentent des problèmes de compatibilité avec le certificat SHA-256.
{: tip}

Un certificat est émis par un organisme de certification et il est signé numériquement par cet organisme. Après avoir créé la demande de signature de certificat, vous pouvez générer votre certificat SSL auprès d'une autorité de certification publique.

### Contenu requis de la demande de signature de certificat

Pour que la demande de signature de certificat soit valide, les informations suivantes doivent être indiquées lors de sa création :

<dl>
<dt>Nom du pays</dt>
<dd>Code à deux chiffres du pays ou de la région. Par exemple, `US` est le code pays des Etats-Unis d'Amérique. Pour les autres pays ou régions, reportez-vous à la [liste des codes de pays ISO ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.iso.org/obp/ui/#search) avant de créer la demande de signature de certificat.
</dd>
<dt>Département ou région</dt>
<dd>Nom entier non abrégé du département ou de la région.</dd>
<dt>Localité</dt>
<dd>Nom entier de la ville.</dd>
<dt>Organisation</dt>
<dd>Nom entier de l'entreprise ou de la société tel qu'enregistré juridiquement auprès de votre localité, ou votre nom. Pour les sociétés, veillez à inclure le suffixe d'enregistrement, par exemple SARL, EURL ou SCI.</dd>
<dt>Unité organisationnelle</dt>
<dd>Nom du service de votre société qui commande le certificat, par exemple Comptabilité ou Marketing.</dd>
<dt>Nom usuel</dt>
<dd>Nom de domaine complet pour lequel vous demandez le certificat SSL.</dd>
</dl>

## Téléchargement de certificats SSL
{: #ssl_certificate}

Vous pouvez appliquer un protocole de sécurité pour garantir la confidentialité des communications avec votre application et empêcher les écoutes clandestines, les altérations et les falsifications de messages Si votre propriétaire de compte dispose d'un compte Lite gratuit, vous devez mettre à niveau votre compte pour télécharger un certificat.

Lorsque vous utilisez un domaine personnalisé pour servir le certificat SSL, utilisez les noeuds finaux de région suivants afin de fournir la route d'URL de votre organisation dans {{site.data.keyword.cloud_notm}} :

* Etats-Unis (Sud) - `custom-domain.us-south.cf.cloud.ibm.com`
* Etats-Unis (Est) - `custom-domain.us-east.cf.cloud.ibm.com`
* EUROPE (ALLEMAGNE) - `custom-domain.eu-de.cf.cloud.ibm.com`
* EUROPE (ROYAUME-UNI) - `custom-domain.eu-gb.cf.cloud.ibm.com`
* AUSTRALIE (SYDNEY) - `custom-domain.au-syd.cf.cloud.ibm.com`

Pour télécharger un certificat pour votre application, procédez comme suit :

1. Accédez à la liste de vos ressources dans la console {{site.data.keyword.cloud_notm}}.

2. Sélectionnez votre application pour consulter les détails concernant cette dernière.

3. Cliquez sur **Routes** > **Gestion des domaines**.

4. Dans la colonne Actions, cliquez sur l'icône Actions ![Icône Plus d'actions](../icons/action-menu-icon.svg) > **Domaines**.

5. Cliquez sur **Télécharger** dans la colonne Certificat SSL puis sélectionnez votre domaine personnalisé :
  
  * Certificat - Document numérique qui associe une clé publique à l'identité du propriétaire du certificat, permettant ainsi l'authentification de ce dernier. Un certificat est émis par un organisme de certification et il est signé numériquement par cet organisme. En général, un certificat est émis et signé par une autorité de certification. Toutefois, pour le test et le développement, vous pouvez utiliser un certificat autosigné.
  * Clé privée - Modèle algorithmique utilisé pour chiffrer des messages que seule la clé publique correspondante peut déchiffrer. La clé privée permet également de déchiffrer les messages encodés par la clé publique correspondante. Elle est conservée sur le système de l'utilisateur et protégée par un mot de passe.
  * Certificat intermédiaire (facultatif) - Certificat subordonné émis par l'autorité de certification racine accréditée spécifiquement pour émettre des certificats serveur d'entité de fin. Le résultat est une chaîne de certificats qui débute à l'autorité de certification racine accréditée, continue avec le certificat intermédiaire et se finit par le certificat SSL émis pour l'organisation. Utilisez un certificat intermédiaire pour vérifier l'authenticité du certificat principal. Les certificats intermédiaires sont généralement obtenus auprès d'un tiers digne de confiance. Vous n'aurez peut-être pas besoin de certificat intermédiaire si vous testez votre application avant de la déployer en production.
  * Activer la demande de certificat client - Lorsque vous activez cette option, un utilisateur qui tente d'accéder à un domaine protégé par SSL doit fournir un certificat côté client. Par exemple, dans un navigateur Web, lorsqu'un utilisateur tente d'accéder à un domaine protégé par SSL, le navigateur Web invite l'utilisateur à fournir un certificat client pour le domaine. 

    La fonction de certificat personnalisé dans la gestion des domaines {{site.data.keyword.cloud_notm}} dépend de l'extension SNI (Server Name Indication) du protocole TLS (Transport Layer Security). Le code client qui accède aux applications {{site.data.keyword.cloud_notm}} protégées par des certificats personnalisés doit prendre en charge l'extension SNI dans l'implémentation TLS. Pour plus d'informations, voir la [section 7.4.2 du RFC 4346 ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://tools.ietf.org/html/rfc4346#section-7.4.2){:new_window} et [Sécurisation des données avec TLS](/docs/get-support/appsectls.html).
    {: note}
  
  * Fichier de clés certifiées de certificat client (facultatif) - Inclut les certificats client pour les utilisateurs que vous désirez autoriser à accéder à votre application. Téléchargez un fichier de ce type pour pouvoir demander un certificat client.
  
    Vous pouvez configurer l'authentification mutuelle en téléchargeant un fichier de clés certifiées de certificat client incluant une clé publique dans ses métadonnées.
    {: tip}

Pour plus d'informations, voir [Importation de certificats SSL](/docs/infrastructure/ssl-certificates/import-ssl-certificate.html#import-an-ssl-certificate).


