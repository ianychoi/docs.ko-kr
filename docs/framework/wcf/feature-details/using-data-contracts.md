---
title: 데이터 계약 사용
description: 각 매개 변수 또는 반환 형식에 대해 WCF 클라이언트와 서버 간에 교환 되도록 serialize 되는 데이터를 정의 하는 데이터 계약에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 97d234d094abf7666a341493f6b394c73513fa70
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289869"
---
# <a name="using-data-contracts"></a><span data-ttu-id="8846f-103">데이터 계약 사용</span><span class="sxs-lookup"><span data-stu-id="8846f-103">Using Data Contracts</span></span>

<span data-ttu-id="8846f-104">*데이터 계약* 은 서비스와 클라이언트 사이에서 교환할 데이터를 추상적으로 설명한 공식 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-104">A *data contract* is a formal agreement between a service and a client that abstractly describes the data to be exchanged.</span></span> <span data-ttu-id="8846f-105">즉, 클라이언트와 서비스가 같은 형식을 공유하지 않고 같은 데이터 계약만 공유해도 통신이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-105">That is, to communicate, the client and the service do not have to share the same types, only the same data contracts.</span></span> <span data-ttu-id="8846f-106">데이터 계약에서는 각 매개 변수 또는 반환 형식에 대해 교환을 위해 serialize(XML로 변환)해야 할 데이터를 세밀하게 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-106">A data contract precisely defines, for each parameter or return type, what data is serialized (turned into XML) to be exchanged.</span></span>  
  
