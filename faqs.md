---

copyright:

  years: 2019

lastupdated: "2019-05-08"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# FAQs
{: #apps-faq}

## What happened to mybluemix.net?
{: #domain-change-faq}
{: faq}

A new host name option `*.appdomain.cloud` is available on cloud.ibm.com.

Previously, the `mybluemix.net` domain was used for hosting apps in various deployment targets, such as {{site.data.keyword.containerlong_notm}} or Cloud Foundry. Any apps that you have hosted on `mybluemix.net` are not impacted.

The subdomain for Cloud Foundry apps is `cf.appdomain.cloud`. The subdomain for apps that you deploy to {{site.data.keyword.containerlong_notm}} is `containers.appdomain.cloud`.

For more information, see [Managing your domains](/docs/apps?topic=creating-apps-update-domain).

## Where can I find a list of my apps?
{: #cf-app}
{: faq}

Your resource list in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") provides summary information for the applications that you created. In the resource list, the **Apps** section contains all apps that you created but *not* deployed to Cloud Foundry. The **Cloud Foundry Apps** section contains all the apps that you created and deployed to Cloud Foundry.

## Why can’t I select a Cloud Foundry space when I try to deploy my app?
{: #cf-space}
{: faq}

You most likely need to create a Cloud Foundry space first. If you are using the Cloud Foundry command-line interface, type `cf create-space <space_name> -o <organization_name>`. Otherwise, complete these steps from the console:

1. From the menu bar in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"), select **Manage** > **Account**.
2. Select **Cloud Foundry orgs**.
3. Click the name of the organization that you want to create a space in, and click **Add a space**.

## How do I delete apps?
{: #delete-apps}
{: faq}

To delete an app that you created, complete these steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"), click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource List**.
2. Click the **Actions** icon ![Actions icon](../icons/action-menu-icon.svg) for the app that you want to delete, and click **Delete**.

## What are toolchains and how do they relate to my app?
{: #toolchains}
{: faq}

A toolchain is a set of tool integrations that support development, deployment, and operations tasks. You can create a toolchain from your app. The toolchain can support continuous development, deployment, monitoring, and more, and it is associated with your app. Each app can be associated with a toolchain. A toolchain can be configured so that changes to the toolchain automatically build and deploy the app. For more information about toolchains, see [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## How do I change the domain for my Cloud Foundry apps?
{: #cf-domains-faq}
{: faq}

For Cloud Foundry apps, you can change your domain from `mybluemix.net` to `appdomain.cloud` by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface. For more information about changing your domain to `appdomain.cloud`, see [Updating your domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

When you create new apps, the default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use.
