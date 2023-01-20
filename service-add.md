---

copyright:
  years: 2015, 2023
lastupdated: "2023-01-20"

keywords: apps, services, add service, application, service, instance, ibmcloud dev edit, connect service, service instance, credentials, starter kit

subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# Adding a service to your app
{: #add-service}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

When you create an app from the {{site.data.keyword.cloud}} console, you can add services from the App details page. You can also provision them directly from the {{site.data.keyword.cloud_notm}} catalog, outside the context of your app.
{: shortdesc}

When you add a service to an app, the action binds the service instance to the app and provisions the credentials.

Only one instance of a Lite plan per service is allowed. To create a new instance, either delete your existing Lite plan instance, or select a paid plan. You can also use your existing instance to connect to your app.

## Auto-provisioned services in starter kits
{: #auto-provision}

If a starter kit requires certain services, {{site.data.keyword.cloud_notm}} automatically creates instances of those services when you create your app. You can also create service instances or select existing service instances to connect to your app. On the App details page, you can see a list of service instances that are associated with your app.

## Creating a service instance for your app
{: #create-service-instance}

To create a service instance for your app, complete the following steps:

1. On the App details page, click **Create service** in the **Services** card.
2. Select the type of service that you want, such as Storage or AI, and then click **Next**.
3. Select the service that you want to connect to your app, and then click **Next**.
4. Select the region and pricing plan, and then click **Create**.

The service instance is created and connected to your app, and the credentials are provisioned.

## Connecting an existing service instance to your app
{: #connect-existing-service}

To connect an existing service instance to your app, complete these steps:

1. On the App details page, click **Connect existing service** in the **Services** card.
2. Select one or more services that you want to connect to your app, and then click **Next**.

The service instance is connected to your app.

## Accessing the service docs and API references
{: #services-docs}

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

## Next steps
{: #services-add-nextsteps}

* You can click the Actions icon ![Actions icon](../icons/actions-icon-vertical.svg) and either [remove the service](/docs/apps?topic=apps-remove-service#remove-service-only) from the app, open the service dashboard, or [delete the service](/docs/apps?topic=apps-remove-service#delete-service).
* [Deploy your app again](/docs/apps?topic=apps-deploying-apps#deploying-your-app-manually).
* Learn more about [service availability](/docs/overview?topic=overview-services_region).
