---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, deploying apps, containers, kubernetes, docker, clusters, devops toolchain, deployment, kube

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Kubernetes로 컨테이너 사용
{: #containers-kube}

Kubernetes 클러스터에서 실행되는 Docker 컨테이너에 고가용성 앱을 배치하여 {{site.data.keyword.containershort}}를 시작하십시오. Git을 사용하여 팀 개발을 관리한 후 DevOps 도구 체인을 사용하여 Kubernetes에 대한 앱 배치를 관리하십시오.
{: shortdesc}

컨테이너는 환경 간에 앱을 원활하게 이동할 수 있도록 앱과 해당 앱에 종속된 모든 항목을 패키징할 수 있는 표준 방법입니다. 가상 머신과는 달리 컨테이너는 운영 체제를 번들화하지 않습니다. 앱 코드, 런타임, 시스템 도구, 라이브러리 및 설정만 컨테이너 내부에 패키징됩니다. 컨테이너는 가상 머신보다 좀 더 경량이고, 휴대하기 쉬우며, 효율적입니다.

서비스에 대해 자세히 알아보려면 [{{site.data.keyword.containershort_notm}} 시작하기](/docs/containers?topic=containers-container_index)를 참조하십시오.

## 배치 구성
{: #config-deploy}

백엔드 또는 웹 제공 앱을 작성하는 경우 Kubernetes 환경을 사용하는 {{site.data.keyword.containershort_notm}} 서비스에 이 앱을 배치할 수 있습니다.

1. 자동화된 클라우드 파이프라인을 설정하여 앱을 클라우드에 배치하십시오.
2. **지속적 딜리버리 구성**을 클릭하십시오.
3. 대상으로 **IBM Kubernetes Service**를 선택하십시오. 아직 클러스터가 하나도 없으면 [클러스터 작성 ](https://{DomainName}/kubernetes/catalog/cluster/create){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")을 수행해야 합니다.
4. 배치가 완료된 후 Delivery Pipeline의 배치 단계에서 로그의 URL을 가져와서 클라우드에 있는 라이브 앱을 확인하십시오. 포트가 포함된 마지막 IP 주소는 앱의 새 홈입니다(예: 169.60.133.124:32355).

## 서비스 바인딩
{: #bind-services}

도구 체인이 작성되면 앱과 연관된 서비스가 Kubernetes 시크릿을 사용하여 Kubernetes 클러스터에 바인드됩니다. 시크릿은 실행 중인 앱의 외부에서 서비스 인증 정보를 관리하는 데 사용됩니다. 앱은 시크릿을 읽은 후 실행을 시작하는 데 필요한 값을 검색합니다. 서비스를 바인드하면 프로덕션 레벨 {{site.data.keyword.cloud}} 서비스 인스턴스를 사용하고 있을 수 있는 다른 Kubernetes 환경에 앱을 배치할 수 있습니다.

서비스 또는 시크릿을 삭제한 경우 수동으로 이를 다시 바인드하거나 도구 체인을 삭제한 후 다시 작성해야 합니다.
{: tip}

자세한 정보는 [시크릿 ](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")을 참조하십시오.

## 개발 시작
{: #dev}

1. 도구 체인에서 새 온라인 Git 저장소를 확인하고 코드 관련 작업을 시작하십시오. 도구 체인을 확인하려면 **도구 체인 보기**를 클릭하십시오.
2. 저장소를 로컬 환경에 복제하여 코드를 작성한 Git 저장소에 액세스하십시오.
3. 선호하는 IDE를 사용하여 프로젝트를 여십시오.

## 도구 체인을 사용하여 빌드 및 배치
{: #bulid-deploy-tc}

도구 체인에는 빌드 단계와 배치 단계가 포함되어 있습니다.

### 빌드 단계
{: #build-stage}
빌드 단계는 `git push`가 Git 저장소에서 실행될 때 트리거됩니다. 파이프라인의 단계에서는 Docker 이미지 빌드를 트리거하고 컨테이너 레지스트리에 이미지를 배치합니다.

자세한 정보는 [IBM Cloud Container 레지스트리 시작하기](/docs/services/Registry?topic=registry-index)를 참조하십시오.

### 배치 단계
{: #deploy-stage}

배치 단계는 {{site.data.keyword.registryshort_notm}}에서 최신 이미지를 검색한 후 Helm 차트를 사용하여 최신 이미지를 Kubernetes 클러스터에 배치합니다. Helm 차트는 클라우드에 배치할 때 앱에 추가되었습니다. Helm 차트를 사용하면 패키징된 컨테이너 이미지의 배치 단계를 쉽게 관리할 수 있습니다.

자세한 정보는 [차트 ](https://docs.helm.sh/developing_charts/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 참조하십시오.

{{site.data.keyword.cloud_notm}}는 다수의 [사전 구성된 Helm 차트 ](https://{DomainName}/kubernetes/solutions/helm-charts){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 지원합니다.

## 앱 보안 확인
{: #sec}

{{site.data.keyword.containershort_notm}}는 보안 취약점에 대한 패키징된 컨테이너 이미지의 스캔을 지원합니다. 보안 스캔은 엔터프라이즈급 애플리케이션을 지원하는 데 필수입니다.

잠재적인 보안 취약점을 확인하려면 컨테이너 [이미지 저장소 ](https://{DomainName}/kubernetes/registry/main/private){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 보십시오.
