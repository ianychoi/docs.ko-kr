---
description: '다음에 대 한 자세한 정보: <switches> 요소'
title: <switches> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: d0ffdf2bdc4dacd157d09d34c40063b687595e3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750522"
---
# <a name="switches-element"></a><span data-ttu-id="20daa-103">\<switches> 요소</span><span class="sxs-lookup"><span data-stu-id="20daa-103">\<switches> Element</span></span>

<span data-ttu-id="20daa-104">추적 스위치 및 추적 스위치가 설정된 수준이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-104">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="20daa-105">구문</span><span class="sxs-lookup"><span data-stu-id="20daa-105">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20daa-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="20daa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="20daa-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20daa-108">특성</span><span class="sxs-lookup"><span data-stu-id="20daa-108">Attributes</span></span>  

 <span data-ttu-id="20daa-109">없음</span><span class="sxs-lookup"><span data-stu-id="20daa-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20daa-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="20daa-110">Child Elements</span></span>  
  
|<span data-ttu-id="20daa-111">요소</span><span class="sxs-lookup"><span data-stu-id="20daa-111">Element</span></span>|<span data-ttu-id="20daa-112">설명</span><span class="sxs-lookup"><span data-stu-id="20daa-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="20daa-113">추적 스위치를 설정하는 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-113">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20daa-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="20daa-114">Parent Elements</span></span>  
  
|<span data-ttu-id="20daa-115">요소</span><span class="sxs-lookup"><span data-stu-id="20daa-115">Element</span></span>|<span data-ttu-id="20daa-116">설명</span><span class="sxs-lookup"><span data-stu-id="20daa-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="20daa-117">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="20daa-118">메시지를 수집하고 저장하고 라우팅하는 추적 수신기를 지정하며, 추적 스위치가 설정되는 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20daa-119">설명</span><span class="sxs-lookup"><span data-stu-id="20daa-119">Remarks</span></span>  

 <span data-ttu-id="20daa-120">구성 파일에 배치 하 여 추적 스위치의 수준을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-120">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="20daa-121">스위치가 인 경우 <xref:System.Diagnostics.BooleanSwitch> 설정 및 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-121">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="20daa-122">스위치가 인 경우 <xref:System.Diagnostics.TraceSwitch> 다른 수준을 할당 하 여 응용 프로그램에서 출력 하는 추적 또는 디버그 메시지의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-122">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20daa-123">예제</span><span class="sxs-lookup"><span data-stu-id="20daa-123">Example</span></span>  

 <span data-ttu-id="20daa-124">다음 예에서는 요소를 사용 하 여 **\<switch>** `General` 추적 스위치를 수준으로 설정 하 <xref:System.Diagnostics.TraceLevel> 고 `Data` 부울 추적 스위치를 사용 하도록 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20daa-124">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20daa-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20daa-125">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="20daa-126">추적 및 디버그 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="20daa-126">Trace and Debug Settings Schema</span></span>](index.md)
