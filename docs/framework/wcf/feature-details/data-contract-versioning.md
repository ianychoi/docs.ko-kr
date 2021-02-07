---
description: '자세한 정보: 데이터 계약 버전 관리'
title: 데이터 계약 버전 관리
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 89b99ccad1671d33383cfce8d25b241d71788670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756606"
---
# <a name="data-contract-versioning"></a><span data-ttu-id="739f5-103">데이터 계약 버전 관리</span><span class="sxs-lookup"><span data-stu-id="739f5-103">Data Contract Versioning</span></span>

<span data-ttu-id="739f5-104">애플리케이션이 발전하면서 서비스가 사용하는 데이터 계약을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-104">As applications evolve, you may also have to change the data contracts the services use.</span></span> <span data-ttu-id="739f5-105">이 항목에서는 데이터 계약의 버전 관리 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-105">This topic explains how to version data contracts.</span></span> <span data-ttu-id="739f5-106">이 항목에서는 데이터 계약 버전 관리 메커니즘에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-106">This topic describes the data contract versioning mechanisms.</span></span> <span data-ttu-id="739f5-107">전체 개요 및 규범적 버전 관리 지침은 [모범 사례: 데이터 계약 버전 관리](../best-practices-data-contract-versioning.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-107">For a complete overview and prescriptive versioning guidance, see [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md).</span></span>  
  
## <a name="breaking-vs-nonbreaking-changes"></a><span data-ttu-id="739f5-108">주요 변경 및 주요 변경 아님</span><span class="sxs-lookup"><span data-stu-id="739f5-108">Breaking vs. Nonbreaking Changes</span></span>  

 <span data-ttu-id="739f5-109">데이터 계약에 대한 변경은 주요 변경 사항이거나 주요 변경 사항이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-109">Changes to a data contract can be breaking or nonbreaking.</span></span> <span data-ttu-id="739f5-110">데이터 계약을 주요 변경 사항이 아닌 것으로 변경할 경우 이전 버전의 계약을 사용하는 애플리케이션은 새 버전을 사용하는 애플리케이션과 통신할 수 있으며, 새 버전의 계약을 사용하는 애플리케이션은 이전 버전을 사용하는 애플리케이션과 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-110">When a data contract is changed in a nonbreaking way, an application using the older version of the contract can communicate with an application using the newer version, and an application using the newer version of the contract can communicate with an application using the older version.</span></span> <span data-ttu-id="739f5-111">반면에 주요 변경 사항은 단방향 또는 양방향으로의 통신을 금지합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-111">On the other hand, a breaking change prevents communication in one or both directions.</span></span>  
  
 <span data-ttu-id="739f5-112">전송 및 수신 방법에 영향을 주지 않는 형식으로의 모든 변경은 주요 변경 사항이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-112">Any changes to a type that do not affect how it is transmitted and received are nonbreaking.</span></span> <span data-ttu-id="739f5-113">이러한 변경은 데이터 계약을 변경하지 않고 기본 형식만 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-113">Such changes do not change the data contract, only the underlying type.</span></span> <span data-ttu-id="739f5-114">예를 들어 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>의 <xref:System.Runtime.Serialization.DataMemberAttribute> 속성을 이전 버전 이름으로 설정한 경우 주요 변경이 아닌 방법으로 필드 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-114">For example, you can change the name of a field in a nonbreaking way if you then set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to the older version name.</span></span> <span data-ttu-id="739f5-115">다음 코드에서는 버전 1의 데이터 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-115">The following code shows version 1 of a data contract.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 <span data-ttu-id="739f5-116">다음 코드에서는 주요 변경에 해당하지 않는 변경을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-116">The following code shows a nonbreaking change.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 <span data-ttu-id="739f5-117">일부 변경은 전송된 데이터를 수정할 수 있지만 주요 변경 사항이거나 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-117">Some changes do modify the transmitted data, but may or may not be breaking.</span></span> <span data-ttu-id="739f5-118">다음 변경은 항상 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-118">The following changes are always breaking:</span></span>  
  
- <span data-ttu-id="739f5-119">데이터 계약의 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 또는 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 값 변경.</span><span class="sxs-lookup"><span data-stu-id="739f5-119">Changing the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> or <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> value of a data contract.</span></span>  
  
