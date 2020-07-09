---

copyright:
  years: 2019
lastupdated: "2019-08-23"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:codeblock: .codeblock}
{:screen: .screen}

# Managing your domains
{: #update-domain}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. Custom domains direct requests for your applications to a URL that you own. A custom domain can be a shared domain, a shared subdomain, or a shared domain and host. Unless a custom domain is specified, {{site.data.keyword.cloud_notm}} uses a default shared domain in the route to your app. The process for managing your domains depends on your deployment target, such as {{site.data.keyword.containershort}}, Cloud Foundry, and others.
{: shortdesc}

To use a custom domain, you must register the custom domain on a public DNS server, and then configure the custom domain in {{site.data.keyword.cloud_notm}}. Next, you must map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your app in {{site.data.keyword.cloud_notm}}.

## Changing your domain for Kubernetes apps
{: #update-domain-kube}

The subdomain for {{site.data.keyword.containershort_notm}} host names is `containers.appdomain.cloud`. The IBM-provided Ingress subdomain wildcard, `*.<cluster_name>.<region>.containers.appdomain.cloud`, is registered by default for your cluster. The IBM-provided TLS certificate is a wildcard certificate and can be used for the wildcard subdomain. For more information, see [Multiple domains within a namespace](/docs/containers?topic=containers-ingress#multi-domains).

## Using a custom domain for Kubernetes apps
{: #custom-domain-kube}

If you want to use a custom domain, you must register the custom domain as a wildcard domain, such as `*.custom_domain.net`. To use TLS, you must get a wildcard certificate. For more information, see [Multiple domains within a namespace](/docs/containers?topic=containers-ingress#multi-domains).

Check out [this tutorial](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) that walks you through scaffolding a web app, running it locally in a container, and then deploying it to a Kubernetes cluster that was created with IBM Kubernetes Service. Additionally, the tutorial shows you how to bind a custom domain, monitor the health of the environment, and scale the app.

## Changing your domain for Cloud Foundry apps
{: #update-domain-cf}

For Cloud Foundry apps, you can change your domain from `mybluemix.net` to `appdomain.cloud` by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface. For more information about changing your domain to `appdomain.cloud`, see [Updating your domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use.
{: tip}

## Using a custom domain for Cloud Foundry apps
{: #custom-domain-cf}

For Cloud Foundry apps, you can create and use a custom domain by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface. For more information, see [adding custom domains](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).