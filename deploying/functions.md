---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating serverless apps
{: #serverless}

For serverless development, you can use IBM's functions as a service (FaaS) offering, {{site.data.keyword.openwhisk}}. You can run application logic with {{site.data.keyword.openwhisk_short}} in response to events or direct invocations from web or mobile apps over HTTP without provisioning or managing servers.{{site.data.keyword.openwhisk_short}} performs system administration like auto-scaling, availability management, and maintenance so that you, as a developer, can focus on writing application logic.
{:shortdesc}

You can use the {{site.data.keyword.openwhisk_short}} user interface (UI) or the command line interface (CLI) to develop your applications. Both have similar capabilities for developing applications. The CLI provides more control over your deployment and operations. For more detailed information about {{site.data.keyword.openwhisk_short}}, check out the full [Openwhisk documentation](/docs/openwhisk/index.html).

## {{site.data.keyword.openwhisk_short}} UI
{: #ui}

Try out {{site.data.keyword.openwhisk_short}} in your [browser ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/openwhisk/actions){:new_window}. Go to the [Concepts ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/openwhisk/learn){:new_window} page for a quick tour of the {{site.data.keyword.openwhisk_short}} user interface.

## Developing with the CLI
{: #openwhisk_start_configure_cli}

To learn more about installing and developing with the {{site.data.keyword.openwhisk_short}} CLI, see [Setting up the {{site.data.keyword.openwhisk_short}} CLI ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/openwhisk/cli){:new_window}.

## Exposing APIs and data sets as web actions
{: #containers}

By default, {{site.data.keyword.openwhisk_short}} defines actions that require an authentication key. In production mobile environments, it is often necessary to authorize mobile clients based on OAuth flows to expose APIs and specific data sets.

{{site.data.keyword.openwhisk_short}} enables developers to expose their functions as web actions, which are annotated, to quickly build web-based applications. You can program backend logic with annotated actions that your web application can access anonymously, without requiring a {{site.data.keyword.openwhisk_short}} authentication key.

To expose an action as a web action, go to the **Endpoints** tab of your action, and select **Enable as Web Action**.

Now, users can reach the action from a browser or cURL request, for example:

```
curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**Output:**

```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} provides a [mobile SDK](/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk) for iOS and watchOS devices that enables mobile apps to easily send remote triggers and invoke remote actions. It also provides a [serverless framework SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/openwhisk/openwhisk_goserverless.html){:new_window} that enables serverless applications.

