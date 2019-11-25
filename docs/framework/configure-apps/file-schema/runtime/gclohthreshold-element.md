---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451325"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="952ec-102">GCLOHThreshold element</span><span class="sxs-lookup"><span data-stu-id="952ec-102">GCLOHThreshold element</span></span>

<span data-ttu-id="952ec-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span><span class="sxs-lookup"><span data-stu-id="952ec-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="952ec-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="952ec-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="952ec-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="952ec-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="952ec-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span><span class="sxs-lookup"><span data-stu-id="952ec-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="952ec-107">구문</span><span class="sxs-lookup"><span data-stu-id="952ec-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="952ec-108">특성</span><span class="sxs-lookup"><span data-stu-id="952ec-108">Attributes</span></span>

|<span data-ttu-id="952ec-109">특성</span><span class="sxs-lookup"><span data-stu-id="952ec-109">Attribute</span></span>|<span data-ttu-id="952ec-110">설명</span><span class="sxs-lookup"><span data-stu-id="952ec-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="952ec-111">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="952ec-111">Required attribute.</span></span><br /><br /><span data-ttu-id="952ec-112">Specifies the threshold size that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="952ec-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="952ec-113">enabled attribute</span><span class="sxs-lookup"><span data-stu-id="952ec-113">enabled attribute</span></span>

|<span data-ttu-id="952ec-114">값</span><span class="sxs-lookup"><span data-stu-id="952ec-114">Value</span></span>|<span data-ttu-id="952ec-115">설명</span><span class="sxs-lookup"><span data-stu-id="952ec-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="952ec-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="952ec-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="952ec-117">자식 요소</span><span class="sxs-lookup"><span data-stu-id="952ec-117">Child elements</span></span>

<span data-ttu-id="952ec-118">없음.</span><span class="sxs-lookup"><span data-stu-id="952ec-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="952ec-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="952ec-119">Parent elements</span></span>

|<span data-ttu-id="952ec-120">요소</span><span class="sxs-lookup"><span data-stu-id="952ec-120">Element</span></span>|<span data-ttu-id="952ec-121">설명</span><span class="sxs-lookup"><span data-stu-id="952ec-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="952ec-122">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="952ec-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="952ec-123">어셈블리 바인딩 및 가비지 컬렉션에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="952ec-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="952ec-124">주의</span><span class="sxs-lookup"><span data-stu-id="952ec-124">Remarks</span></span>

<span data-ttu-id="952ec-125">This setting was introduced in .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="952ec-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="952ec-126">참조</span><span class="sxs-lookup"><span data-stu-id="952ec-126">See also</span></span>

- [<span data-ttu-id="952ec-127">Run-time settings schema</span><span class="sxs-lookup"><span data-stu-id="952ec-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="952ec-128">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="952ec-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="952ec-129">가비지 컬렉션 기본 사항</span><span class="sxs-lookup"><span data-stu-id="952ec-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="952ec-130">NET Core run-time config options for GC</span><span class="sxs-lookup"><span data-stu-id="952ec-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)