---

copyright:
  years: 2015, 2019
lastupdated: "2019-07-25"

keywords: apps, application, ssl, certificates, access, restrict access, create, csr, upload, import

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Création de demandes de signature de certificat
{: #ssl_csr}

Vous pouvez sécuriser vos applications en téléchargeant des certificats SSL et en limitant l'accès aux applications.
{: shortdesc}

## Création d'une demande de signature de certificat
{: #create_csr}

Pour pouvoir télécharger les certificats SSL pour lesquels vous disposez d'une habilitation dans {{site.data.keyword.cloud}}, vous devez créer une demande de signature de certificat sur votre serveur. Une demande de signature de certificat est un message qui est envoyé à une autorité de certification afin de demander la signature d'une clé publique et des informations associées. En général, les demandes de signature de certificat sont au format PKCS #10. Une demande de signature de certificat inclut une clé publique, un nom usuel, une organisation, une ville, un état, un pays et une adresse électronique. Les demandes de certificat SSL ne sont acceptées qu'avec une longueur de clé de demande de signature de certificat de 2048 bits.

Les méthodes de création d'une demande de signature de certificat varient selon le système d'exploitation. L'exemple suivant présente comment créer une demande de signature de certificat à l'aide de l'[outil de ligne de commande OpenSSL](https://www.openssl.org/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") :

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privatekey.key
```
{: codeblock}

L'implémentation d'OpenSSL SHA-512 dépend du support de compilateur pour le type entier 64 bits. Vous pouvez utiliser l'option SHA-1 pour les applications qui présentent des problèmes de compatibilité avec le certificat SHA-256.
{: tip}

### Contenu requis de la demande de signature de certificat

Pour que la demande de signature de certificat soit valide, les informations suivantes doivent être indiquées lors de sa création :

 * **Nom du pays** : Code à deux chiffres du pays ou de la région. Par exemple, `US` est le code pays des Etats-Unis d'Amérique. Pour les autres pays ou régions, reportez-vous à la [liste des codes de pays ISO ](https://www.iso.org/obp/ui/#search){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") avant de créer la demande de signature de certificat.
 * **Etat ou province** : Nom complet non abrégé de l'état ou de la province.
 * **Localité** : Nom complet de la ville ou métropole.
 * **Organisation** : Nom complet de l'entreprise ou de la société tel qu'il est légalement enregistré dans votre localité, ou votre nom. Pour les sociétés, veillez à inclure le suffixe SARL, EURL ou SCI, par exemple.
 * **Unité organisationnelle** : le nom de la division de votre entreprise qui commande le certificat, comme par exemple le département de comptabilité ou de marketing.
 * **Nom usuel** : Nom de domaine complet pour lequel vous demandez le certificat SSL.

Vous pouvez utiliser des noms alternatifs (SAN) mais les noms d'hôte fournis ne doivent pas être émis dans d'autres certificats déployés et ce afin d'éviter des collisions de nom commun.
{: note}

Un certificat est émis par un organisme de certification et il est signé numériquement par cet organisme. Après avoir créé la demande de signature de certificat, vous pouvez générer votre certificat SSL auprès d'une autorité de certification publique.

## Téléchargement de certificats SSL
{: #ssl_certificate}

Vous pouvez appliquer un protocole de sécurité pour garantir la confidentialité des communications avec votre application et empêcher les écoutes clandestines, les altérations et les falsifications de messages. Si vous disposez d'un compte Lite, vous devez mettre à niveau votre compte pour télécharger un certificat.

Lorsqu'un certificat qui a expiré ou arrive à expiration doit être renouvelé, et lorsque le nouveau certificat est prêt, supprimez le certificat existant et ajoutez le nouveau.
{: note}

Lorsque vous utilisez un domaine personnalisé pour servir le certificat SSL, utilisez les noeuds finals de région suivants afin de fournir la route d'URL de votre organisation dans {{site.data.keyword.cloud_notm}} :

| Région | Noeud final |
| ------ | -------- |
| Sud des Etats-Unis | `custom-domain.us-south.cf.cloud.ibm.com` |
| Est des Etats-Unis | `custom-domain.us-east.cf.cloud.ibm.com` |
| UE - Allemagne | `custom-domain.eu-de.cf.cloud.ibm.com` |
| UE - Royaume-Uni | `custom-domain.eu-gb.cf.cloud.ibm.com` |
| Australie - Sydney | `custom-domain.au-syd.cf.cloud.ibm.com` | 
{: caption="Tableau 1. Noeuds finaux de région de domaine personnalisé Cloud Foundry" caption-side="top"}

Pour télécharger un certificat pour votre application Cloud Foundry, procédez comme suit :

1. Depuis la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur l'icône **Menu** ![Icône Menu](../icons/icon_hamburger.svg) et sélectionnez **Liste de ressources**.
2. Cliquez sur **Applications Cloud Foundry**.
3. Cliquez sur l'application pour laquelle vous voulez changer le domaine. 
4. Sur la page Détails de l'application, cliquez sur **Routes** et sélectionnez **Gestion des domaines**.
5. Dans la colonne Actions, cliquez sur l'icône Actions ![Icône Plus d'actions](../icons/action-menu-icon.svg) puis sélectionnez **Domaines**.
6. Cliquez sur **Télécharger** pour votre domaine personnalisé.
7. Sélectionnez une option puis cliquez sur **Ajouter**.
  
  * Certificat - Document numérique qui associe une clé publique à l'identité du propriétaire du certificat, permettant ainsi l'authentification de ce dernier. Un certificat est émis par un organisme de certification et il est signé numériquement par cet organisme. En général, un certificat est émis et signé par une autorité de certification. Toutefois, pour le test et le développement, vous pouvez utiliser un certificat autosigné.
  * Clé privée - Modèle algorithmique utilisé pour chiffrer des messages que seule la clé publique correspondante peut déchiffrer. La clé privée sert également à déchiffrer les messages encodés par la clé publique correspondante. Elle est conservée sur le système de l'utilisateur et protégée par un mot de passe.
  * Certificat intermédiaire (facultatif) - Certificat subordonné émis par l'autorité de certification racine accréditée spécifiquement pour émettre des certificats serveur d'entité de fin. Le résultat est une chaîne de certificats qui débute à l'autorité de certification racine accréditée, continue avec le certificat intermédiaire et se finit par le certificat SSL émis pour l'organisation. Utilisez un certificat intermédiaire pour vérifier l'authenticité du certificat principal. Les certificats intermédiaires sont généralement obtenus auprès d'un tiers digne de confiance. Vous n'aurez peut-être pas besoin de certificat intermédiaire si vous testez votre application avant de la déployer en production.
  * Activer la demande de certificat client - Lorsque vous activez cette option, un utilisateur qui tente d'accéder à un domaine protégé par SSL doit fournir un certificat côté client. Par exemple, dans un navigateur Web, lorsqu'un utilisateur tente d'accéder à un domaine protégé par SSL, le navigateur Web invite l'utilisateur à fournir un certificat client pour le domaine.   
  * Fichier de clés certifiées de certificat client (facultatif) - Inclut les certificats client pour les utilisateurs que vous désirez autoriser à accéder à votre application. Téléchargez un fichier de ce type pour pouvoir demander un certificat client.
  
    Vous pouvez configurer l'authentification mutuelle en téléchargeant un fichier de clés certifiées de certificat client incluant une clé publique dans ses métadonnées.
    {: tip}


