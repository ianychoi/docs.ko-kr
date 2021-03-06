---
description: 다음에 대해 자세히 알아보세요. <audienceUris>
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 98b411e73d4b9941e65daaf5d1d63285cdc90fd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681853"
---
# \<audienceUris>

RP (신뢰 당사자)에 허용 되는 식별자를 지정 하는 Uri 집합을 지정 합니다. 허용 되는 대상 Uri 중 하나에 대해 범위가 지정 되지 않는 한 토큰을 허용 하지 않습니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|mode|<xref:System.IdentityModel.Selectors.AudienceUriMode>대상 제한이 들어오는 토큰에 적용 되어야 하는지 여부를 지정 하는 값입니다. 가능한 값은 "Always", "Never" 및 "BearerKeyOnly"입니다. 기본값은 "Always"입니다. 선택 사항입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`<add value=xs:string>`|특성에 지정 된 URI를 `value` audienceUris 컬렉션에 추가 합니다. `value` 특성은 필수입니다. URI는 대/소문자를 구분 합니다.|  
|`<clear>`|AudienceUris 컬렉션을 지웁니다. 모든 식별자는 컬렉션에서 제거 됩니다.|  
|`<remove value=xs:string>`|AudienceUris collection에서 특성으로 지정 된 URI를 제거 합니다 `value` . `value` 특성은 필수입니다. URI는 대/소문자를 구분 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|보안 토큰 처리기의 컬렉션에 대 한 구성을 제공 합니다.|  
  
## <a name="remarks"></a>설명  

 기본적으로 컬렉션은 비어 있습니다. `<add>`, `<clear>` 및 요소를 사용 하 여 컬렉션을 `<remove>` 수정 합니다. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 및 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 개체는 대상 uri 컬렉션의 값을 사용 하 여 개체에서 허용 되는 대상 uri 제한을 구성 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 합니다.  
  
 합니다 `<audienceUris>` 에서 요소가 표시 되는 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> 클래스입니다. 컬렉션에 추가 된 개별 URI는 클래스로 표현 됩니다 <xref:System.IdentityModel.Configuration.AudienceUriElement> .  
  
> [!NOTE]
> 요소를 `<audienceUris>` 요소의 자식 요소로 사용 하는 것은 [\<identityConfiguration>](identityconfiguration.md) 더 이상 사용 되지 않지만 이전 버전과의 호환성을 위해 계속 지원 됩니다. `<securityTokenHandlerConfiguration>`요소의 설정은 요소의 설정을 재정의 `<identityConfiguration>` 합니다.  
  
## <a name="example"></a>예제  

 다음 XML에서는 응용 프로그램에 대 한 허용 가능한 대상 Uri를 구성 하는 방법을 보여 줍니다. 이 예제에서는 단일 URI를 구성 합니다. 이 URI에 대해 범위가 지정 된 토큰은 수락 되며 다른 모든 토큰은 거부 됩니다.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