- <span data-ttu-id="739f5-120"><xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>의 <xref:System.Runtime.Serialization.DataMemberAttribute> 속성을 사용하여 데이터 멤버 순서 변경.</span><span class="sxs-lookup"><span data-stu-id="739f5-120">Changing the order of data members by using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute>.</span></span>  
  
- <span data-ttu-id="739f5-121">데이터 멤버 이름 바꾸기.</span><span class="sxs-lookup"><span data-stu-id="739f5-121">Renaming a data member.</span></span>  
  
- <span data-ttu-id="739f5-122">데이터 멤버의 데이터 계약 변경.</span><span class="sxs-lookup"><span data-stu-id="739f5-122">Changing the data contract of a data member.</span></span> <span data-ttu-id="739f5-123">예를 들어 데이터 멤버의 형식을 정수에서 문자열로 변경하거나 "Customer"라는 이름의 데이터 계약 형식을 "Person"이라는 이름의 데이터 계약 형식으로 변경을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-123">For example, changing the type of data member from an integer to a string, or from a type with a data contract named "Customer" to a type with a data contract named "Person".</span></span>  
  
 <span data-ttu-id="739f5-124">또한 다음 변경도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-124">The following changes are also possible.</span></span>  
  
## <a name="adding-and-removing-data-members"></a><span data-ttu-id="739f5-125">데이터 멤버 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="739f5-125">Adding and Removing Data Members</span></span>  

 <span data-ttu-id="739f5-126">대부분의 경우 엄격한 스키마 유효성 검사(기존 스키마에 대한 새 인스턴스 유효성 검사)가 필요하지 않는 한 데이터 멤버 추가 또는 제거는 주요 변경 사항이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-126">In most cases, adding or removing a data member is not a breaking change, unless you require strict schema validity (new instances validating against the old schema).</span></span>  
  
 <span data-ttu-id="739f5-127">추가 필드의 형식을 누락된 필드의 형식으로 역직렬화하는 경우 추가 정보는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-127">When a type with an extra field is deserialized into a type with a missing field, the extra information is ignored.</span></span> <span data-ttu-id="739f5-128">라운드트립 용으로 저장 될 수도 있습니다. 자세한 내용은 [전방 호환 데이터 계약](forward-compatible-data-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-128">(It may also be stored for round-tripping purposes; for more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md)).</span></span>  
  
 <span data-ttu-id="739f5-129">누락된 필드의 형식을 추가 필드 형식으로 역직렬화하는 경우 추가 필드는 일반적으로 0 또는 `null`인 기본값으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-129">When a type with a missing field is deserialized into a type with an extra field, the extra field is left at its default value, usually zero or `null`.</span></span> <span data-ttu-id="739f5-130">기본값은 변경 될 수 있습니다. 자세한 내용은 [버전 허용 Serialization 콜백](version-tolerant-serialization-callbacks.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-130">(The default value may be changed; for more information, see [Version-Tolerant Serialization Callbacks](version-tolerant-serialization-callbacks.md).)</span></span>  
  
 <span data-ttu-id="739f5-131">예를 들어 클라이언트에서 `CarV1` 클래스를 사용하고 서비스에서 `CarV2` 클래스를 사용하거나, 서비스에서 `CarV1` 클래스를 사용하고 클라이언트에서 `CarV2` 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-131">For example, you can use the `CarV1` class on a client and the `CarV2` class on a service, or you can use the `CarV1` class on a service and the `CarV2` class on a client.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 <span data-ttu-id="739f5-132">버전 2 엔드포인트가 데이터를 버전 1 엔드포인트에 성공적으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-132">The version 2 endpoint can successfully send data to the version 1 endpoint.</span></span> <span data-ttu-id="739f5-133">`Car` 데이터 계약의 버전 2를 직렬화하면 다음과 유사한 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-133">Serializing version 2 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 <span data-ttu-id="739f5-134">V1에 대한 deserialization 엔진은 `HorsePower` 필드에서 일치하는 데이터 멤버를 찾지 못하고 해당 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-134">The deserialization engine on V1 does not find a matching data member for the `HorsePower` field, and discards that data.</span></span>  
  
 <span data-ttu-id="739f5-135">또한 버전 1 엔드포인트가 데이터를 버전 2 엔드포인트에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-135">Also, the version 1 endpoint can send data to the version 2 endpoint.</span></span> <span data-ttu-id="739f5-136">`Car` 데이터 계약의 버전 1을 Serialize하면 다음과 유사하게 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-136">Serializing version 1 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 <span data-ttu-id="739f5-137">버전 2 역직렬 변환기는 들어오는 XML에서 일치하는 데이터가 없기 때문에 `HorsePower` 필드에 설정된 값을 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-137">The version 2 deserializer does not know what to set the `HorsePower` field to, because there is no matching data in the incoming XML.</span></span> <span data-ttu-id="739f5-138">대신 해당 필드가 기본값 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-138">Instead, the field is set to the default value of 0.</span></span>  
  