## <a name="data-contract-basics"></a><span data-ttu-id="8846f-107">데이터 계약 기본 사항</span><span class="sxs-lookup"><span data-stu-id="8846f-107">Data Contract Basics</span></span>  

 <span data-ttu-id="8846f-108">WCF (Windows Communication Foundation)에서는 기본적으로 데이터 계약 Serializer 라는 serialization 엔진을 사용 하 여 데이터를 serialize 및 deserialize (XML로 변환 및 변환) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-108">Windows Communication Foundation (WCF) uses a serialization engine called the Data Contract Serializer by default to serialize and deserialize data (convert it to and from XML).</span></span> <span data-ttu-id="8846f-109">정수 및 문자열과 같은 모든 .NET Framework 기본 형식 및 및와 같은 기본 형식으로 처리 되는 특정 형식 (예: <xref:System.DateTime> 및) <xref:System.Xml.XmlElement> 은 다른 준비 없이 serialize 할 수 있으며 기본 데이터 계약이 있는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-109">All .NET Framework primitive types, such as integers and strings, as well as certain types treated as primitives, such as <xref:System.DateTime> and <xref:System.Xml.XmlElement>, can be serialized with no other preparation and are considered as having default data contracts.</span></span> <span data-ttu-id="8846f-110">많은 .NET Framework 형식에도 기존 데이터 계약이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-110">Many .NET Framework types also have existing data contracts.</span></span> <span data-ttu-id="8846f-111">모든 serialize 가능 형식의 목록은 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8846f-111">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="8846f-112">새로 만든 복합 형식을 serialize하려면 데이터 계약이 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-112">New complex types that you create must have a data contract defined for them to be serializable.</span></span> <span data-ttu-id="8846f-113">기본적으로 <xref:System.Runtime.Serialization.DataContractSerializer> 는 데이터 계약을 유추하고 모든 공개 형식을 serialize합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-113">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> infers the data contract and serializes all publicly visible types.</span></span> <span data-ttu-id="8846f-114">이 경우 형식의 모든 공개 읽기/쓰기 속성과 필드가 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-114">All public read/write properties and fields of the type are serialized.</span></span> <span data-ttu-id="8846f-115"><xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>를 사용하여 멤버의 serialization을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-115">You can opt out members from serialization by using the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>.</span></span> <span data-ttu-id="8846f-116">또한 <xref:System.Runtime.Serialization.DataContractAttribute> 및 <xref:System.Runtime.Serialization.DataMemberAttribute> 특성을 사용하여 데이터 계약을 명시적으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-116">You can also explicitly create a data contract by using <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="8846f-117">보통은 형식에 <xref:System.Runtime.Serialization.DataContractAttribute> 특성을 적용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-117">This is normally done by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="8846f-118">이 특성을 클래스, 구조 및 열거에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-118">This attribute can be applied to classes, structures, and enumerations.</span></span> <span data-ttu-id="8846f-119">그런 다음 데이터 계약 형식의 각 멤버에 <xref:System.Runtime.Serialization.DataMemberAttribute> 특성을 적용하여 *데이터 멤버* 이며 serialize되어야 한다는 것을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-119">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute must then be applied to each member of the data contract type to indicate that it is a *data member*, that is, it should be serialized.</span></span> <span data-ttu-id="8846f-120">자세한 내용은 [Serializable 형식](serializable-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8846f-120">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="8846f-121">예제</span><span class="sxs-lookup"><span data-stu-id="8846f-121">Example</span></span>  

 <span data-ttu-id="8846f-122">다음 예제에서는 <xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute> 특성이 명시적으로 적용된 서비스 계약(인터페이스)을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-122">The following example shows a service contract (an interface) to which the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes have been explicitly applied.</span></span> <span data-ttu-id="8846f-123">이 예제는 기본 형식에는 데이터 계약이 필요 없지만 복합 형식에는 필요하다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-123">The example shows that primitive types do not require a data contract, while a complex type does.</span></span>  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 <span data-ttu-id="8846f-124">다음 예제에서는 클래스 및 해당 멤버에 `MyTypes.PurchaseOrder` 및 <xref:System.Runtime.Serialization.DataContractAttribute> 특성을 적용하여 <xref:System.Runtime.Serialization.DataMemberAttribute> 형식의 데이터 계약을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-124">The following example shows how a data contract for the `MyTypes.PurchaseOrder` type is created by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a><span data-ttu-id="8846f-125">참고</span><span class="sxs-lookup"><span data-stu-id="8846f-125">Notes</span></span>  

 <span data-ttu-id="8846f-126">다음 참고 사항에서는 데이터 계약을 만들 때 고려해야 할 항목을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-126">The following notes provide items to consider when creating data contracts:</span></span>  
  
- <span data-ttu-id="8846f-127"><xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 특성은 표시되지 않은 형식으로 사용한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-127">The <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute is only honored when used with unmarked types.</span></span> <span data-ttu-id="8846f-128">여기에는 <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>또는 <xref:System.Runtime.Serialization.EnumMemberAttribute> 특성 중 하나로 표시되지 않은 형식이나 다른 방법(예: <xref:System.Xml.Serialization.IXmlSerializable>)으로 serialize할 수 있는 것으로 표시된 형식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-128">This includes types that are not marked with one of the <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, or <xref:System.Runtime.Serialization.EnumMemberAttribute> attributes, or marked as serializable by any other means (such as <xref:System.Xml.Serialization.IXmlSerializable>).</span></span>  
  
- <span data-ttu-id="8846f-129">필드 및 속성에 <xref:System.Runtime.Serialization.DataMemberAttribute> 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-129">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to fields, and properties.</span></span>  
  
- <span data-ttu-id="8846f-130">멤버 액세스 가능성 수준(internal, private, protected 또는 public)은 데이터 계약에 어떤 방식으로도 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-130">Member accessibility levels (internal, private, protected, or public) do not affect the data contract in any way.</span></span>  
  
- <span data-ttu-id="8846f-131"><xref:System.Runtime.Serialization.DataMemberAttribute> 특성은 정적 멤버에 적용하면 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-131">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is ignored if it is applied to static members.</span></span>  
  
- <span data-ttu-id="8846f-132">serialization을 수행하는 동안 속성 데이터 멤버에 대해 property-get 코드를 호출하여 serialize할 속성의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-132">During serialization, property-get code is called for property data members to get the value of the properties to be serialized.</span></span>  
  
- <span data-ttu-id="8846f-133">역직렬화를 수행하는 동안 초기화되지 않은 개체가 형식에서 생성자를 호출하지 않고 먼저 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-133">During deserialization, an uninitialized object is first created, without calling any constructors on the type.</span></span> <span data-ttu-id="8846f-134">그러면 모든 데이터 멤버가 역직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-134">Then all data members are deserialized.</span></span>  
  
- <span data-ttu-id="8846f-135">deserialization을 수행하는 동안 속성 데이터 멤버에 대해 property-set 코드를 호출하여 역직렬화할 값으로 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-135">During deserialization, property-set code is called for property data members to set the properties to the value being deserialized.</span></span>  
  
- <span data-ttu-id="8846f-136">유효한 데이터 계약에서는 모든 데이터 멤버를 serialize할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-136">For a data contract to be valid, it must be possible to serialize all of its data members.</span></span> <span data-ttu-id="8846f-137">모든 serialize 가능 형식의 목록은 [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8846f-137">For a full list of serializable types, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span>  
  
     <span data-ttu-id="8846f-138">제네릭 형식은 비제네릭 형식과 완전히 같은 방식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-138">Generic types are handled in exactly the same way as non-generic types.</span></span> <span data-ttu-id="8846f-139">제네릭 매개 변수에 대한 특수 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-139">There are no special requirements for generic parameters.</span></span> <span data-ttu-id="8846f-140">다음 형식을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-140">For example, consider the following type.</span></span>  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 <span data-ttu-id="8846f-141">제네릭 형식 매개 변수(`T`)에 사용된 형식이 serialize 가능한지 여부에 관계없이 이 형식은 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-141">This type is serializable whether the type used for the generic type parameter (`T`) is serializable or not.</span></span> <span data-ttu-id="8846f-142">모든 데이터 멤버를 serialize할 수 있어야 하기 때문에 다음 코드에 표시된 것과 같이 제네릭 형식 매개 변수도 serialize할 수 있는 경우에만 다음 형식을 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8846f-142">Because it must be possible to serialize all data members, the following type is serializable only if the generic type parameter is also serializable, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 <span data-ttu-id="8846f-143">데이터 계약을 정의하는 WCF 서비스의 전체 코드 샘플을 보려면 [Basic Data Contract](../samples/basic-data-contract.md) 샘플을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8846f-143">For a complete code sample of a WCF service that defines a data contract see the [Basic Data Contract](../samples/basic-data-contract.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8846f-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8846f-144">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="8846f-145">직렬화 가능 형식</span><span class="sxs-lookup"><span data-stu-id="8846f-145">Serializable Types</span></span>](serializable-types.md)
- [<span data-ttu-id="8846f-146">데이터 계약 이름</span><span class="sxs-lookup"><span data-stu-id="8846f-146">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="8846f-147">데이터 계약 동등성</span><span class="sxs-lookup"><span data-stu-id="8846f-147">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="8846f-148">데이터 멤버 순서</span><span class="sxs-lookup"><span data-stu-id="8846f-148">Data Member Order</span></span>](data-member-order.md)
- [<span data-ttu-id="8846f-149">데이터 계약 알려진 형식</span><span class="sxs-lookup"><span data-stu-id="8846f-149">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="8846f-150">이후 버전과 호환되는 데이터 계약</span><span class="sxs-lookup"><span data-stu-id="8846f-150">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
- [<span data-ttu-id="8846f-151">데이터 계약 버전 관리</span><span class="sxs-lookup"><span data-stu-id="8846f-151">Data Contract Versioning</span></span>](data-contract-versioning.md)
- [<span data-ttu-id="8846f-152">버전 독립적 Serialization 콜백</span><span class="sxs-lookup"><span data-stu-id="8846f-152">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="8846f-153">데이터 멤버 기본값</span><span class="sxs-lookup"><span data-stu-id="8846f-153">Data Member Default Values</span></span>](data-member-default-values.md)
- [<span data-ttu-id="8846f-154">데이터 계약 직렬 변환기에서 지원하는 형식</span><span class="sxs-lookup"><span data-stu-id="8846f-154">Types Supported by the Data Contract Serializer</span></span>](types-supported-by-the-data-contract-serializer.md)
- [<span data-ttu-id="8846f-155">방법: 클래스 또는 구조체에 대한 기본 데이터 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="8846f-155">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
