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

# Python app files
{: #python-project-files}

For Python apps, the following information is an inventory of what you typically find in {{site.data.keyword.Bluemix}}. When you create a starter kit, these files are created for you. If you're migrating an app to host in {{site.data.keyword.Bluemix_notm}}, you might want to review this information to avoid potential conflicts.
{:shortdesc}

The following table lists the common directories and files that are included in a generated Python app.

| Root directory                                     | Description                       |
|:------------------------------------------------|:------------------------------------------|
| requirements.txt | Required Python packages |
| setup.py | Python installer script |
| cli-config.yml | CLI configuration options |
| manifest.yml | Cloud Foundry deployment file |
| Dockerfile | Dockerfile for `ibmcloud dev run`, `ibmcloud dev deploy`, and `docker` commands |
| `Dockerfile-tools` | Dockerfile for `ibmcloud dev build` and `ibmcloud dev test` |
| LICENSE | License file |
| README.md | Description of app |
{: caption="Table 1. Contents of a generated Python app root directory" caption-side="top"}

| `./public/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| swagger.yml | Swagger specification for describing REST APIs |
| index.html | Skeleton markup for web applications |
{: caption="Table 2. Contents of a generated Python app public directory" caption-side="top"}

| `./server/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Marks directories as Python package directories |
{: caption="Table 3. Contents of a generated Python app server directory" caption-side="top"}

| `./tests/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| app_tests.py | Python server test cases |
{: caption="Table 4. Contents of a generated Python app tests directory" caption-side="top"}

| `./.bluemix/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container build script |
| deploy.json | Deployment information |
| kube_deploy.sh | Kubernetes deployment script |
| pipeline.yml | IBM Cloud pipeline definition |
| toolchain.yml | IBM Cloud toolchain definition |
{: caption="Table 5. Contents of a generated Python app bluemix directory" caption-side="top"}

| `./chart/<projectname>/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm chart |
| `./chart/<projectname>/values.yaml` | Helm chart values |
| `./chart/<projectname>/templates/deployment.yaml` | Deployment template |
| `./chart/<projectname>/templates/service.yaml` | Service template |
{: caption="Table 6. Contents of a generated Python app chart directory" caption-side="top"}
