---
title: 서비스 계약 디자인
description: WCF 프로그래밍에서 서비스 계약을 만드는 방법, 사용 가능한 작업 및 데이터 형식, 서비스 계약의 기타 측면을 포함 하 여 서비스 계약에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 11d2019023c7389d27607c93b920946837b5c365
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294831"
---
# <a name="designing-service-contracts"></a><span data-ttu-id="1c05d-103">서비스 계약 디자인</span><span class="sxs-lookup"><span data-stu-id="1c05d-103">Designing Service Contracts</span></span>

<span data-ttu-id="1c05d-104">이 항목에서는 서비스 계약의 정의, 서비스 계약을 정의하는 방법, 사용 가능한 작업(및 기본 메시지 교환에 미치는 영향), 사용되는 데이터 형식 및 시나리오 요구 사항을 만족하는 작업을 디자인하는 데 도움이 되는 기타 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-104">This topic describes what service contracts are, how they are defined, what operations are available (and the implications for the underlying message exchanges), what data types are used, and other issues that help you design operations that satisfy the requirements of your scenario.</span></span>  
  
## <a name="creating-a-service-contract"></a><span data-ttu-id="1c05d-105">서비스 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="1c05d-105">Creating a Service Contract</span></span>  

 <span data-ttu-id="1c05d-106">서비스는 여러 연산을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-106">Services expose a number of operations.</span></span> <span data-ttu-id="1c05d-107">WCF (Windows Communication Foundation) 응용 프로그램에서 메서드를 만들고 특성으로 표시 하 여 작업을 정의 합니다 <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1c05d-107">In Windows Communication Foundation (WCF) applications, define the operations by creating a method and marking it with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> <span data-ttu-id="1c05d-108">그런 다음 서비스 계약을 만들려면 <xref:System.ServiceModel.ServiceContractAttribute> 특성으로 표시한 인터페이스 내에 작업을 선언하거나 같은 특성으로 표시된 클래스에 작업을 정의하여 작업을 함께 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-108">Then, to create a service contract, group together your operations, either by declaring them within an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute, or by defining them in a class marked with the same attribute.</span></span> <span data-ttu-id="1c05d-109">(기본 예제는 [방법: 서비스 계약 정의](how-to-define-a-wcf-service-contract.md)를 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="1c05d-109">(For a basic example, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).)</span></span>  
  
 <span data-ttu-id="1c05d-110">특성이 없는 메서드는 <xref:System.ServiceModel.OperationContractAttribute> 서비스 작업이 아니고 WCF 서비스에 의해 노출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-110">Any methods that do not have a <xref:System.ServiceModel.OperationContractAttribute> attribute are not service operations and are not exposed by WCF services.</span></span>  
  
 <span data-ttu-id="1c05d-111">이 항목에서는 다음과 같이 서비스 계약을 디자인할 때의 결정 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-111">This topic describes the following decision points when designing a service contract:</span></span>  
  
- <span data-ttu-id="1c05d-112">클래스 또는 인터페이스 사용 여부</span><span class="sxs-lookup"><span data-stu-id="1c05d-112">Whether to use classes or interfaces.</span></span>  
  
- <span data-ttu-id="1c05d-113">교환할 데이터 형식 지정 방법</span><span class="sxs-lookup"><span data-stu-id="1c05d-113">How to specify the data types you want to exchange.</span></span>  
  
- <span data-ttu-id="1c05d-114">사용할 수 있는 교환 패턴 형식</span><span class="sxs-lookup"><span data-stu-id="1c05d-114">The types of exchange patterns you can use.</span></span>  
  
- <span data-ttu-id="1c05d-115">계약의 명시적 보안 요구 사항 부분을 만들 수 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="1c05d-115">Whether you can make explicit security requirements part of the contract.</span></span>  
  
- <span data-ttu-id="1c05d-116">작업 입력 및 출력에 대한 제한</span><span class="sxs-lookup"><span data-stu-id="1c05d-116">The restrictions for operation inputs and outputs.</span></span>  
  
## <a name="classes-or-interfaces"></a><span data-ttu-id="1c05d-117">클래스 또는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1c05d-117">Classes or Interfaces</span></span>  

 <span data-ttu-id="1c05d-118">클래스와 인터페이스는 모두 기능 그룹화를 나타내므로 WCF 서비스 계약을 정의 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-118">Both classes and interfaces represent a grouping of functionality and, therefore, both can be used to define a WCF service contract.</span></span> <span data-ttu-id="1c05d-119">그러나 인터페이스는 서비스 계약을 직접 모델링하므로 인터페이스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-119">However, it is recommended that you use interfaces because they directly model service contracts.</span></span> <span data-ttu-id="1c05d-120">구현을 사용하지 않으면 인터페이스는 특정 서명이 있는 메서드 그룹화만 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-120">Without an implementation, interfaces do no more than define a grouping of methods with certain signatures.</span></span> <span data-ttu-id="1c05d-121">서비스 계약 인터페이스를 구현 하 고 WCF 서비스를 구현 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-121">Implement a service contract interface and you have implemented a WCF service.</span></span>  
  
 <span data-ttu-id="1c05d-122">관리되는 인터페이스의 모든 장점이 서비스 계약 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-122">All the benefits of managed interfaces apply to service contract interfaces:</span></span>  
  
- <span data-ttu-id="1c05d-123">서비스 계약 인터페이스는 다른 여러 서비스 계약 인터페이스를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-123">Service contract interfaces can extend any number of other service contract interfaces.</span></span>  
  
- <span data-ttu-id="1c05d-124">단일 클래스는 그러한 서비스 계약 인터페이스를 구현하여 원하는 만큼 서비스 계약을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-124">A single class can implement any number of service contracts by implementing those service contract interfaces.</span></span>  
  
- <span data-ttu-id="1c05d-125">인터페이스 구현을 변경하여 서비스 계약의 구현을 수정할 수 있지만 서비스 계약은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-125">You can modify the implementation of a service contract by changing the interface implementation, while the service contract remains the same.</span></span>  
  
