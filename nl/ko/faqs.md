---

copyright:

  years: 2019

lastupdated: "2019-04-03"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# FAQ
{: #apps-faq}

## 내 앱 목록을 어디서 찾을 수 있습니까?
{: #cf-app}
{: faq}

[{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon")의 리소스 목록은 작성된 애플리케이션에 대한 요약 정보를 제공합니다. 리소스 목록의 **앱** 섹션에는 사용자가 작성했지만 Cloud Foundry에 배치하지 *않은* 모든 앱이 포함되어 있습니다. **Cloud Foundry 앱** 섹션에는 사용자가 작성하여 Cloud Foundry에 배치한 모든 앱이 포함되어 있습니다. 

## 내 앱을 배치하려고 할 때 Cloud Foundry 영역을 선택할 수 없는 이유는 무엇입니까?
{: #cf-space}
{: faq}

먼저 Cloud Foundry 영역을 작성해야 합니다. Cloud Foundry 명령행 인터페이스를 사용하는 경우 `cf create-space <space_name> -o <organization_name>`을 입력하십시오. 또는 콘솔에서 다음 단계를 완료하십시오. 

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 메뉴 표시줄에서 **관리** > **계정**을 선택하십시오. 
2. **Cloud Foundry 조직**을 선택하십시오.
3. 영역을 작성할 조직의 이름을 클릭하고 **영역 추가**를 클릭하십시오.

## 앱을 어떻게 삭제합니까?
{: #delete-apps}
{: faq}

작성한 앱을 삭제하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 **메뉴** 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg)을 클릭하고 **리소스 목록**을 선택하십시오.
2. 삭제하려는 앱에 대해 **조치** 아이콘 ![조치 아이콘](../icons/action-menu-icon.svg)을 클릭하고 **삭제**를 클릭하십시오. 

## 도구 체인은 무엇이고 내 앱과 어떻게 관련되어 있습니까?
{: #toolchains}
{: faq}

도구 체인은 개발, 배치 및 오퍼레이션 태스크를 지원하는 도구 통합 세트입니다. 앱에서 도구 체인을 작성할 수 있습니다. 도구 체인은 지속적 개발, 배치, 모니터링 등을 지원할 수 있으며 사용자 앱과 연관됩니다. 개별 앱은 도구 체인과 연관될 수 있습니다.  도구 체인을 구성하여 도구 체인의 변경사항을 자동으로 빌드하고 앱을 배치할 수 있습니다. 도구 체인에 대한 자세한 정보는 [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)을 참조하십시오. 
