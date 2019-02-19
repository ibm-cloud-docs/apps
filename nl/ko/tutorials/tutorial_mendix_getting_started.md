---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-06"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Mendix를 사용하여 앱 작성
{: #create-mendix}

Mendix는 {{site.data.keyword.cloud}}에서 실행되는 로우 코드(low-code) 개발 환경이자 도구 세트로, 더 적은 개발 리소스를 사용하여 보다 신속하게 여러 장치 애플리케이션을 제공하는 데 도움을 줍니다. Mendix 로우 코드 스타터 킷을 선택하면 Mendix 플랫폼에서 계정을 설정하고, 프로젝트를 시작하며, Cloud Foundry 또는 Kubernetes 클러스터 중에서 개발 환경을 선택하는 과정을 안내합니다.
{: shortdesc}

## 스타터 킷 선택
{: #starterkit-mendix}

1. [{{site.data.keyword.cloud_notm}} 앱 서비스 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/developer/appservice/dashboard){: new_window}에서 **시작하기**를 클릭하십시오.
2. 다음 카테고리 중 하나에서 Mendix 로우 코드 스타터 킷을 선택하십시오.
  * [모바일 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson 웹 또는 모바일 앱 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [웹 앱 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app)
3. **앱 작성**을 클릭하십시오.
4. **앱 세부사항** 페이지에서 앱의 이름을 지정하고 앱을 분류하기 위한 태그를 선택적으로 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources/tagging_resources.html#tag)을 참조하십시오.
5. **작성**을 클릭하십시오.


## IBM에 Mendix 및 링크 계정에서 프로젝트를 작성할 권한 부여
{: #link-mendix-account}

아직 {{site.data.keyword.cloud_notm}}에서 Mendix를 사용하고 있지 않으면, Mendix 플랫폼에 가입하고 사용자 대신 Mendix 플랫폼에서 새 프로젝트를 작성하도록 {{site.data.keyword.cloud_notm}}에 권한을 부여하는 과정을 안내합니다. 이 프로젝트는 {{site.data.keyword.cloud_notm}}에 링크되므로 배치는 자동으로 {{site.data.keyword.cloud_notm}}으로 이동합니다.

1. "앱 작성을 완료하려면 Mendix 사용자 계정이 필요합니다. 지금 계정에 링크하시겠습니까?"라는 메시지가 표시되면, **계정 링크**를 클릭하십시오.
2. Mendix 확인 페이지에서 **Mendix 개인정보처리방침 및 이용 약관에 동의합니다**를 선택하고 **확인**을 클릭하십시오.
3. 프롬프트가 표시되면 이메일 주소, 비밀번호 및 국가를 지정하고 **작성**을 클릭하십시오.
4. **Mendix 계정에 액세스할 권한 부여** 페이지에서 **권한 부여**를 클릭하십시오.

권한 부여가 완료되면, 브라우저가 작성 중인 Mendix 앱으로 돌아갑니다. **배치 환경 선택** 페이지가 표시됩니다.

## Mendix 앱의 배치 옵션 선택
{: #select-deployment}

1. **배치 환경 선택** 페이지에서 Cloud Foundry, 또는 {{site.data.keyword.cloud_notm}}에서 실행 중인 Kubernetes 클러스터 중 하나를 선택하십시오. 계정에 {{site.data.keyword.cfee_full_notm}}에 대한 액세스 권한이 있는 경우에는 **[퍼블릭 클라우드](/docs/cloud-foundry-public/about-cf.html#about-cf)** Cloud Foundry 배치자 유형을 선택하거나, 사용자 엔터프라이즈 전용으로 Cloud Foundry 애플리케이션을 호스팅하는 격리된 환경을 작성하고 관리하는 데 사용할 수 있는 **[엔터프라이즈 환경](/docs/cloud-foundry-public/cfee.html#cfee)** Cloud Foundry 배치자 유형을 선택할 수 있습니다. 
2. 선택사항. Kubernetes 클러스터가 없는 경우 지금 하나를 작성할 수 있습니다.
3. **도구 체인 구성** 페이지에서 사용자의 영역과 리소스 그룹을 선택한 후 **작성**을 클릭하십시오.

DevOps 도구 체인이 작성됩니다. 도구 체인은 {{site.data.keyword.cloud_notm}} 환경에서 Mandix 플랫폼 내에 Mendix 프로젝트를 통합합니다. DevOps 도구 체인이 완료 시 애플리케이션이 배치되었는지 확인할 수 있도록 기본 애플리케이션이 대상 배치에 배치됩니다.

Mendix Cloud Foundry 배치에는 Lite 티어 없는 PostGRES 데이터베이스 서비스가 필요합니다. Lite 계정을 사용하여 Mendix 스타터 킷을 평가하려는 경우, 평가판 Kubernetes 클러스터를 대상으로 할 수 있습니다.
{: tip}

배치에 Kubernetes 클러스터를 선택한 경우, [Mendix Kubernetes 튜토리얼](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube)을 참조하여 프로덕션 사용을 위해 클러스터를 구성하는 방법을 알아보십시오.


## Mendix 배치 및 배치 라이프사이클 계속 수행
{: #dev-lifecycle-mendix}

Mendix는 로우 코드 작성 환경입니다. 개발 라이프사이클을 수행하려면 Mendix Modeler 데스크탑 애플리케이션에서 프로젝트를 열어야 합니다.

1. {{site.data.keyword.cloud_notm}} 애플리케이션에서 **Mendix에서 편집**을 클릭하십시오.
2. Mendix 웹 포털에서 **Desktop Modeler에서 편집**을 클릭하십시오.
  Mendix 애플리케이션이 Desktop Modeler에서 열립니다.
3. Mendix 앱을 을 편집하고 변경사항을 저장하십시오.
4. Mendix Desktop Modeler 애플리케이션의 **실행** 메뉴를 사용하고 **실행** 옵션을 선택하십시오.
  배치 패키지가 작성되어 Mendix에 업로드됩니다. 배치 패키지가 작성되면 애플리케이션을 {{site.data.keyword.cloud_notm}}에 배치할 수 있습니다.
5. Mendix 애플리케이션을 배치하려면 {{site.data.keyword.cloud_notm}}의 **앱 세부사항** 페이지로 돌아가 **애플리케이션 배치**를 클릭하십시오.
  이 조치는 애플리케이션의 DevOps 도구 체인을 시작하며, 이를 통해 Mendix에서 최근 배치를 가져와서 대상 환경에서 배치합니다. 배치가 완료되면 최신 버전의 애플리케이션이 자동으로 시작되고 사용 가능하게 됩니다.

{{site.data.keyword.cloud_notm}}의 **앱 세부사항** 페이지에서 **애플리케이션 배치**를 클릭하면 모든 Mendix 애플리케이션이 {{site.data.keyword.cloud_notm}}에 배치됩니다. IBM DevOps 인터페이스를 통해 Mendix 도구 체인을 수동으로 호출하지 마십시오. DevOps 인터페이스를 통해 도구 체인을 수동으로 실행하면 Mendix 배치에 중요한 필수 메타데이터 부족으로 인해 배치가 실패할 수 있습니다. 애플리케이션 상태에 따라 DevOps 도구 체인 실행 중에 실패하거나 배포된 애플리케이션에서 오류가 발생할 수 있습니다. 도구 체인을 수동으로 실행하여 실패하는 경우 {{site.data.keyword.cloud_notm}}의 **앱 세부사항** 페이지에서 **애플리케이션 배치**를 클릭하여 애플리케이션 배치를 복원할 수 있습니다. 이 조치는 Mendix 애플리케이션을 위한 완전한 DevOps 플로우를 트리거하며, 여기에는 필수 메타데이터가 포함되어 있습니다.
{: tip}

## 다음 단계 
{: #next-steps-mendix}

앱을 {{site.data.keyword.containerlong_notm}}에 배치하려면 프로덕션 배치를 위해 앱을 구성하십시오. 자세한 정보는 [Mendix Kubernetes 튜토리얼](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube)을 참조하십시오.  
