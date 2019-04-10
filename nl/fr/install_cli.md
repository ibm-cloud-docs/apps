---

copyright:

  years: 2015，2017, 2018

lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:prereq: .prereq}
{:download: .download}
{:pre: .pre}
{:app_name: data-hd-keyref="app_name"}
{:app_key: data-hd-keyref="app_key"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:host: data-hd-keyref="host"}
{:org_name: data-hd-keyref="org_name"}
{:route: data-hd-keyref="route"}
{:space_name: data-hd-keyref="space_name"}
{:service_name: data-hd-keyref="service_name"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:user_ID: data-hd-keyref="user_ID"}
{:note: .note}

# Déploiement d'applications avec l'interface de ligne de commande

Utilisez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} pour déployer vos applications et instances de service.
{:shortdesc}

Avant de commencer, téléchargez et installez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}.

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(Ouverture dans un nouvel onglet ou une nouvelle fenêtre)"><img class="image" src="images/btn_bx_commandline.svg" alt="Télécharger l'interface de ligne de commande IBM Cloud" /> </a>
</p>

**Restriction :** l'outil de ligne de commande n'est pas pris en charge par Cygwin. Utilisez-le dans une fenêtre de ligne de commande autre que Cygwin.
{:prereq}

Une fois l'interface de ligne de commande installée, vous pouvez commencer :

  1. {: download} Téléchargez le code de votre application dans un nouveau répertoire afin de configurer votre environnement de développement.

    <a class="xref" href="http://bluemix.net" target="_blank" title="(Ouverture dans un nouvel onglet ou une nouvelle fenêtre)"><img class="image" src="images/btn_starter-code.svg" alt="Télécharger le code de l'application" /> </a>

  2. Placez-vous dans le répertoire dans lequel se trouve votre code.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">votre_nouveau_répertoire</var></code></pre>

  3.  Modifiez le code de votre application. Ainsi, si vous utilisez une application exemple {{site.data.keyword.Bluemix}} et qu'elle contient le fichier `src/main/webapp/index.html`, vous pouvez le modifier et éditer la chaîne "Thanks for creating ..." pour le remplacer par quelque chose d'autre. Vérifiez que l'application s'exécute localement avant de la déployer à nouveau dans {{site.data.keyword.Bluemix_notm}}.

    Tenez compte du fichier `manifest.yml`. Lorsque vous déployez à nouveau votre application dans {{site.data.keyword.Bluemix_notm}}, il est utilisé pour déterminer l'adresse URL de votre application, l'allocation de mémoire, le nombre d'instance et d'autres paramètres essentiels.

    Prêtez également attention au fichier `README.md`, qui contient des détails tels que les instructions de génération, le cas échéant.

    Si votre application est une application Liberty, vous devez la générer avant de la redéployer.{: note}

  4. Connectez-vous à {{site.data.keyword.Bluemix_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  Si vous utilisez un ID fédéré, utilisez l'option `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  Vous devez ajouter des apostrophes ou des guillemets autour des éléments `username`, `org_name` et `space_name`, si cette valeur contient un espace, `-o "my org"`, par exemple.
  {: note}

  5. A partir de <var class="keyword varname">votre_nouveau_répertoire</var>, redéployez votre application dans {{site.data.keyword.Bluemix_notm}} à l'aide de la commande `ibmcloud app push`. Pour plus d'informations sur la commande `ibmcloud app push`, voir [Téléchargement de votre application](/docs/starters/upload_app.html).

  <pre class="pre"><code class="hljs">ibmcloud app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Accédez à votre application via https://<var class="keyword varname" data-hd-keyref="app_url">url_app</var>.<span class="keyword" data-hd-keyref="APPDomain">nom_domaine_app</span>.
