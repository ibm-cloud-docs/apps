---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 암호화 기술로 키와 데이터 보호
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}는 IBM Z 암호화를 클라우드에 제공합니다. {{site.data.keyword.cloud_notm}}는 금융 및 재무 서비스에서 필요로 하는 동일한 암호화 기술을 제공합니다.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}는 산업의 가장 높은 보안 레벨(FIPS 140-2 레벨 4)로 사용하지 않는 중, 사용 중 및 전송 중에 키와 암호를 보호합니다. {{site.data.keyword.hscrypto}}는 [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html#get-started) 서비스를 이용한 키 저장소이며 IBM Z의 하이퍼 보안 환경에서 키를 보호합니다.

## ACSP 클라이언트 설치 및 구성
{: ##crypto_config}

ACSP(Advanced Cryptography Service Provider) 클라이언트를 설치하기 전에 [카탈로그 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/hyper-protect-crypto-services){:new_window}에서 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}의 인스턴스를 작성하고 프로비저닝하십시오. 그런 다음, 사용자의 환경에서 (ACSP) 클라이언트를 설치하고 구성해야 합니다.

1. [GitHub 저장소 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window}에서 설치 패키지를 다운로드하십시오. **packages** 폴더에서 운영 체제 및 CPU 아키텍처에 적합한 설치 패키지 파일을 선택하십시오. 예를 들어, Ubuntu on x86의 경우 `acsp-pkcs11-client_1.5-3.5_amd64.deb`를 선택하십시오.
2. ACSP 클라이언트 라이브러리를 설치하려면 `dpkg` 명령을 사용하여 패키지를 설치하십시오(예: `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`).
3. {{site.data.keyword.cloud_notm}}에 있는 {{site.data.keyword.hscrypto}} 서비스 인스턴스의 경우, 네비게이터에서 **관리**를 선택하십시오.
4. 관리 창에서 **구성 다운로드**를 클릭하여 `acsp_client_credentials.uue` 파일을 다운로드하십시오.
5. 로컬 환경에서 `acsp_client_credentials.uue` 파일을 `/opt/ibm/acsp-pkcs11-client/config` 디렉토리에 복사하십시오.
6. `/opt/ibm/acsp-pkcs11-client/config` 디렉토리에서 다음 명령을 사용하여 파일을 디코딩하십시오.
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. 다음 명령을 사용하여 클라이언트 인증 정보 파일을 추출하십시오.
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. 다음 명령을 사용하여 `server-config` 파일을 기본 위치로 이동하십시오.
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. 다음 명령을 사용하여 클라이언트 인증 정보 파일의 이름을 바꾸십시오.
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (선택사항) 다음 명령을 사용하여 파일의 그룹 ID를 변경하십시오.
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. ACSP를 사용으로 설정하여 클라우드의 서비스 인스턴스에 적절한 구성을 사용하십시오.
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

이제 ACSP 클라이언트가 작동되며 {{site.data.keyword.hscrypto}}를 사용할 준비가 되었습니다!

## 다음 단계
{: ##next-steps}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}으로 시작하면 {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}를 쉽게 채택할 수 있습니다. {{site.data.keyword.hsplatform}}에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}} 시작하기](/docs/services/hypersecure-platform/index.html)를 참조하십시오.
