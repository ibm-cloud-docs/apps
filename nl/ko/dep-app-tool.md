---
copyright:

  years: 2018

lastupdated: "2018-03-17"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# 앱 배치
{: #deploy}

도구 체인 또는 명령행 인터페이스를 사용하여 앱을 배치할 수 있습니다. 도구 체인은 도구 통합 세트입니다. 명령행 인터페이스는 앱 및 서비스 인스턴스를 배치하는 간단한 방법입니다.
{: shortdesc}

## 도구 체인을 사용한 앱 배치
{: #toolchains_getting_started}

공개 도구 체인은 {{site.data.keyword.Bluemix}}의 퍼블릭 및 데디케이티드 환경에서 사용 가능합니다. 두 가지 방법으로 도구 체인을 작성할 수 있습니다. 즉, 템플리트를 사용하여 도구 체인을 작성하거나 앱에서 도구 체인을 작성할 수 있습니다. 도구 체인에 대해 자세히 알아보려면 [도구 체인 작성](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)을 참조하십시오. 

도구 체인이 적절히 구성되고 나면 앱 배치는 간단합니다. 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. 

{{site.data.keyword.Bluemix}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다.
{: tip}

## 명령행 인터페이스로 앱 배치
{: #cli}

IBM Cloud는 강력한 CLI, 그리고 CLI와 통합되는 플러그인 및 개발자 도구 확장을 제공합니다. 

{{site.data.keyword.Bluemix_notm}} 명령행 인터페이스를 사용하여 앱 및 서비스 인스턴스를 배치하십시오.
{:shortdesc}

시작하기 전에 {{site.data.keyword.Bluemix_notm}} 명령행 인터페이스를 다운로드하여 설치하십시오.

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(새 탭 또는 창에서 열림)"><img class="image" src="images/btn_bx_commandline.svg" alt="Bluemix 명령행 인터페이스 다운로드" /> </a>
</p>

**제한사항:** 명령행 도구는 Cygwin에서 지원되지 않습니다. Cygwin 명령행 창 이외의 명령행 창에서 도구를 사용하십시오.
{:prereq}

명령행 인터페이스를 설치한 후 시작할 수 있습니다.

  1. {: download} 앱에 대한 코드를 새 디렉토리에 다운로드하여 개발 환경을 설정하십시오.

    <a class="xref" href="http://bluemix.net" target="_blank" title="(새 탭 또는 창에서 열림)"></a>

  2. 코드가 있는 디렉토리로 변경하십시오.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  앱 코드를 변경하십시오. 예를 들어, {{site.data.keyword.Bluemix_notm}} 샘플 애플리케이션을 사용 중이며 사용자 앱에 `src/main/webapp/index.html` 파일이 포함되어 있는 경우에는 이를 수정하여 새로운 내용을 표시하기 위해 "Thanks for creating ..."을 편집할 수 있습니다. 앱을 {{site.data.keyword.Bluemix_notm}}에 다시 배치하기 전에 로컬로 실행되고 있는지 확인하십시오.

    `manifest.yml` 파일에 주의하십시오. 앱을 다시 {{site.data.keyword.Bluemix_notm}}에 배치할 때 이 파일이 애플리케이션의 URL, 메모리 할당, 인스턴스 수 및 기타 중요한 매개변수 판별에 사용됩니다.

    또한 해당하는 경우 빌드 지시사항과 같은 세부사항이 포함되어 있는 `README.md` 파일도 주의하십시오.

    참고: 애플리케이션이 Liberty 앱인 경우 재배치 전에 먼저 빌드해야 합니다.

  4. {{site.data.keyword.Bluemix_notm}}에 연결하고 로그인하십시오.

  <pre class="pre"><code class="hljs">bluemix api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">bluemix login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  연합 ID를 사용 중인 경우에는 `-sso` 옵션을 사용하십시오. 

  <pre class="pre"><code class="hljs">bluemix login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **참고**: 값에 간격이 포함되어 있는 경우에는 `-o "my org"`와 같이 `username`, `org_name` 및 `space_name` 앞뒤에 작은따옴표 또는 큰따옴표를 추가해야 합니다. 

  5. <var class="keyword varname">your_new_directory</var>에서 `bluemix app push` 명령을 사용하여 {{site.data.keyword.Bluemix_notm}}에 앱을 재배치하십시오. `bx app push` 명령에 대한 자세한 정보는 [애플리케이션 업로드](/docs/starters/upload_app.html)를 참조하십시오.

  <pre class="pre"><code class="hljs">bluemix app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>을 브라우징하여 앱에 액세스하십시오.
