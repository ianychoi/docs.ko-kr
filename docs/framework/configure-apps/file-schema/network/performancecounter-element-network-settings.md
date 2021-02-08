---
description: '다음에 대 한 자세한 정보: <performanceCounters> 요소 (네트워크 설정)'
title: <performanceCounters> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: a923ba2420bd15e33f4564a196854fdf9e130e12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804116"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="c3125-103">\<performanceCounters> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="c3125-103">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="c3125-104">네트워킹 성능 카운터를 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-104">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="c3125-105">구문</span><span class="sxs-lookup"><span data-stu-id="c3125-105">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3125-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c3125-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c3125-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3125-108">특성</span><span class="sxs-lookup"><span data-stu-id="c3125-108">Attributes</span></span>  
  
|<span data-ttu-id="c3125-109">attribute</span><span class="sxs-lookup"><span data-stu-id="c3125-109">Attribute</span></span>|<span data-ttu-id="c3125-110">설명</span><span class="sxs-lookup"><span data-stu-id="c3125-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c3125-111">네트워킹 성능 카운터의 사용 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-111">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="c3125-112">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3125-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c3125-113">Child Elements</span></span>  

 <span data-ttu-id="c3125-114">없음</span><span class="sxs-lookup"><span data-stu-id="c3125-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3125-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c3125-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c3125-116">요소</span><span class="sxs-lookup"><span data-stu-id="c3125-116">Element</span></span>|<span data-ttu-id="c3125-117">설명</span><span class="sxs-lookup"><span data-stu-id="c3125-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3125-118">설정</span><span class="sxs-lookup"><span data-stu-id="c3125-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="c3125-119"><xref:System.Net> 네임스페이스에 대한 기본 네트워크 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3125-120">설명</span><span class="sxs-lookup"><span data-stu-id="c3125-120">Remarks</span></span>  

 <span data-ttu-id="c3125-121">이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="c3125-122">네트워킹 성능 카운터를 사용하려면 구성 파일에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-122">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="c3125-123">구성 파일의 단일 설정을 통해 모든 네트워킹 성능 카운터를 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-123">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="c3125-124">개별 네트워킹 성능 카운터를 사용하거나 사용하지 않도록 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-124">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="c3125-125">특정 네트워킹 성능 카운터에 대 한 자세한 내용은 [네트워킹 성능 카운터](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3125-125">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="c3125-126">기본값은 네트워킹 성능 카운터를 사용 하지 않도록 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-126">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="c3125-127"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>속성을 사용 하 여 적용 가능한 구성 파일에서 **활성화** 된 특성의 현재 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-127">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3125-128">예제</span><span class="sxs-lookup"><span data-stu-id="c3125-128">Example</span></span>  

 <span data-ttu-id="c3125-129">다음 예제에서는 <xref:System.Net> 및 관련 네임 스페이스를 구성 하 여 네트워킹 성능 카운터를 사용 하도록 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3125-129">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3125-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3125-130">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c3125-131">네트워크 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="c3125-131">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c3125-132">네트워킹 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="c3125-132">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
