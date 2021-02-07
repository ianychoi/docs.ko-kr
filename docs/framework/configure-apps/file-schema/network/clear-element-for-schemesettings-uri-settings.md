---
description: '자세한 정보: <clear> schemeSettings 요소에 대 한 요소 (Uri 설정)'
title: schemeSettings의 <clear> 요소(URI 설정)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 719296285c9a7da26eb6eaf16c630a63a10698b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740459"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="c3a39-103">schemeSettings의 \<clear> 요소(URI 설정)</span><span class="sxs-lookup"><span data-stu-id="c3a39-103">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="c3a39-104">기존 구성표 설정을 모두 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-104">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="c3a39-105">구문</span><span class="sxs-lookup"><span data-stu-id="c3a39-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3a39-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c3a39-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c3a39-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3a39-108">특성</span><span class="sxs-lookup"><span data-stu-id="c3a39-108">Attributes</span></span>  

 <span data-ttu-id="c3a39-109">없음</span><span class="sxs-lookup"><span data-stu-id="c3a39-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3a39-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c3a39-110">Child Elements</span></span>  

 <span data-ttu-id="c3a39-111">없음</span><span class="sxs-lookup"><span data-stu-id="c3a39-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3a39-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c3a39-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c3a39-113">요소</span><span class="sxs-lookup"><span data-stu-id="c3a39-113">Element</span></span>|<span data-ttu-id="c3a39-114">설명</span><span class="sxs-lookup"><span data-stu-id="c3a39-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3a39-115">\<schemeSettings> 요소 (Uri 설정)</span><span class="sxs-lookup"><span data-stu-id="c3a39-115">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="c3a39-116">특정 체계에 대해 <xref:System.Uri>가 구문 분석되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-116">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a39-117">설명</span><span class="sxs-lookup"><span data-stu-id="c3a39-117">Remarks</span></span>  

 <span data-ttu-id="c3a39-118">기본적으로 클래스는 <xref:System.Uri?displayProperty=nameWithType> 경로 압축을 실행 하기 전에 인코딩된 경로 구분 기호 비율을 이스케이프 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-118">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="c3a39-119">이는 다음과 같은 공격에 대 한 보안 메커니즘으로 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-119">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c3a39-120">% 인코딩된 문자를 올바르게 처리 하지 않는 모듈에이 URI가 전달 되 면 서버에서 다음 명령을 실행 하 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-120">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="c3a39-121">따라서 <xref:System.Uri?displayProperty=nameWithType> 클래스는 먼저 경로 구분 기호를 이스케이프 해제 한 후 경로 압축을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-121">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="c3a39-122">위의 악성 URL을 클래스 생성자에 전달 하면 <xref:System.Uri?displayProperty=nameWithType> 다음 URI가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-122">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c3a39-123">이 기본 동작은 특정 스키마에 대 한 schemeSettings 구성 옵션을 사용 하 여 인코딩된 경로 구분 기호를 이스케이프 해제 하지 않도록 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-123">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c3a39-124">구성 파일</span><span class="sxs-lookup"><span data-stu-id="c3a39-124">Configuration Files</span></span>  

 <span data-ttu-id="c3a39-125">이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a39-126">예제</span><span class="sxs-lookup"><span data-stu-id="c3a39-126">Example</span></span>  

 <span data-ttu-id="c3a39-127">다음 예제에서는 클래스에서 사용 하는 구성을 보여 줍니다 <xref:System.Uri> .이 구성은 모든 체계 설정을 지운 다음 http 체계의 백분율 인코딩된 경로 구분 기호를 이스케이프 하지 않는 지원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-127">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3a39-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3a39-128">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="c3a39-129">네트워크 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="c3a39-129">Network Settings Schema</span></span>](index.md)
