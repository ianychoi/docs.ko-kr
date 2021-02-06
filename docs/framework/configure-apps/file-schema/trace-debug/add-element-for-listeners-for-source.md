---
description: '자세히 알아보기: <add> 의에 대 한 요소 <listeners><source>'
title: <add>의에 대 한 요소 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: cb2145738b81574397a8de13f68d0d4e572f20cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639837"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="667f5-103">\<add>의에 대 한 요소 \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="667f5-103">\<add> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="667f5-104">추적 소스의 `Listeners` 컬렉션에 수신기를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-104">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="667f5-105">구문</span><span class="sxs-lookup"><span data-stu-id="667f5-105">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="667f5-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="667f5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="667f5-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="667f5-108">특성</span><span class="sxs-lookup"><span data-stu-id="667f5-108">Attributes</span></span>  
  
|<span data-ttu-id="667f5-109">attribute</span><span class="sxs-lookup"><span data-stu-id="667f5-109">Attribute</span></span>|<span data-ttu-id="667f5-110">설명</span><span class="sxs-lookup"><span data-stu-id="667f5-110">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="667f5-111">컬렉션에서 수신기를 참조 하는 경우를 제외 하 고 `sharedListeners` 이름으로 참조 하기만 하면 되는 경우 필수 특성입니다 ( [예제](#example)참조).</span><span class="sxs-lookup"><span data-stu-id="667f5-111">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="667f5-112">수신기의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-112">Specifies the type of the listener.</span></span> <span data-ttu-id="667f5-113">정규화 된 [형식 이름 지정](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)에 지정 된 요구 사항을 충족 하는 문자열을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="667f5-114">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="667f5-115">지정 된 클래스의 생성자에 전달 된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-115">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="667f5-116"><xref:System.Configuration.ConfigurationException>클래스에 문자열을 사용 하는 생성자가 없으면이 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-116">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="667f5-117">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="667f5-118">수신기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-118">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="667f5-119">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="667f5-120"><xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>추적 수신기의 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-120">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="667f5-121">[사용자 지정 특성]</span><span class="sxs-lookup"><span data-stu-id="667f5-121">[custom attributes]</span></span>|<span data-ttu-id="667f5-122">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-122">Optional attributes.</span></span><br /><br /> <span data-ttu-id="667f5-123">해당 수신기에 대해 메서드로 식별 되는 수신기 별 특성의 값을 지정 합니다 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="667f5-123">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="667f5-124"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 는 클래스에 고유한 추가 특성의 한 예입니다 <xref:System.Diagnostics.DelimitedListTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="667f5-124"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="667f5-125">자식 요소</span><span class="sxs-lookup"><span data-stu-id="667f5-125">Child Elements</span></span>  
  
|<span data-ttu-id="667f5-126">요소</span><span class="sxs-lookup"><span data-stu-id="667f5-126">Element</span></span>|<span data-ttu-id="667f5-127">설명</span><span class="sxs-lookup"><span data-stu-id="667f5-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="667f5-128">추적 소스의 `Listeners` 컬렉션에 있는 수신기에 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-128">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="667f5-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="667f5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="667f5-130">요소</span><span class="sxs-lookup"><span data-stu-id="667f5-130">Element</span></span>|<span data-ttu-id="667f5-131">설명</span><span class="sxs-lookup"><span data-stu-id="667f5-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="667f5-132">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="667f5-133">메시지를 수집하고 저장하고 라우팅하는 추적 수신기를 지정하며, 추적 스위치가 설정되는 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="667f5-134">추적 메시지를 시작하는 추적 소스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-134">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="667f5-135">추적 메시지를 시작하는 추적 소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-135">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="667f5-136">메시지를 수집, 저장 및 라우팅하는 수신기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-136">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="667f5-137">설명</span><span class="sxs-lookup"><span data-stu-id="667f5-137">Remarks</span></span>  

 <span data-ttu-id="667f5-138">.NET Framework와 함께 제공 되는 수신기 클래스는 클래스에서 파생 <xref:System.Diagnostics.TraceListener> 됩니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-138">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="667f5-139">추적 수신기의 특성을 지정 하지 않는 경우 `name` <xref:System.Diagnostics.TraceListener.Name%2A> 추적 수신기의 속성은 기본적으로 빈 문자열 ("")로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-139">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="667f5-140">응용 프로그램에 수신기가 하나만 있는 경우 이름을 지정 하지 않고 수신기를 추가 하 고 이름에 대해 빈 문자열을 지정 하 여 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-140">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="667f5-141">그러나 응용 프로그램에 둘 이상의 수신기가 있는 경우 각 추적 수신기에 고유한 이름을 지정 하 여 컬렉션에서 개별 추적 수신기를 식별 하 고 관리할 수 있도록 해야 합니다 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="667f5-141">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="667f5-142">동일한 형식의 추적 수신기를 두 개 이상 추가 하면 해당 형식 및 이름이 컬렉션에 추가 되는 하나의 추적 수신기만 생성 `Listeners` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-142">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="667f5-143">그러나 컬렉션에 여러 개의 동일한 수신기를 프로그래밍 방식으로 추가할 수 있습니다 `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="667f5-143">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="667f5-144">특성의 값은 `initializeData` 만드는 수신기의 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-144">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="667f5-145">모든 추적 수신기에서을 지정 해야 하는 것은 아닙니다 `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="667f5-145">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="667f5-146">특성을 사용 하는 경우 `initializeData` 컴파일러 경고 "' initializeData ' 특성이 선언 되지 않았습니다." 라는 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-146">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="667f5-147">이 경고는 특성을 인식 하지 않는 추상 기본 클래스에 대해 구성 설정의 유효성을 검사 하기 때문에 발생 합니다 <xref:System.Diagnostics.TraceListener> `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="667f5-147">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="667f5-148">일반적으로 매개 변수를 사용 하는 생성자가 있는 추적 수신기 구현에 대해서는이 경고를 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-148">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="667f5-149">다음 표에서는 .NET Framework에 포함 된 추적 수신기를 보여 주고 해당 특성의 값을 설명 합니다 `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="667f5-149">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="667f5-150">추적 수신기 클래스</span><span class="sxs-lookup"><span data-stu-id="667f5-150">Trace listener class</span></span>|<span data-ttu-id="667f5-151">initializeData 특성 값</span><span class="sxs-lookup"><span data-stu-id="667f5-151">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-152">`useErrorStream`생성자에 대 한 값 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-152">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="667f5-153">`initializeData` `true` 표준 오류 스트림에 추적 및 디버그 출력을 쓰려면 특성을 ""로 설정 하 고, `false` 표준 출력 스트림에 쓰려면 ""로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-153">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-154"><xref:System.Diagnostics.DelimitedListTraceListener>가 쓸 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-154">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-155">기존 이벤트 로그 소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-155">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-156">에서 쓰는 파일의 이름입니다 <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="667f5-156">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-157">에서 쓰는 파일의 이름입니다 <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="667f5-157">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="667f5-158">에서 쓰는 파일의 이름입니다 <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="667f5-158">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="667f5-159">구성 파일</span><span class="sxs-lookup"><span data-stu-id="667f5-159">Configuration File</span></span>  

 <span data-ttu-id="667f5-160">이 요소는 컴퓨터 구성 파일 (Machine.config) 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-160">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="667f5-161">예제</span><span class="sxs-lookup"><span data-stu-id="667f5-161">Example</span></span>  

 <span data-ttu-id="667f5-162">다음 예제에서는 요소를 사용 하 여 `<add>` 수신기를 `console` `textListener` `Listeners` 추적 소스에 대 한 컬렉션에 추가 `TraceSourceApp` 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-162">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="667f5-163">`textListener`수신기는 추적 출력을 myListener .log 파일에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="667f5-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="667f5-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="667f5-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="667f5-165">추적 및 디버그 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="667f5-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="667f5-166">추적 수신기</span><span class="sxs-lookup"><span data-stu-id="667f5-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