## <a name="required-data-members"></a><span data-ttu-id="739f5-139">필수 데이터 멤버</span><span class="sxs-lookup"><span data-stu-id="739f5-139">Required Data Members</span></span>  

 <span data-ttu-id="739f5-140"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>의 <xref:System.Runtime.Serialization.DataMemberAttribute> 속성을 `true`로 설정하여 데이터 멤버를 필수 항목으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-140">A data member may be marked as being required by setting the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to `true`.</span></span> <span data-ttu-id="739f5-141">역직렬화하는 동안 필수 데이터가 누락되는 경우 데이터 멤버를 기본값으로 설정하는 대신 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-141">If required data is missing while deserializing, an exception is thrown instead of setting the data member to its default value.</span></span>  
  
 <span data-ttu-id="739f5-142">필수 데이터 멤버 추가는 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-142">Adding a required data member is a breaking change.</span></span> <span data-ttu-id="739f5-143">즉, 새 형식을 계속해서 이전 형식의 엔드포인트에 보낼 수 있지만 그 반대의 경우는 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-143">That is, the newer type can still be sent to endpoints with the older type, but not the other way around.</span></span> <span data-ttu-id="739f5-144">또한 이전 모든 버전에서 필수 항목으로 표시된 데이터 멤버 제거도 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-144">Removing a data member that was marked as required in any prior version is also a breaking change.</span></span>  
  
 <span data-ttu-id="739f5-145"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 속성 값을 `true`에서 `false`로 변경하는 것은 주요 변경 사항이 아니지만, `false`에서 `true`로의 변경은 이전 버전의 형식에 해당 데이터 멤버가 없는 경우 주요 변경 사항이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-145">Changing the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property value from `true` to `false` is not breaking, but changing it from `false` to `true` may be breaking if any prior versions of the type do not have the data member in question.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="739f5-146"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 속성을 `true`로 설정하더라도 들어오는 데이터가 null 또는 0이 될 수 있으며 이 가능성을 처리하기 위해 형식을 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-146">Although the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property is set to `true`, the incoming data may be null or zero, and a type must be prepared to handle this possibility.</span></span> <span data-ttu-id="739f5-147">잘못된 들어오는 데이터로부터 보호하기 위해 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>를 보안 메커니즘으로 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="739f5-147">Do not use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> as a security mechanism to protect against bad incoming data.</span></span>  
  
## <a name="omitted-default-values"></a><span data-ttu-id="739f5-148">생략된 기본값</span><span class="sxs-lookup"><span data-stu-id="739f5-148">Omitted Default Values</span></span>  

 <span data-ttu-id="739f5-149">`EmitDefaultValue` `false` [데이터 멤버 기본값](data-member-default-values.md)에 설명 된 대로 DataMemberAttribute 특성의 속성을로 설정 하는 것은 권장 되지 않지만 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-149">It is possible (although not recommended) to set the `EmitDefaultValue` property on the DataMemberAttribute attribute to `false`, as described in [Data Member Default Values](data-member-default-values.md).</span></span> <span data-ttu-id="739f5-150">이 설정이 `false`인 경우 데이터 멤버가 기본값(일반적으로 null 또는 0)으로 설정되면 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-150">If this setting is `false`, the data member will not be emitted if it is set to its default value (usually null or zero).</span></span> <span data-ttu-id="739f5-151">이것은 다음 두 가지 방법으로 서로 다른 버전에서 필수 데이터 멤버와 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-151">This is not compatible with required data members in different versions in two ways:</span></span>  
  
- <span data-ttu-id="739f5-152">특정 버전에서 필요한 데이터 멤버를 가진 데이터 계약은 다른 버전에서 `EmitDefaultValue`가 `false`로 설정된 데이터 멤버의 기본(null 또는 0) 데이터를 받을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-152">A data contract with a data member that is required in one version cannot receive default (null or zero) data from a different version in which the data member has `EmitDefaultValue` set to `false`.</span></span>  
  