- <span data-ttu-id="1c05d-126">기존 인터페이스와 새 인터페이스를 구현하여 서비스에 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-126">You can version your service by implementing the old interface and the new one.</span></span> <span data-ttu-id="1c05d-127">기존 클라이언트는 원래 버전에 연결하며, 새 클라이언트는 새 버전에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-127">Old clients connect to the original version, while newer clients can connect to the newer version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c05d-128">다른 서비스 계약 인터페이스에서 상속할 때 이름 또는 네임스페이스와 같은 작업 속성은 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-128">When inheriting from other service contract interfaces, you cannot override operation properties, such as the name or namespace.</span></span> <span data-ttu-id="1c05d-129">재정의하려면 현재 서비스 계약에 새 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-129">If you attempt to do so, you create a new operation in the current service contract.</span></span>  
  
 <span data-ttu-id="1c05d-130">인터페이스를 사용 하 여 서비스 계약을 만드는 방법에 대 한 예제는 [방법: 계약 인터페이스를 사용 하 여 서비스 만들기](./feature-details/how-to-create-a-service-with-a-contract-interface.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-130">For an example of using an interface to create a service contract, see [How to: Create a Service with a Contract Interface](./feature-details/how-to-create-a-service-with-a-contract-interface.md).</span></span>  
  
 <span data-ttu-id="1c05d-131">하지만 클래스를 사용하여 서비스 계약을 정의하고 그 계약을 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-131">You can, however, use a class to define a service contract and implement that contract at the same time.</span></span> <span data-ttu-id="1c05d-132"><xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute>를 클래스와 클래스의 메서드에 각각 직접 적용하여 서비스를 만들면 빠르고 간편하다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-132">The advantage of creating your services by applying <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> directly to the class and the methods on the class, respectively, is speed and simplicity.</span></span> <span data-ttu-id="1c05d-133">단점은 관리되는 클래스가 여러 상속을 지원하지 않으므로 따라서 한 번에 하나의 서비스 계약만 구현할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-133">The disadvantages are that managed classes do not support multiple inheritance, and as a result they can only implement one service contract at a time.</span></span> <span data-ttu-id="1c05d-134">또한 클래스 또는 메서드 서명을 수정하면 해당 서비스에 대한 공용 계약이 수정되므로 수정되지 않은 클라이언트는 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-134">In addition, any modification to the class or method signatures modifies the public contract for that service, which can prevent unmodified clients from using your service.</span></span> <span data-ttu-id="1c05d-135">자세한 내용은 [서비스 계약 구현](implementing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-135">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
 <span data-ttu-id="1c05d-136">클래스를 사용 하 여 서비스 계약을 만들고 동시에 구현 하는 예제는 [방법: 계약 클래스를 사용 하 여 서비스 만들기](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-136">For an example that uses a class to create a service contract and implements it at the same time, see [How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).</span></span>  
  
 <span data-ttu-id="1c05d-137">이때 인터페이스를 사용하여 서비스 계약을 정의하는 경우와 클래스를 사용하여 서비스 계약을 정의하는 경우의 차이를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-137">At this point, you should understand the difference between defining your service contract by using an interface and by using a class.</span></span> <span data-ttu-id="1c05d-138">다음 단계에서는 서비스와 클라이언트 간에 주고받을 수 있는 데이터를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-138">The next step is deciding what data can be passed back and forth between a service and its clients.</span></span>  
  
## <a name="parameters-and-return-values"></a><span data-ttu-id="1c05d-139">매개 변수 및 반환 값</span><span class="sxs-lookup"><span data-stu-id="1c05d-139">Parameters and Return Values</span></span>  

 <span data-ttu-id="1c05d-140">각 작업마다 반환 값과 매개 변수가 있으며, 값이 `void`인 경우에도 값은 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-140">Each operation has a return value and a parameter, even if these are `void`.</span></span> <span data-ttu-id="1c05d-141">그러나 개체 간에 개체에 대한 참조를 전달할 수 있는 로컬 메서드와 달리 서비스 작업은 개체에 대한 참조를 전달하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-141">However, unlike a local method, in which you can pass references to objects from one object to another, service operations do not pass references to objects.</span></span> <span data-ttu-id="1c05d-142">대신 개체 복사본을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-142">Instead, they pass copies of the objects.</span></span>  
  
 <span data-ttu-id="1c05d-143">매개 변수 또는 반환 값에 사용되는 각 형식이 serialize될 수 있어야 하므로 이것은 중요한 사항입니다. 즉, 해당 형식의 개체를 바이트 스트림으로 변환하고 바이트 스트림에서 개체로 변환할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-143">This is significant because each type used in a parameter or return value must be serializable; that is, it must be possible to convert an object of that type into a stream of bytes and from a stream of bytes into an object.</span></span>  
  
 <span data-ttu-id="1c05d-144">.NET Framework에 여러 가지 형식이 있으므로 기본적으로 기본 형식을 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-144">Primitive types are serializable by default, as are many types in the .NET Framework.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c05d-145">작업 시그니처의 매개 변수 이름 값은 계약의 일부 이며 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-145">The value of the parameter names in the operation signature are part of the contract and are case sensitive.</span></span> <span data-ttu-id="1c05d-146">같은 매개 변수 이름을 로컬로 사용하지만 게시된 메타데이터에서 이름을 수정하려면 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1c05d-146">If you want to use the same parameter name locally but modify the name in the published metadata, see the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.</span></span>  
  
#### <a name="data-contracts"></a><span data-ttu-id="1c05d-147">데이터 계약</span><span class="sxs-lookup"><span data-stu-id="1c05d-147">Data Contracts</span></span>  

 <span data-ttu-id="1c05d-148">WCF (Windows Communication Foundation) 응용 프로그램과 같은 서비스 지향 응용 프로그램은 Microsoft 및 Microsoft 이외의 플랫폼에서 가장 광범위 하 게 사용할 수 있는 클라이언트 응용 프로그램과 상호 운용 되도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-148">Service-oriented applications like Windows Communication Foundation (WCF) applications are designed to interoperate with the widest possible number of client applications on both Microsoft and non-Microsoft platforms.</span></span> <span data-ttu-id="1c05d-149">광범위한 상호 운용을 위해 <xref:System.Runtime.Serialization.DataContractAttribute> 및 <xref:System.Runtime.Serialization.DataMemberAttribute> 특성으로 형식을 표시하여 서비스 작업이 교환하는 데이터를 설명하는 서비스 계약의 부분인 데이터 계약을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-149">For the widest possible interoperability, it is recommended that you mark your types with the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create a data contract, which is the portion of the service contract that describes the data that your service operations exchange.</span></span>  
  
 <span data-ttu-id="1c05d-150">데이터 계약은 옵트인 스타일 계약입니다. 데이터 계약 특성을 명시적으로 적용하지 않으면 형식이나 데이터 멤버가 serialize되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-150">Data contracts are opt-in style contracts: No type or data member is serialized unless you explicitly apply the data contract attribute.</span></span> <span data-ttu-id="1c05d-151">데이터 계약은 관리되는 코드의 액세스 범위와 관련이 없습니다. 전용 데이터 멤버는 serialize될 수 있고 공개적으로 액세스할 다른 곳으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-151">Data contracts are unrelated to the access scope of the managed code: Private data members can be serialized and sent elsewhere to be accessed publicly.</span></span> <span data-ttu-id="1c05d-152">(데이터 계약의 기본 예제는 [방법: 클래스 또는 구조체에 대 한 기본 데이터 계약 만들기](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)를 참조 하세요.) WCF는 작업의 기능을 사용할 수 있도록 하는 기본 SOAP 메시지의 정의와 메시지 본문의 데이터 형식에 대 한 serialization을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-152">(For a basic example of a data contract, see [How to: Create a Basic Data Contract for a Class or Structure](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF handles the definition of the underlying SOAP messages that enable the operation's functionality as well as the serialization of your data types into and out of the body of the messages.</span></span> <span data-ttu-id="1c05d-153">데이터 형식을 serialize할 수 있다면 작업을 디자인할 때 기본 메시지 교환 인프라에 대해 고려하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-153">As long as your data types are serializable, you do not need to think about the underlying message exchange infrastructure when designing your operations.</span></span>  
  
 <span data-ttu-id="1c05d-154">일반적인 WCF 응용 프로그램에서는 및 특성을 사용 하 여 <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> 작업에 대 한 데이터 계약을 만들기는 하지만 다른 serialization 메커니즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-154">Although the typical WCF application uses the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create data contracts for operations, you can use other serialization mechanisms.</span></span> <span data-ttu-id="1c05d-155">표준 <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> 및 <xref:System.Xml.Serialization.IXmlSerializable> 메커니즘은 모두 애플리케이션 간에 데이터 형식을 전달하는 기본 SOAP 메시지에 데이터 형식의 serialization을 처리하는 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-155">The standard <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> and <xref:System.Xml.Serialization.IXmlSerializable> mechanisms all work to handle the serialization of your data types into the underlying SOAP messages that carry them from one application to another.</span></span> <span data-ttu-id="1c05d-156">데이터 형식에 특별 지원이 필요할 경우 더 많은 serialization 전략을 채택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-156">You can employ more serialization strategies if your data types require special support.</span></span> <span data-ttu-id="1c05d-157">WCF 응용 프로그램에서 데이터 형식의 serialization을 위한 선택 사항에 대 한 자세한 내용은 [서비스 계약의 데이터 전송 지정](./feature-details/specifying-data-transfer-in-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-157">For more information about the choices for serialization of data types in WCF applications, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span>  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a><span data-ttu-id="1c05d-158">메시지 교환에 매개 변수 및 반환 값 매핑</span><span class="sxs-lookup"><span data-stu-id="1c05d-158">Mapping Parameters and Return Values to Message Exchanges</span></span>  

 <span data-ttu-id="1c05d-159">서비스 작업은 애플리케이션 데이터뿐만 아니라 애플리케이션이 특정 표준 보안, 트랜잭션 및 세션 관련 기능을 지원하는 데 필요한 데이터를 주고받는 SOAP 메시지의 기본 교환에 의해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-159">Service operations are supported by an underlying exchange of SOAP messages that transfer application data back and forth, in addition to the data required by the application to support certain standard security, transaction, and session-related features.</span></span> <span data-ttu-id="1c05d-160">이 경우 서비스 작업의 서명은 데이터 전송 및 작업에 필요한 기능을 지원할 수 있는 특정 기본 mep ( *메시지 교환 패턴* )를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-160">Because this is the case, the signature of a service operation dictates a certain underlying *message exchange pattern* (MEP) that can support the data transfer and the features an operation requires.</span></span> <span data-ttu-id="1c05d-161">WCF 프로그래밍 모델에서 요청/회신, 단방향 및 이중 메시지 패턴의 세 가지 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-161">You can specify three patterns in the WCF programming model: request/reply, one-way, and duplex message patterns.</span></span>  
  
##### <a name="requestreply"></a><span data-ttu-id="1c05d-162">요청/회신</span><span class="sxs-lookup"><span data-stu-id="1c05d-162">Request/Reply</span></span>  

 <span data-ttu-id="1c05d-163">요청/회신 패턴은 요청 발신자(클라이언트 애플리케이션)가 요청과 상호 관련된 회신을 받는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-163">A request/reply pattern is one in which a request sender (a client application) receives a reply with which the request is correlated.</span></span> <span data-ttu-id="1c05d-164">이 패턴은 하나 이상의 매개 변수가 작업에 전달되고 반환값이 다시 호출자에게 전달되는 작업을 지원하므로 기본 MEP입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-164">This is the default MEP because it supports an operation in which one or more parameters are passed to the operation and a return value is passed back to the caller.</span></span> <span data-ttu-id="1c05d-165">예를 들어, 다음 C# 코드 예제에서는 문자열 하나를 사용하여 문자열을 반환하는 기본적인 서비스 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-165">For example, the following C# code example shows a basic service operation that takes one string and returns a string.</span></span>  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 <span data-ttu-id="1c05d-166">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-166">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 <span data-ttu-id="1c05d-167">이 작업 서명은 기본 메시지 교환 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-167">This operation signature dictates the form of underlying message exchange.</span></span> <span data-ttu-id="1c05d-168">상관 관계가 없는 경우 WCF는 반환 값이 의도 한 작업을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-168">If no correlation existed, WCF cannot determine for which operation the return value is intended.</span></span>  
  
 <span data-ttu-id="1c05d-169">다른 기본 메시지 패턴을 지정 하지 않을 경우 (Visual Basic)을 반환 하는 서비스 작업 `void` `Nothing` 은 요청/회신 메시지 교환입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-169">Note that unless you specify a different underlying message pattern, even service operations that return `void` (`Nothing` in Visual Basic) are request/reply message exchanges.</span></span> <span data-ttu-id="1c05d-170">작업 결과, 클라이언트가 작업을 비동기적으로 호출하지 않으면 일반적인 경우 메시지가 비어 있어도 클라이언트가 반환 메시지를 받을 때까지 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-170">The result for your operation is that unless a client invokes the operation asynchronously, the client stops processing until the return message is received, even though that message is empty in the normal case.</span></span> <span data-ttu-id="1c05d-171">다음 C# 코드 예제에서는 클라이언트가 빈 메시지를 응답으로 받을 때까지 반환되지 않는 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-171">The following C# code example shows an operation that does not return until the client has received an empty message in response.</span></span>  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="1c05d-172">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-172">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="1c05d-173">앞의 예제에서는 작업을 수행하는 데 시간이 오래 걸릴 경우 클라이언트 성능 및 응답성이 저하될 수 있지만 `void`를 반환하는 경우에도 요청/회신 작업에 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-173">The preceding example can slow client performance and responsiveness if the operation takes a long time to perform, but there are advantages to request/reply operations even when they return `void`.</span></span> <span data-ttu-id="1c05d-174">명백한 점은 통신에서든 처리 중에든 일부 서비스 관련 오류 조건이 발생했음을 나타내는 응답 메시지에 SOAP 오류가 반환될 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-174">The most obvious one is that SOAP faults can be returned in the response message, which indicates that some service-related error condition has occurred, whether in communication or processing.</span></span> <span data-ttu-id="1c05d-175">서비스 계약에 지정된 SOAP 오류는 클라이언트 애플리케이션에 <xref:System.ServiceModel.FaultException%601> 개체로 전달됩니다. 여기서 형식 매개 변수는 서비스 계약에 지정된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-175">SOAP faults that are specified in a service contract are passed to the client application as a <xref:System.ServiceModel.FaultException%601> object, where the type parameter is the type specified in the service contract.</span></span> <span data-ttu-id="1c05d-176">이렇게 하면 클라이언트에 WCF 서비스의 오류 조건에 대 한 정보를 쉽게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-176">This makes notifying clients about error conditions in WCF services easy.</span></span> <span data-ttu-id="1c05d-177">예외, SOAP 오류 및 오류 처리에 대 한 자세한 내용은 [계약 및 서비스에서 오류 지정 및 처리](specifying-and-handling-faults-in-contracts-and-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-177">For more information about exceptions, SOAP faults, and error handling, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span> <span data-ttu-id="1c05d-178">요청/회신 서비스 및 클라이언트의 예를 보려면 [방법: Request-Reply 계약 만들기](./feature-details/how-to-create-a-request-reply-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-178">To see an example of a request/reply service and client, see [How to: Create a Request-Reply Contract](./feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="1c05d-179">요청-회신 패턴의 문제에 대 한 자세한 내용은 [요청-회신 서비스](./feature-details/request-reply-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-179">For more information about issues with the request-reply pattern, see [Request-Reply Services](./feature-details/request-reply-services.md).</span></span>  
  
##### <a name="one-way"></a><span data-ttu-id="1c05d-180">단방향</span><span class="sxs-lookup"><span data-stu-id="1c05d-180">One-way</span></span>  

 <span data-ttu-id="1c05d-181">WCF 서비스 응용 프로그램의 클라이언트가 작업이 완료 될 때까지 기다리지 않고 SOAP 오류를 처리 하지 않으면 작업에서 단방향 메시지 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-181">If the client of a WCF service application should not wait for the operation to complete and does not process SOAP faults, the operation can specify a one-way message pattern.</span></span> <span data-ttu-id="1c05d-182">단방향 작업은 클라이언트에서 작업을 호출 하 고 WCF가 네트워크에 메시지를 쓴 후 처리를 계속 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-182">A one-way operation is one in which a client invokes an operation and continues processing after WCF writes the message to the network.</span></span> <span data-ttu-id="1c05d-183">일반적으로 아웃바운드 메시지에 보내는 데이터가 아주 크지 않은 경우 데이터를 보내는 데 문제가 없다면 클라이언트가 바로 계속해서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-183">Typically this means that unless the data being sent in the outbound message is extremely large the client continues running almost immediately (unless there is an error sending the data).</span></span> <span data-ttu-id="1c05d-184">이러한 형식의 메시지 교환 패턴은 클라이언트에서 서비스 애플리케이션으로 이벤트와 비슷한 동작을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-184">This type of message exchange pattern supports event-like behavior from a client to a service application.</span></span>  
  
 <span data-ttu-id="1c05d-185">메시지를 보내지만 반환되는 메시지가 없는 메시지 교환은 `void` 이외의 반환 값을 지정하는 서비스 작업을 지원할 수 없습니다. 이 경우 <xref:System.InvalidOperationException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-185">A message exchange in which one message is sent and none are received cannot support a service operation that specifies a return value other than `void`; in this case an <xref:System.InvalidOperationException> exception is thrown.</span></span>  
  
 <span data-ttu-id="1c05d-186">반환 메시지가 없다는 것은 처리 또는 통신 오류를 나타내는 SOAP 오류가 반환되지 않았음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-186">No return message also means that there can be no SOAP fault returned to indicate any errors in processing or communication.</span></span> <span data-ttu-id="1c05d-187">단방향 작업인 경우 통신 오류 정보에 이중 메시지 교환 패턴이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-187">(Communicating error information when operations are one-way operations requires a duplex message exchange pattern.)</span></span>  
  
 <span data-ttu-id="1c05d-188">`void`를 반환하는 작업에 단방향 메시지 교환을 지정하려면 다음 C# 코드 예제처럼 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-188">To specify a one-way message exchange for an operation that returns `void`, set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as in the following C# code example.</span></span>  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="1c05d-189">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-189">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="1c05d-190">이 메서드는 앞의 요청/회신 예제와 동일하지만 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성을 `true`로 설정한다는 것은 메서드는 같지만 서비스 작업에서 반환 메시지를 보내지 않으며 아웃바운드 메시지가 채널 계층에 전달되면 바로 클라이언트가 반환된다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-190">This method is identical to the preceding request/reply example, but setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` means that although the method is identical, the service operation does not send a return message and clients return immediately once the outbound message has been handed to the channel layer.</span></span> <span data-ttu-id="1c05d-191">예제는 [방법: One-Way 계약 만들기](./feature-details/how-to-create-a-one-way-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-191">For an example, see [How to: Create a One-Way Contract](./feature-details/how-to-create-a-one-way-contract.md).</span></span> <span data-ttu-id="1c05d-192">단방향 패턴에 대 한 자세한 내용은 단방향 [서비스](./feature-details/one-way-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-192">For more information about the one-way pattern, see [One-Way Services](./feature-details/one-way-services.md).</span></span>  
  
##### <a name="duplex"></a><span data-ttu-id="1c05d-193">이중</span><span class="sxs-lookup"><span data-stu-id="1c05d-193">Duplex</span></span>  

 <span data-ttu-id="1c05d-194">이중 패턴의 특징은 단방향 메시징을 사용하든 요청/회신 메시징을 사용하든 관계없이 서비스와 클라이언트 모두 서로 독립적으로 메시지를 보낼 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-194">A duplex pattern is characterized by the ability of both the service and the client to send messages to each other independently whether using one-way or request/reply messaging.</span></span> <span data-ttu-id="1c05d-195">이와 같은 형식의 양방향 통신은 클라이언트와 직접 통신해야 하는 서비스에 유용하며, 메시지를 교환하는 양측에 이벤트와 유사한 동작을 비롯하여 비동기 환경을 제공하는 데도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-195">This form of two-way communication is useful for services that must communicate directly to the client or for providing an asynchronous experience to either side of a message exchange, including event-like behavior.</span></span>  
  
 <span data-ttu-id="1c05d-196">이중 패턴은 클라이언트와 통신하기 위한 추가 메커니즘 때문에 요청/회신 또는 단방향 패턴보다 조금 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-196">The duplex pattern is slightly more complex than the request/reply or one-way patterns because of the additional mechanism for communicating with the client.</span></span>  
  
 <span data-ttu-id="1c05d-197">이중 계약을 디자인하려면 콜백 계약도 디자인하고 서비스 계약을 표시하는 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 특성의 <xref:System.ServiceModel.ServiceContractAttribute> 속성에 해당 콜백 계약의 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-197">To design a duplex contract, you must also design a callback contract and assign the type of that callback contract to the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property of the <xref:System.ServiceModel.ServiceContractAttribute> attribute that marks your service contract.</span></span>  
  
 <span data-ttu-id="1c05d-198">이중 패턴을 구현하려면 클라이언트에서 호출되는 메서드 선언을 포함하는 다른 인터페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-198">To implement a duplex pattern, you must create a second interface that contains the method declarations that are called on the client.</span></span>  
  
 <span data-ttu-id="1c05d-199">서비스 및 해당 서비스에 액세스 하는 클라이언트를 만드는 방법에 대 한 예제는 [방법: 이중 계약 만들기](./feature-details/how-to-create-a-duplex-contract.md) 및 [방법: 이중 계약을 사용 하 여 서비스 액세스](./feature-details/how-to-access-services-with-a-duplex-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-199">For an example of creating a service, and a client that accesses that service, see [How to: Create a Duplex Contract](./feature-details/how-to-create-a-duplex-contract.md) and [How to: Access Services with a Duplex Contract](./feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="1c05d-200">작업 샘플은 [이중](./samples/duplex.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-200">For a working sample, see [Duplex](./samples/duplex.md).</span></span> <span data-ttu-id="1c05d-201">이중 계약을 사용 하는 문제에 대 한 자세한 내용은 [이중 서비스](./feature-details/duplex-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-201">For more information about issues using duplex contracts, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1c05d-202">서비스가 이중 메시지를 받으면 들어오는 해당 메시지에서 `ReplyTo` 요소를 확인하여 회신을 보낼 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-202">When a service receives a duplex message, it looks at the `ReplyTo` element in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="1c05d-203">메시지를 받는 데 사용되는 채널이 보안되지 않으면 신뢰할 수 없는 클라이언트가 대상 컴퓨터의 `ReplyTo`를 사용하여 악의적인 메시지를 보낼 수 있으므로 해당 대상 컴퓨터의 서비스 거부(DOS)가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-203">If the channel that is used to receive the message is not secured, then an untrusted client could send a malicious message with a target machine's `ReplyTo`, leading to a denial of service (DOS) of that target machine.</span></span>  
  
##### <a name="out-and-ref-parameters"></a><span data-ttu-id="1c05d-204">Out 및 Ref 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c05d-204">Out and Ref Parameters</span></span>  

 <span data-ttu-id="1c05d-205">대부분의 경우 `in` 매개 변수 ( `ByVal` Visual Basic) 및 `out` 및 `ref` 매개 변수 ( `ByRef` Visual Basic)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-205">In most cases, you can use `in` parameters (`ByVal` in Visual Basic) and `out` and `ref` parameters (`ByRef` in Visual Basic).</span></span> <span data-ttu-id="1c05d-206">`out` 및 `ref` 매개 변수 모두 데이터가 작업에서 반환됨을 나타내기 때문에 다음과 같은 작업 서명은 작업 서명이 `void`를 반환해도 요청/회신 작업이 필요하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-206">Because both `out` and `ref` parameters indicate that data is returned from an operation, an operation signature such as the following specifies that a request/reply operation is required even though the operation signature returns `void`.</span></span>  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 <span data-ttu-id="1c05d-207">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-207">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 <span data-ttu-id="1c05d-208">서명에 특정한 구조가 있는 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-208">The only exceptions are those cases in which your signature has a particular structure.</span></span> <span data-ttu-id="1c05d-209">예를 들어, 작업을 선언하는 데 사용된 메서드가 <xref:System.ServiceModel.NetMsmqBinding>를 반환하는 경우에만 `void` 바인딩을 사용하여 클라이언트와 통신할 수 있습니다. 반환 값이든 `ref` 또는 `out` 매개 변수든 출력 값이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-209">For example, you can use the <xref:System.ServiceModel.NetMsmqBinding> binding to communicate with clients only if the method used to declare an operation returns `void`; there can be no output value, whether it is a return value, `ref`, or `out` parameter.</span></span>  
  
 <span data-ttu-id="1c05d-210">또한 `out` 또는 `ref` 매개 변수를 사용하려면 작업에 수정된 개체를 다시 전달할 기본 응답 메시지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-210">In addition, using `out` or `ref` parameters requires that the operation have an underlying response message to carry back the modified object.</span></span> <span data-ttu-id="1c05d-211">단방향 작업인 경우 런타임에 <xref:System.InvalidOperationException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-211">If your operation is a one-way operation, an <xref:System.InvalidOperationException> exception is thrown at runtime.</span></span>  
  
### <a name="specify-message-protection-level-on-the-contract"></a><span data-ttu-id="1c05d-212">계약에 메시지 보호 수준 지정</span><span class="sxs-lookup"><span data-stu-id="1c05d-212">Specify Message Protection Level on the Contract</span></span>  

 <span data-ttu-id="1c05d-213">계약을 디자인할 때 계약을 구현하는 서비스의 메시지 보호 수준도 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-213">When designing your contract, you must also decide the message protection level of services that implement your contract.</span></span> <span data-ttu-id="1c05d-214">이 작업은 메시지 보안이 계약의 엔드포인트에 있는 바인딩에 적용되는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-214">This is necessary only if message security is applied to the binding in the contract's endpoint.</span></span> <span data-ttu-id="1c05d-215">바인딩에 보안이 해제된 경우(시스템 제공 바인딩이 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>를 <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType> 값으로 설정한 경우) 계약에 대한 메시지 보호 수준을 결정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-215">If the binding has security turned off (that is, if the system-provided binding sets the <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> to the value <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) then you do not have to decide on the message protection level for the contract.</span></span> <span data-ttu-id="1c05d-216">대부분의 경우 적용된 메시지 수준 보안과 함께 시스템 제공 바인딩은 충분한 보호 수준을 제공하므로 작업별 또는 메시지별로 보호 수준을 고려하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-216">In most cases, system-provided bindings with message-level security applied provide a sufficient protection level and you do not have to consider the protection level for each operation or for each message.</span></span>  
  
 <span data-ttu-id="1c05d-217">보호 수준은 서비스를 지원하는 메시지(또는 메시지 부분)가 서명되어 있는지, 서명 및 암호화되어 있는지 또는 서명이나 암호화 없이 보내졌는지를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-217">The protection level is a value that specifies whether the messages (or message parts) that support a service are signed, signed and encrypted, or sent without signatures or encryption.</span></span> <span data-ttu-id="1c05d-218">보호 수준은 여러 범위에서 설정될 수 있습니다. 서비스 수준에서는 특정 작업, 해당 작업 내의 메시지 또는 메시지 부분에 대해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-218">The protection level can be set at various scopes: At the service level, for a particular operation, for a message within that operation, or a message part.</span></span> <span data-ttu-id="1c05d-219">한 범위에 설정된 값은 명시적으로 재정의되지 않는 한 더 작은 범위의 기본값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-219">Values set at one scope become the default value for smaller scopes unless explicitly overridden.</span></span> <span data-ttu-id="1c05d-220">바인딩 구성에서 계약에 필요한 최소 보호 수준을 제공할 수 없으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-220">If a binding configuration cannot provide the required minimum protection level for the contract, an exception is thrown.</span></span> <span data-ttu-id="1c05d-221">또한 보호 수준 값이 계약에 명시적으로 설정되어 있지 않을 때 바인딩에 메시지 보안이 있는 경우에는 바인딩 구성이 모든 메시지에 대한 보호 수준을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-221">And when no protection level values are explicitly set on the contract, the binding configuration controls the protection level for all messages if the binding has message security.</span></span> <span data-ttu-id="1c05d-222">이것은 기본적인 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-222">This is the default behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1c05d-223">계약의 여러 범위를 명시적으로 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType>의 전체 보호 수준보다 낮게 설정할 것인지를 결정하는 것은 일반적으로 향상된 성능의 보안 정도를 절충하는 결정입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-223">Deciding whether to explicitly set various scopes of a contract to less than the full protection level of <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> is generally a decision that trades some degree of security for increased performance.</span></span> <span data-ttu-id="1c05d-224">이러한 경우 사용자는 작업과 관련된 사항을 확인하고 작업에서 교환하는 데이터 값을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-224">In these cases, your decisions must revolve around your operations and the value of the data they exchange.</span></span> <span data-ttu-id="1c05d-225">자세한 내용은 [서비스 보안](securing-services.md)설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-225">For more information, see [Securing Services](securing-services.md).</span></span>  
  
 <span data-ttu-id="1c05d-226">예를 들어, 다음 코드 예제는 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 또는 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 속성을 계약에 설정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-226">For example, the following code example does not set either the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> or the <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> property on the contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 <span data-ttu-id="1c05d-227">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-227">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 <span data-ttu-id="1c05d-228">기본 `ISampleService`(<xref:System.ServiceModel.WSHttpBinding>인 기본 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>)을 사용하여 엔드포인트의 <xref:System.ServiceModel.SecurityMode.Message> 구현과 상호 작용할 때 이것이 기본 보호 수준이므로 모든 메시지가 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-228">When interacting with an `ISampleService` implementation in an endpoint with a default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>), all messages are encrypted and signed because this is the default protection level.</span></span> <span data-ttu-id="1c05d-229">그러나 `ISampleService` 서비스가 기본 <xref:System.ServiceModel.BasicHttpBinding>(<xref:System.ServiceModel.SecurityMode>인 기본 <xref:System.ServiceModel.SecurityMode.None>)과 함께 사용되면 이 바인딩에 대한 보안이 없으므로 보호 수준이 무시되기 때문에(메시지가 암호화되거나 서명되지 않으므로) 모든 메시지가 텍스트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-229">However, when an `ISampleService` service is used with a default <xref:System.ServiceModel.BasicHttpBinding> (the default <xref:System.ServiceModel.SecurityMode>, which is <xref:System.ServiceModel.SecurityMode.None>), all messages are sent as text because there is no security for this binding and so the protection level is ignored (that is, the messages are neither encrypted nor signed).</span></span> <span data-ttu-id="1c05d-230"><xref:System.ServiceModel.SecurityMode>가 <xref:System.ServiceModel.SecurityMode.Message>로 변경된 경우에는 바인딩의 기본 보호 수준이 되므로 이러한 메시지가 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-230">If the <xref:System.ServiceModel.SecurityMode> was changed to <xref:System.ServiceModel.SecurityMode.Message>, then these messages would be encrypted and signed (because that would now be the binding's default protection level).</span></span>  
  
 <span data-ttu-id="1c05d-231">계약에 대한 보호 요구 사항을 명시적으로 지정하거나 조정하려면 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 속성(또는 더 작은 범위의 `ProtectionLevel` 속성 중 하나)을 서비스 계약에서 필요로 하는 수준으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-231">If you want to explicitly specify or adjust the protection requirements for your contract, set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property (or any of the `ProtectionLevel` properties at a smaller scope) to the level your service contract requires.</span></span> <span data-ttu-id="1c05d-232">이 경우 명시적 설정을 사용하려면 사용된 범위에 대해 최소한 해당 설정을 지원할 바인딩이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-232">In this case, using an explicit setting requires the binding to support that setting at a minimum for the scope used.</span></span> <span data-ttu-id="1c05d-233">예를 들어, 다음 코드 예제에서는 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 작업에 대해 하나의 `GetGuid` 값을 명시적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-233">For example, the following code example specifies one <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> value explicitly, for the `GetGuid` operation.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 <span data-ttu-id="1c05d-234">다음은 해당 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-234">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 <span data-ttu-id="1c05d-235">이 `IExplicitProtectionLevelSampleService` 계약을 구현하고 기본 <xref:System.ServiceModel.WSHttpBinding>(<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>인 기본 <xref:System.ServiceModel.SecurityMode.Message>)을 사용하는 엔드포인트가 있는 서비스는 다음과 같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-235">A service that implements this `IExplicitProtectionLevelSampleService` contract and has an endpoint that uses the default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>) has the following behavior:</span></span>  
  
- <span data-ttu-id="1c05d-236">`GetString` 작업 메시지가 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-236">The `GetString` operation messages are encrypted and signed.</span></span>  
  
- <span data-ttu-id="1c05d-237">`GetInt` 작업 메시지는 암호화되지 않고 서명되지 않은(일반 텍스트) 텍스트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-237">The `GetInt` operation messages are sent as unencrypted and unsigned (that is, plain) text.</span></span>  
  
- <span data-ttu-id="1c05d-238">`GetGuid` 작업 <xref:System.Guid?displayProperty=nameWithType>는 암호화되고 서명된 메시지에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-238">The `GetGuid` operation <xref:System.Guid?displayProperty=nameWithType> is returned in a message that is encrypted and signed.</span></span>  
  
 <span data-ttu-id="1c05d-239">보호 수준 및 사용 방법에 대 한 자세한 내용은 [보호 수준 이해](understanding-protection-level.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-239">For more information about protection levels and how to use them, see [Understanding Protection Level](understanding-protection-level.md).</span></span> <span data-ttu-id="1c05d-240">보안에 대 한 자세한 내용은 [서비스](securing-services.md)보안 설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-240">For more information about security, see [Securing Services](securing-services.md).</span></span>  
  
##### <a name="other-operation-signature-requirements"></a><span data-ttu-id="1c05d-241">기타 작업 서명 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1c05d-241">Other Operation Signature Requirements</span></span>  

 <span data-ttu-id="1c05d-242">일부 애플리케이션 기능에는 특정한 종류의 작업 서명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-242">Some application features require a particular kind of operation signature.</span></span> <span data-ttu-id="1c05d-243">예를 들어, <xref:System.ServiceModel.NetMsmqBinding> 바인딩은 애플리케이션이 통신 중에 다시 시작할 수 있으며 메시지를 누락하지 않고 중지된 지점을 선택할 수 있는 영속 서비스 및 클라이언트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-243">For example, the <xref:System.ServiceModel.NetMsmqBinding> binding supports durable services and clients, in which an application can restart in the middle of communication and pick up where it left off without missing any messages.</span></span> <span data-ttu-id="1c05d-244">자세한 내용은 [WCF의 큐](./feature-details/queues-in-wcf.md)를 참조 하십시오. 그러나 영 속 작업에서는 하나의 매개 변수만 사용 `in` 하 고 반환 값은 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-244">(For more information, see [Queues in WCF](./feature-details/queues-in-wcf.md).) However, durable operations must take only one `in` parameter and have no return value.</span></span>  
  
 <span data-ttu-id="1c05d-245">또 다른 예제는 작업에 <xref:System.IO.Stream> 형식을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-245">Another example is the use of <xref:System.IO.Stream> types in operations.</span></span> <span data-ttu-id="1c05d-246"><xref:System.IO.Stream> 매개 변수에 전체 메시지 본문이 포함되므로 입력 또는 출력(`ref` 매개 변수, `out` 매개 변수 또는 반환 값)이 <xref:System.IO.Stream> 형식이면 작업에 지정된 입력 또는 출력이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-246">Because the <xref:System.IO.Stream> parameter includes the entire message body, if an input or an output (that is, `ref` parameter, `out` parameter, or return value) is of type <xref:System.IO.Stream>, then it must be the only input or output specified in your operation.</span></span> <span data-ttu-id="1c05d-247">또한 매개 변수나 반환 형식이 <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> 또는 <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-247">In addition, the parameter or return type must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, or <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c05d-248">스트림에 대 한 자세한 내용은 [대량 데이터 및 스트리밍](./feature-details/large-data-and-streaming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c05d-248">For more information about streams, see [Large Data and Streaming](./feature-details/large-data-and-streaming.md).</span></span>  
  
##### <a name="names-namespaces-and-obfuscation"></a><span data-ttu-id="1c05d-249">이름, 네임스페이스 및 난독 처리</span><span class="sxs-lookup"><span data-stu-id="1c05d-249">Names, Namespaces, and Obfuscation</span></span>  

 <span data-ttu-id="1c05d-250">계약을 WSDL로 변환하고 계약 메시지를 만들어 보낼 때는 계약 및 작업에 대한 정의에서 .NET 형식의 이름 및 네임스페이스가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-250">The names and namespaces of the .NET types in the definition of contracts and operations are significant when contracts are converted into WSDL and when contract messages are created and sent.</span></span> <span data-ttu-id="1c05d-251">따라서 `Name`, `Namespace`, <xref:System.ServiceModel.ServiceContractAttribute>,  <xref:System.ServiceModel.OperationContractAttribute> 및 다른 계약 특성과 같은 지원되는 모든 계약 특성의 <xref:System.Runtime.Serialization.DataContractAttribute> 및 <xref:System.Runtime.Serialization.DataMemberAttribute> 속성을 사용하여 서비스 계약 이름 및 네임스페이스를 명시적으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-251">Therefore, it is strongly recommended that service contract names and namespaces are explicitly set using the `Name` and `Namespace` properties of all supporting contract attributes such as the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>, and other contract attributes.</span></span>  
  
 <span data-ttu-id="1c05d-252">이름과 네임스페이스를 명시적으로 설정하지 않는 경우 어셈블리에서 IL 난독 처리를 사용하면 계약 형식 이름과 네임스페이스가 변경되고 WSDL 및 통신 교환이 수정되어 일반적으로 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-252">One result of this is that if the names and namespaces are not explicitly set, the use of IL obfuscation on the assembly alters the contract type names and namespaces and results in modified WSDL and wire exchanges that typically fail.</span></span> <span data-ttu-id="1c05d-253">계약 이름과 네임스페이스를 명시적으로 설정하지 않고 난독 처리를 사용하려면 <xref:System.Reflection.ObfuscationAttribute> 및 <xref:System.Reflection.ObfuscateAssemblyAttribute> 특성을 사용하여 계약 형식 이름 및 네임스페이스가 수정되지 않게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c05d-253">If you do not set the contract names and namespaces explicitly but do intend to use obfuscation, use the <xref:System.Reflection.ObfuscationAttribute> and <xref:System.Reflection.ObfuscateAssemblyAttribute> attributes to prevent the modification of the contract type names and namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c05d-254">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c05d-254">See also</span></span>

- [<span data-ttu-id="1c05d-255">방법: 요청-회신 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="1c05d-255">How to: Create a Request-Reply Contract</span></span>](./feature-details/how-to-create-a-request-reply-contract.md)
- [<span data-ttu-id="1c05d-256">방법: 단방향 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="1c05d-256">How to: Create a One-Way Contract</span></span>](./feature-details/how-to-create-a-one-way-contract.md)
- [<span data-ttu-id="1c05d-257">방법: 이중 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="1c05d-257">How to: Create a Duplex Contract</span></span>](./feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="1c05d-258">서비스 계약에서 데이터 전송 지정</span><span class="sxs-lookup"><span data-stu-id="1c05d-258">Specifying Data Transfer in Service Contracts</span></span>](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [<span data-ttu-id="1c05d-259">계약 및 서비스에서 오류 지정 및 처리</span><span class="sxs-lookup"><span data-stu-id="1c05d-259">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="1c05d-260">세션 사용</span><span class="sxs-lookup"><span data-stu-id="1c05d-260">Using Sessions</span></span>](using-sessions.md)
- [<span data-ttu-id="1c05d-261">동기 및 비동기 작업</span><span class="sxs-lookup"><span data-stu-id="1c05d-261">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="1c05d-262">신뢰할 수 있는 서비스</span><span class="sxs-lookup"><span data-stu-id="1c05d-262">Reliable Services</span></span>](reliable-services.md)
- [<span data-ttu-id="1c05d-263">서비스 및 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="1c05d-263">Services and Transactions</span></span>](services-and-transactions.md)
