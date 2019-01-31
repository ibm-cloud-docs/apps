---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} 개발자 콘솔 검토
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience를 사용하여 클라우드 고유 애플리케이션 개발자는 다양한 스타터 킷에서 앱을 작성하고 주요 {{site.data.keyword.Bluemix_notm}} 최적화된 서비스를 작성 및 연결한 후에 작업 중인 코드를 신속하게 다운로드하거나 지속적 딜리버리를 위해 설정할 수 있습니다. Developer Experience는 앱 작성, 보기, 구성 및 관리는 물론 이를 devops 파이프라인에 배치하거나 로컬 개발을 위해 이를 다운로드할 수 있도록 허용하는 {{site.data.keyword.Bluemix_notm}}에서의 개발자 콘솔 세트를 제공합니다. 

{{site.data.keyword.cloud_notm}} 개발자 콘솔을 통해 앱을 작성하면 앱의 모든 필수 부분이 {{site.data.keyword.cloud_notm}} 서버에서 사용자 계정으로 유지보수됩니다. 따라서 선택이 필요한 경우 개발자 콘솔 GUI 및 [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) 간의 상호 이동이 가능합니다. 

{{site.data.keyword.cloud_notm}} 개발자 콘솔은 선택된 유스 케이스에 대해 프로덕션 준비된 스타터 앱을 빌드하기 위한 완벽한 경로를 제공합니다. 해당 과정에서 취할 수 있는 단계를 살펴봅니다. 

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##개요 화면
{: #overview_screen}

개요 화면은 작업 중인 개발자 콘솔의 주제 또는 채널 초점에 맞게 조정된 컨텐츠를 제공합니다. 개요 화면에서 문서를 보고 학습 리소스에 액세스하며 서비스를 찾아보고 주요 스타터 킷을 보거나 보다 큰 스타터 킷 콜렉션에 링크할 수 있습니다. 탐색에서 `스타터 킷`을 클릭하여 스타터 킷 보기를 시작하십시오. 

![개발자 콘솔 개요 화면](images/overview_screen.png "개요 화면") <br> *개발자 콘솔 개요 화면*

##스타터 킷 보기
{: #starter_kits_view}

스타터 킷 보기는 유스 케이스 영역에 특정한 스타터 킷의 콜렉션을 표시합니다. 스타터 킷 카드의 다양한 링크를 클릭하여 데모와 자세한 정보를 볼 수 있습니다. 앱 새로 작성 보기로 이동하려면 스타터 킷을 선택하십시오. 

일부 경우, 스타터 킷을 선택하면 스타터 킷에 대한 상세 정보로 이동됩니다. 해당 경우에는 단순히 `작성` 단추를 클릭하여 앱 새로 작성 보기로 이동하십시오. {: tip}

![개발자 콘솔 스타터 킷 보기](images/starter_kits_view.png "스타터 킷 보기") <br> *개발자 콘솔 스타터 킷 보기*

##앱 새로 작성 보기
{: #create_new_project_view}

앱 새로 작성 보기에서 앱 이름을 지정하고 배치 및 라우팅 정보를 제공하며 언어를 선택합니다. 참고로, 오른쪽에서 가격 플랜 및 각각의 이용 약관과 함께 앱 작성 시에 자동으로 프로비저닝될 서비스를 볼 수도 있습니다. 앱 세부사항 보기로 이동하려면 `작성`을 클릭하십시오. 아직 {{site.data.keyword.cloud_notm}}에 로그인하지 않았으면 지금 로그인해야 합니다. 

![개발자 콘솔 앱 새로 작성 보기](images/create_new_project_view.png "앱 새로 작성 보기") <br> *개발자 콘솔 앱 새로 작성 보기*

## 앱 세부사항 보기
{: #project_details_view}

앱 세부사항 보기는 앱에 대해 구성된 서비스의 목록을 표시합니다. 목록의 각 항목에 대해 서비스 이름, 기타 정보에 대한 링크 및 3개의 수직 배열된 점이 있는 *조치* 단추가 나타납니다. *조치* 단추 옵션은 앱에서 서비스를 제거하고 서비스의 대시보드를 열며 서비스를 삭제하는 용도로 사용됩니다. 참고로, 서비스 인스턴스 제거는 단지 이 앱에 대한 연관만 제거하며 서비스 인스턴스를 삭제하지는 않습니다. 또한 가져오기 위해 각각의 개별 서비스 인스턴스 보기를 방문할 필요가 없도록 서비스 인증 정보는 이 보기에서 통합되어 있음을 참고하십시오. 

![개발자 콘솔 앱 세부사항 보기](images/project_details_view.png "앱 세부사항 보기") <br> *개발자 콘솔 앱 세부사항 보기*

또한 앱 세부사항 보기를 사용하여 신규 또는 기존 서비스를 원래 스타터 킷의 일부가 아닌 사용자 앱에 추가할 수 있습니다. 이를 수행하려면 서비스 목록 상자에서 `리소스 추가` 링크를 클릭하십시오. 사용 가능한 서비스가 지역에서 사용 가능한 서비스와 앱의 유형에 따라 다르므로, 모든 서비스가 모든 앱과의 연관에 사용 가능하지는 않습니다. 

![개발자 콘솔 리소스 추가 대화 상자](images/add_resource_dialog.png "리소스 추가 대화 상자") <br> *개발자 콘솔 리소스 추가 대화 상자*

앱 세부사항 보기에서 두 가지 방법으로 코드에 액세스할 수 있습니다. 

*  [권장사항] `클라우드에 배치` 단추를 클릭하여 코드를 저장소에 푸시하고 앱을 {{site.data.keyword.cloud_notm}}에 배치하십시오. {{site.data.keyword.cloud_notm}} DevOps 도구 체인에 대한 자세한 정보를 보려면 [여기](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about)를 클릭하십시오. 
*  앱 코드를 빨리 살펴보려면 `코드 다운로드`를 선택하여 앱에 대한 코드를 생성하고 이를 다운로드하십시오. 

##앱 목록 보기
{: #project_list_view}

앱 목록 보기에서 작성된 모든 앱의 목록을 볼 수 있습니다. 여기서 앱의 이름을 바꾸거나 앱을 삭제할 수 있습니다. 앱 세부사항 보기로 돌아가려면 앱 이름 행을 클릭하십시오. 

![개발자 콘솔 앱 목록 보기](images/project_list_view.png "앱 목록 보기") <br> *개발자 콘솔 앱 목록 보기*
