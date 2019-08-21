---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: apps, mendix, mendix app, deploy, cos, storage bucket, devops toolchain, deploy, kubernetes, kube

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.containerlong_notm}}에 Mendix 앱 배치
{: #deploy-mendix-kube}

기본적으로 {{site.data.keyword.containerlong}} 배치를 대상으로 하는 Mendix 애플리케이션은 평가 모드로 설정됩니다. 이 모드를 사용하면 앱을 신속하게 빌드하기 시작하고 클라우드에 배치할 수 있지만 데이터 지속성 또는 고급 Kubernetes 구성을 구성하지는 않습니다. 이 튜토리얼은 {{site.data.keyword.cos_full_notm}} 서비스로 Kubernetes에서 지속적 스토리지 볼륨을 설정하여 프로덕션 환경에 대한 구성을 안내합니다.
{: shortdesc}

## 시작하기 전에
{: #prereqs-mendix-kube}

* Mendix 앱을 작성하십시오. 자세한 정보는 [Mendix 앱 작성](/docs/apps/tutorials?topic=creating-apps-create-mendix)을 참조하십시오.
* {{site.data.keyword.containershort_notm}} CLI를 포함하여 [{{site.data.keyword.dev_cli_notm}} 명령행 인터페이스(CLI)](/docs/cli?topic=cloud-cli-getting-started)를 설치하십시오.
* `ibmcloud` CLI에 로그인하고 [Kubernetes 클러스터에 액세스](/docs/containers?topic=containers-cs_cluster_tutorial#cs_cluster_tutorial_lesson3)할 수 있도록 `kubectl`을 구성하십시오.

## Cloud Object Storage 서비스 인스턴스 작성
{: #cos-mendix-kube}

**앱 세부사항** 페이지에서 시작하여 다음 단계를 수행하십시오.
1. **서비스 추가**를 클릭하십시오.
2. **스토리지**를 선택하고 **다음**을 클릭하십시오.
3. 다음으로, **Cloud Object Storage** 옵션을 선택하고 **다음**을 클릭하십시오.
4.  {{site.data.keyword.cos_full_notm}} 인스턴스에 대한 가격 플랜이 제시됩니다. 사용자 요구에 가장 적합한 가격 플랜을 선택한 다음 **작성**을 클릭하여 Mendix 앱에서 사용할 {{site.data.keyword.cos_full_notm}} 서비스의 인스턴스를 작성하십시오.

  {{site.data.keyword.cos_full_notm}} 서비스의 기존 인스턴스를 사용하려면 **서비스 추가**를 클릭하고 사용할 앱의 기존 인스턴스를 선택하십시오.
  {: tip}

## 스토리지 버킷 작성
{: #storage-bucket-mendix-kube}

{{site.data.keyword.cos_full_notm}} 서비스의 인스턴스가 Mendix 앱과 연관되면 데이터를 저장할 수 있는 스토리지 버킷을 작성해야 합니다. 버킷을 작성하려면 {{site.data.keyword.cos_full_notm}} 인스턴스의 **...**를 클릭하고 **대시보드 열기**를 선택하십시오.  

{{site.data.keyword.cos_full_notm}} 서비스 대시보드가 새 창의 **버킷** 탭에서 열립니다. **버킷 작성**을 클릭하고, 단계에 따라 고유한 이름을 사용하여 버킷을 작성하십시오. 이 튜토리얼에서는 `my-mendix-bucket`이라는 버킷을 작성하십시오.

## 지속적 스토리지 구성
{: #kube-storage-mendix}

다음으로, [{{site.data.keyword.cos_full_notm}}에 데이터 저장](/docs/containers?topic=containers-object_storage)에 대한 문서를 따르십시오. `PersistentVolumeClaim` 및 `PersistentVolume`이 Kubernetes 클러스터에 작성되고, Mendix 앱의 일부로 클러스터에서 실행되는 PostGres 데이터베이스 인스턴스에서 이를 사용할 수 있습니다. 이전 단계에서 설명한 대로 `my-mendix-bucket` 버킷을 사용하여 `PersistentVolumeClaim`을 작성해야 하며 다음 단계에서 사용하기 위해 `PersistentVolumeClaim` 이름을 검토해야 합니다.

## `postgres-deployment.yaml` 파일 편집
{: #postgres-deploy-mendix}

Kubernetes 클러스터에 대한 지속적 볼륨이 구성되고 나면 다음 단계는 클러스터 내에서 실행되는 PostGres 데이터베이스 배치를 수정하는 것입니다. 먼저 IBM DevOps 도구 체인 통합 단계의 일부로 작성된 파일을 Git 저장소에서 편집해야 합니다. Git 저장소를 찾으려면 **앱 세부사항** 페이지로 돌아가서 **배치 세부사항** 타일에서 Git URL 링크를 클릭하십시오.

Git 저장소를 로컬 시스템에 복제하거나 온라인 편집기에서 다음을 변경할 수 있습니다. `chart/{app name}/templates/postgres-deployment.yaml` 파일을 여십시오(`{app name}`은 Mendix 앱 이름으로 대체). 파일에는 기본적으로 기존 `volumeMount` 또는 `volumes` 항목이 없으므로 모든 데이터는 실행 중인 배치 팟(Pod) 내의 인메모리에 저장됩니다. 데이터를 {{site.data.keyword.cos_full_notm}}에 저장하고 팟을 다시 시작하는 경우에도 데이터가 유실되지 않도록 하려면 `volumeMount` 및 `volumes` 항목을 모두 Kubernetes `deployment.yaml` 파일에 추가해야 합니다. 

`volumeMount` 및 `volumes` 항목이 포함된 다음 샘플 `postgres-deployment.yaml`을 참조하십시오.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

`{pvc-name}`을 이전 단계의 `PersistentVolumeClaim` 이름으로 대체해야 하며, Git 저장소의 파일에 이미 설정된 앱 이름을 겹쳐쓰지 않도록 주의해야 합니다. 그런 다음 변경사항을 Git 저장소에 다시 커미트하십시오.

## 재배치
{: #redeploy-mendix-kube}

`postgres-deployment.yaml` 파일 변경사항이 저장소에 다시 커미트되고 나면 새 DevOps 파이프라인 실행이 자동으로 트리거됩니다. 그러나 기본 앱을 다시 배치합니다. 지속적 볼륨에 대한 최신 변경사항이 포함된 최신 버전의 앱을 배치하려면 최신 버전의 Mendix 앱을 다시 배치해야 합니다.

다시 배치하려면 **앱 세부사항** 페이지로 이동하여 **앱 배치** 타일에 있는 **지속적 딜리버리 구성**을 클릭하십시오. 앱의 `.mda` 파일을 찾을 수 없다는 오류와 함께 DevOps 도구 체인 내에서 배치가 실패하면 Mendix에서 앱을 다시 내보내야 합니다. Mendix Modeler 데스크탑 앱에서 내보내거나 **Mendix에서 편집**을 클릭하여 내보낼 수 있습니다. 그런 다음 Mendix 웹 인터페이스에서 **환경** 섹션으로 이동하여 **팀 서버에서 패키지 작성**을 클릭한 후 해당 단계를 수행하십시오. Mendix에서 앱을 내보낸 후 **앱 세부사항** 페이지로 돌아가 **지속적 딜리버리 구성**을 한 번 더 클릭하십시오. {{site.data.keyword.cloud}} DevOps 도구 체인을 사용하여 최근에 내보낸 앱을 Kubernetes 클러스터에 배치합니다. 배치가 완료되면, 앱이 활성 상태가 되고 프로덕션에 사용할 준비가 됩니다.

## 앱이 실행 중인지 확인
{: #verify-mendix-kube}

앱을 배치하고 나면 Delivery Pipeline 또는 명령행이 사용자를 앱의 URL로 이동시킵니다.

1. DevOps 도구 체인에서 **Delivery Pipeline**을 클릭한 후 **배치 단계**를 선택하십시오.
2. **로그 및 히스토리 보기**를 클릭하십시오.
3. 로그 파일에서 앱의 URL을 찾으십시오.

    로그 파일의 끝에서 단어 `urls` 또는 `view`를 찾으십시오. 예를 들면, 로그 파일에서 `urls: my-app-devhost.mybluemix.net` 또는 `View the application health at: http://<ipaddress>:<port>/health`와 같은 행을 볼 수 있습니다.

4. 브라우저에서 해당 URL로 이동하십시오. 앱이 실행 중인 경우에는 `Congratulations` 또는 `{"status":"UP"}`와 같은 항목을 포함하는 메시지가 표시됩니다.

명령행을 사용하는 경우에는 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 명령을 사용하여 앱의 URL을 보십시오. 그 후 브라우저에서 해당 URL로 이동하십시오.

## 추가 정보
{: #more-info-mendix-kube}

Kubernetes 환경에서 실행 중인 Mendix 앱에 대한 아키텍처 세부사항을 보려면 Mendix 사용자 문서의 [Kubernetes에서 Mendix 실행](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 절을 검토하십시오.
