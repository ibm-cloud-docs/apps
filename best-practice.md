---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-26"

keywords: apps, best practices, best practice create app, good app, app general, common practice, cloud app help

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# What makes a good app?
{: #best-practice}

Build your application in {{site.data.keyword.cloud}} to take advantage of all the things cloud offers. These best practices can help you ensure that your apps are cloud-ready.
{: shortdesc}

## Build your app to be independent of topology

In a non-cloud environment, your app might use a particular deployment topology. However, your app topology might change in cloud apps because the cloud-ready apps and services allow immediate scalability changes. These changes include dynamic scaling and manually resizing the number of instances of an app.

Build your app to be as generic and stateless as possible to keep your app from being affected by scalability changes.

## Assume that the local file system isn't permanent

Don't rely on the files that are written to the file system because an app instance can be moved, deleted, or duplicated on cloud. If an app uses the local file system as a cache of frequently used information (including app logs), the information is lost when the instance is shut down and restarted at a different location or a different VM.

You can store information in a service, such as an SQL or NoSQL database instead of the local file system. In a dynamic cloud environment, it's also critical to have your logs available on a service that outlives the app instances where the logs are generated.

## Exclude session state from your app

The state of your system is defined by your databases and shared storage, and not by each individual running app instance. Statefulness of any sort limits the extensibility of an app. Try to minimize the impact of session state by storing it in a centralized location on the server.

If you can't eliminate session state entirely, push it out to a highly available store that is external to your app server. The stores include IBM WebSphere eXtreme Scale, Redis, or Memcached, or an external database.

## Use an external service registry to resolve service endpoints

Don't assume that the services your app uses are allocated particular host names or IP addresses. The services might be relocated or regenerated in your cloud environment and the host names and IP addresses can also change.

Extracting environment-specific dependencies into a set of property files is an improvement, but it’s still inadequate. The best practice is to use an external service registry to resolve service endpoints, or delegate the entire routing function to a service bus or a load balancer with a virtual name.

## Build your app by using a multi-region architecture
{: #multiregion}

You can run more than one instance to avoid downtime in a single region. To deliver an even more robust app, consider a multi-region architecture.

For more information, see [Strategies for resilient applications tutorial](/docs/tutorials?topic=solution-tutorials-strategies-for-resilient-applications).

## Ensure you're monitoring your apps
{: #monitoring}

{{site.data.keyword.cloud_notm}} makes it easy to monitor your app with services like [New Relic](https://newrelic.com/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

## Take advantage of support options
{: #support}

{{site.data.keyword.cloud_notm}} paid pricing plan offers a number of different account types with optional paid support. No matter the type of your account, if you plan to bring an app to production on {{site.data.keyword.cloud_notm}}, consider enrolling in this option.

With or without paid support, you can get help as described at [support](/docs/get-support?topic=get-support-getting-customer-support), which offers insurance against unforeseen issues.

## Avoid infrastructure APIs in your app

If you rely on a specific infrastructure API in your app, changing the infrastructure is more challenging, because an infrastructure API can refer to many different layers in your software stack.

You can rely on existing open source or commercial products instead, and leave PaaS solutions in the PaaS layer to keep them out of your app code.

## Use standard protocols

Don't use obscure protocols that require extra configuration for resiliency.

Apps based on standard protocols are more resilient with the configuration items that are delegated to the platform. The standard protocols include HTTP, SSL, standard database, queuing, and web service connections.

## Use compatibility libraries instead of OS-specific features

If you are using OS-specific features, you can fix this issue by using compatibility libraries instead. For example, Cygwin and Mono. Cygwin is a compatibility library that provides a set of Linux&trade; tools in a Windows&trade; environment. Mono is a compatibility library that provides Microsoft&trade; .NET tools in Linux.

Avoid the OS-specific dependencies; instead, use services that are provided by the middleware infrastructure or service providers.

## Script your installation process

Your app might be installed frequently on-demand on the dynamic cloud environment. The installation process must be scripted and reliable, and the configuration data must be externalized from the scripts.

Capture your app installation as a uniform set of scripts that is independent of the operating system. Keep your app installation small and portable to adapt to different automation techniques. Also, minimize the dependencies that are required by the app installation.

For more information about cloud-ready apps, see [The 12-factor app](https://12factor.net/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").


