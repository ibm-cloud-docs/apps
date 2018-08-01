---
copyright:

  years: 2018

lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Déploiement d'applications
{: #deploy}

Vous pouvez déployer vos applications avec une chaîne d'outils ou une interface de ligne de commande. Une chaîne d'outils est un ensemble d'intégrations d'outils. L'interface de ligne de commande constitue un moyen simple de déployer vos applications et vos instances de service.
{: shortdesc}

## Déploiement d'applications avec des chaînes d'outils
{: #toolchains_getting_started}

Des chaînes d'outils ouvertes sont disponibles dans les environnements {{site.data.keyword.Bluemix}} Public et Dédié. Vous pouvez créer une chaîne d'outils de deux manières, soit  à l'aide d'un modèle, soit à partir d'une application. Pour en savoir plus sur les chaînes d'outils, voir [Création de chaînes d'outils](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

Avec une chaîne d'outils correctement configurée, le déploiement de votre application devient un jeu d'enfants : un cycle de création/déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel.

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.Bluemix}} sont configurées pour un déploiement automatique.
{: tip}

## Déploiement d'applications avec l'interface de ligne de commande
{: #cli}

IBM Cloud fournit une interface de ligne de commande robuste, ainsi que des plug-in et des extensions d'outil de développement qui s'intègrent à l'interface de ligne de commande.

Utilisez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} pour déployer vos applications et instances de service.
{:shortdesc}

Avant de commencer, [téléchargez et installez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}](/docs/cli/index.html).

<p>
<a class="xref" href="https://console.bluemix.net/docs/cli/index.html#overview" target="_blank" title="(Ouverture dans un nouvel onglet ou une nouvelle fenêtre)"><img class="image" src="images/btn_bx_commandline.svg" alt="Télécharger IBM Cloud Developer Tools" /></a>
</p>

**Restriction :** l'outil de ligne de commande n'est pas pris en charge par Cygwin. Utilisez-le dans une fenêtre de ligne de commande autre que Cygwin.
{:prereq}

Une fois l'interface de ligne de commande installée, vous pouvez commencer :

  1. {: download} Téléchargez le code de votre application dans un nouveau répertoire afin de configurer votre environnement de développement.

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Ouverture dans un nouvel onglet ou une nouvelle fenêtre)"></a>

  2. Placez-vous dans le répertoire dans lequel se trouve votre code.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Modifiez le code de votre application. Par exemple, si vous utilisez un exemple d'application {{site.data.keyword.Bluemix_notm}} qui contient le fichier `src/main/webapp/index.html`, vous pouvez le modifier et éditer "Thanks for creating ..." pour indiquer un nouveau contenu. Vérifiez que l'application s'exécute localement avant de la déployer à nouveau dans {{site.data.keyword.Bluemix_notm}}.

    Tenez compte du fichier `manifest.yml`. Lorsque vous déployez à nouveau votre application dans {{site.data.keyword.Bluemix_notm}}, il est utilisé pour déterminer l'adresse URL de votre application, l'allocation de mémoire, le nombre d'instance et d'autres paramètres essentiels.

    Prêtez également attention au fichier `README.md`, qui contient des détails tels que les instructions de génération, le cas échéant.

    Remarque : Si votre application est une application Liberty, vous devez la générer avant de la redéployer.

  4. Connectez-vous à {{site.data.keyword.Bluemix_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  Si vous utilisez un ID fédéré, utilisez l'option `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **Remarque **: si la valeur contient un espace, vous devez ajouter des apostrophes ou des guillemets autour de `username`, `org_name` et `space_name`. Par exemple, `-o "my org"`.

  5. A partir du répertoire <var class="keyword varname">your_new_directory</var>, redéployez votre application dans {{site.data.keyword.Bluemix_notm}} en utilisant la commande `ibmcloud dev deploy`. Pour plus d'informations, voir la [documentation concernant l'interface CLI](docs/cli/idt/commands.html#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Accédez à votre application via https://<var class="keyword varname" data-hd-keyref="app_url">url_app</var>.<span class="keyword" data-hd-keyref="APPDomain">nom_domaine_app</span>.
