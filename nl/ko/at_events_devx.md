---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} 이벤트
{: #at_events}

보안 담당자, 감사자 또는 관리자는 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자와 애플리케이션이 {{site.data.keyword.cloud}}에서 {{site.data.keyword.dev_console}}과 상호작용하는 방식을 추적할 수 있습니다.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.cloud_notm}}의 서비스 상태를 변경하는 사용자가 시작한 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 정보](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)를 참조하십시오. 

## 이벤트 확인 위치
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 {{site.data.keyword.dev_console}} 이벤트가 생성된 {{site.data.keyword.cloud_notm}} 지역에서 사용 가능한 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인에서 사용 가능합니다. 

사용자 조치 모니터링을 시작하려면 [시작하기 튜토리얼](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)을 참조하십시오. 

## 이벤트 목록
{: #events}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>사용자가 애플리케이션을 작성할 때 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>다음 상황 중 하나가 발생할 때 이벤트가 생성됩니다. </br><ul><li>사용자가 애플리케이션 코드를 다운로드합니다.</li> <li>사용자가 {{site.data.keyword.dev_console}} CLI를 사용하여 인증 정보 파일을 다운로드합니다.</li> <li>개발자 환경 인프라에서 애플리케이션과 연관된 리소스에 대한 인증 정보를 읽습니다.</li> <li>사용자가 애플리케이션 목록을 봅니다(예: 사용자가 {{site.data.keyword.dev_console}} 콘솔에서 또는 {{site.data.keyword.dev_cli_short}} CLI를 통해 애플리케이션의 목록을 보는 경우).</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>다음 상황 중 하나가 발생할 때 이벤트가 생성됩니다. </br><ul><li>애플리케이션에 대한 항목이 변경됩니다(예: 사용자가 애플리케이션의 이름을 수정하는 경우). </li><li>새 리소스가 작성되어 애플리케이션에 추가됩니다. </li><li>기존 리소스가 애플리케이션에 추가됩니다.</li><li>서비스가 애플리케이션에서 제거됩니다.</li><li>애플리케이션에 대한 코드가 생성됩니다.</li><li>예를 들어 *클라우드에 배치*를 선택하여 개발자 환경을 통해 DevOps 도구 체인이 추가됩니다.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>사용자가 애플리케이션을 삭제할 때 이벤트가 생성됩니다.</td>
  </tr>
</table>
