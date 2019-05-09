---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, get started coding, DevOps, toolchain, monitoring, monitor, health

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.prf_hubshort}}
{: #monitor-overview}

You can start monitoring your application availability and performance immediately. When you bind {{site.data.keyword.prf_hubshort}} to your app, a synthetic test is automatically created to monitor the main app URL by default.

{{site.data.keyword.prf_hublong}} is available as a service in the DevOps domain in the {{site.data.keyword.cloud_notm}} catalog. It is also available by on the Cloud Foundry application dashboard on the **Monitoring** tab. 
{: shortdesc}

You can test, monitor, and improve your application’s health as you build it by adding the {{site.data.keyword.prf_hubshort}} to your DevOps toolchain.

This tool integration is available only for Cloud Foundry apps. It is preconfigured and does not require any configuration parameters. You cannot reconfigure this tool integration.
{: tip}

To add the {{site.data.keyword.prf_hubshort}} tool integration to your DevOps toolchain, complete these steps:

1. [Create your app](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started).
2. On App details page, click **Configure continuous delivery** and follow the steps for configuring a DevOps toolchain. The steps vary, depending on which deployment target that you select.
3. When you see the "Configured" message on the App details page, click **View toolchain**.
4. On the toolchain's Overview page, click **Add a Tool**.
5. Select **{{site.data.keyword.prf_hubshort}}**.
6. Click **Create Integration**. {{site.data.keyword.prf_hubshort}} is added to your toolchain.

For more information, see the [{{site.data.keyword.prf_hubshort}} Getting started tutorial](/docs/services/AvailabilityMonitoring?topic=availability-monitoring-avmon_gettingstarted). 
