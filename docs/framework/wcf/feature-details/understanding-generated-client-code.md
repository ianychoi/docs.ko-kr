---
title: 생성된 클라이언트 코드 이해
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 22cb7a7b4cd6712d509586cb2ae7699d233eff2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281627"
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="19a76-102">생성된 클라이언트 코드 이해</span><span class="sxs-lookup"><span data-stu-id="19a76-102">Understanding Generated Client Code</span></span>

<span data-ttu-id="19a76-103">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 는 클라이언트 애플리케이션을 빌드하는 데 사용할 클라이언트 애플리케이션 구성 파일과 클라이언트 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-103">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="19a76-104">이 항목에서는 표준 서비스 계약 시나리오를 위해 생성된 코드 예제를 간략히 살펴 봅니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-104">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> <span data-ttu-id="19a76-105">생성 된 코드를 사용 하 여 클라이언트 응용 프로그램을 빌드하는 방법에 대 한 자세한 내용은 [WCF 클라이언트 개요](../wcf-client-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19a76-105">For more information about building a client application using the generated code, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="19a76-106">개요</span><span class="sxs-lookup"><span data-stu-id="19a76-106">Overview</span></span>  

 <span data-ttu-id="19a76-107">Visual Studio를 사용 하 여 프로젝트에 대 한 WCF (Windows Communication Foundation) 클라이언트 형식을 생성 하는 경우 일반적으로 생성 된 클라이언트 코드를 검사할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-107">If you use Visual Studio to generate Windows Communication Foundation (WCF) client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="19a76-108">동일한 서비스를 수행하는 개발 환경을 사용하지 않는 경우 Svcutil.exe 같은 도구를 사용하여 클라이언트 코드를 생성한 다음 해당 코드를 사용하여 클라이언트 애플리케이션을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-108">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="19a76-109">Svcutil.exe에는 생성된 형식 정보를 수정하는 많은 옵션이 있으므로 이 항목에서 모든 시나리오에 대해 설명하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-109">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="19a76-110">그러나 다음 표준 작업에는 생성된 코드를 찾는 과정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-110">However, the following standard tasks involve locating generated code:</span></span>  
  
- <span data-ttu-id="19a76-111">서비스 계약 인터페이스 식별</span><span class="sxs-lookup"><span data-stu-id="19a76-111">Identifying service contract interfaces.</span></span>  
  
- <span data-ttu-id="19a76-112">WCF 클라이언트 클래스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-112">Identifying the WCF client class.</span></span>  
  
- <span data-ttu-id="19a76-113">데이터 형식 식별</span><span class="sxs-lookup"><span data-stu-id="19a76-113">Identifying data types.</span></span>  
  
- <span data-ttu-id="19a76-114">이중 서비스에 대한 콜백 계약 식별</span><span class="sxs-lookup"><span data-stu-id="19a76-114">Identifying callback contracts for duplex services.</span></span>  
  
- <span data-ttu-id="19a76-115">도우미 서비스 계약 채널 인터페이스 식별</span><span class="sxs-lookup"><span data-stu-id="19a76-115">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="19a76-116">서비스 계약 인터페이스 찾기</span><span class="sxs-lookup"><span data-stu-id="19a76-116">Finding Service Contract Interfaces</span></span>  

 <span data-ttu-id="19a76-117">서비스 계약을 모델링하는 인터페이스를 찾으려면 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 특성으로 표시된 인터페이스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-117">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="19a76-118">다른 특성이 있고 특성 자체에 명시적 속성이 설정되어 있어 빠른 읽기로 이 특성을 찾기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-118">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="19a76-119">서비스 계약 인터페이스와 클라이언트 계약 인터페이스는 두 가지 다른 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-119">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="19a76-120">다음 코드 예제에서는 원래 서비스 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-120">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="19a76-121">다음 코드 예제에서는 Svcutil.exe에서 생성된 것과 동일한 서비스 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-121">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="19a76-122">생성 된 서비스 계약 인터페이스를 클래스와 함께 사용 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 하 여 서비스 작업을 호출 하는 데 사용할 WCF 채널 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-122">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a WCF channel object with which to invoke service operations.</span></span> <span data-ttu-id="19a76-123">자세한 내용은 [방법: ChannelFactory 사용](how-to-use-the-channelfactory.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19a76-123">For more information, see [How to: Use the ChannelFactory](how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="19a76-124">WCF 클라이언트 클래스 찾기</span><span class="sxs-lookup"><span data-stu-id="19a76-124">Finding WCF Client Classes</span></span>  

 <span data-ttu-id="19a76-125">사용할 서비스 계약을 구현 하는 WCF 클라이언트 클래스를 찾으려면 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 형식 매개 변수가 이전에 찾아서 해당 인터페이스를 확장 하는 서비스 계약 인터페이스인의 확장을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-125">To locate the WCF client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="19a76-126">다음 코드 예제에서는 <xref:System.ServiceModel.ClientBase%601> 형식의 `ISampleService`클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-126">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="19a76-127">이 WCF 클라이언트 클래스의 새 인스턴스를 만들고이 클래스에서 구현 하는 메서드를 호출 하 여이 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-127">You can use this WCF client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="19a76-128">이러한 메서드는 상호 작용하도록 디자인 및 구성된 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-128">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> <span data-ttu-id="19a76-129">자세한 내용은 [WCF 클라이언트 개요](../wcf-client-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19a76-129">For more information, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19a76-130">SvcUtil.exe는 WCF 클라이언트 클래스를 생성할 때 디버거가 WCF 클라이언트 클래스를 단계별로 실행하지 못하도록 하는 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 를 클라이언트 클래스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-130">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="19a76-131">데이터 형식 찾기</span><span class="sxs-lookup"><span data-stu-id="19a76-131">Finding Data Types</span></span>  

 <span data-ttu-id="19a76-132">생성된 코드에서 데이터 형식을 찾으려는 경우 가장 기본적인 메커니즘은 계약에 지정된 형식 이름을 식별하고 해당 형식 선언에 대해 코드를 검색하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-132">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="19a76-133">예를 들어 다음 계약은 `SampleMethod` 에서 `microsoft.wcf.documentation.SampleFault`형식의 SOAP 오류를 반환할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-133">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="19a76-134">`SampleFault` 를 검색하면 다음 형식 선언을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-134">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="19a76-135">이 경우 데이터 형식은 클라이언트의 특정 예외인 <xref:System.ServiceModel.FaultException%601> 에서 throw되는 세부 유형이며, 여기서 세부 유형 매개 변수는 `microsoft.wcf.documentation.SampleFault`입니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-135">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> <span data-ttu-id="19a76-136">데이터 형식에 대 한 자세한 내용은 [서비스 계약의 데이터 전송 지정](specifying-data-transfer-in-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19a76-136">For more information about data types, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="19a76-137">클라이언트에서 예외를 처리 하는 방법에 대 한 자세한 내용은 [오류 보내기 및 받기](../sending-and-receiving-faults.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="19a76-137">For more information about handling exceptions in clients, see [Sending and Receiving Faults](../sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="19a76-138">이중 서비스에 대한 콜백 계약 찾기</span><span class="sxs-lookup"><span data-stu-id="19a76-138">Finding Callback Contracts for Duplex Services</span></span>  

 <span data-ttu-id="19a76-139">계약 인터페이스가 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 속성 값을 지정하는 서비스 계약을 찾으면 해당 계약이 이중 계약을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-139">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="19a76-140">이중 계약에서는 클라이언트 애플리케이션이 콜백 계약을 구현하는 콜백 클래스를 만들고 해당 클래스의 인스턴스를 서비스와의 통신에 사용되는 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> 로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-140">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> <span data-ttu-id="19a76-141">이중 클라이언트에 대 한 자세한 내용은 [방법: 이중 계약을 사용 하 여 서비스 액세스](how-to-access-services-with-a-duplex-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19a76-141">For more information about duplex clients, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="19a76-142">다음 계약에서는 `SampleDuplexHelloCallback`형식의 콜백 계약을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-142">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="19a76-143">해당 콜백 계약을 검색하면 클라이언트 애플리케이션이 구현해야 하는 다음 인터페이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-143">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="19a76-144">서비스 계약 채널 인터페이스 찾기</span><span class="sxs-lookup"><span data-stu-id="19a76-144">Finding Service Contract Channel Interfaces</span></span>  

 <span data-ttu-id="19a76-145"><xref:System.ServiceModel.ChannelFactory> 클래스를 서비스 계약 인터페이스와 함께 사용하면 채널을 명시적으로 열고, 닫고, 중단할 수 있도록 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 인터페이스로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-145">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="19a76-146">더 편리하게 작업할 수 있도록 Svcutil.exe 도구에서는 서비스 계약 인터페이스와 <xref:System.ServiceModel.IClientChannel> 을 모두 구현하는 도우미 인터페이스도 생성되므로 캐스팅하지 않고도 클라이언트 채널 인프라와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-146">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="19a76-147">다음 코드에서는 이전의 서비스 계약을 구현하는 도우미 클라이언트 채널에 대한 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19a76-147">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="19a76-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19a76-148">See also</span></span>

- [<span data-ttu-id="19a76-149">WCF 클라이언트 개요</span><span class="sxs-lookup"><span data-stu-id="19a76-149">WCF Client Overview</span></span>](../wcf-client-overview.md)
