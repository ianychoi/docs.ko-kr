---
description: 다음에 대해 자세히 알아보세요. <netNamedPipeBinding>
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b6ee706337d3dd33c653bfa0d2b91f4eda0fcea5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683946"
---
# \<netNamedPipeBinding>

<span data-ttu-id="9bd3d-102">프로세스 간 시스템 통신에 적합한, 안전하고 신뢰할 수 있는 바인딩을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="9bd3d-103">기본적으로 이 바인딩에서는 안정성을 위한 WS-ReliableMessaging, 전송 보안을 위한 전송 보안, 메시지 배달을 위한 명명된 파이프 및 이진 메시지 인코딩을 지원하는 런타임 통신 스택을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9bd3d-104">구문</span><span class="sxs-lookup"><span data-stu-id="9bd3d-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bd3d-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9bd3d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9bd3d-106">다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bd3d-107">특성</span><span class="sxs-lookup"><span data-stu-id="9bd3d-107">Attributes</span></span>  
  
|<span data-ttu-id="9bd3d-108">attribute</span><span class="sxs-lookup"><span data-stu-id="9bd3d-108">Attribute</span></span>|<span data-ttu-id="9bd3d-109">설명</span><span class="sxs-lookup"><span data-stu-id="9bd3d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bd3d-110">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="9bd3d-110">closeTimeout</span></span>|<span data-ttu-id="9bd3d-111">닫기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9bd3d-112">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9bd3d-113">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-113">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9bd3d-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="9bd3d-114">hostNameComparisonMode</span></span>|<span data-ttu-id="9bd3d-115">URI 구문 분석에 사용되는 HTTP 호스트 이름 비교 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-115">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9bd3d-116">이 특성은 <xref:System.ServiceModel.HostNameComparisonMode> 형식이며 URI에 대해 비교할 때 호스트 이름이 서비스에 연결하는 데 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-116">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9bd3d-117">기본값은 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>이며 이 값은 비교 시 호스트 이름을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-117">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="9bd3d-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9bd3d-118">maxBufferPoolSize</span></span>|<span data-ttu-id="9bd3d-119">이 바인딩의 최대 버퍼 풀 크기를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9bd3d-120">기본값은 524,288바이트(512 \* 1024)입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-120">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9bd3d-121">WCF(Windows Communication Foundation)의 많은 부분에서 버퍼를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9bd3d-122">버퍼를 사용할 때마다 만들고 삭제하면 비용이 많이 들며, 버퍼에 대한 가비지 수집 역시 비용이 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9bd3d-123">버퍼 풀이 있으면 이 풀로부터 버퍼를 가져와 사용한 다음 다시 풀로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9bd3d-124">따라서 버퍼를 만들고 제거하는 데 오버헤드를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="9bd3d-125">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="9bd3d-125">maxBufferSize</span></span>|<span data-ttu-id="9bd3d-126">메시지를 메모리에 저장하는 데 사용되는 버퍼의 최대 크기(바이트)를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-126">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="9bd3d-127">버퍼가 꽉 차면 초과 데이터는 버퍼에 공간이 생길 때까지 내부 소켓에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-127">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="9bd3d-128">이 값은 `maxReceivedMessageSize` 특성보다 작을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-128">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="9bd3d-129">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-129">The default is 65536.</span></span> <span data-ttu-id="9bd3d-130">자세한 내용은 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-130">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="9bd3d-131">maxConnections</span><span class="sxs-lookup"><span data-stu-id="9bd3d-131">maxConnections</span></span>|<span data-ttu-id="9bd3d-132">서비스에서 생성하고 수락하는 최대 아웃바운드 및 인바운드 연결 수를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-132">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="9bd3d-133">들어오는 연결과 나가는 연결 수는 이 특성에서 지정한 별도의 제한에 따라 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-133">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="9bd3d-134">이 제한을 초과하는 인바운드 연결은 연결 수가 제한 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-134">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="9bd3d-135">이 한도를 초과하는 아웃바운드 연결은 연결 수가 한도 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-135">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="9bd3d-136">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-136">The default is 10.</span></span>|  
|<span data-ttu-id="9bd3d-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9bd3d-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="9bd3d-138">헤더를 비롯하여 이 바인딩으로 구성된 채널에서 받을 수 있는 최대 메시지 크기(바이트)를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9bd3d-139">이 한도를 초과하는 메시지를 보낸 사람은 SOAP 오류를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="9bd3d-140">수신자는 메시지를 삭제하고 추적 로그에 이벤트 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9bd3d-141">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-141">The default is 65536.</span></span>|  
|<span data-ttu-id="9bd3d-142">name</span><span class="sxs-lookup"><span data-stu-id="9bd3d-142">name</span></span>|<span data-ttu-id="9bd3d-143">바인딩의 구성 이름을 포함하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9bd3d-144">이 값은 바인딩의 ID로 사용되므로 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9bd3d-145">.NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-145">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9bd3d-146">기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="9bd3d-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="9bd3d-147">openTimeout</span></span>|<span data-ttu-id="9bd3d-148">열기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9bd3d-149">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9bd3d-150">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9bd3d-151">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="9bd3d-151">receiveTimeout</span></span>|<span data-ttu-id="9bd3d-152">받기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9bd3d-153">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9bd3d-154">기본값은 00:10:00입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-154">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="9bd3d-155">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="9bd3d-155">sendTimeout</span></span>|<span data-ttu-id="9bd3d-156">보내기 작업을 완료하기 위해 제공된 시간 간격을 지정하는 <xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9bd3d-157">이 값은 <xref:System.TimeSpan.Zero>보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9bd3d-158">기본값은 00:01:00입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="9bd3d-159">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="9bd3d-159">transactionFlow</span></span>|<span data-ttu-id="9bd3d-160">바인딩에서 WS-Transactions 이동을 지원할지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9bd3d-161">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-161">The default is `false`.</span></span>|  
|<span data-ttu-id="9bd3d-162">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="9bd3d-162">transactionProtocol</span></span>|<span data-ttu-id="9bd3d-163">이 바인딩과 함께 사용되는 트랜잭션 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-163">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="9bd3d-164">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-164">Valid values are</span></span><br /><br /> <span data-ttu-id="9bd3d-165">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="9bd3d-165">-   OleTransactions</span></span><br /><span data-ttu-id="9bd3d-166">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="9bd3d-166">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="9bd3d-167">기본값은 OleTransactions입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-167">The default is OleTransactions.</span></span> <span data-ttu-id="9bd3d-168">이 특성은 <xref:System.ServiceModel.TransactionProtocol> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-168">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="9bd3d-169">transferMode</span><span class="sxs-lookup"><span data-stu-id="9bd3d-169">transferMode</span></span>|<span data-ttu-id="9bd3d-170">메시지가 버퍼링되거나 스트리밍되는지 또는 요청이나 응답인지 지정하는 <xref:System.ServiceModel.TransferMode> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-170">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bd3d-171">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9bd3d-171">Child Elements</span></span>  
  
