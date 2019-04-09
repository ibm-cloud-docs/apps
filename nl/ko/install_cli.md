---

copyright:

  years: 2015，2017, 2018

lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:prereq: .prereq}
{:download: .download}
{:pre: .pre}
{:app_name: data-hd-keyref="app_name"}
{:app_key: data-hd-keyref="app_key"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:host: data-hd-keyref="host"}
{:org_name: data-hd-keyref="org_name"}
{:route: data-hd-keyref="route"}
{:space_name: data-hd-keyref="space_name"}
{:service_name: data-hd-keyref="service_name"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:user_ID: data-hd-keyref="user_ID"}

# 명령행 인터페이스로 앱 배치

{{site.data.keyword.Bluemix_notm}} 명령행 인터페이스를 사용하여 앱 및 서비스 인스턴스를 배치하십시오.
{:shortdesc}

시작하기 전에 {{site.data.keyword.Bluemix_notm}} 명령행 인터페이스를 다운로드하여 설치하십시오.

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(새 탭 또는 창에서 열림)"><img class="image" src="images/btn_bx_commandline.svg" alt="IBM Cloud 명령행 인터페이스 다운로드" /> </a>
</p>

**제한사항:** 명령행 도구는 Cygwin에서 지원되지 않습니다. Cygwin 명령행 창 이외의 명령행 창에서 도구를 사용하십시오.
{:prereq}

명령행 인터페이스를 설치한 후 시작할 수 있습니다.

  1. {: download} 앱에 대한 코드를 새 디렉토리에 다운로드하여 개발 환경을 설정하십시오.

    <a class="xref" href="http://bluemix.net" target="_blank" title="(새 탭 또는 창에서 열림)"><img class="image" src="images/btn_starter-code.svg" alt="애플리케이션 코드 다운로드" /> </a>

  2. 코드가 있는 디렉토리로 변경하십시오.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  앱 코드를 변경하십시오. 예를 들어, {{site.data.keyword.Bluemix}} 샘플 애플리케이션을 사용 중이고 사용자 앱에 `src/main/webapp/index.html` 파일이 포함되어 있는 경우 이를 수정할 수 있으며 새로운 내용을 설명하기 위해 "Thanks for creating ..."을 편집할 수 있습니다. 앱을 {{site.data.keyword.Bluemix_notm}}에 다시 배치하기 전에 로컬에서 실행되는지 확인하십시오. 

    `manifest.yml` 파일에 주의하십시오. 앱을 다시 {{site.data.keyword.Bluemix_notm}}에 배치할 때 이 파일이 애플리케이션의 URL, 메모리 할당, 인스턴스 수 및 기타 중요한 매개변수 판별에 사용됩니다.

    또한 해당하는 경우 빌드 지시사항과 같은 세부사항이 포함되어 있는 `README.md` 파일도 주의하십시오.

    참고: 애플리케이션이 Liberty 앱인 경우 재배치 전에 먼저 빌드해야 합니다.

  4. {{site.data.keyword.Bluemix_notm}}에 연결하고 로그인하십시오.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  연합 ID를 사용하는 경우에는 `-sso` 옵션을 추가하십시오. 

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **참고**: 값에 간격이 포함되어 있는 경우에는 `-o "my org"`와 같이 `username`, `org_name` 및 `space_name` 앞뒤에 작은따옴표 또는 큰따옴표를 추가해야 합니다.

  5. <var class="keyword varname">your_new_directory</var>에서 `ibmcloud app push` 명령을 사용하여 {{site.data.keyword.Bluemix_notm}}에 앱을 재배치하십시오. `ibmcloud app push` 명령에 대한 자세한 정보는 [애플리케이션 업로드](/docs/starters/upload_app.html)를 참조하십시오. 

  <pre class="pre"><code class="hljs">ibmcloud app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>을 브라우징하여 앱에 액세스하십시오.
