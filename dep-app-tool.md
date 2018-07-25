---
copyright:

  years: 2018

lastupdated: "2018-07-25"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Deploying apps
{: #deploy}

You can deploy your apps with a toolchain or a command line interface. A toolchain is a set of tool integrations. The command line interface is a simple way to deploy your apps and service instances.
{: shortdesc}

## Deploying apps with toolchains
{: #toolchains_getting_started}

Open toolchains are available in the Public and Dedicated environments on {{site.data.keyword.Bluemix}}. You can create a toolchain in two ways: use a template to create a toolchain or create a toolchain from an app. To learn more about toolchains, see [Creating toolchains](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

With a properly configured toolchain, deploying your app is trivial:  a build-deploy cycle will automatically start with each merge to the Master branch in your repo.

All toolchains that are created from an {{site.data.keyword.Bluemix}} developer dashboard are configured for automatic deployment.
{: tip}

## Deploying apps with the command line interface
{: #cli}

IBM Cloud provides a robust CLI as well as plug-ins and developer tool extensions that integrate with the CLI.

Use {{site.data.keyword.Bluemix_notm}} command line interface to deploy your apps and service instances.
{:shortdesc}

Before you begin, [download and install the {{site.data.keyword.Bluemix_notm}} command line interface](/docs/cli/index.html).

<p>
<a class="xref" href="https://console.bluemix.net/docs/cli/index.html#overview" target="_blank" title="(Opens in a new tab or window)"><img class="image" src="images/btn_bx_commandline.svg" alt="Download IBM Cloud Developer Tools" /></a>
</p>

**Restriction:** The command line tool isn’t supported by Cygwin. Use the tool in a command line window other than the Cygwin command line window.
{:prereq}

After you install the command line interface, you can get started:

  1. {: download} Download the code for your app to a new directory to set up your development environment.

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Opens in a new tab or window)"></a>

  2. Change to the directory where your code is located.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Make changes to your app code. For example, if you're using a {{site.data.keyword.Bluemix_notm}} sample application and your app contains the `src/main/webapp/index.html` file, you can modify it and edit "Thanks for creating ..." to say something new. Ensure that the app runs locally before you deploy it back to {{site.data.keyword.Bluemix_notm}}.

    Take note of the `manifest.yml` file. When deploying your app back to {{site.data.keyword.Bluemix_notm}}, this file is used to determine your application’s URL, memory allocation, number of instances, and other crucial parameters.

    Also pay attention to the `README.md` file, which contains details such as build instructions if applicable.

    Note: If your application is a Liberty app, you must build it before redeploying.

  4. Connect and log in to {{site.data.keyword.Bluemix_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  If you use a federated ID, add the `-sso` option.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **Note**: If the value contains a space, you must add single or double quotation marks around `username`, `org_name`, and  `space_name`, for example, `-o "my org"`.

  5. From <var class="keyword varname">your_new_directory</var>, redeploy your app to {{site.data.keyword.Bluemix_notm}} by using the `ibmcloud dev deploy` command. For more information, see [the CLI documentation](/docs/cli/idt/commands.html#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Access your app by browsing to https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
