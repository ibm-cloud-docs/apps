---

copyright:
  years: 2019, 2022
lastupdated: "2022-05-17"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: apps

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}

# FAQs
{: #apps-faq}

## What happened to mybluemix.net?
{: #domain-change-faq}
{: faq}

A new host name option `*.appdomain.cloud` is available on cloud.ibm.com.

Previously, the `mybluemix.net` domain was used for hosting applications in various deployment targets, such as {{site.data.keyword.containerlong_notm}}. Any apps that are hosted on `mybluemix.net` are not impacted.

The subdomain for apps that you deploy to {{site.data.keyword.containerlong_notm}} is `containers.appdomain.cloud`.

For more information, see [Managing your domains](/docs/apps?topic=apps-update-domain).

## Where can I find a list of my apps?
{: #cf-app}
{: faq}

The Resource list in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external} provides summary information for the apps that you created. From the [Resource list](https://cloud.ibm.com/resources), the **Apps** section contains all apps that you created.

## How do I delete apps?
{: #delete-apps}
{: faq}

To delete an app that you created, complete these steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource list**.
2. Click the **Actions** icon ![Actions icon](../icons/action-menu-icon.svg) for the app that you want to delete, and click **Delete**.

## What are toolchains?
{: #toolchains}
{: faq}

A toolchain is a set of tool integrations that support development, deployment, and operations tasks. You can create a toolchain from your app. The toolchain can support continuous development, deployment, monitoring, and more, and it is associated with your app. Each app can be associated with a toolchain. A toolchain can be configured so that changes to the toolchain automatically build and deploy the app. For more information about toolchains, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## How do I extract a toolchain template from an existing toolchain?
{: #toolchain-template}
{: faq}

You can run the [toolchain-to-template script](https://github.com/open-toolchain/toolchain-to-template#setup) to extract a toolchain template from an existing toolchain. This script uses a toolchain URL and generates an open toolchain (OTC) template in the current folder. When the script runs, it creates a clone of your original toolchain.
