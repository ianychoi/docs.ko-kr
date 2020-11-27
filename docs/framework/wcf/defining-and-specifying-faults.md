---
title: 오류 정의 및 지정
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: 67096c4531d13bc66f584c09c458c0a5a2a41c6b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260905"
---
# <a name="defining-and-specifying-faults"></a><span data-ttu-id="45c81-102">오류 정의 및 지정</span><span class="sxs-lookup"><span data-stu-id="45c81-102">Defining and Specifying Faults</span></span>

<span data-ttu-id="45c81-103">SOAP 오류는 오류 조건 정보를 서비스에서 클라이언트로 전달하고 양방향인 경우 상호 운용 가능한 방식으로 클라이언트에서 서비스로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-103">SOAP faults convey error condition information from a service to a client and, in the duplex case, from a client to a service in an interoperable way.</span></span> <span data-ttu-id="45c81-104">이 항목에서는 사용자 지정 오류 내용을 정의하는 시간과 방법에 대해 설명하고 이들을 반환할 수 있는 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-104">This topic discusses when and how to define custom fault content and specify which operations can return them.</span></span> <span data-ttu-id="45c81-105">서비스 또는 이중 클라이언트에서 이러한 오류를 보낼 수 있는 방법과 클라이언트 또는 서비스 응용 프로그램이 이러한 오류를 처리 하는 방법에 대 한 자세한 내용은 [오류 전송 및 수신](sending-and-receiving-faults.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45c81-105">For more information about how a service, or duplex client, can send those faults and how a client or service application handles these faults, see [Sending and Receiving Faults](sending-and-receiving-faults.md).</span></span> <span data-ttu-id="45c81-106">WCF (Windows Communication Foundation) 응용 프로그램의 오류 처리에 대 한 개요는 [계약 및 서비스에서 오류 지정 및 처리](specifying-and-handling-faults-in-contracts-and-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45c81-106">For an overview of error handling in Windows Communication Foundation (WCF) applications, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="45c81-107">개요</span><span class="sxs-lookup"><span data-stu-id="45c81-107">Overview</span></span>  

 <span data-ttu-id="45c81-108">선언된 SOAP 오류는 작업에 사용자 지정 SOAP 오류 유형을 지정하는 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>가 있는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-108">Declared SOAP faults are those in which an operation has a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> that specifies a custom SOAP fault type.</span></span> <span data-ttu-id="45c81-109">선언되지 않은 SOAP 오류는 작업 계약에 지정되지 않은 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-109">Undeclared SOAP faults are those that are not specified in the contract for an operation.</span></span> <span data-ttu-id="45c81-110">이 항목에서는 이러한 오류 조건을 식별하고, 클라이언트가 사용자 지정 SOAP 오류의 알림을 받을 때 이러한 오류 조건을 제대로 처리하는 데 사용할 수 있는 서비스에 대한 오류 계약을 만드는 과정을 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-110">This topic helps you identify those error conditions and create a fault contract for your service that clients can use to properly handle those error conditions when notified by custom SOAP faults.</span></span> <span data-ttu-id="45c81-111">기본 작업은 순서대로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-111">The basic tasks are, in order:</span></span>  
  
1. <span data-ttu-id="45c81-112">서비스 클라이언트에서 알아야 하는 오류 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-112">Define the error conditions that a client of your service should know about.</span></span>  
  
2. <span data-ttu-id="45c81-113">이러한 오류 조건에 대한 SOAP 오류의 사용자 지정 콘텐츠를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-113">Define the custom content of the SOAP faults for those error conditions.</span></span>  
  
3. <span data-ttu-id="45c81-114">throw하는 특정 SOAP 오류가 WSDL로 클라이언트에 노출되도록 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-114">Mark your operations so that the specific SOAP faults that they throw are exposed to clients in WSDL.</span></span>  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a><span data-ttu-id="45c81-115">클라이언트가 알아야 하는 오류 조건 정의</span><span class="sxs-lookup"><span data-stu-id="45c81-115">Defining Error Conditions That Clients Should Know About</span></span>  

 <span data-ttu-id="45c81-116">SOAP 오류는 특정 작업에 대한 오류 정보를 전달하는 공개적으로 설명된 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-116">SOAP faults are publicly described messages that carry fault information for a particular operation.</span></span> <span data-ttu-id="45c81-117">WSDL로 다른 작업 메시지와 함께 설명되므로 클라이언트는 작업을 호출할 때 이러한 오류를 알고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-117">Because they are described along with other operation messages in WSDL, clients know and, therefore, expect to handle such faults when invoking an operation.</span></span> <span data-ttu-id="45c81-118">그러나 WCF 서비스는 관리 코드로 작성 되므로 오류로 변환 되 고 클라이언트로 반환 되는 오류 조건을 결정 하는 것은 클라이언트를 사용 하는 공식 오류 대화에서 서비스의 오류 조건 및 버그를 구분할 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-118">But because WCF services are written in managed code, deciding which error conditions in managed code are to be converted into faults and returned to the client provides you the opportunity to separate error conditions and bugs in your service from the formal error conversation you have with a client.</span></span>  
  
 <span data-ttu-id="45c81-119">예를 들어 다음 코드 예제에서는 두 개의 정수를 받고 다른 정수를 반환하는 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-119">For example, the following code example shows an operation that takes two integers and returns another integer.</span></span> <span data-ttu-id="45c81-120">여기서 여러 개의 예외가 throw될 수 있으므로 오류 계약을 디자인할 때 클라이언트에 중요한 오류 조건을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-120">Several exceptions can be thrown here, so when designing the fault contract, you must determine which error conditions are important for your client.</span></span> <span data-ttu-id="45c81-121">이 경우 서비스에서 <xref:System.DivideByZeroException?displayProperty=nameWithType> 예외를 감지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-121">In this case, the service should detect the <xref:System.DivideByZeroException?displayProperty=nameWithType> exception.</span></span>  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb
<ServiceContract> _
Public Class CalculatorService
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 <span data-ttu-id="45c81-122">앞의 예제에서 작업은 0으로 나누기와 관련된 사용자 지정 SOAP 오류, 수학 연산과 관련이 있지만 0으로 나누기와 관련된 정보를 포함하는 사용자 지정 오류, 다른 여러 오류 상태에 대한 여러 개의 오류 또는 SOAP 오류 없음을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-122">In the preceding example the operation can either return a custom SOAP fault that is specific to dividing by zero, a custom fault that is specific to math operations but that contains information specific to dividing by zero, multiple faults for several different error situations, or no SOAP fault at all.</span></span>  
  
### <a name="define-the-content-of-error-conditions"></a><span data-ttu-id="45c81-123">오류 조건의 콘텐츠 정의</span><span class="sxs-lookup"><span data-stu-id="45c81-123">Define the Content of Error Conditions</span></span>  

 <span data-ttu-id="45c81-124">오류 조건이 유용하게 사용자 지정 SOAP 오류를 반환할 수 있는 오류 조건으로 식별되고 나면 다음 단계로 해당 오류의 콘텐츠를 정의하고 콘텐츠 구조가 serialize될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-124">Once an error condition has been identified as one that can usefully return a custom SOAP fault, the next step is to define the contents of that fault and ensure that the content structure can be serialized.</span></span> <span data-ttu-id="45c81-125">이전 섹션의 코드 예제에서는 `Divide` 작업과 관련이 있는 오류를 보여 주지만 `Calculator` 서비스에 다른 작업이 있는 경우 하나의 사용자 지정 SOAP 오류에서 `Divide`를 포함한 모든 계산기 오류 조건을 클라이언트에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-125">The code example in the preceding section shows an error specific to a `Divide` operation, but if there are other operations on the `Calculator` service, then a single custom SOAP fault can inform the client of all calculator error conditions, `Divide` included.</span></span> <span data-ttu-id="45c81-126">다음 코드 예제에서는 `MathFault`를 비롯하여 모든 수학 연산의 오류를 보고할 수 있는 사용자 지정 SOAP 오류인 `Divide`를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-126">The following code example shows the creation of a custom SOAP fault, `MathFault`, which can report errors made using all math operations, including `Divide`.</span></span> <span data-ttu-id="45c81-127">클래스에서 작업(`Operation` 속성)과 문제를 설명하는 값(`ProblemType` 속성)을 지정할 수 있지만 클래스 및 이러한 속성을 사용자 지정 SOAP 오류로 클라이언트에 전송하려면 serialize할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-127">While the class can specify an operation (the `Operation` property) and a value that describes the problem (the `ProblemType` property), the class and these properties must be serializable to be transferred to the client in a custom SOAP fault.</span></span> <span data-ttu-id="45c81-128">따라서 <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> 및 <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> 특성이 사용되어 형식과 해당 속성을 serialize할 수 있고 가능한 한 상호 운용될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-128">Therefore, the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> and <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> attributes are used to make the type and its properties serializable and as interoperable as possible.</span></span>  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 <span data-ttu-id="45c81-129">데이터를 serialize 할 수 있는지 확인 하는 방법에 대 한 자세한 내용은 [서비스 계약의 데이터 전송 지정](./feature-details/specifying-data-transfer-in-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45c81-129">For more information about how to ensure your data is serializable, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="45c81-130">에서 제공 하는 serialization 지원 목록은 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> [데이터 계약 Serializer에서 지 원하는 형식](./feature-details/types-supported-by-the-data-contract-serializer.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45c81-130">For a list of the serialization support that <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> provides, see [Types Supported by the Data Contract Serializer](./feature-details/types-supported-by-the-data-contract-serializer.md).</span></span>  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a><span data-ttu-id="45c81-131">오류 계약을 설정하도록 작업 표시</span><span class="sxs-lookup"><span data-stu-id="45c81-131">Mark Operations to Establish the Fault Contract</span></span>  

 <span data-ttu-id="45c81-132">사용자 지정 SOAP 오류의 일부로 반환되는 serialize될 수 있는 데이터 구조를 정의하고 나면 마지막 단계로 해당 형식의 SOAP 오류를 throw하는 것으로 작업 계약을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-132">Once a serializable data structure that is returned as part of a custom SOAP fault is defined, the last step is to mark your operation contract as throwing a SOAP fault of that type.</span></span> <span data-ttu-id="45c81-133">이렇게 하려면 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 특성을 사용하고 생성한 사용자 지정 데이터 형식을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-133">To do this, use the <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> attribute and pass the type of the custom data type that you have constructed.</span></span> <span data-ttu-id="45c81-134">다음 코드 예제에서는 <xref:System.ServiceModel.FaultContractAttribute> 특성을 사용하여 `Divide` 작업에서 `MathFault` 형식의 SOAP 오류를 반환할 수 있도록 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-134">The following code example shows how to use the <xref:System.ServiceModel.FaultContractAttribute> attribute to specify that the `Divide` operation can return a SOAP fault of type `MathFault`.</span></span> <span data-ttu-id="45c81-135">이제 다른 수학 기반 연산에서도 `MathFault`를 반환할 수 있도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-135">Other math-based operations can now also specify that they can return a `MathFault`.</span></span>  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 <span data-ttu-id="45c81-136">둘 이상의 <xref:System.ServiceModel.FaultContractAttribute> 특성으로 작업을 표시하여 해당 작업에서 둘 이상의 사용자 지정 오류를 반환하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-136">An operation can specify that it returns more than one custom fault by marking that operation with more than one <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span>  
  
 <span data-ttu-id="45c81-137">작업 구현에서 오류 계약을 구현 하는 다음 단계는 [오류 송수신](sending-and-receiving-faults.md)항목에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-137">The next step, to implement the fault contract in your operation implementation, is described in the topic [Sending and Receiving Faults](sending-and-receiving-faults.md).</span></span>  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a><span data-ttu-id="45c81-138">SOAP, WSDL 및 상호 운용성 고려 사항</span><span class="sxs-lookup"><span data-stu-id="45c81-138">SOAP, WSDL, and Interoperability Considerations</span></span>  

 <span data-ttu-id="45c81-139">경우에 따라, 특히 다른 플랫폼과 상호 운용하는 경우 오류가 SOAP 메시지에 나타나는 방식이나 WSDL 메타데이터에 설명되는 방식의 제어가 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-139">In some circumstances, especially when interoperating with other platforms, it may be important to control the way a fault appears in a SOAP message or the way it is described in the WSDL metadata.</span></span>  
  
 <span data-ttu-id="45c81-140"><xref:System.ServiceModel.FaultContractAttribute> 특성에는 해당 오류의 메타데이터에 생성되는 WSDL 오류 요소 이름을 제어할 수 있는 <xref:System.ServiceModel.FaultContractAttribute.Name%2A> 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-140">The <xref:System.ServiceModel.FaultContractAttribute> attribute has a <xref:System.ServiceModel.FaultContractAttribute.Name%2A> property that allows control of the WSDL fault element name that is generated in the metadata for that fault.</span></span>  
  
 <span data-ttu-id="45c81-141">SOAP 표준에 따라 오류에는 `Action`, `Code` 및 `Reason`이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-141">According to the SOAP standard, a fault can have an `Action`, a `Code`, and a `Reason`.</span></span> <span data-ttu-id="45c81-142">`Action`은 <xref:System.ServiceModel.FaultContractAttribute.Action%2A> 속성에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-142">The `Action` is controlled by the <xref:System.ServiceModel.FaultContractAttribute.Action%2A> property.</span></span> <span data-ttu-id="45c81-143"><xref:System.ServiceModel.FaultException.Code%2A> 속성과 <xref:System.ServiceModel.FaultException.Reason%2A> 속성은 모두 제네릭 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>의 부모 클래스인 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> 클래스의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-143">The <xref:System.ServiceModel.FaultException.Code%2A> property and <xref:System.ServiceModel.FaultException.Reason%2A> property are both properties of the <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> class, which is the parent class of the generic <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45c81-144">`Code` 속성에는 <xref:System.ServiceModel.FaultCode.SubCode%2A> 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-144">The `Code` property includes a <xref:System.ServiceModel.FaultCode.SubCode%2A> member.</span></span>  
  
 <span data-ttu-id="45c81-145">오류를 생성하는 비서비스에 액세스하는 경우 특정 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-145">When accessing non-services that generate faults, certain limitations exist.</span></span> <span data-ttu-id="45c81-146">WCF는 스키마가 설명 하 고 데이터 계약과 호환 되는 세부 유형의 오류만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-146">WCF supports only faults with detail types that the schema describes and that are compatible with data contracts.</span></span> <span data-ttu-id="45c81-147">예를 들어 위에서 언급 한 것 처럼 WCF는 세부 정보 형식에서 XML 특성을 사용 하는 오류를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45c81-147">For example, as mentioned above, WCF does not support faults that use XML attributes in their detail types, or faults with more than one top-level element in the detail section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c81-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45c81-148">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="45c81-149">계약 및 서비스에서 오류 지정 및 처리</span><span class="sxs-lookup"><span data-stu-id="45c81-149">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="45c81-150">오류 보내기 및 받기</span><span class="sxs-lookup"><span data-stu-id="45c81-150">Sending and Receiving Faults</span></span>](sending-and-receiving-faults.md)
- [<span data-ttu-id="45c81-151">방법: 서비스 계약에서 오류 선언</span><span class="sxs-lookup"><span data-stu-id="45c81-151">How to: Declare Faults in Service Contracts</span></span>](how-to-declare-faults-in-service-contracts.md)
- [<span data-ttu-id="45c81-152">보호 수준 이해</span><span class="sxs-lookup"><span data-stu-id="45c81-152">Understanding Protection Level</span></span>](understanding-protection-level.md)
- [<span data-ttu-id="45c81-153">방법: ProtectionLevel 속성 설정</span><span class="sxs-lookup"><span data-stu-id="45c81-153">How to: Set the ProtectionLevel Property</span></span>](how-to-set-the-protectionlevel-property.md)
- [<span data-ttu-id="45c81-154">서비스 계약에서 데이터 전송 지정</span><span class="sxs-lookup"><span data-stu-id="45c81-154">Specifying Data Transfer in Service Contracts</span></span>](./feature-details/specifying-data-transfer-in-service-contracts.md)