- <span data-ttu-id="739f5-153">`EmitDefaultValue`가 `false`로 설정된 필수 데이터 멤버는 기본(null 또는 0) 값을 serialize하는 데 사용할 수 없지만 deserialization 시 이러한 값을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-153">A required data member that has `EmitDefaultValue` set to `false` cannot be used to serialize its default (null or zero) value, but can receive such a value on deserialization.</span></span> <span data-ttu-id="739f5-154">이 경우 라운드트립 문제가 발생합니다(데이터를 읽을 수 있지만 동일한 데이터를 작성할 수 없음).</span><span class="sxs-lookup"><span data-stu-id="739f5-154">This creates a round-tripping problem (data can be read in but the same data cannot then be written out).</span></span> <span data-ttu-id="739f5-155">따라서 특정 버전에서 `IsRequired`가 `true`이고 `EmitDefaultValue`가 `false`인 경우, 특정 버전의 데이터 계약이 라운드트립이 발생되지 않는 값을 생성할 수 없도록 다른 모든 버전에 대해 동일한 조합이 적용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-155">Therefore, if `IsRequired` is `true` and `EmitDefaultValue` is `false` in one version, the same combination should apply to all other versions such that no version of the data contract would be able to produce a value that does not result in a round trip.</span></span>  
  
