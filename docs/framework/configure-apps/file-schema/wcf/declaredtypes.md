---
description: 다음에 대해 자세히 알아보세요. <declaredTypes>
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: e5f60209dd556edc7cf47b01b1a58c1f17d74eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803934"
---
# \<declaredTypes>

<span data-ttu-id="86d65-102">역직렬화할 때 <xref:System.Runtime.Serialization.DataContractSerializer>에서 사용하는 알려진 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-102">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="86d65-103">데이터 계약 및 알려진 형식에 대 한 자세한 내용은 [데이터 계약 알려진 형식](../../../wcf/feature-details/data-contract-known-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d65-103">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="86d65-104">구문</span><span class="sxs-lookup"><span data-stu-id="86d65-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86d65-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="86d65-105">Attributes and Elements</span></span>  

 <span data-ttu-id="86d65-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86d65-107">특성</span><span class="sxs-lookup"><span data-stu-id="86d65-107">Attributes</span></span>  

 <span data-ttu-id="86d65-108">없음</span><span class="sxs-lookup"><span data-stu-id="86d65-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="86d65-109">자식 요소</span><span class="sxs-lookup"><span data-stu-id="86d65-109">Child Elements</span></span>  
  
|<span data-ttu-id="86d65-110">요소</span><span class="sxs-lookup"><span data-stu-id="86d65-110">Element</span></span>|<span data-ttu-id="86d65-111">설명</span><span class="sxs-lookup"><span data-stu-id="86d65-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="86d65-112">알려진 형식을 필요로 하는 형식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-112">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86d65-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="86d65-113">Parent Elements</span></span>  
  
|<span data-ttu-id="86d65-114">요소</span><span class="sxs-lookup"><span data-stu-id="86d65-114">Element</span></span>|<span data-ttu-id="86d65-115">설명</span><span class="sxs-lookup"><span data-stu-id="86d65-115">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="86d65-116"><xref:System.Runtime.Serialization.DataContractSerializer>에 대한 구성 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-116">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86d65-117">설명</span><span class="sxs-lookup"><span data-stu-id="86d65-117">Remarks</span></span>  

 <span data-ttu-id="86d65-118">알려진 형식에 대 한 자세한 내용은 [데이터 계약 알려진 형식](../../../wcf/feature-details/data-contract-known-types.md) 및을 참조 하십시오 <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="86d65-118">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d65-119">예제</span><span class="sxs-lookup"><span data-stu-id="86d65-119">Example</span></span>  

 <span data-ttu-id="86d65-120">다음 XML 코드는 요소에 추가 된 선언 된 형식 및 알려진 형식을 보여 줍니다 `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="86d65-120">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="86d65-121">예제에서는 추가되는 세 가지 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-121">The example shows three types being added.</span></span> <span data-ttu-id="86d65-122">첫 번째는 "Item"이라는 알려진 형식을 사용하는 "Orders"라는 사용자 지정 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-122">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="86d65-123">두 번째 선언된 형식은 <xref:System.Collections.Generic.List%601>을 알려진 형식으로 사용하는 `Item`입니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-123">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="86d65-124">마지막으로 세 번째 선언된 형식은 <xref:System.Collections.Generic.Dictionary%602>입니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-124">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="86d65-125"><xref:System.Collections.Generic.Dictionary%602> 클래스 형식은 두 개의 형식 매개 변수가 있는 제네릭 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-125">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="86d65-126">첫 번째는 키를 나타내고 두 번째는 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-126">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="86d65-127">다음 예제에서는 알려진 형식 목록에 두 번째 형식(값)의 <xref:System.Collections.Generic.List%601>을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-127">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="86d65-128">`index` 특성을 사용하여 알려진 형식에 사용할 형식 매개 변수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d65-128">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="86d65-129">이 경우 값 형식은 "1"로 설정된 index 특성으로 표시됩니다(컬렉션은 0부터 시작).</span><span class="sxs-lookup"><span data-stu-id="86d65-129">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="86d65-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86d65-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="86d65-131">데이터 계약 알려진 형식</span><span class="sxs-lookup"><span data-stu-id="86d65-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
