---
title: 메시지 필터
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a0cc4663b9a3044d0ab80f03479a024acba50a3f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279781"
---
# <a name="message-filters"></a><span data-ttu-id="d20db-102">메시지 필터</span><span class="sxs-lookup"><span data-stu-id="d20db-102">Message Filters</span></span>

<span data-ttu-id="d20db-103">라우팅 서비스는 내용 기반 라우팅을 구현하기 위해 주소, 엔드포인트 이름 또는 특정 XPath 문과 같은 메시지의 특정 섹션을 검사하는 <xref:System.ServiceModel.Dispatcher.MessageFilter> 구현을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-103">To implement content-based routing, the Routing Service uses <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that inspect specific sections of a message, such as the address, endpoint name, or a specific XPath statement.</span></span> <span data-ttu-id="d20db-104">[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]에 제공되는 메시지 필터 중 요구 사항을 충족하는 필터가 없는 경우 기본 <xref:System.ServiceModel.Dispatcher.MessageFilter> 클래스의 새 구현을 만드는 방법으로 사용자 지정 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-104">If none of the message filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] meet your needs, you can create a custom filter by creating a new implementation of the base <xref:System.ServiceModel.Dispatcher.MessageFilter> class.</span></span>  
  
 <span data-ttu-id="d20db-105">라우팅 서비스를 구성할 때 <xref:System.ServiceModel.Routing.Configuration.FilterElement> 메시지 내에서 검색할 특정 문자열 값과 같이 필터를 만드는 데 필요한 지원 데이터 및 **messagefilter** 의 형식을 설명 하는 필터 요소 (개체)를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-105">When configuring the Routing Service, you must define filter elements (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objects) that describe the type of **MessageFilter** and any supporting data required to create the filter, such as specific string values to search for within the message.</span></span> <span data-ttu-id="d20db-106">필터 요소를 만들 경우 개별 메시지 필터만 정의됩니다. 필터를 사용하여 메시지를 평가 및 라우트하려면 필터 테이블(<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>)도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-106">Note that creating the filter elements only defines the individual message filters; to use the filters to evaluate and route messages you must also define a filter table (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).</span></span>  
  
 <span data-ttu-id="d20db-107">필터 테이블의 각 항목은 필터 요소를 참조하며 메시지가 필터와 일치할 경우 메시지가 라우트될 클라이언트 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-107">Each entry in the filter table references a filter element and specifies the client endpoint that a message will be routed to if the message matches the filter.</span></span> <span data-ttu-id="d20db-108">또한 필터 테이블 항목을 통해 백업 엔드포인트 컬렉션(<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)을 지정할 수 있습니다. 여기에는 기본 엔드포인트로 보내는 중 전송 오류가 발생할 경우 메시지를 전송할 엔드포인트 목록이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-108">The filter table entries also allow you to specify a collection of backup endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), which defines a list of endpoints that the message will be transmitted to in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="d20db-109">전송이 성공하는 엔드포인트가 나올 때까지 여기에 지정된 엔드포인트에 대해 순서대로 전송이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-109">These endpoints will be tried in the order specified until one succeeds.</span></span>  
  
## <a name="message-filters"></a><span data-ttu-id="d20db-110">메시지 필터</span><span class="sxs-lookup"><span data-stu-id="d20db-110">Message Filters</span></span>  

 <span data-ttu-id="d20db-111">라우팅 서비스에 사용되는 메시지 필터는 SOAP 동작, 메시지가 전송된 주소나 주소 접두사 또는 메시지를 보내는 엔드포인트 이름 평가와 같은 일반적인 메시지 선택 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-111">The message filters used by the Routing Service provide common message selection functionality, such as evaluating the name of the endpoint that a message was sent to, the SOAP action, or the address or address prefix that the message was sent to.</span></span> <span data-ttu-id="d20db-112">또한 필터를 `AND` 조건과 결합하면 메시지가 두 필터에 모두 일치하는 경우에만 엔드포인트에 라우트되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-112">Filters can also be joined with an `AND` condition, so that messages will only be routed to an endpoint if the message matches both filters.</span></span> <span data-ttu-id="d20db-113">사용자 고유의 <xref:System.ServiceModel.Dispatcher.MessageFilter> 구현을 만들어 사용자 지정 필터를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-113">You can also create custom filters by creating your own implementation of <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span></span>  
  
 <span data-ttu-id="d20db-114">다음 표에서는 라우팅 서비스에 사용되는 <xref:System.ServiceModel.Routing.Configuration.FilterType>, 특정 메시지 필터를 구현하는 클래스 및 필수 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-114">The following table lists the <xref:System.ServiceModel.Routing.Configuration.FilterType> used by the Routing Service, the class that implements the specific message filter, and the required <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parameters.</span></span>  
  
