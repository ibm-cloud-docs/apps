---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-29"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom route, dns, domainname, domain name, endpoint

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Adding and using a custom domain
{: #updatingapps}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. Custom domains direct requests for your applications to a URL that you own. A custom domain can be a shared domain, a shared subdomain, or a shared domain and host. Unless a custom domain is specified, {{site.data.keyword.cloud_notm}} uses a default shared domain in the route to your application. You can create and use a custom domain by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface.
{:shortdesc}

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use. For more information about migrating to `appdomain.cloud`, see [Updating your domain](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

To use a custom domain, you must register the custom domain on a public DNS server, and then configure the custom domain in {{site.data.keyword.cloud_notm}}. Next, you must map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your application in {{site.data.keyword.cloud_notm}}.

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} console
{: #custom-domain-console}

Complete these steps to add a custom domain for your org by using the console:

1. Go to **Manage > Account**, and select **Cloud Foundry orgs**.
2. Click the name of the org for which you're creating a custom domain.
3. Click the **Domains** tab to view a list of available domains.
4. Click **Add a domain**, enter your domain name, and select the region.
5. Confirm your updates, and click **Add**.

## Adding the route with the custom domain to an application

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"), click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and select **Resource List**.
2. On the **Resource List** page, click **Cloud Foundry Apps**.
3. Click the application that you want to add the route to. The app's **Overview** page is displayed.
4. Select the **Routes** menu, and select **Edit routes**.
5. Click **Add route**, and specify the route that you want to use for the application.
6. Confirm your updates by clicking **Save**.

As an example, you can use `*.mycompany.com` to associate the route `www.mybluemix.net` to your app. You can also use `example.mycompany.com` to associate the route `www.example.bluemix.net` to your app.
{: tip}

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} command-line interface
{: #custom-domain-cli}

1. For Cloud Foundry apps, connect to your targeted Cloud Foundry API endpoint by typing the following command:
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Cloud Foundry API endpoints:**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. Create a custom domain for your organization by typing the following command:
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. Add the route with the custom domain to an application.

   For Cloud Foundry apps, type the following command:
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## Mapping the custom domain to the system domain
{: #mapcustomdomain}

After you configure the custom domain in {{site.data.keyword.cloud_notm}}, map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on your registered DNS server:

1. Set up a 'CNAME' record for the custom domain name on your DNS server. Steps for setting up the CNAME record vary depending on your DNS provider. For example, if you use GoDaddy, you follow the [Domains Help](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") guidance from GoDaddy.
2. Map the custom domain name to the secure endpoint for the {{site.data.keyword.cloud_notm}} region where your application is running. Use the following region endpoints to provide the URL route that is allocated to your organization in {{site.data.keyword.cloud_notm}}. For example, point your CNAME to `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Cloud Foundry endpoints:**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Accessing your application
{: #access-app}

In a browser, enter the following URL to access your application, where `hostname` is your host name, and `mydomain` is your domain name:
```
http://hostname.mydomain
```

## Removing an orphaned route
{: #remove-orphaned-route}

To remove an orphaned route, run the following command:
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

In that example, `domain` is the name of your domain, and `hostname` is the host name of the route for your application. For more information about the `ibmcloud app route-delete` command, enter the command `ibmcloud app route-delete -h`.

## Using a custom domain for Kubernetes apps
{: #kube-custom-domain}

The subdomain for IBM Cloud Kubernetes Service host names is `containers.appdomain.cloud`. The IBM-provided Ingress subdomain wildcard, `*.<cluster_name>.<region>.containers.mybluemix.net`, is registered by default for your cluster. The IBM-provided TLS certificate is a wildcard certificate and can be used for the wildcard subdomain. If you want to use a custom domain, you must register the custom domain as a wildcard domain such as `*.custom_domain.net`. To use TLS, you must get a wildcard certificate. For more information, see [Multiple domains within a namespace](/docs/containers?topic=containers-ingress#multi-domains).

Check out [this tutorial](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) that walks you through scaffolding a web application, running it locally in a container, and then deploying it to a Kubernetes cluster that was created with IBM Kubernetes Service. Additionally, you will learn how to bind a custom domain, monitor the health of the environment, and scale the application.