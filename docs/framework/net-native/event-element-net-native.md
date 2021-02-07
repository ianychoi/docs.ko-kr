---
description: '자세히 알아보기: <Event> 요소 (.NET 네이티브)'
title: <Event> 요소 (.NET 네이티브)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 16ef4376e5953da514598bd7cdcbe0c196ee4da5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747883"
---
# <a name="event-element-net-native"></a><span data-ttu-id="04763-103">\<Event> 요소 (.NET 네이티브)</span><span class="sxs-lookup"><span data-stu-id="04763-103">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="04763-104">런타임 리플렉션 정책을 이벤트에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-104">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04763-105">구문</span><span class="sxs-lookup"><span data-stu-id="04763-105">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04763-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="04763-106">Attributes and Elements</span></span>  

 <span data-ttu-id="04763-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04763-108">특성</span><span class="sxs-lookup"><span data-stu-id="04763-108">Attributes</span></span>  
  
|<span data-ttu-id="04763-109">attribute</span><span class="sxs-lookup"><span data-stu-id="04763-109">Attribute</span></span>|<span data-ttu-id="04763-110">특성 유형</span><span class="sxs-lookup"><span data-stu-id="04763-110">Attribute type</span></span>|<span data-ttu-id="04763-111">설명</span><span class="sxs-lookup"><span data-stu-id="04763-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="04763-112">일반</span><span class="sxs-lookup"><span data-stu-id="04763-112">General</span></span>|<span data-ttu-id="04763-113">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-113">Required attribute.</span></span> <span data-ttu-id="04763-114">이벤트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-114">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="04763-115">반사</span><span class="sxs-lookup"><span data-stu-id="04763-115">Reflection</span></span>|<span data-ttu-id="04763-116">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-116">Optional attribute.</span></span> <span data-ttu-id="04763-117">이벤트에 대한 정보 쿼리 또는 이벤트 열거는 제어하지만 런타임에 동적 호출을 사용하도록 설정하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04763-117">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="04763-118">반사</span><span class="sxs-lookup"><span data-stu-id="04763-118">Reflection</span></span>|<span data-ttu-id="04763-119">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-119">Optional attribute.</span></span> <span data-ttu-id="04763-120">동적 프로그래밍을 수행할 수 있도록 이벤트에 대한 런타임 액세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-120">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="04763-121">이 정책을 사용하면 런타임에 이벤트를 동적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04763-121">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="04763-122">Name 특성</span><span class="sxs-lookup"><span data-stu-id="04763-122">Name attribute</span></span>  
  
|<span data-ttu-id="04763-123">값</span><span class="sxs-lookup"><span data-stu-id="04763-123">Value</span></span>|<span data-ttu-id="04763-124">설명</span><span class="sxs-lookup"><span data-stu-id="04763-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04763-125">*method_name*</span><span class="sxs-lookup"><span data-stu-id="04763-125">*method_name*</span></span>|<span data-ttu-id="04763-126">이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-126">The event name.</span></span> <span data-ttu-id="04763-127">이벤트의 형식은 부모 [\<Type>](type-element-net-native.md) 또는 요소로 정의 됩니다 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="04763-127">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="04763-128">기타 모든 특성</span><span class="sxs-lookup"><span data-stu-id="04763-128">All other attributes</span></span>  
  
|<span data-ttu-id="04763-129">값</span><span class="sxs-lookup"><span data-stu-id="04763-129">Value</span></span>|<span data-ttu-id="04763-130">설명</span><span class="sxs-lookup"><span data-stu-id="04763-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04763-131">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="04763-131">*policy_setting*</span></span>|<span data-ttu-id="04763-132">이벤트에 대해 이 정책 형식에 적용할 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-132">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="04763-133">가능한 값은 `Auto`, `Excluded`, `Included` 및 `Required`입니다.</span><span class="sxs-lookup"><span data-stu-id="04763-133">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="04763-134">자세한 내용은 [런타임 지시문 정책 설정](runtime-directive-policy-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04763-134">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04763-135">자식 요소</span><span class="sxs-lookup"><span data-stu-id="04763-135">Child Elements</span></span>  

 <span data-ttu-id="04763-136">없음</span><span class="sxs-lookup"><span data-stu-id="04763-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04763-137">부모 요소</span><span class="sxs-lookup"><span data-stu-id="04763-137">Parent Elements</span></span>  
  
|<span data-ttu-id="04763-138">요소</span><span class="sxs-lookup"><span data-stu-id="04763-138">Element</span></span>|<span data-ttu-id="04763-139">설명</span><span class="sxs-lookup"><span data-stu-id="04763-139">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="04763-140">형식 및 모든 해당 멤버에 리플렉션 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-140">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="04763-141">생성된 제네릭 형식 및 모든 해당 멤버에 리플렉션 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-141">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04763-142">설명</span><span class="sxs-lookup"><span data-stu-id="04763-142">Remarks</span></span>  

 <span data-ttu-id="04763-143">이벤트의 정책이 명시적으로 정의되어 있지 않으면 부모 요소의 런타임 정책을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="04763-143">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04763-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04763-144">See also</span></span>

- [<span data-ttu-id="04763-145">런타임 지시문(rd.xml) 구성 파일 참조</span><span class="sxs-lookup"><span data-stu-id="04763-145">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="04763-146">런타임 지시문 요소</span><span class="sxs-lookup"><span data-stu-id="04763-146">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="04763-147">런타임 지시문 정책 설정</span><span class="sxs-lookup"><span data-stu-id="04763-147">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
