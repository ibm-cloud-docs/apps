---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: apps, credentials, kubernetes, kube, add, custom, deployment.yml, cluster, deployment, environment, kubectl, secret

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Kubernetes 환경에 서비스 인증 정보 추가
{: #add-credentials-kube}

Kubernetes 배치 환경에 서비스 인증 정보를 추가하는 방법에 대해 알아봅니다.
{: shortdesc}

다음 시나리오에서는 배치 환경에 서비스 인증 정보를 수동으로 추가해야 합니다.
 * 자체 코드를 가져옵니다.
 * 공백 스타터 킷 템플리트에서 시작합니다.
 * 배치된 _이후_ 스타터 킷 기반 앱에 서비스를 추가합니다.

## 사용자 코드 + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### 올바른 코딩

예방적 측면에서, 해당 환경이 애플리케이션의 기본 시작점에서 완료되었는지 확인하도록 애플리케이션을 코딩할 수 있습니다. 해당 환경이 완료되지 않은 클러스터로 애플리케이션을 승격하여 제품에 지장을 초래하는 일은 원하지 않습니다. 애플리케이션은 시작을 거부할 수 있으며 Kubernetes 구성은 자동으로 이러한 지장을 방지할 수 있습니다.

다음 2개의 환경 변수가 있다고 가정합니다.
* `SECRET`
* `NOT_SECRET`

데이터베이스의 경우, 변수는 `APIKEY` 및 `DB_URL`일 수 있습니다. 여기서 앞의 변수는 민감하며 뒤의 변수는 그렇지 않습니다.

Java에서 사용자는 다음과 같이 기본 애플리케이션 시작점에서 무언가를 작성하고자 할 수 있습니다.
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

Node에서 유사한 예를 확인하십시오.
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### 환경 준비

Kubernetes `deployment.yml` 파일에서 환경 변수 또는 _클러스터의 시크릿에 대한 참조_가 정의될 수 있습니다.

#### 환경에서 인증 정보를 가져오도록 배치 설정

`kind: Deployment`의 섹션에서 `spec.template.spec.containers` 이후의 들여쓰기 레벨에 다음의 예제 코드를 추가하십시오.
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* **저장**을 클릭하십시오.

동일한 `name-secret` 및 키 `KEY_SECRET`의 _secretKeyRef_가 값으로 분석되도록 클러스터를 구성하십시오.

#### 사전 필수 도구 설치

워크스테이션에서 터미널을 사용하여 다음 도구를 설치하십시오.

1. [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 설치하십시오.
2. `ibmcloud login` 명령을 사용하여 로그인하십시오.
3. `ibmcloud cs cluster-config {your_cluster_name}`을 실행하여 클러스터에 연결하십시오.
4. `export` 명령을 복사하여 붙여넣고 터미널에서 이를 실행하십시오.

#### 클러스터에서 시크릿 정의

{{site.data.keyword.dev_cli_notm}}에서는 `kubectl`을 제공하며, 사용자가 Kubernetes 클러스터에 연결되어 있으므로 이를 실행할 수 있습니다.

분석 가능한 시크릿을 정의하려면 다음의 `kubectl` 명령을 사용하십시오.
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

이제 Kubernetes 클러스터가 분석 가능한 시크릿과 함께 준비되었으므로 `deployment.yml` 파일에 정의된 환경 변수를 사용하도록 애플리케이션을 업데이트할 수 있습니다.

## 스타터 킷 앱 및 Kubernetes
{: #credentials-starterkit-kube}

1. 앱의 **앱 세부사항** 페이지로 이동하십시오.

2. Cloud Object Storage의 인스턴스를 작성하려면 **서비스 추가** > **스토리지** > **Cloud Object Storage** > **Lite 플랜(무료)** > **작성**을 선택하십시오.

3. **코드 다운로드**를 클릭하여 삽입된 코드 스니펫으로 앱을 다시 생성하십시오.

4. 로컬로 인증 정보에 액세스하려면 새로 생성된 `.zip` 파일에서 인증 정보에 액세스하기 위한 로컬 Git 복제본으로 다음 파일을 복사하여 대체하십시오. 인증 정보를 호스팅할 수 있도록 클러스터에서 여전히 Kubernetes 시크릿을 작성해야 합니다.

   - `chart/{appName}/bindings.yaml` - 시크릿을 지시하는 Kubernetes 클러스터에서 환경 변수를 생성합니다.
   - `src/main/resources/localdev-config.json` - 로컬로 앱을 실행하는 중에 인증 정보에 액세스합니다.
   - `src/main/resources/mappings.json` - 코드에서 환경 변수에 액세스하기 위한 [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) 메소드에 대한 액세스를 제공하는 맵핑입니다.
   - `manifest.yml` - 이 파일은 서비스를 Cloud Foundry 애플리케이션에 바인딩합니다.

  나중에 리소스 제어기 리소스(조직 또는 영역이 아닌 리소스 그룹에 있는)로 Cloud Foundry 애플리케이션에 배치하도록 선택하는 경우에는 1개의 추가 파일을 복사해야 합니다.
  {: note}

5. 해당 지역(무료인 경우 미국 남부)의 [Kubernetes 클러스터 보기](https://{DomainName}/kubernetes/clusters){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 확인하십시오.

6. 클러스터를 클릭하고 오른쪽 상단에서 **Kubernetes 대시보드**를 선택하여 클러스터 대시보드를 보십시오.

7. **시크릿**이라는 레이블이 지정된 섹션이 보일 때까지 아래로 스크롤하십시오. `binding-{appName}-{serviceName}-{timestamp}` 규약을 사용하는 {{site.data.keyword.cloudant_short_notm}} 서비스 인스턴스의 시크릿을 볼 수 있습니다. `chart/{appName}/bindings.yaml` 파일에서 해당되는 {{site.data.keyword.cloudant_short_notm}} 시크릿을 찾을 수 있습니다.

8. 이제 `binding-create-app-ktibr-cloudobjectstor-1538170732311`과 유사해 보이는 `chart/{appName}/bindings.yaml`에서 이미 생성된 시크릿 이름의 Cloud Object Storage 인스턴스에 대해 해당되는 항목을 작성할 수 있습니다.

9. 대시보드의 **앱 세부사항** 페이지로 이동하여 Cloud Object Storage 인스턴스의 인증 정보를 복사하십시오. 다음의 예제 인증 정보 출력을 확인하십시오.
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
    "resource_instance_id": "crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. `ibmcloud cs cluster-config {your_cluster_name}`을 사용하고 다음의 지시사항의 명령을 내보내서 클러스터가 구성되었는지 확인하십시오.

11. `echo` 명령을 사용하여 인증 정보를 `binding` 파일에 두십시오.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`으로 시크릿을 작성하십시오. Kubernetes 클러스터 대시보드로 되돌아가면 작성된 시크릿을 볼 수 있습니다.

  Cloud Foundry 애플리케이션을 배치하는 경우, 리소스 제어기 인스턴스를 사용 중이면 사용자 제공 서비스를 작성해야 합니다(리소스가 리소스 그룹 대 조직 또는 영역에 있는 경우). 
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"ccrn:v1:staging:public:cloud-object-storage:global::a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  사용자 제공 서비스의 이름은 해당되는 인스턴스 이름으로 `manifest.yml` 파일에서 찾을 수 있습니다.

13. 이제 애플리케이션이 Kubernetes 클러스터에서 실행될 때 `env.getProperty` 메소드를 통해 환경 변수를 이용하여 시크릿에 액세스할 수 있습니다.

### Kubernetes 클러스터의 준비 방법

**지속적 딜리버리 구성** 기능을 사용하여 앱을 IBM Kubernetes 클러스터에 배치할 수 있습니다. 이 기능은 앱과 연관된 리소스의 인증 정보에 대한 시크릿으로 Kubernetes 클러스터를 준비합니다. 다음 단계를 완료하여 클러스터 준비의 결과를 관찰할 수 있습니다.

1. 결과를 보려면 다음 명령을 실행하십시오.

  ```
  kubectl get secrets
  ```
  {: codeblock}

  [시크릿에 대한 추가 문서](https://kubernetes.io/docs/concepts/configuration/secret/)를 볼 수 있습니다.
  {: tip}

2. 시크릿 이름이 리소스 이름인지 관찰하십시오.
3. `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml`을 사용하여 시크릿에 대한 상세 정보를 보십시오.

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  `binding`은 시크릿의 base64 인코딩된 값입니다. 이를 디코딩하면 서비스 인스턴스의 `credentials` 및 일부 `iam_...` 값의 원시 JSON에 불과함이 드러납니다.
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

`deployment.yml`이 시크릿을 참조하는 `env` 값을 선언하지 않는 한 애플리케이션 코드로 Kubernetes 시크릿을 검색할 수 없습니다. 스타터 킷을 사용하면 해당 코드가 자동 생성됩니다.

### 스타터 킷에서 생성된 코드
{: #credentials-starterkit-kube-gencode}

이 경우에는 사용자가 스타터 킷에서 이 애플리케이션을 작성했습니다. 스타터 킷에서 생성된 코드는 Cloud Foundry 또는 Kubernetes에서 로컬로 실행되는 이식 가능한 코드가 될 수 있습니다. `IBMCloudEnv` 라이브러리는 서비스 인스턴스의 인증 정보를 보유하는 환경 변수의 검색 및 애플리케이션 코드 간의 추상 계층을 제공하는 데 사용됩니다.

스타터 킷에서 작성된 코드에는 `IBMCloudEnv` 라이브러리에 대한 종속성이 있으며 다음과 같은 결과를 생성합니다.

* `bindings.yml` 파일 - 다음 컨텐츠로 `deployment.yml` 파일에서 인라인으로 포함됩니다.
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  `secretKeyRef.name`은 애플리케이션 코드의 단순 환경 변수로서 애플리케이션이 검색할 수 있는 정의된 Kubernetes 시크릿을 노출합니다.

* `IBMCloudEnv` 라이브러리에 대한 지시사항은 스타터 킷에서 생성된 코드 베이스에 있는 `mappings.json` 파일에 캡슐화되어 있습니다. `mappings.json`에는 각 인증 정보의 개별 정의가 있습니다.
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

  `mappings.json` 파일은 `jsonpath` 구문과 `searchPatterns` 배열의 순서를 사용하여 `IBMCloudEnv` 로직을 설명합니다.

* 다음 코드를 사용하여 Cloudant API 키를 검색하십시오(유사 코드).
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

`IBMCloudEnv` 라이브러리는 애플리케이션이 Kubernetes, Cloud Foundry 또는 가상 서버 인스턴스(로컬 Docker와 동일하게 처리됨)에서 실행 중인지 여부를 자동으로 감지하며, 올바른 `searchPattern`를 적용하여 리턴 값을 찾습니다.

따라서 `mappings.json` 파일은 앱이 실행되는 환경에서 가져온 즉시 사용 가능한 사전 구성 값의 _정의 목록_으로 간주됩니다. 값은 **지속적 딜리버리 구성** 기능을 사용한 시점에 대상으로 지정한 클러스터의 환경에서 채워집니다.
