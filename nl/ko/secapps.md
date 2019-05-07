---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-25"

keywords: apps, application, ssl, certificates, access, restrict access, create, csr, upload, import

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# 인증서 서명 요청 작성
{: #ssl_csr}

SSL 인증서를 작성하고 업로드하며 애플리케이션 액세스를 제한하여 애플리케이션 보안을 유지할 수 있습니다.
{:shortdesc}

{{site.data.keyword.cloud}}에서 권한이 부여된 SSL 인증서를 업로드하려면 먼저 서버에서 인증서 서명 요청(CSR)을 작성해야 합니다. CSR은 공개 키 서명과 연관된 정보를 요청하기 위해 인증 기관에 보내는 메시지입니다. CSR은 PKCS #10 형식이 가장 일반적입니다. CSR에는 공개 키 및 공통 이름, 조직, 도시, 구/군/시, 시/도, 국가, 이메일이 포함되어 있습니다. SSL 인증서 요청은 CSR 키 길이가 2048비트인 경우에만 허용됩니다.

## CSR 작성

CSR 작성 방법은 운영 체제에 따라 다릅니다. 다음 예는 [OpenSSL 명령행 도구 ](http://www.openssl.org/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 사용하여 CSR을 작성하는 방법을 보여줍니다.

```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privatekey.key
```
{: codeblock}

OpenSSL SHA-512 구현은 64비트 정수 유형에 대한 컴파일러 지원에 따라 달라집니다. SHA-1 옵션은 SHA-256 인증서와 관련하여 호환성 문제가 있는 애플리케이션에 사용할 수 있습니다.
{: tip}

인증서는 인증 기관에서 발행하며 인증 기관의 디지털 서명이 있습니다. CSR을 작성한 후 잘 알려진 인증 기간에서 SSL 인증서를 생성할 수 있습니다.

### 필수 CSR 컨텐츠

CSR이 유효하려면 CSR을 작성할 때 다음 정보를 입력해야 합니다.

 * **국가 이름**. 국가 또는 지역의 두 자릿수 코드입니다. 예를 들어, `US`는 미국의 국가 코드입니다. 기타 국가 또는 지역의 경우에는 CSR을 작성하기 전에 [ISO 국가 코드의 목록](https://www.iso.org/obp/ui/#search){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 확인하십시오.
 * **시 또는 도**. 시/도의 축약되지 않은 전체 이름입니다.
 * **지역**. 구/군/시의 전체 이름입니다.
 * **조직**. 해당 지역에 법적으로 등록된 비즈니스 또는 회사의 전체 이름 또는 개인 이름입니다. 회사의 경우 Ltd., Inc., NV 등의 등록 접미부를 포함시켜야 합니다.
 * **조직 단위**. 인증서를 주문하는 회사의 지점 이름입니다(예: 회계 또는 마케팅).
 * **공통 이름**. SSL 인증서 요청의 대상인 완전한 도메인 이름(FQDN)입니다.

SAN(Subject Alternative Names)을 사용할 수 있지만 CN 충돌을 방지하기 위해 제공된 호스트 이름을 배치된 다른 인증서에 발행하면 안 됩니다.
{: note}

## SSL 인증서 업로드
{: #ssl_certificate}

보안 프로토콜을 적용하여 도청, 변조 및 메시지 위조를 방지하도록 애플리케이션에 대한 통신 개인정보 보호를 제공할 수 있습니다. 계정 소유자에게 무료 Lite 계정이 있는 경우 인증서를 업로드하려면 계정을 업그레이드해야 합니다.

사용자 정의 도메인을 사용하여 SSL 인증서를 제공하려면 다음 지역 엔드포인트를 사용하여 {{site.data.keyword.cloud_notm}}에서 조직에 대한 URL 라우트를 제공하십시오.

* US-South - `custom-domain.us-south.cf.cloud.ibm.com`
* US-East - `custom-domain.us-east.cf.cloud.ibm.com`
* EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
* EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
* AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

Cloud Foundry 애플리케이션의 인증서를 업로드하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} 콘솔![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}){: new_window}에서 **메뉴** 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg)을 클릭하고 **리소스 목록**을 선택하십시오.
2. **리소스 목록** 페이지에서 **Cloud Foundry 앱**을 클릭하십시오.
3. 도메인을 변경할 애플리케이션을 클릭하십시오. 해당 앱의 **개요** 페이지가 표시됩니다.
4. **라우트** 메뉴를 선택하고 **도메인 관리**를 클릭하십시오.
5. 조치 열에서 조치 아이콘 ![추가 조치 아이콘](../icons/action-menu-icon.svg)을 클릭하고 **도메인**을 선택하십시오.
6. 사용자 정의 도메인에 대해 **SSL 인증서 열**에서 **업로드**를 클릭하십시오.
7. 옵션을 선택하고 파일을 업로드한 다음 **추가**를 클릭하십시오.
  
  * 인증서: 공개 키를 인증서 소유자의 ID에 바인드하여 인증서 소유자를 인증하는 디지털 문서입니다. 인증서는 인증 기관에서 발행하며 인증 기관의 디지털 서명이 있습니다. 인증서는 일반적으로 인증 기관에서 발행하고 서명합니다. 그러나 테스트 및 개발 목적으로 자체 서명된 인증서를 사용할 수도 있습니다.
  * 개인 키: 메시지를 암호화하는 데 사용되는 알고리즘 패턴으로, 해당 공개 키로만 메시지를 복호화할 수 있습니다. 개인 키는 또한 해당 공개 키로 암호화된 메시지를 복호화하는 데도 사용됩니다. 개인 키는 사용자 시스템에 보존되며 비밀번호로 보호됩니다.
  * 중간 인증서(선택사항): 특히 최종 엔티티 서버 인증서를 발행하기 위해 신뢰할 수 있는 루트 인증 기관(CA)에서 발행하는 하위 인증서입니다. 결과적으로 신뢰할 수 있는 루트 CA에서 시작되고, 중간 인증서를 통과하여, 조직에 발행된 SSL 인증서로 끝나는 인증서 체인이 생성됩니다. 중간 인증서를 사용하여 기본 인증서의 신뢰성을 확인하십시오. 중간 인증서는 보통 신뢰할 수 있는 서드파티에서 얻을 수 있습니다. 프로덕션에 배치하기 전 애플리케이션을 테스트하는 경우에는 중간 인증서가 필요하지 않습니다.
  * 클라이언트 인증서 요청 사용: 이 옵션을 사용하면 SSL 보호 도메인에 액세스하려는 사용자는 클라이언트 측 인증서를 제공하도록 요청을 받습니다. 예를 들어, 웹 브라우저에서 SSL 보호 도메인에 액세스하려고 하면 웹 브라우저에 도메인의 클라이언트 인증서를 제공하라는 메시지가 표시됩니다.   
  * 클라이언트 인증서 신뢰 저장소(선택사항): 애플리케이션에 대한 액세스를 허용할 사용자에 대한 클라이언트 인증서가 포함됩니다. 클라이언트 인증서를 요청하는 옵션을 사용으로 설정하려면 클라이언트 인증서 신뢰 저장소 파일을 업로드하십시오.
  
    메타데이터에 공개 키가 포함된 클라이언트 인증서 신뢰 저장소를 업로드하여 상호 인증을 설정할 수 있습니다.
    {: tip}

자세한 정보는 [SSL 인증서 가져오기](/docs/ssl-certificates?topic=ssl-certificates-importing-ssl-certificates)를 참조하십시오.
