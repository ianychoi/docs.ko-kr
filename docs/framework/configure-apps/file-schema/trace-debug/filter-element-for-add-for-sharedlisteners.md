---
description: '자세히 알아보기: <filter> 의에 대 한 요소 <add><sharedListeners>'
title: <filter>의에 대 한 요소 <add><sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 5d6567ff029dea5ed98054dbc524bb7ed405324c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802374"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="bfee1-103">\<filter>의에 대 한 요소 \<add>\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="bfee1-103">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="bfee1-104">`sharedListeners` 컬렉션에 있는 수신기에 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-104">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="bfee1-105">구문</span><span class="sxs-lookup"><span data-stu-id="bfee1-105">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfee1-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="bfee1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bfee1-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfee1-108">특성</span><span class="sxs-lookup"><span data-stu-id="bfee1-108">Attributes</span></span>  
  
|<span data-ttu-id="bfee1-109">attribute</span><span class="sxs-lookup"><span data-stu-id="bfee1-109">Attribute</span></span>|<span data-ttu-id="bfee1-110">Description</span><span class="sxs-lookup"><span data-stu-id="bfee1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfee1-111">**type**</span><span class="sxs-lookup"><span data-stu-id="bfee1-111">**type**</span></span>|<span data-ttu-id="bfee1-112">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="bfee1-113">필터의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-113">Specifies the type of the filter.</span></span> <span data-ttu-id="bfee1-114">형식의 전체 이름만 사용 하거나 (속성 형식으로 <xref:System.Type.FullName%2A?displayProperty=nameWithType> ) 어셈블리 정보를 포함 하 여 정규화 된 형식 이름을 속성 형식으로 사용할 수 있습니다 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bfee1-114">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="bfee1-115">정규화 된 형식 이름을 만드는 방법에 대 한 자세한 내용은 정규화 된 [형식 이름 지정](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfee1-115">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="bfee1-116">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="bfee1-116">**initializeData**</span></span>|<span data-ttu-id="bfee1-117">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bfee1-118">지정 된 클래스의 생성자에 전달 된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-118">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfee1-119">자식 요소</span><span class="sxs-lookup"><span data-stu-id="bfee1-119">Child Elements</span></span>  

 <span data-ttu-id="bfee1-120">없음</span><span class="sxs-lookup"><span data-stu-id="bfee1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfee1-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="bfee1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bfee1-122">요소</span><span class="sxs-lookup"><span data-stu-id="bfee1-122">Element</span></span>|<span data-ttu-id="bfee1-123">설명</span><span class="sxs-lookup"><span data-stu-id="bfee1-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bfee1-124">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bfee1-125">메시지를 수집하고 저장하고 라우팅하는 추적 수신기를 지정하며, 추적 스위치가 설정되는 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="bfee1-126">모든 소스 또는 추적 요소가 참조할 수 있는 수신기의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-126">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="bfee1-127">**Sharedlisteners** 컬렉션에 수신기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-127">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfee1-128">설명</span><span class="sxs-lookup"><span data-stu-id="bfee1-128">Remarks</span></span>  

 <span data-ttu-id="bfee1-129">수신기가 요소의 요소에 정의 된 경우 `<add>` `<sharedListeners>` 해당 수신기의 필터는 요소의 자식인 요소에 정의 되어야 합니다 `<filter>` `<add>` .</span><span class="sxs-lookup"><span data-stu-id="bfee1-129">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="bfee1-130">이 요소는 컴퓨터 구성 파일 (Machine.config) 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfee1-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfee1-131">예제</span><span class="sxs-lookup"><span data-stu-id="bfee1-131">Example</span></span>  

 <span data-ttu-id="bfee1-132">다음 예제에서는 요소를 사용 하 여 `<filter>` 컬렉션의 추적 수신기에 필터를 추가 하는 방법을 보여 줍니다 `console` `sharedListeners` .</span><span class="sxs-lookup"><span data-stu-id="bfee1-132">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfee1-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfee1-133">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="bfee1-134">추적 및 디버그 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="bfee1-134">Trace and Debug Settings Schema</span></span>](index.md)
