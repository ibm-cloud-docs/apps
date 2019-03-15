---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, deploying apps, toolchains, cli

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deploying apps
{: #deploying-apps}

You can deploy your apps with a toolchain or the command-line interface (CLI). A toolchain is a set of tool integrations. The CLI is a simple way to deploy your apps and service instances.
{: shortdesc}

## Deploying apps by using toolchains
{: #toolchain-deploy-apps}

Open toolchains are available in the Public and Dedicated environments on {{site.data.keyword.Bluemix}}. With a properly configured toolchain, deploying your app is easy. A build-deploy cycle automatically starts with each merge to the master branch in your repo.

You can create a toolchain in these ways:
* Use a template to create a toolchain.
* Create a toolchain from an app.

To learn more about toolchains, see [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Deploying apps by using the CLI
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} provides a robust CLI and plug-ins and developer tool extensions that integrate with the CLI.

Before you begin, [download and install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli).

The CLI isn’t supported by Cygwin. Use the tool in a window other than the Cygwin command-line window.
{: important}

  1. {: download} Download the code for your app to a new directory to set up your development environment.

    <a class="xref" href="https://cloud.ibm.com" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Opens in a new tab or window)"></a>

  2. Change to the directory where your code is located.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Make changes to your app code. For example, if you're using aN {{site.data.keyword.cloud_notm}} sample application and your app contains the `src/main/webapp/index.html` file, you can modify it and edit the `Thanks for creating ...` line. Ensure that the app runs locally before you deploy it back to {{site.data.keyword.cloud_notm}}.

    Take note of the `manifest.yml` file. When deploying your app back to {{site.data.keyword.cloud_notm}}, this file is used to determine your application’s URL, memory allocation, number of instances, and other crucial parameters.

    Also review the `README.md` file, which contains details such as build instructions if applicable.

  If your application is a Liberty app, you must build it before you deploy it again.
  {: note}

  4. Connect and log in to {{site.data.keyword.cloud_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  If you use a federated ID, add the `-sso` option.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  If the value contains a space, you must add single or double quotation marks around `username`, `org_name`, and  `space_name`, for example, `-o "my org"`.
  {: note}

  5. From your new directory, deploy your app to {{site.data.keyword.cloud_notm}} by using the `ibmcloud dev deploy` command. For more information, see [the CLI documentation](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Access your app by going to https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
