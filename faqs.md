---

copyright:
  years: 2019, 2023
lastupdated: "2022-06-02"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: apps

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}

# FAQs
{: #apps-faq}

## Where can I find a list of my apps?
{: #list-app}
{: faq}

The [Resource list](/resources){: external} in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external} provides summary information for the apps that you created. The **Apps** section in the Resource list contains all apps that you created.

## How do I delete apps?
{: #delete-apps}
{: faq}

To delete an app that you created, complete these steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource list**.
2. Click the **Actions** icon ![Actions icon](../icons/action-menu-icon.svg) for the app that you want to delete, and click **Delete**.

## What are toolchains?
{: #toolchains}
{: faq}

A toolchain is a set of tool integrations that support continuous development, deployment, monitoring, operations, and more. For more information about toolchains, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## How do I extract a toolchain template from an existing toolchain?
{: #toolchain-template}
{: faq}

You can run the [toolchain-to-template script](https://github.com/open-toolchain/toolchain-to-template#setup){: external} to extract a toolchain template from an existing toolchain. This script uses a toolchain URL and generates an open toolchain (OTC) template in the current folder. When the script runs, it creates a clone of your original toolchain.
