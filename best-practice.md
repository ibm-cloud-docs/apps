---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-21"

---

# What makes a good app?
{: #best-practice}

Build your app in {{site.data.keyword.Bluemix_notm}} to take advantage of all the things cloud offers. These best practices can help you ensure that your apps are cloud-ready.
{:shortdesc}

## Build your app to be independent of topology

In a non-cloud environment, your app might use a particular deployment topology. However, your app topology might change in cloud apps, because the cloud-ready apps and services allow immediate scalability changes. The scalability changes include dynamic scaling and manually resizing the number of instances of an app.

Build your app to be as generic and stateless as possible to keep your app from being affected by scalability changes.

## Assume that the local File System isn't permanent

Because an app instance can be moved, deleted, or duplicated on cloud, don't rely on the files that are written to the file system. If an app uses the local file system as a cache of frequently used information including app logs, the information is lost when the instance is shut down and restarted at a different location or a different VM.

You can store information in a service, such as an SQL or NoSQL database instead of the local file system. In a dynamic cloud environment, it's also critical to have your logs available on a service that outlives the app instances where the logs are generated.

## Store session state outside of your app

The state of your system is defined by your databases and shared storage, and not by each individual running app instance. Statefulness of any sort limits the scalability of an app. Try to minimize the impact of session state by storing it in a centralized location on the server.

If you can't eliminate session state entirely, push it out to a highly available store that is external to your app server. The stores include IBM WebSphere eXtreme Scale, Redis, or Memcached, or an external database.

## Use an external service registry to resolve service endpoints

Don't assume that the services your app uses are allocated particular host names or IP addresses. The services might be relocated or regenerated in your cloud environment and the host names and IP addresses can also change.

Extracting environment-specific dependencies into a set of property files is an improvement, but it’s still inadequate. The best practice is to use an external service registry to resolve service endpoints, or delegate the entire routing function to a service bus or a load balancer with a virtual name.

## Build your app by using a multi-region architecture
{: #multiregion}

Run multiple instances to avoid downtime in a single region, but to deliver an even more robust application, consider a multi-region architecture.

## Ensure you're monitoring your apps
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} makes it easy to monitor your application with services like [New Relic ![External link icon](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Check out [monitoring and logging](../monitor_log/logging.html#logging) for more information.

## Take advantage of support options
{: #support}

{{site.data.keyword.Bluemix_notm}} paid pricing plan offers a number of different account types with optional paid support. No matter the type of your account, if you plan to bring an application to production on {{site.data.keyword.Bluemix_notm}}, consider enrolling in this option.

With or without paid support, you can get help as described at [support](../get-support/howtogetsupport.html), which offers insurance against unforeseen issues.

## Avoid infrastructure APIs in your app

If you rely on a specific infrastructure API in your app, changing the infrastructure is more challenging, because an infrastructure API can refer to many different layers in your software stack.

You can rely on existing open source or commercial products instead, and leave PaaS solutions in the PaaS layer to keep them out of your app code.

## Use standard protocols

Don't use obscure protocols that require extra configuration for resiliency.

Apps based on standard protocols are more resilient with the configuration items that are delegated to the platform. The standard protocols include HTTP, SSL, standard database, queuing, and web service connections.

## Use compatibility libraries instead of OS-specific features

If you have already used OS-specific features, you can fix this issue by using compatibility libraries, for example, Cygwin and Mono. Cygwin is a compatibility library that provides a set of Linux tools in a Windows environment. Mono is a compatibility library that provides Windows .NET capabilities in Linux.

Avoid the OS-specific dependencies; instead, use services that are provided by the middleware infrastructure or service providers.

## Script your installation process

Your app might be installed frequently on-demand on the dynamic cloud environment. The installation process must be scripted and reliable, and the configuration data must be externalized from the scripts.

Capture your app installation as a uniform set of scripts that is independent of the operating system. Keep your app installation small and portable to adapt to different automation techniques. Also, minimize the dependencies that are required by the app installation.

For more information about cloud-ready apps, see [The 12-factor app ![External link icon](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.


