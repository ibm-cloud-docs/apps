---

copyright:
  years: 2018, 2023
lastupdated: "2023-01-27"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# Manually adding service credentials to your deployment environment
{: #credentials_overview}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

You want your application logic to acquire sensitive service credentials, such as database API keys or passwords, from the environment in which your app runs. That way, you don't keep credentials in your source code repository.
{: shortdesc}

If you create an app by using a starter kit, the environment is prepared for you automatically. When you connect a service to your starter kit before you deploy your app, the service credentials are automatically added to your environment.

You must manually add the service credentials to your deployment environment in either of the following scenarios:

* You bring your own code.
* You add a service to a starter kit-based app after the app is deployed.

The process for adding the service credentials depends on your deployment target and your programming language. For more information about configuring service credentials for your deployment target, see the documentation that is specific to your hosting environment:

* [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-service-binding#adding_app)
