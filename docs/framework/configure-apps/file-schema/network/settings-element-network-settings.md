---
description: '다음에 대 한 자세한 정보: <settings> 요소 (네트워크 설정)'
title: <settings> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: e6ed242e68ac9a9e2c20067d66681bbcd51fcc50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712976"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="393d8-103">\<settings> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="393d8-103">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="393d8-104"><xref:System.Net?displayProperty=nameWithType> 네임스페이스에 대한 기본 네트워크 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-104">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="393d8-105">구문</span><span class="sxs-lookup"><span data-stu-id="393d8-105">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="393d8-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="393d8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="393d8-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="393d8-108">특성</span><span class="sxs-lookup"><span data-stu-id="393d8-108">Attributes</span></span>  

 <span data-ttu-id="393d8-109">없음</span><span class="sxs-lookup"><span data-stu-id="393d8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="393d8-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="393d8-110">Child Elements</span></span>  
  
|<span data-ttu-id="393d8-111">요소</span><span class="sxs-lookup"><span data-stu-id="393d8-111">Element</span></span>|<span data-ttu-id="393d8-112">설명</span><span class="sxs-lookup"><span data-stu-id="393d8-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="393d8-113">httpListener</span><span class="sxs-lookup"><span data-stu-id="393d8-113">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="393d8-114">클래스에서 사용 하는 매개 변수를 사용자 지정 <xref:System.Net.HttpListener> 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-114">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="393d8-115">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="393d8-115">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="393d8-116">웹 요청 매개 변수를 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-116">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="393d8-117">ipv6)</span><span class="sxs-lookup"><span data-stu-id="393d8-117">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="393d8-118">IPv6 (인터넷 프로토콜 버전 6) 지원을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-118">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="393d8-119">\<performanceCounter> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="393d8-119">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="393d8-120">네트워크 성능 카운터를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-120">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="393d8-121">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="393d8-121">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="393d8-122">네트워크 리소스에 대 한 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-122">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="393d8-123">소켓이</span><span class="sxs-lookup"><span data-stu-id="393d8-123">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="393d8-124">소켓 작업에서 완료 포트를 사용 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-124">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="393d8-125">\<webProxyScript> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="393d8-125">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="393d8-126">웹 프록시를 검색 하는 데 사용 되는 스크립트의 특징을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-126">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="393d8-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="393d8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="393d8-128">요소</span><span class="sxs-lookup"><span data-stu-id="393d8-128">Element</span></span>|<span data-ttu-id="393d8-129">설명</span><span class="sxs-lookup"><span data-stu-id="393d8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="393d8-130">system.net</span><span class="sxs-lookup"><span data-stu-id="393d8-130">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="393d8-131">.NET Framework의 네트워크 연결 방법을 지정하는 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-131">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="393d8-132">설명</span><span class="sxs-lookup"><span data-stu-id="393d8-132">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="393d8-133">구성 파일</span><span class="sxs-lookup"><span data-stu-id="393d8-133">Configuration Files</span></span>  

 <span data-ttu-id="393d8-134">이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="393d8-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393d8-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="393d8-135">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="393d8-136">네트워크 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="393d8-136">Network Settings Schema</span></span>](index.md)