|<span data-ttu-id="d20db-115">필터 형식</span><span class="sxs-lookup"><span data-stu-id="d20db-115">Filter  Type</span></span>|<span data-ttu-id="d20db-116">Description</span><span class="sxs-lookup"><span data-stu-id="d20db-116">Description</span></span>|<span data-ttu-id="d20db-117">필터 데이터 의미</span><span class="sxs-lookup"><span data-stu-id="d20db-117">Filter Data Meaning</span></span>|<span data-ttu-id="d20db-118">예제 필터</span><span class="sxs-lookup"><span data-stu-id="d20db-118">Example Filter</span></span>|  
|------------------|-----------------|-------------------------|--------------------|  
|<span data-ttu-id="d20db-119">작업</span><span class="sxs-lookup"><span data-stu-id="d20db-119">Action</span></span>|<span data-ttu-id="d20db-120"><xref:System.ServiceModel.Dispatcher.ActionMessageFilter> 클래스를 사용하여 특정 작업이 포함된 메시지를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-120">Uses the <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> class to match messages containing a specific action.</span></span>|<span data-ttu-id="d20db-121">필터링할 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-121">The action to filter upon.</span></span>|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|<span data-ttu-id="d20db-122">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="d20db-122">EndpointAddress</span></span>|<span data-ttu-id="d20db-123">는 클래스를 사용 하 여 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 특정 주소를 포함 하는 메시지를 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-123">Uses the <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address.</span></span>|<span data-ttu-id="d20db-124">To 헤더의 필터링할 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-124">The address to filter upon (in the To header).</span></span>|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|<span data-ttu-id="d20db-125">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="d20db-125">EndpointAddressPrefix</span></span>|<span data-ttu-id="d20db-126">는 클래스를 사용 하 여 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 특정 주소 접두사를 포함 하는 메시지를 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-126">Uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address prefix.</span></span>|<span data-ttu-id="d20db-127">가장 긴 접두사 일치를 사용하여 필터링을 적용할 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-127">The address to filter upon using longest prefix matching.</span></span>|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|<span data-ttu-id="d20db-128">and</span><span class="sxs-lookup"><span data-stu-id="d20db-128">And</span></span>|<span data-ttu-id="d20db-129">반환 전에 항상 두 조건을 모두 평가하는 <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-129">Uses the <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> class that always evaluates both conditions before returning.</span></span>|<span data-ttu-id="d20db-130">filterData는 사용 되지 않습니다. 대신 filter1 및 filter2에는 해당 메시지 필터의 이름 (테이블에도 포함)이 포함 되어 **있고** 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-130">filterData is not used; instead filter1 and filter2 have the names of the corresponding message filters (also in the table), which should be **AND** ed together.</span></span>|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|<span data-ttu-id="d20db-131">사용자 지정</span><span class="sxs-lookup"><span data-stu-id="d20db-131">Custom</span></span>|<span data-ttu-id="d20db-132"><xref:System.ServiceModel.Dispatcher.MessageFilter> 클래스를 확장하고 문자열을 사용하는 생성자를 포함하는 사용자 정의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-132">A user-defined type that extends the <xref:System.ServiceModel.Dispatcher.MessageFilter> class and has a constructor taking a string.</span></span>|<span data-ttu-id="d20db-133">customType 특성은 만들 클래스의 정규화된 형식 이름입니다. filterData는 필터를 만들 때 생성자에 전달할 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-133">The customType attribute is the fully qualified type name of the class to create; filterData is the string to pass to the constructor when creating the filter.</span></span>|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|<span data-ttu-id="d20db-134">EndpointName</span><span class="sxs-lookup"><span data-stu-id="d20db-134">EndpointName</span></span>|<span data-ttu-id="d20db-135">ph x="1" /&gt; 클래스를 사용하여 메시지가 도착하는 서비스 엔드포인트의 이름을 기반으로 메시지를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-135">Uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> class to match messages based on the name of the service endpoint they arrived on.</span></span>|<span data-ttu-id="d20db-136">서비스 끝점의 이름 예: "serviceEndpoint1"입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-136">The name of the service endpoint, for example: "serviceEndpoint1".</span></span>  <span data-ttu-id="d20db-137">이는 라우팅 서비스에서 노출되는 엔드포인트 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-137">This should be one of the endpoints exposed on the Routing Service.</span></span>|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|<span data-ttu-id="d20db-138">MatchAll</span><span class="sxs-lookup"><span data-stu-id="d20db-138">MatchAll</span></span>|<span data-ttu-id="d20db-139"><xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-139">Uses the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span> <span data-ttu-id="d20db-140">이 필터는 도착하는 메시지를 모두 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-140">This filter matches all arriving messages.</span></span>|<span data-ttu-id="d20db-141">filterData는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-141">filterData is not used.</span></span> <span data-ttu-id="d20db-142">이 필터는 항상 모든 메시지를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-142">This filter will always match all messages.</span></span>|\<filter name="matchAll1" filterType="MatchAll" />|  
|<span data-ttu-id="d20db-143">XPath</span><span class="sxs-lookup"><span data-stu-id="d20db-143">XPath</span></span>|<span data-ttu-id="d20db-144"><xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 클래스를 사용하여 메시지 내의 특정 XPath 쿼리를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-144">Uses the <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> class to match specific XPath queries within the message.</span></span>|<span data-ttu-id="d20db-145">메시지를 대조할 때 사용하는 XPath 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-145">The XPath query to use when matching messages.</span></span>|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 <span data-ttu-id="d20db-146">다음 예제에서는 XPath, EndpointName 및 PrefixEndpointAddress 메시지 필터를 사용하는 필터 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-146">The following example defines filter entries that use the XPath, EndpointName, and PrefixEndpointAddress message filters.</span></span> <span data-ttu-id="d20db-147">이 예제에서는 RoundRobinFilter1 및 RoundRobinFilter2 항목에 대해 사용자 지정 필터를 사용하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-147">This example also demonstrates using a custom filter for the RoundRobinFilter1 and RoundRobinFilter2 entries.</span></span>  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> <span data-ttu-id="d20db-148">단순히 필터를 정의하는 것만으로는 메시지에 필터가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-148">Simply defining a filter does not cause messages to be evaluated against the filter.</span></span> <span data-ttu-id="d20db-149">필터는 필터 테이블에 추가되어야 하며, 그러면 필터 테이블은 라우팅 서비스에 의해 노출되는 서비스 엔드포인트와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-149">The filter must be added to a filter table, which is then associated with the service endpoint exposed by the Routing Service.</span></span>  
  
