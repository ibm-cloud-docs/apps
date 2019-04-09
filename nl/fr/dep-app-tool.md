---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Déploiement d'applications
{: #deploying-apps}

Vous pouvez déployer vos applications avec une chaîne d'outils ou l'interface de ligne de commande (CLI). Une chaîne d'outils est un ensemble d'intégrations d'outils. L'interface de ligne de commande constitue un moyen simple de déployer vos applications et vos instances de service.
{: shortdesc}

## Déploiement d'applications en utilisant des chaînes d'outils
{: #toolchain-deploy-apps}

Des chaînes d'outils ouvertes sont disponibles dans les environnements {{site.data.keyword.Bluemix}} Public et Dédié. Avec une chaîne d'outils correctement configurée, le déploiement de votre application devient un jeu d'enfants. Un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel.

Vous pouvez créer une chaîne d'outils d'une des manières suivantes :
* En utilisant un modèle pour créer une chaîne d'outils.
* En créant une chaîne d'outils à partir d'une application.

Pour en savoir plus sur les chaînes d'outils, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Déploiement d'applications en utilisant l'interface de ligne de commande
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} fournit une interface de ligne de commande robuste, ainsi que des plug-in et des extensions d'outil de développement qui s'intègrent à l'interface de ligne de commande.

Avant de commencer, [téléchargez et installez l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli/index.html).

L'interface de ligne de commande n'est pas prise en charge par Cygwin. Utilisez l'outil dans une fenêtre autre que la fenêtre de ligne de commande Cygwin.
{: important}

  1. {: download} Téléchargez le code de votre application dans un nouveau répertoire afin de configurer votre environnement de développement.

    <a class="xref" href="https://cloud.ibm.com" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Ouverture dans un nouvel onglet ou une nouvelle fenêtre)"></a>

  2. Placez-vous dans le répertoire dans lequel se trouve votre code.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Modifiez le code de votre application. Par exemple, si vous utilisez un exemple d'application {{site.data.keyword.cloud_notm}} qui contient le fichier `src/main/webapp/index.html`, vous pouvez le modifier et éditer la ligne `"Thanks for creating ..."`. Vérifiez que l'application s'exécute localement avant de la déployer à nouveau dans {{site.data.keyword.cloud_notm}}.

    Tenez compte du fichier `manifest.yml`. Lorsque vous déployez à nouveau votre application dans {{site.data.keyword.cloud_notm}}, il est utilisé pour déterminer l'adresse URL de votre application, l'allocation de mémoire, le nombre d'instance et d'autres paramètres essentiels.

    Consultez également le fichier `README.md`, qui contient des informations, telles que les instructions de génération.

  Si votre application est une application Liberty, vous devez la générer avant de la redéployer.
  {: note}

  4. Connectez-vous à {{site.data.keyword.cloud_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  Si vous utilisez un ID fédéré, utilisez l'option `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  Si la valeur contient un espace, vous devez ajouter des apostrophes ou des guillemets autour des éléments `username`, `org_name` et `space_name`. Par exemple, `-o "my org"`.
  {: note}

  5. A partir du nouveau répertoire, déployez votre application dans {{site.data.keyword.cloud_notm}} en utilisant la commande `ibmcloud dev deploy`. Pour plus d'informations, voir la [documentation concernant l'interface CLI](/docs/cli/idt/commands.html#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Accédez à votre application via https://<var class="keyword varname" data-hd-keyref="app_url">url_app</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
