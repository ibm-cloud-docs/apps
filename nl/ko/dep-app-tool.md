---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, deploying apps, toolchains, cli

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 앱 배치
{: #deploying-apps}

도구 체인 또는 명령행 인터페이스(CLI)를 사용하여 앱을 배치할 수 있습니다. 도구 체인은 도구 통합 세트입니다. CLI는 앱 및 서비스 인스턴스를 배치하는 간단한 방법입니다.
{: shortdesc}

## 도구 체인을 사용한 앱 배치
{: #toolchain-deploy-apps}

공개 도구 체인은 {{site.data.keyword.Bluemix}}의 퍼블릭 및 데디케이티드 환경에서 사용 가능합니다. 알맞게 구성된 도구 체인을 사용하면 손쉽게 앱을 배치할 수 있습니다. 빌드-배치 주기는 저장소의 마스터 분기에 대한 각각의 병합으로 자동 시작됩니다.

도구 체인은 다음 방법으로 작성할 수 있습니다.
* 템플리트를 사용하여 도구 체인을 작성합니다.
* 앱에서 도구 체인을 작성합니다.

도구 체인에 대해 자세히 알아보려면 [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)을 참조하십시오.

## CLI를 사용하여 앱 배치
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}}에서는 강력한 CLI 및 이 CLI와 통합되는 플러그인과 개발자 도구 확장기능을 제공합니다.

시작하기 전에 [{{site.data.keyword.cloud_notm}} CLI를 다운로드 및 설치](/docs/cli?topic=cloud-cli-ibmcloud-cli)하십시오.

CLI는 Cygwin에 의해 지원되지 않습니다. Cygwin 명령행 창 이외의 창에서 도구를 사용하십시오.
{: important}

  1. {: download}앱에 대한 코드를 새 디렉토리에 다운로드하여 개발 환경을 설정하십시오.

    <a class="xref" href="https://{DomainName}" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(새 탭 또는 창에서 열림)"></a>

  2. 코드가 있는 디렉토리로 변경하십시오.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  앱 코드를 변경하십시오. {{site.data.keyword.cloud_notm}} 샘플 애플리케이션을 사용 중이며 사용자 앱에 `src/main/webapp/index.html` 파일이 포함되어 있는 경우에는 이를 수정하여 `Thanks for creating ...` 행을 편집할 수 있습니다. 앱을 {{site.data.keyword.cloud_notm}}에 다시 배치하기 전에 로컬에서 실행되는지 확인하십시오.

    `manifest.yml` 파일에 주의하십시오. 앱을 다시 {{site.data.keyword.cloud_notm}}에 배치할 때 이 파일이 애플리케이션의 URL, 메모리 할당, 인스턴스 수 및 기타 중요한 매개변수 판별에 사용됩니다.

    또한 빌드 지시사항 등의 세부사항이 포함되어 있는 `README.md` 파일을 검토하십시오(해당하는 경우).

  애플리케이션이 Liberty 앱인 경우에는 다시 배치하기 전에 우선 이를 빌드해야 합니다.
  {: note}

  4. {{site.data.keyword.cloud_notm}}에 연결하고 로그인하십시오.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  연합 ID를 사용하는 경우에는 `-sso` 옵션을 추가하십시오.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  값에 공백이 포함된 경우에는 `username`, `org_name` 및 `space_name`의 앞뒤에 작은따옴표 또는 큰따옴표를 추가해야 합니다(예: `-o "my org"`).
  {: note}

  5. 새 디렉토리에서 `ibmcloud dev deploy` 명령을 사용하여 {{site.data.keyword.cloud_notm}}에 앱을 배치하십시오. 자세한 정보는 [CLI 문서](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy)를 참조하십시오.

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>으로 이동하여 앱에 액세스하십시오.