### <a name="namespace-table"></a><span data-ttu-id="d20db-150">네임스페이스 테이블</span><span class="sxs-lookup"><span data-stu-id="d20db-150">Namespace Table</span></span>  

 <span data-ttu-id="d20db-151">XPath 필터를 사용할 때 XPath 쿼리가 포함된 필터 데이터는 네임스페이스 사용으로 인해 그 크기가 상당히 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-151">When using an XPath filter, the filter data that contains the XPath query can become extremely large due to the use of namespaces.</span></span> <span data-ttu-id="d20db-152">이 문제를 완화하기 위해 라우팅 서비스는 네임스페이스 테이블을 사용하여 사용자 고유의 네임스페이스 접두사를 정의할 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-152">To alleviate this problem the Routing Service provides the ability to define your own namespace prefixes by using the namespace table.</span></span>  
  
 <span data-ttu-id="d20db-153">네임스페이스 테이블은 XPath에 사용 가능한 공통 네임스페이스를 위한 네임스페이스 접두사를 정의하는 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> 개체 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-153">The namespace table is a collection of <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objects that defines the namespace prefixes for common namespaces that can be used in an XPath.</span></span> <span data-ttu-id="d20db-154">다음은 네임스페이스 테이블에 포함된 기본 네임스페이스 및 네임스페이스 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-154">The following are the default namespaces and namespace prefixes that are contained in the namespace table.</span></span>  
  
