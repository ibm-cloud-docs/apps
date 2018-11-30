---
copyright:
  years: 2015, 2018
lastupdated: "2018-11-16"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Node.js app files
{: #node-project-files}

For Node.js apps, the following information is an inventory of what you typically find in {{site.data.keyword.Bluemix}}. When you create a starter kit, these files are created for you. If you're migrating an app to host in {{site.data.keyword.Bluemix_notm}}, you might want to review this information to avoid potential conflicts. 
{:shortdesc}

The following table lists the common directories and files that are included in a generated Node.js app.

| Root directory                                     | Description                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | Metadata information about the package including name, version, and dependencies. |
|cli-config.yml | CLI configuration options |
|manifest.yml | Cloud Foundry deployment file |
|Dockerfile | Dockerfile for `ibmcloud dev run`, `ibmcloud dev deploy`, and `docker` commands |
|Dockerfile-tools | Dockerfile for `ibmcloud dev build` and `ibmcloud dev test` |
|docker-compose.yml | App service configuration for Docker Compose |
|webpack.config.js | Web pack configuration for build related information |
| LICENSE | License file |
|README.md | Description of app |
{: caption="Table 1. Contents of a generated Node.js app root directory" caption-side="top"}

| `./public/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Swagger specification for describing REST APIs |
| `./public/index.html` | Skeleton markup for web applications |
|`./public/server/server.js` | Server implementation file |
{: caption="Table 2. Contents of a generated Node.js app public directory" caption-side="top"}

| `./test/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Integration test for Express server |
{: caption="Table 3. Contents of a generated Node.js app test directory" caption-side="top"}

| `./.bluemix/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container build script |
| deploy.json | Deployment information |
| kube_deploy.sh | Kubernetes deployment script |
| pipeline.yml | IBM Cloud pipeline definition |
| toolchain.yml | IBM Cloud toolchain definition |
{: caption="Table 4. Contents of a generated Node.js app bluemix directory" caption-side="top"}

| `./chart/<projectname>/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm chart |
| `./chart/<projectname>/values.yaml` | Helm chart values |
| `./chart/<projectname>/templates/deployment.yaml` | Deployment template |
| `./chart/<projectname>/templates/service.yaml` | Service template |
{: caption="Table 5. Contents of a generated Node.js app chart directory" caption-side="top"}