|<span data-ttu-id="9bd3d-172">요소</span><span class="sxs-lookup"><span data-stu-id="9bd3d-172">Element</span></span>|<span data-ttu-id="9bd3d-173">설명</span><span class="sxs-lookup"><span data-stu-id="9bd3d-173">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="9bd3d-174">바인딩에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-174">Defines the security settings for the binding.</span></span> <span data-ttu-id="9bd3d-175">이 요소는 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-175">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9bd3d-176">이 바인딩으로 구성된 엔드포인트에서 처리할 수 있는 SOAP 메시지의 복잡성에 대한 제약 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9bd3d-177">이 요소는 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bd3d-178">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9bd3d-178">Parent Elements</span></span>  
  
|<span data-ttu-id="9bd3d-179">요소</span><span class="sxs-lookup"><span data-stu-id="9bd3d-179">Element</span></span>|<span data-ttu-id="9bd3d-180">설명</span><span class="sxs-lookup"><span data-stu-id="9bd3d-180">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="9bd3d-181">이 요소는 표준 및 사용자 지정 바인딩의 컬렉션을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-181">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd3d-182">설명</span><span class="sxs-lookup"><span data-stu-id="9bd3d-182">Remarks</span></span>  

 <span data-ttu-id="9bd3d-183">`NetNamedPipeBinding`에서는 기본적으로 런타임 통신 스택을 생성하며, 이 스택은 전송 보안, 메시지 배달을 위한 명명된 파이프 및 이진 메시지 인코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-183">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="9bd3d-184">이 바인딩은 시스템 통신을 위한 적절한 WCF(Windows Communication Foundation) 시스템 제공 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-184">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="9bd3d-185">트랜잭션도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-185">It also supports transactions.</span></span>  
  
 <span data-ttu-id="9bd3d-186">`NetNamedPipeBinding`의 기본 구성은 `NetTcpBinding`에서 제공하는 구성과 비슷하지만, WCF 구현이 시스템에서만 사용되므로 노출되는 기능이 더 적기 때문에 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-186">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="9bd3d-187">가장 두드러진 차이점은 `securityMode` 설정에서는 `None` 및 `Transport` 옵션만 제공한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-187">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="9bd3d-188">SOAP 보안 지원은 포함된 옵션이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-188">SOAP security support is not an included option.</span></span> <span data-ttu-id="9bd3d-189">보안 동작은 선택적 `securityMode` 특성을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd3d-190">예제</span><span class="sxs-lookup"><span data-stu-id="9bd3d-190">Example</span></span>  

 <span data-ttu-id="9bd3d-191">다음은 netNamedPipeBinding 바인딩의 예로, 동일한 시스템에서 프로세스 간 통신을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-191">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="9bd3d-192">이름이 지정된 파이프는 시스템 간에 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-192">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="9bd3d-193">클라이언트 및 서비스 구성 파일에 바인딩이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-193">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="9bd3d-194">바인딩 형식은 `binding` 요소의 `<endpoint>` 특성에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-194">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="9bd3d-195">netNamedPipeBinding 바인딩을 구성하고 설정 중 일부를 변경하려면 바인딩 구성을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-195">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="9bd3d-196">엔드포인트는 `bindingConfiguration` 특성이 있는 이름으로 바인딩 구성을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-196">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="9bd3d-197">이 예제에서는 바인딩 구성 이름이 Binding1로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd3d-197">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="9bd3d-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bd3d-198">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="9bd3d-199">바인딩</span><span class="sxs-lookup"><span data-stu-id="9bd3d-199">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9bd3d-200">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="9bd3d-200">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9bd3d-201">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="9bd3d-201">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