|<span data-ttu-id="d20db-155">접두사</span><span class="sxs-lookup"><span data-stu-id="d20db-155">Prefix</span></span>|<span data-ttu-id="d20db-156">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="d20db-156">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="d20db-157">s11</span><span class="sxs-lookup"><span data-stu-id="d20db-157">s11</span></span>|`http://schemas.xmlsoap.org/soap/envelope`|  
|<span data-ttu-id="d20db-158">s12</span><span class="sxs-lookup"><span data-stu-id="d20db-158">s12</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="d20db-159">wsaAugust2004</span><span class="sxs-lookup"><span data-stu-id="d20db-159">wsaAugust2004</span></span>|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|<span data-ttu-id="d20db-160">wsa10</span><span class="sxs-lookup"><span data-stu-id="d20db-160">wsa10</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="d20db-161">sm</span><span class="sxs-lookup"><span data-stu-id="d20db-161">sm</span></span>|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|<span data-ttu-id="d20db-162">tempuri</span><span class="sxs-lookup"><span data-stu-id="d20db-162">tempuri</span></span>|`http://tempuri.org`|  
|<span data-ttu-id="d20db-163">ser</span><span class="sxs-lookup"><span data-stu-id="d20db-163">ser</span></span>|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 <span data-ttu-id="d20db-164">XPath 쿼리에서 특정 네임스페이스를 사용할 예정인 경우 이를 고유한 네임스페이스 접두사와 함께 네임스페이스 테이블에 추가하면 모든 XPath 쿼리에서 전체 네임스페이스 대신 이 접두사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-164">When you know that you will be using a specific namespace in your XPath queries, you can add it to the namespace table along with a unique namespace prefix and use the prefix in any XPath query instead of the full namespace.</span></span> <span data-ttu-id="d20db-165">다음 예에서는 네임 스페이스에 대 한 "custom" 접두사를 정의 합니다 `"http://my.custom.namespace"` .이 접두사는 filterData에 포함 된 XPath 쿼리에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-165">The following example defines a prefix of "custom" for the namespace `"http://my.custom.namespace"`, which is then used in the XPath query contained in filterData.</span></span>  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a><span data-ttu-id="d20db-166">필터 테이블</span><span class="sxs-lookup"><span data-stu-id="d20db-166">Filter Tables</span></span>  

 <span data-ttu-id="d20db-167">각 필터 요소는 메시지에 적용할 수 있는 논리 비교를 정의하며 필터 테이블은 필터 요소와 대상 클라이언트 엔드포인트 간의 연결을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-167">While each filter element defines a logical comparison that can be applied to a message, the filter table provides the association between the filter element and the destination client endpoint.</span></span> <span data-ttu-id="d20db-168">필터 테이블은 필터, 기본 대상 엔드포인트 및 대체 백업 엔드포인트 목록 간의 연결을 정의하는 명명된 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> 개체 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-168">A filter table is a named collection of <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objects that define the association between a filter, a primary destination endpoint, and a list of alternative backup endpoints.</span></span> <span data-ttu-id="d20db-169">또한 필터 테이블 항목을 통해 각 필터 조건에 대해 선택적인 우선 순위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-169">The filter table entries also allow you to specify an optional priority for each filter condition.</span></span> <span data-ttu-id="d20db-170">다음 예제에서는 두 가지 필터를 정의한 다음 각 필터를 대상 엔드포인트와 연결하는 필터 테이블을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-170">The following example defines two filters and then defines a filter table that associates each filter with a destination endpoint.</span></span>  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a><span data-ttu-id="d20db-171">필터 평가 우선 순위</span><span class="sxs-lookup"><span data-stu-id="d20db-171">Filter Evaluation Priority</span></span>  

 <span data-ttu-id="d20db-172">기본적으로 필터 테이블의 모든 항목은 동시에 평가되며, 평가되는 메시지는 일치하는 각 필터 항목에 연결된 엔드포인트로 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-172">By default, all entries in the filter table are evaluated simultaneously, and the message being evaluated is routed to the endpoint(s) associated with each matching filter entry.</span></span> <span data-ttu-id="d20db-173">여러 필터가 `true`를 반환하고 메시지가 단방향 또는 이중인 경우 메시지는 일치하는 모든 필터에 대한 엔드포인트로 멀티캐스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-173">If multiple filters evaluate to `true`, and the message is one-way or duplex, the message is multicast to the endpoints for all matching filters.</span></span> <span data-ttu-id="d20db-174">요청-회신 메시지의 경우 클라이언트에 하나의 회신만 반환할 수 있으므로 멀티캐스트될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-174">Request-reply messages cannot be multicast because only one reply can be returned to the client.</span></span>  
  
 <span data-ttu-id="d20db-175">각 필터에 우선 순위를 지정하면 더 복잡한 라우팅 논리를 구현할 수 있습니다. 라우팅 서비스는 가장 우선 순위가 높은 필터부터 시작하여 모든 필터를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-175">More complex routing logic can be implemented by specifying priority levels for each filter; the Routing Service evaluates all filters at the highest priority level first.</span></span> <span data-ttu-id="d20db-176">메시지가 이 수준의 필터와 일치할 경우 우선 순위가 더 아래인 필터는 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-176">If a message matches a filter of this level, no filters of a lower priority are processed.</span></span> <span data-ttu-id="d20db-177">예를 들어 들어오는 단방향 메시지는 먼저 우선 순위가 2인 모든 필터를 기준으로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-177">For example, an incoming one-way message is first evaluated against all filters with a priority of 2.</span></span> <span data-ttu-id="d20db-178">이 우선 순위에서 메시지와 일치하는 필터가 없으므로 그 다음으로 우선 순위가 1인 필터와 메시지가 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-178">The message does not match any filter at this priority level, so next the message is compared against filters with a priority of 1.</span></span> <span data-ttu-id="d20db-179">두 개의 우선 순위 1 필터가 메시지와 일치하며, 메시지가 단방향 메시지이므로 두 대상 엔드포인트 모두로 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-179">Two priority 1 filters match the message, and because it is a one-way message it is routed to both destination endpoints.</span></span>  <span data-ttu-id="d20db-180">우선 순위 1 필터 중에서 일치가 발견되었으므로 우선 순위가 0인 필터는 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-180">Because a match was found among the priority 1 filters, no filters of priority 0 are evaluated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d20db-181">우선 순위가 지정되지 않으면 기본 우선 순위인 0이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-181">If no priority is specified, the default priority of 0 is used.</span></span>  
  
 <span data-ttu-id="d20db-182">다음 예제에서는 테이블에서 참조되는 필터에 대해 우선 순위 2, 1 및 0을 지정하는 필터 테이블을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-182">The following example defines a filter table that specifies priorities of 2, 1, and 0 for the filters referenced in the table.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 <span data-ttu-id="d20db-183">앞의 예제에서 메시지가 XPathFilter와 일치할 경우 roundingCalcEndpoint로 라우트되며, 테이블의 다른 모든 필터는 우선 순위가 더 낮으므로 더 이상 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-183">In the preceding example, if a message matches the XPathFilter, it will be routed to the roundingCalcEndpoint and no further filters in the table will be evaluated because all other filters are of a lower priority.</span></span> <span data-ttu-id="d20db-184">그러나 메시지가 XPathFilter와 일치하지 않는 경우 그 다음 우선 순위의 모든 필터(EndpointNameFilter 및 PrefixAddressFilter)를 기준으로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-184">However, if the message does not match the XPathFilter it will then be evaluated against all filters of the next lower priority, EndpointNameFilter and PrefixAddressFilter.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d20db-185">우선 순위 평가로 인해 성능이 저하될 수 있으므로 가능한 경우 우선 순위를 지정하는 대신 단독 필터를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d20db-185">When possible, use exclusive filters instead of specifying a priority because priority evaluation can result in performance degradation.</span></span>  
  
