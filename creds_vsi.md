---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Adding credentials to your virtual instance or local docker environment
{: #add-credentials-vsi}

Learn how to add service credentials to your virtual server instance or local docker deployment environment.
{: shortdesc}

## Your code + Virtual Server Instance or local docker
{: #credentials-byoc-vsi}

Under VSI or local docker, the environment is entirely yours. For example, you can write your code like the following example, and provide the credential's environment value to your application when you run it.
```
password = getEnvironment('password');
```
{: codeblock}

In Bash, you can write your code like the following example:
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

In Docker, you can write your code like the following example:
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Starter kit + VSI (or local Docker)
{: #credentials-starterkit-vsi}

### How the virtual server instance is prepared

The environment is entirely under your control, as if you're running the application from your notebook. In other words, local Docker. Because VSI is effectively bare metal from the running application's perspective, no _secrets_ (like in Kubernetes) or _services_ (like in Cloud Foundry) exist.

### The starter kit generated code
{: #starterkit-generated-code-vsi}

Code that is generated from a starter kit has the native `IBMCloudEnv` library, which abstracts the retrieval of environment values so that the application code is portable to run on several target deployments. With virtual or local Docker, that environment must be prepared with values that satisfy the `IBMCloudEnv` library that _don't necessarily_ come from actual environment variables.

For your convenience, the `mappings.json` instructions that are included with the starter kit-generated output, have references to a local file from which the `IBMCloudEnv` library sources the values that the application can use.

For example, notice the last line in the following section from the `mappings.json` file:
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

If you use the "Deploy to Cloud" feature when you create an app, the `/server/localdev-config.json` file is removed from the GitLab repository. For security reasons, you don't want to put your credentials in a source code repository.

If you use `git clone` on the created GitLab repository to start active development, notice that the `.gitignore` file specifically ignores `server/localdev-config.json` to help prevent accidental check-in of a file that has sensitive credentials. However, VSI _does_ need that file, as does the Developer that works on a notebook.

You can retrieve the `server/localdev-config.json` file by completing these steps:

1. Use `git clone` on the Git lab repository that was automatically created when you used the "Deploy to Cloud" feature.
2. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html), which includes the `dev` plug-in.
3. Use the `ibmcloud` command line to log in to {{site.data.keyword.cloud_notm}}.
4. Run `ibmcloud dev get-credentials`, which refers to the `cli-config.yml` file. The `cli-config.yml` file includes information about which application and generation job has the credentials.

If any resource is removed from the application between using the "Deploy to Cloud" feature and `ibmcloud dev get-credentials`, the downloaded file `/server/localdev-config.json` wouldn't have all of the credentials your original `git clone` codebase might require.
{: tip}

If you're running your application in a Docker container, you might choose to remove the `/server/localdev-config.json` file entirely and pass the environment variables on the Docker command line.

Continuing with the "cloudant_apikey" section from the `mappings.json` file, notice the `env:cloudant_apikey` before the `file...` line. That means an environment variable that is named `cloudant_apikey` takes precedence over the contents of the file. So, even if the file is present in the Docker image that you built (which isn't required), you can override values by passing them on the Docker command line.

For example:
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}