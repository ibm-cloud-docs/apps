---
copyright:
  years: 2015, 2018
lastupdated: "2018-10-05"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Swift app files
{: #swift-project-files}

For Swift apps, the following information is an inventory of what you typically find in {{site.data.keyword.Bluemix}}. When you create a starter kit, these files are created for you. If you're migrating an app to host in {{site.data.keyword.Bluemix_notm}}, you might want to review this information to avoid potential conflicts. 
{:shortdesc}

The following table lists the common directories and files that are included in a generated Swift app.

| Root directory                                     | Description |
|:------------------------------------------------|:------------------------------------------|
| Package.swift| Swift dependency definition file |
| cli-config.yml | CLI configuration options |
| manifest.yml | Cloud Foundry deployment file |
| Dockerfile | Dockerfile for `ibmcloud dev run`, `ibmcloud dev deploy`, and `docker` commands |
| `Dockerfile-tools` | Dockerfile for `ibmcloud dev build` and `ibmcloud dev test` |
| LICENSE | License file |
| README.md | Description of app |
{: caption="Table 1. Contents of a generated Swift app root directory" caption-side="top"}

| `./Sources/Application/` directory | Description  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | The Swift Application file |
| `./Sources/<projectname>/main.swift` | The Swift Main file |
{: caption="Table 2. Contents of a generated Swift app /Sources/Application/ directory" caption-side="top"}

| `./test/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Utility methods for testing with Kitura |
{: caption="Table 3. Contents of a generated Swift app test directory" caption-side="top"}

| `./Tests/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Utility for testing on Linux |
| `./Tests/ApplicationTests>/RouteTests.swift` | File that includes test cases |
{: caption="Table 4. Contents of a generated Swift app tests directory" caption-side="top"}

| `./.bluemix/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container build script |
| deploy.json | Deployment information |
| kube_deploy.sh | Kubernetes deployment script |
| pipeline.yml | IBM Cloud pipeline definition |
| toolchain.yml | IBM Cloud toolchain definition |
{: caption="Table 5. Contents of a generated Swift app bluemix directory" caption-side="top"}

| `./chart/<projectname>/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm chart |
| `./chart/<projectname>/values.yaml` | Helm chart values |
| `./chart/<projectname>/templates/deployment.yaml` | Deployment template |
| `./chart/<projectname>/templates/service.yaml` | Service template |
{: caption="Table 6. Contents of a generated Swift app chart directory" caption-side="top"}

| `./manifests/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes Service & Deployment yaml |
{: caption="Table 7. Contents of a generated manifests directory" caption-side="top"}