### <a name="backup-lists"></a><span data-ttu-id="d20db-186">백업 목록</span><span class="sxs-lookup"><span data-stu-id="d20db-186">Backup Lists</span></span>  

 <span data-ttu-id="d20db-187">필터 테이블의 각 필터는 선택적으로 백업 목록을 지정할 수 있습니다. 백업 목록은 명명된 엔드포인트 컬렉션입니다(<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>).</span><span class="sxs-lookup"><span data-stu-id="d20db-187">Each filter in the filter table can optionally specify a backup list, which is a named collection of endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>).</span></span> <span data-ttu-id="d20db-188">이 컬렉션에는 <xref:System.ServiceModel.CommunicationException>에 지정된 기본 엔드포인트로 보낼 때 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>이 발생하는 경우 메시지를 전송할 엔드포인트가 순서대로 나열된 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-188">This collection contains an ordered list of endpoints that the message will be transmitted to in the event of a <xref:System.ServiceModel.CommunicationException> when sending to the primary endpoint specified in <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>.</span></span> <span data-ttu-id="d20db-189">다음 예에서는 두 개의 끝점이 포함 된 "backupServiceEndpoints" 라는 백업 목록을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-189">The following example defines a backup list named "backupServiceEndpoints" that contains two endpoints.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 <span data-ttu-id="d20db-190">앞의 예제에서 기본 끝점 "대상"에 대 한 송신이 실패 하면 라우팅 서비스는 나열 된 시퀀스에서 각 끝점에 송신을 시도 하 고, 먼저 backupServiceQueue로 보낸 후 backupServiceQueue에 보내기에 실패 하는 경우 alternateServiceQueue에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-190">In the preceding example, if a send to the primary endpoint "Destination" fails, the Routing Service will try sending to each endpoint in the sequence they are listed, first sending to backupServiceQueue and subsequently sending to alternateServiceQueue if the send to backupServiceQueue fails.</span></span> <span data-ttu-id="d20db-191">모든 백업 엔드포인트가 실패할 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d20db-191">If all backup endpoints fail, a fault is returned.</span></span>
