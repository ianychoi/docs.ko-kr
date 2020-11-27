---
title: 메시지 계약 사용
description: 메시지 계약 특성을 사용 하 여 WFC에서 SOAP 메시지의 구조를 지정 하는 메시지 계약을 만드는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 39838ac219f095b727ad953158d54da2682a09fa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282017"
---
# <a name="using-message-contracts"></a><span data-ttu-id="35547-103">메시지 계약 사용</span><span class="sxs-lookup"><span data-stu-id="35547-103">Using Message Contracts</span></span>

<span data-ttu-id="35547-104">일반적으로 WCF (Windows Communication Foundation) 응용 프로그램을 빌드할 때 개발자는 데이터 구조 및 serialization 문제에 특히 주의를 기울여야 하며 데이터가 전달 되는 메시지의 구조를 고려 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-104">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="35547-105">이러한 애플리케이션의 경우 매개 변수 또는 반환 값에 대한 데이터 계약을 만드는 과정은 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-105">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="35547-106">자세한 내용은 [서비스 계약에서 데이터 전송 지정](specifying-data-transfer-in-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35547-106">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="35547-107">그러나 SOAP 메시지의 구조를 완벽하게 제어하는 것이 SOAP 메시지의 내용을 제어하는 것만큼이나 중요한 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-107">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="35547-108">특히 상호 운용성이 중요한 경우 또는 메시지나 메시지 부분의 수준에서 보안 문제를 특별히 제어해야 하는 경우에는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-108">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="35547-109">이러한 경우 필요한 정확한 SOAP 메시지의 구조를 지정할 수 있도록 하는 *메시지 계약* 을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-109">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="35547-110">이 항목에서는 다양한 메시지 계약 특성을 사용하여 작업에 대한 특정 메시지 계약을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-110">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="35547-111">작업에서 메시지 계약 사용</span><span class="sxs-lookup"><span data-stu-id="35547-111">Using Message Contracts in Operations</span></span>  

 <span data-ttu-id="35547-112">WCF는 *RPC (원격 프로시저 호출) 스타일* 또는 *메시징 스타일* 에서 모델링 된 작업을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-112">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="35547-113">RPC 스타일 작업에서는 serialize할 수 있는 형식을 모두 사용할 수 있으며, 여러 매개 변수, `ref` 및 `out` 매개 변수와 같은 로컬 호출에 사용 가능한 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-113">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="35547-114">이 스타일에서는 선택한 serialization 형식이 기본 메시지의 데이터 구조를 제어 하 고 WCF 런타임에서는 작업을 지원 하기 위한 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35547-114">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="35547-115">이를 통해 SOAP 및 SOAP 메시지에 익숙하지 않은 개발자도 서비스 애플리케이션을 빠르고 쉽게 만들고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-115">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="35547-116">다음 코드 예제에서는 RPC 스타일로 모델링된 서비스 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35547-116">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="35547-117">일반적으로 데이터 계약만으로도 메시지에 대한 스키마를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-117">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="35547-118">예를 들어 앞의 예제에서 `BankingTransaction` 및 `BankingTransactionResponse`가 기본 SOAP 메시지의 내용을 정의하기 위한 데이터 계약을 가지고 있는 경우, 대부분의 애플리케이션에서 스키마를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-118">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="35547-119">데이터 계약에 대 한 자세한 내용은 [데이터 계약 사용](using-data-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35547-119">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="35547-120">그러나 연결을 통해 SOAP 메시지 구조가 전송되는 방식을 정확하게 제어해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-120">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="35547-121">이를 위한 가장 일반적인 시나리오는 사용자 지정 SOAP 헤더를 삽입하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-121">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="35547-122">또 다른 일반적인 시나리오는 메시지의 헤더 및 본문에 대한 보안 속성을 정의하는 것, 즉 이러한 요소를 디지털 서명 및 암호화할지 여부를 결정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-122">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="35547-123">마지막으로, 일부 타사 SOAP 스택에서는 메시지가 특정 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-123">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="35547-124">메시징 스타일 작업에서는 이 컨트롤을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-124">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="35547-125">메시징 스타일 작업은 메시지 형식이 두 가지인 경우에 최대 하나의 매개 변수 및 하나의 반환 값만 가질 수 있습니다. 즉, 지정된 SOAP 메시지 구조로 직접 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-125">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="35547-126">이는 <xref:System.ServiceModel.MessageContractAttribute>로 표시된 형식 또는 <xref:System.ServiceModel.Channels.Message> 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-126">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="35547-127">다음 코드 예제에서는 이전 RCP 스타일과 유사하지만 메시징 스타일을 사용하는 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35547-127">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="35547-128">예를 들어 `BankingTransaction` 및 `BankingTransactionResponse`가 모두 메시지 계약을 가진 형식일 경우 다음 작업의 코드는 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-128">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="35547-129">그러나 다음 코드는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-129">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="35547-130">메시지 계약 형식이 포함되어 있지만 유효한 패턴 중 하나를 따르지 않는 모든 작업에 대해서는 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-130">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="35547-131">물론 메시지 계약 형식이 포함되지 않은 작업에는 이러한 제한이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-131">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="35547-132">한 형식이 메시지 계약과 데이터 계약을 둘 다 가진 경우에는 메시지 계약만 작업에서 해당 형식을 사용할 때 고려됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-132">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="35547-133">메시지 계약 정의</span><span class="sxs-lookup"><span data-stu-id="35547-133">Defining Message Contracts</span></span>  

 <span data-ttu-id="35547-134">형식에 대한 메시지 계약을 정의하려면, 즉 형식과 SOAP 봉투 간의 매핑을 정의하려면 해당 형식에 <xref:System.ServiceModel.MessageContractAttribute>를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-134">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="35547-135">그런 다음 <xref:System.ServiceModel.MessageHeaderAttribute>를 SOAP 헤더로 만들려는 형식의 멤버에 적용하고, <xref:System.ServiceModel.MessageBodyMemberAttribute>를 메시지의 SOAP 본문 부분으로 만들려는 멤버에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-135">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="35547-136">다음 코드에서는 메시지 계약을 사용하는 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35547-136">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="35547-137">이 형식을 작업 매개 변수로 사용할 경우 다음 SOAP 봉투가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-137">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="35547-138">`operation` 및 `transactionDate`는 SOAP 헤더로 나타나고 SOAP 본문은 `BankingTransaction`, `sourceAccount` 및 `targetAccount`가 포함된 래퍼 요소 `amount`으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-138">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="35547-139"><xref:System.ServiceModel.MessageHeaderAttribute> 및 <xref:System.ServiceModel.MessageBodyMemberAttribute>는 public, private, protected, internal 중 무엇인지 관계없이 모든 필드, 속성 및 이벤트에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-139">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="35547-140"><xref:System.ServiceModel.MessageContractAttribute>를 사용하면 SOAP 메시지 본문에서 래퍼 요소의 이름을 제어하는 WrapperName 및 WrapperNamespace 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-140">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="35547-141">기본적으로 메시지 계약 형식의 이름이 래퍼로 사용되며 메시지 계약이 정의된 네임스페이스 `http://tempuri.org/`가 기본 네임스페이스로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-141">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35547-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> 특성은 메시지 계약에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="35547-143"><xref:System.Runtime.Serialization.KnownTypeAttribute>가 필요할 경우 해당 메시지 계약을 사용 중인 작업에 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="35547-143">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="35547-144">헤더와 본문 부분의 이름 및 네임스페이스 제어</span><span class="sxs-lookup"><span data-stu-id="35547-144">Controlling Header and Body Part Names and Namespaces</span></span>  

 <span data-ttu-id="35547-145">메시지 계약의 SOAP 표현에서 각 헤더 및 본문 부분은 하나의 이름과 하나의 네임스페이스를 가진 XML 요소로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-145">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="35547-146">기본적으로 네임스페이스는 메시지가 참여 중인 서비스 계약의 네임스페이스와 동일하며, 이름은 <xref:System.ServiceModel.MessageHeaderAttribute> 또는 <xref:System.ServiceModel.MessageBodyMemberAttribute> 특성이 적용되는 멤버 이름에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-146">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="35547-147"><xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> 및 <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> 특성의 부모 클래스에서 <xref:System.ServiceModel.MessageHeaderAttribute> 및 <xref:System.ServiceModel.MessageBodyMemberAttribute>를 조작함으로써 이러한 기본값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-147">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="35547-148">다음과 같은 코드의 클래스를 예로 들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-148">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="35547-149">이 예제에서는 `IsAudited` 헤더가 코드에서 지정된 네임스페이스에 있으며, `theData` 멤버를 나타내는 본문 부분은 이름 `transactionData`와 함께 XML 요소로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-149">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="35547-150">다음 예제에서는 이 메시지 계약에 대해 생성된 XML을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35547-150">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="35547-151">SOAP 본문 부분의 래핑 여부 제어</span><span class="sxs-lookup"><span data-stu-id="35547-151">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  

 <span data-ttu-id="35547-152">기본적으로 SOAP 본문 부분은 래핑된 요소 내부에서 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-152">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="35547-153">예를 들어 다음 코드에서는 `HelloGreetingMessage` 메시지에 대한 메시지 계약에서 <xref:System.ServiceModel.MessageContractAttribute> 형식의 이름으로부터 생성된 `HelloGreetingMessage` 래퍼 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35547-153">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="35547-154">래퍼 요소를 표시하지 않으려면 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 속성을 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-154">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="35547-155">래퍼 요소의 이름 및 네임스페이스를 제어하려면 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 및 <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-155">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35547-156">래핑되지 않은 메시지에 메시지 본문 부분이 두 개 이상이면 WS-I Basic Profile 1.1과 호환되지 않으므로, 새 메시지 계약을 디자인할 때는 이러한 경우를 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-156">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="35547-157">그러나 특정 상호 운용성 시나리오에서는 래핑되지 않은 메시지 본문 부분이 두 개 이상이어야 할 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-157">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="35547-158">메시지 본문에서 두 개 이상의 데이터를 전송하려는 경우 기본(래핑된) 모드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-158">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="35547-159">래핑되지 않은 메시지에 메시지 헤더가 두 개 이상 있는 것도 전적으로 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-159">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="35547-160">메시지 계약에 사용자 지정 형식 사용</span><span class="sxs-lookup"><span data-stu-id="35547-160">Using Custom Types Inside Message Contracts</span></span>  

 <span data-ttu-id="35547-161">개별 메시지 헤더 및 메시지 본문 부분은 메시지를 사용하는 서비스 계약에 대해 선택한 serialization 엔진을 사용하여 serialize됩니다(XML로 변경됨).</span><span class="sxs-lookup"><span data-stu-id="35547-161">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="35547-162">기본 serialization 엔진인 `XmlFormatter`는 데이터 계약을 가지고 있는 모든 형식을 명시적으로(<xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>를 가짐으로써) 또는 암시적으로(<xref:System.SerializableAttribute?displayProperty=nameWithType> 등을 사용하는 기본 형식이 됨으로써) 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-162">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="35547-163">자세한 내용은 [데이터 계약 사용](using-data-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35547-163">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="35547-164">앞의 예제에서는 `Operation`이 기본 형식이고 따라서 암시적 데이터 계약을 가지므로 `BankingTransactionData` 및 `transactionDate` 형식은 데이터 계약을 가져야 하며 <xref:System.DateTime>는 serialize할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-164">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="35547-165">그러나 `XmlSerializer`라는 다른 serialization 엔진으로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-165">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="35547-166">이와 같은 전환을 수행할 경우에는 메시지 헤더 및 본문 부분에 사용하는 모든 형식이 `XmlSerializer`를 사용하여 serialize할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-166">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="35547-167">메시지 계약에 배열 사용</span><span class="sxs-lookup"><span data-stu-id="35547-167">Using Arrays Inside Message Contracts</span></span>  

 <span data-ttu-id="35547-168">메시지 계약에 반복되는 요소의 배열을 두 가지 방식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-168">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="35547-169">첫 번째 방법은 <xref:System.ServiceModel.MessageHeaderAttribute> 또는 <xref:System.ServiceModel.MessageBodyMemberAttribute>를 배열에서 직접 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-169">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="35547-170">이 경우에는 모든 배열이 여러 자식 요소와 함께 하나의 요소, 즉 하나의 헤더 또는 하나의 본문 부분으로 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-170">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="35547-171">다음과 같은 클래스를 예로 들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-171">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="35547-172">이로 인해 SOAP 헤더는 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-172">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="35547-173">이에 대한 대체 방법은 <xref:System.ServiceModel.MessageHeaderArrayAttribute>를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-173">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="35547-174">이 경우에는 각 배열 요소가 개별적으로 serialize되기 때문에 각 배열 요소가 다음과 유사한 헤더를 하나씩 가집니다.</span><span class="sxs-lookup"><span data-stu-id="35547-174">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="35547-175">배열 항목의 기본 이름은 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 특성이 적용되는 멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-175">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="35547-176"><xref:System.ServiceModel.MessageHeaderArrayAttribute> 특성은 <xref:System.ServiceModel.MessageHeaderAttribute>에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-176">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="35547-177">이 특성은 배열이 아닌 특성과 동일한 기능 집합을 가집니다. 예를 들어 단일 헤더에 대해 설정하는 것과 동일한 방식으로 헤더의 배열에 대해 순서, 이름 및 네임스페이스를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-177">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="35547-178">배열에서 `Order` 속성을 사용하면 해당 속성이 전체 배열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-178">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="35547-179">컬렉션이 아닌 배열에만 <xref:System.ServiceModel.MessageHeaderArrayAttribute>를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-179">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="35547-180">메시지 계약에 바이트 배열 사용</span><span class="sxs-lookup"><span data-stu-id="35547-180">Using Byte Arrays in Message Contracts</span></span>  

 <span data-ttu-id="35547-181">바이트 배열은 배열이 아닌 특성(<xref:System.ServiceModel.MessageBodyMemberAttribute> 및 <xref:System.ServiceModel.MessageHeaderAttribute>)과 함께 사용할 때 배열로 처리되는 것이 아니라 결과 XML에서 Base64로 인코딩된 데이터로 표시되는 특별한 기본 형식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-181">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="35547-182">바이트 배열을 배열 특성 <xref:System.ServiceModel.MessageHeaderArrayAttribute>와 함께 사용할 때 결과는 사용하는 serializer에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="35547-182">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="35547-183">기본 serializer를 사용하면 배열이 각 바이트에 대해 개별 항목으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-183">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="35547-184">그러나 `XmlSerializer`를 선택하면(서비스 계약에서 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 사용) 배열 특성을 사용하는지 또는 배열이 아닌 특성을 사용하는지에 관계없이 바이트 배열이 Base64 데이터로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-184">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="35547-185">메시지 부분의 서명 및 암호화</span><span class="sxs-lookup"><span data-stu-id="35547-185">Signing and Encrypting Parts of the Message</span></span>  

 <span data-ttu-id="35547-186">메시지 계약에서는 메시지 헤더 및/또는 메시지 본문을 디지털 서명 및 암호화해야 하는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-186">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="35547-187">이렇게 하려면 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> 및 <xref:System.ServiceModel.MessageHeaderAttribute> 특성에서 <xref:System.ServiceModel.MessageBodyMemberAttribute> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-187">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="35547-188">속성은 <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> 형식의 열거형이며, <xref:System.Net.Security.ProtectionLevel.None>(암호화 또는 서명 없음), <xref:System.Net.Security.ProtectionLevel.Sign>(디지털 서명만 수행) 또는 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>(암호화 및 디지털 서명 모두 수행)으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-188">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="35547-189">기본값은 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-189">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="35547-190">이러한 보안 기능이 작동하려면 바인딩 및 동작을 적절히 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-190">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="35547-191">이러한 보안 기능을 제대로 구성하지 않고 사용하면(예를 들어 자격 증명을 제공하지 않고 메시지를 서명하려는 경우) 유효성을 검사할 때 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-191">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="35547-192">메시지 헤더의 경우 보호 수준은 각 헤더에 대해 별도로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-192">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="35547-193">메시지 본문 부분의 경우 보호 수준을 "최소 보호 수준"으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-193">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="35547-194">본문 부분의 수에 관계없이 본문에는 보호 수준이 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-194">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="35547-195">본문의 보호 수준은 모든 본문 부분 중 가장 높은 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> 속성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-195">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="35547-196">그러나 각 본문 부분의 보호 수준을 실제로 필요한 최소 보호 수준으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-196">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="35547-197">다음과 같은 코드의 클래스를 예로 들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-197">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="35547-198">이 예제에서는 `recordID` 헤더가 보호되지 않고, `patientName`이 `signed`이고, `SSN`이 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-198">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="35547-199">주석 및 진단 본문 부분에서 보호 수준을 더 낮게 지정하더라도 `medicalHistory`을 적용하는 본문 부분인 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>가 적어도 하나는 있으므로 전체 메시지 본문에 대해 암호화 및 서명이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-199">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="35547-200">SOAP 동작</span><span class="sxs-lookup"><span data-stu-id="35547-200">SOAP Action</span></span>  

 <span data-ttu-id="35547-201">SOAP 및 관련 웹 서비스 표준은 보낸 모든 SOAP 메시지에 대해 표시할 수 있는 `Action`이라는 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-201">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="35547-202">작업의 <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> 및 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> 속성이 이 속성의 값을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-202">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="35547-203">SOAP 헤더 특성</span><span class="sxs-lookup"><span data-stu-id="35547-203">SOAP Header Attributes</span></span>  

 <span data-ttu-id="35547-204">SOAP 표준은 헤더에 있을 수 있는 다음 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-204">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="35547-205">`Actor/Role`(SOAP 1.1에서는 `Actor`, SOAP 1.2에서는 `Role`)</span><span class="sxs-lookup"><span data-stu-id="35547-205">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="35547-206">`Actor` 또는 `Role` 특성은 지정된 헤더를 사용할 노드의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-206">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="35547-207">`MustUnderstand` 특성은 헤더에서 노드 처리를 인식해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-207">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="35547-208">`Relay`특성은 헤더를 다운스트림 노드로 릴레이할 지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-208">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="35547-209">WCF는 `MustUnderstand` 이 항목의 뒷부분에 나오는 "메시지 계약 버전 관리" 단원에 지정 된 대로 특성을 제외 하 고 들어오는 메시지에 대해 이러한 특성의 처리를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-209">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="35547-210">그러나 다음 설명에서와 같이 필요에 따라 이러한 특성을 읽고 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-210">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="35547-211">메시지를 보낼 때 이러한 특성은 기본적으로 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-211">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="35547-212">다음 두 가지 방법으로 이를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-212">You can change this in two ways.</span></span> <span data-ttu-id="35547-213">첫 번째 방법은 다음 코드 예제에서처럼 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, 및 <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> 속성을 변경함으로써 원하는 값으로 정적으로 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-213">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="35547-214">(`Role` 속성은 없으며, <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> 속성을 설정하면 SOAP 1.2를 사용할 경우 `Role` 특성을 내보냅니다.)</span><span class="sxs-lookup"><span data-stu-id="35547-214">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="35547-215">이러한 특성을 제어하는 두 번째 방법은 코드를 통한 동적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="35547-215">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="35547-216"><xref:System.ServiceModel.MessageHeader%601> 형식에서 원하는 헤더 형식을 래핑하고(이 형식을 제네릭이 아닌 버전과 혼동하지 않기 위해), 해당 형식을 <xref:System.ServiceModel.MessageHeaderAttribute>와 함께 사용함으로써 이를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-216">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="35547-217">그런 다음, 다음 코드 예제에서처럼 <xref:System.ServiceModel.MessageHeader%601>에서 속성을 사용하여 SOAP 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-217">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="35547-218">동적 및 정적 제어 메커니즘을 모두 사용할 경우 정적 설정이 기본값으로 사용되지만 다음 코드에서처럼 동적 메커니즘을 사용하여 나중에 재정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-218">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="35547-219">다음 코드에서처럼 동적 특성 제어로 반복되는 헤더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-219">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="35547-220">해당 형식으로 헤더에 <xref:System.ServiceModel.MessageHeader%601> 클래스를 사용하는 경우 받는 쪽에서는 이러한 SOAP 특성을 읽을 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-220">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="35547-221">받은 메시지에서 특성 설정을 검색하려면 `Actor` 형식 헤더의 `Relay`, `MustUnderstand` 또는 <xref:System.ServiceModel.MessageHeader%601> 속성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-221">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="35547-222">메시지를 받은 다음 다시 보내면 SOAP 특성 설정은 <xref:System.ServiceModel.MessageHeader%601> 형식의 헤더에 대해서 라운드트립만 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-222">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="35547-223">SOAP 본문 부분의 순서</span><span class="sxs-lookup"><span data-stu-id="35547-223">Order of SOAP Body Parts</span></span>  

 <span data-ttu-id="35547-224">본문 부분의 순서를 제어해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-224">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="35547-225">기본적으로 본문 요소의 순서는 사전순이지만 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 속성을 사용하여 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-225">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="35547-226">이 속성은 상속 시나리오에서의 동작을 제외하고는 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> 속성과 동일한 의미 체계를 가집니다. 메시지 계약에서는 파생 형식 본문 멤버 앞에 기본 형식 본문 멤버가 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-226">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="35547-227">자세한 내용은 [데이터 멤버 순서](data-member-order.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35547-227">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="35547-228">다음 예제에서 `amount`는 사전순으로 처음이기 때문에 일반적인 경우에는 처음에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-228">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="35547-229">그러나 이 경우에는 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> 속성 때문에 세 번째 위치에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="35547-229">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="35547-230">메시지 계약 버전 관리</span><span class="sxs-lookup"><span data-stu-id="35547-230">Message Contract Versioning</span></span>  

 <span data-ttu-id="35547-231">필요에 따라 메시지 계약을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-231">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="35547-232">예를 들어 사용자 애플리케이션의 새 버전은 메시지에 헤더를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-232">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="35547-233">그런 다음 새 버전에서 이전 버전으로 보낼 때 시스템에서는 추가 헤더뿐 아니라 다른 방향으로 전송할 때 누락된 헤더도 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-233">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="35547-234">헤더 버전 관리를 위해 다음 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-234">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="35547-235">WCF는 누락 된 헤더에 대 한 개체를 나타내지 않습니다. 해당 멤버는 기본값을 그대로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-235">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="35547-236">또한 WCF는 예기치 않은 추가 헤더를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-236">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="35547-237">이 규칙에 대한 한 가지 예외는 들어오는 SOAP 메시지에서 추가 헤더가 `MustUnderstand`로 설정된 `true` 특성을 가진 경우입니다. 이 경우 인식되어야 하는 헤더를 처리할 수 없으므로 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-237">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="35547-238">메시지 본문은 유사한 버전 관리 규칙을 가지며, 누락된 메시지 본문 부분과 추가 메시지 본문 부분은 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-238">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="35547-239">상속 고려 사항</span><span class="sxs-lookup"><span data-stu-id="35547-239">Inheritance Considerations</span></span>  

 <span data-ttu-id="35547-240">메시지 계약 형식은 기본 형식에도 메시지 계약이 있는 한 다른 형식으로부터 상속될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-240">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="35547-241">다른 메시지 계약 형식으로부터 상속되는 메시지 계약 형식을 사용하여 메시지를 만들거나 액세스할 때는 다음 규칙을 적용하십시오.</span><span class="sxs-lookup"><span data-stu-id="35547-241">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="35547-242">상속 계층 구조에서는 모든 메시지 헤더가 함께 수집되어 메시지에 대한 전체 헤더 집합을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-242">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="35547-243">상속 계층 구조에서는 모든 메시지 본문 부분이 함께 수집되어 전체 메시지 본문을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-243">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="35547-244">본문 부분의 순서는 상속 계층 구조에서의 위치와 상관없이 일반 순서 지정 규칙에 따라 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 속성별로 지정된 다음 사전순으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-244">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="35547-245">메시지 본문 부분이 상속 트리의 여러 수준에 표시되면 메시지 계약 상속을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-245">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="35547-246">기본 클래스 및 파생 클래스가 헤더 또는 본문 부분을 동일한 이름으로 정의하는 경우 해당 헤더 또는 본문 부분의 값을 저장하기 위해 기본-최상 클래스의 멤버가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-246">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="35547-247">다음과 같은 코드의 클래스를 예로 들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-247">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="35547-248">`PatientRecord` 클래스는 `ID`라는 하나의 헤더로 메시지를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-248">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="35547-249">기본-최상 멤버를 선택했으므로 헤더는 `personID` 멤버가 아닌 `patientID`에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-249">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="35547-250">따라서 이 경우에는 `patientID` 필드가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-250">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="35547-251">사전순이므로 메시지 본문에는 `diagnosis` 요소가 `patientName` 요소보다 먼저 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-251">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="35547-252">예제에서는 사용해서는 안 되는 패턴을 보여 줍니다. 기본 메시지 계약 및 파생 메시지 계약에는 모두 메시지 본문 부분이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-252">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="35547-253">WSDL 고려 사항</span><span class="sxs-lookup"><span data-stu-id="35547-253">WSDL Considerations</span></span>  

 <span data-ttu-id="35547-254">메시지 계약을 사용하는 서비스로부터 WSDL(웹 서비스 기술 언어) 계약을 생성할 때는 메시지 계약 기능 중 일부가 결과 WSDL에서 반영되지 않을 수 있다는 점을 기억해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-254">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="35547-255">다음 사항을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-255">Consider the following points:</span></span>  
  
- <span data-ttu-id="35547-256">WSDL은 헤더 배열의 개념을 표현할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-256">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="35547-257"><xref:System.ServiceModel.MessageHeaderArrayAttribute>를 사용하여 헤더 배열과 함께 메시지를 만들 때 결과 WSDL은 배열 대신 하나의 헤더만 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-257">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="35547-258">결과 WSDL 문서는 일부 보호 수준 정보를 반영하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-258">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="35547-259">WSDL에서 생성된 메시지 형식은 메시지 계약 형식의 클래스 이름과 동일한 이름을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="35547-259">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="35547-260">여러 작업에서 동일한 메시지 계약을 사용할 때 여러 메시지 유형이 WSDL 문서에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-260">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="35547-261">다음에 사용할 때에는 숫자 "2", "3" 등을 추가함으로써 고유한 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35547-261">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="35547-262">WSDL을 다시 가져올 때 여러 메시지 계약 형식이 만들어지며 이름을 제외하고는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-262">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="35547-263">SOAP 인코딩 고려 사항</span><span class="sxs-lookup"><span data-stu-id="35547-263">SOAP Encoding Considerations</span></span>  

 <span data-ttu-id="35547-264">WCF를 사용 하면 XML의 레거시 SOAP 인코딩 스타일을 사용할 수 있지만 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-264">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="35547-265">이 스타일을 사용할 때(서비스 계약에 적용된 `Use`에서 `Encoded` 속성을 <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>로 설정), 다음 추가 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-265">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="35547-266">메시지 헤더는 지원되지 않습니다. 이는 특성 <xref:System.ServiceModel.MessageHeaderAttribute> 및 배열 특성 <xref:System.ServiceModel.MessageHeaderArrayAttribute>가 SOAP 인코딩과 호환되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-266">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="35547-267">메시지 계약이 래핑되지 않으면, 즉 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 속성이 `false`로 설정되면 메시지 계약에는 하나의 본문 부분만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-267">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="35547-268">요청 메시지 계약에 대한 래퍼 요소의 이름은 작업 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-268">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="35547-269">이름을 일치시키려면 메시지 계약의 `WrapperName` 속성을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="35547-269">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="35547-270">응답 메시지 계약에 대한 래퍼 요소의 이름은 접미사가 'Response'인 작업의 이름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-270">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="35547-271">이름을 일치시키려면 메시지 계약의 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 속성을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="35547-271">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="35547-272">SOAP 인코딩은 개체 참조를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-272">SOAP encoding preserves object references.</span></span> <span data-ttu-id="35547-273">예를 들어, 다음과 같은 코드를 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-273">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="35547-274">SOAP 인코딩을 사용하여 메시지를 serialize한 후에 `changedFrom` 및 `changedTo`는 `p`의 자체 복사본을 포함하지 않으며, 대신 `changedBy` 요소 내의 복사본을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="35547-274">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="35547-275">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="35547-275">Performance Considerations</span></span>  

 <span data-ttu-id="35547-276">모든 메시지 헤더 및 메시지 본문 부분이 나머지에 대해 각각 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-276">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="35547-277">그러므로 각 헤더 및 본문 부분에 대해 동일한 네임스페이스를 다시 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35547-277">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="35547-278">성능을 향상시키기 위해 통신 중에 특히 메시지의 크기를 기준으로 여러 헤더와 본문 부분을 단일 헤더 또는 본문 부분으로 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-278">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="35547-279">예를 들면 다음 코드 대신</span><span class="sxs-lookup"><span data-stu-id="35547-279">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="35547-280">아래와 같은 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-280">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="35547-281">이벤트 기반 비동기 및 메시지 계약</span><span class="sxs-lookup"><span data-stu-id="35547-281">Event-based Asynchronous and Message Contracts</span></span>  

 <span data-ttu-id="35547-282">이벤트 기반 비동기 모델에 대한 디자인 지침에 따르면 둘 이상의 값이 반환될 경우 그 중 하나는 `Result` 속성으로 반환되고 나머지 값은 <xref:System.EventArgs> 개체의 속성으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-282">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="35547-283">따라서 클라이언트가 이벤트 기반 비동기 명령 옵션을 사용하여 메타데이터를 가져오고 작업이 둘 이상의 값을 반환할 경우 기본 <xref:System.EventArgs> 개체는 그 중 하나를 `Result` 속성으로 반환하고, 나머지 값은 <xref:System.EventArgs> 개체의 속성이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-283">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="35547-284">메시지 개체를 `Result` 속성으로 수신하고 반환된 값을 해당 개체의 속성으로 포함하려면 `/messageContract` 명령 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35547-284">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="35547-285">이렇게 하면 응답 메시지를 `Result` 개체의 <xref:System.EventArgs> 속성으로 반환하는 서명이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-285">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="35547-286">모든 내부 반환 값은 응답 메시지 개체의 속성이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35547-286">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35547-287">참조</span><span class="sxs-lookup"><span data-stu-id="35547-287">See also</span></span>

- [<span data-ttu-id="35547-288">데이터 계약 사용</span><span class="sxs-lookup"><span data-stu-id="35547-288">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="35547-289">서비스 디자인 및 구현</span><span class="sxs-lookup"><span data-stu-id="35547-289">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