## <a name="schema-considerations"></a><span data-ttu-id="739f5-156">스키마 고려 사항</span><span class="sxs-lookup"><span data-stu-id="739f5-156">Schema Considerations</span></span>  

 <span data-ttu-id="739f5-157">데이터 계약 형식에 대해 생성 되는 스키마에 대 한 자세한 내용은 [데이터 계약 스키마 참조](data-contract-schema-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-157">For an explanation of what schema is produced for data contract types, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span>  
  
 <span data-ttu-id="739f5-158">WCF가 데이터 계약 형식에 대해 생성 하는 스키마는 버전 관리를 위한 프로 비전을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-158">The schema WCF produces for data contract types makes no provisions for versioning.</span></span> <span data-ttu-id="739f5-159">즉, 특정 버전 형식에서 내보낸 스키마는 해당 버전에 존재하는 데이터 멤버만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-159">That is, the schema exported from a certain version of a type contains only those data members present in that version.</span></span> <span data-ttu-id="739f5-160"><xref:System.Runtime.Serialization.IExtensibleDataObject> 인터페이스를 구현하더라도 특정 형식의 스키마는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-160">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface does not change the schema for a type.</span></span>  
  
 <span data-ttu-id="739f5-161">기본적으로 데이터 멤버를 선택적 요소로 스키마에 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-161">Data members are exported to the schema as optional elements by default.</span></span> <span data-ttu-id="739f5-162">즉, `minOccurs`(XML 특성) 값이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-162">That is, the `minOccurs` (XML attribute) value is set to 0.</span></span> <span data-ttu-id="739f5-163">필수 데이터 멤버는 `minOccurs`가 1로 설정된 상태에서 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-163">Required data members are exported with `minOccurs` set to 1.</span></span>  
  
 <span data-ttu-id="739f5-164">주요 변경이 아닌 것으로 판단되는 많은 변경 사항은 스키마를 엄격하게 적용해야 하는 경우 실제 주요 변경 사항이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-164">Many of the changes considered to be nonbreaking are actually breaking if strict adherence to the schema is required.</span></span> <span data-ttu-id="739f5-165">이전 예제에서 `CarV1` 요소만 있는 `Model` 인스턴스는 `CarV2` 스키마(`Model` 및 `Horsepower`를 둘 다 포함하지만 모두 선택 사항)에 대해 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-165">In the preceding example, a `CarV1` instance with just the `Model` element would validate against the `CarV2` schema (which has both `Model` and `Horsepower`, but both are optional).</span></span> <span data-ttu-id="739f5-166">그러나 그 반대는 성립하지 않습니다. `CarV2` 인스턴스는 `CarV1` 스키마에 대한 유효성 검사에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-166">However, the reverse is not true: a `CarV2` instance would fail validation against the `CarV1` schema.</span></span>  
  
 <span data-ttu-id="739f5-167">라운드트립에서는 또한 몇 가지 추가로 고려해야 할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-167">Round-tripping also entails some additional considerations.</span></span> <span data-ttu-id="739f5-168">자세한 내용은 [전방 호환 데이터 계약](forward-compatible-data-contracts.md)의 "스키마 고려 사항" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-168">For more information, see the "Schema Considerations" section in [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
### <a name="other-permitted-changes"></a><span data-ttu-id="739f5-169">기타 허용된 변경 사항</span><span class="sxs-lookup"><span data-stu-id="739f5-169">Other Permitted Changes</span></span>  

 <span data-ttu-id="739f5-170"><xref:System.Runtime.Serialization.IExtensibleDataObject> 인터페이스 구현은 주요 변경에 해당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-170">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface is a nonbreaking change.</span></span> <span data-ttu-id="739f5-171">그러나 <xref:System.Runtime.Serialization.IExtensibleDataObject>를 구현한 버전보다 이전 형식의 버전에는 라운드트립이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-171">However, round-tripping support does not exist for versions of the type prior to the version in which <xref:System.Runtime.Serialization.IExtensibleDataObject> was implemented.</span></span> <span data-ttu-id="739f5-172">자세한 내용은 [호환 가능한 데이터 계약](forward-compatible-data-contracts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-172">For more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="739f5-173">열거형</span><span class="sxs-lookup"><span data-stu-id="739f5-173">Enumerations</span></span>  

 <span data-ttu-id="739f5-174">열거형 멤버 추가 또는 제거는 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-174">Adding or removing an enumeration member is a breaking change.</span></span> <span data-ttu-id="739f5-175">열거형 멤버 이름 변경은 `EnumMemberAttribute` 특성을 사용하여 계약 이름을 이전 버전과 동일하게 유지하지 않는 한 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-175">Changing the name of an enumeration member is breaking, unless its contract name is kept the same as in the old version by using the `EnumMemberAttribute` attribute.</span></span> <span data-ttu-id="739f5-176">자세한 내용은 [데이터 계약의 열거형 형식](enumeration-types-in-data-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-176">For more information, see [Enumeration Types in Data Contracts](enumeration-types-in-data-contracts.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="739f5-177">컬렉션</span><span class="sxs-lookup"><span data-stu-id="739f5-177">Collections</span></span>  

 <span data-ttu-id="739f5-178">대부분의 컬렉션 형식이 데이터 계약 모델에서 서로 간에 상호 변경이 가능하기 때문에 대부분의 컬렉션 변경은 주요 변경 사항이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-178">Most collection changes are nonbreaking because most collection types are interchangeable with each other in the data contract model.</span></span> <span data-ttu-id="739f5-179">그러나 사용자 지정되지 않은 컬렉션을 사용자 지정하거나 그 반대로 할 경우 주요 변경 사항이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-179">However, making a noncustomized collection customized or vice versa is a breaking change.</span></span> <span data-ttu-id="739f5-180">또한 컬렉션의 사용자 지정 설정 변경은 주요 변경 사항입니다. 즉, 데이터 계약 이름 및 네임스페이스 변경, 요소 이름, 주요 요소 이름 및 값 요소 이름 반복은 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-180">Also, changing the collection's customization settings is a breaking change; that is, changing its data contract name and namespace, repeating element name, key element name, and value element name.</span></span> <span data-ttu-id="739f5-181">컬렉션 사용자 지정에 대 한 자세한 내용은 [데이터 계약의 컬렉션 형식](collection-types-in-data-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="739f5-181">For more information about collection customization, see [Collection Types in Data Contracts](collection-types-in-data-contracts.md).</span></span>  
<span data-ttu-id="739f5-182">기본적으로 컬렉션 콘텐츠 중 데이터 계약 변경(예: 정수 목록에서 문자열 목록으로 변경)은 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="739f5-182">Naturally, changing the data contract of contents of a collection (for example, changing from a list of integers to a list of strings) is a breaking change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739f5-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="739f5-183">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [<span data-ttu-id="739f5-184">버전 독립적 Serialization 콜백</span><span class="sxs-lookup"><span data-stu-id="739f5-184">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="739f5-185">모범 사례: 데이터 계약 버전 관리</span><span class="sxs-lookup"><span data-stu-id="739f5-185">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="739f5-186">데이터 계약 사용</span><span class="sxs-lookup"><span data-stu-id="739f5-186">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="739f5-187">데이터 계약 동등성</span><span class="sxs-lookup"><span data-stu-id="739f5-187">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="739f5-188">이후 버전과 호환되는 데이터 계약</span><span class="sxs-lookup"><span data-stu-id="739f5-188">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
