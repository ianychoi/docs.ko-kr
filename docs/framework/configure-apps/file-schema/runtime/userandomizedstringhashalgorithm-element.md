---
description: '다음에 대 한 자세한 정보: <UseRandomizedStringHashAlgorithm> 요소'
title: <UseRandomizedStringHashAlgorithm> 요소
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: bb651fc9c9f6f3df448ed5ce19e81c1ae092838c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639980"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="29cba-103">\<UseRandomizedStringHashAlgorithm> 요소</span><span class="sxs-lookup"><span data-stu-id="29cba-103">\<UseRandomizedStringHashAlgorithm> Element</span></span>

<span data-ttu-id="29cba-104">공용 언어 런타임이 응용 프로그램 도메인 별로 문자열의 해시 코드를 계산할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-104">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="29cba-105">구문</span><span class="sxs-lookup"><span data-stu-id="29cba-105">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29cba-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="29cba-106">Attributes and Elements</span></span>  

 <span data-ttu-id="29cba-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29cba-108">특성</span><span class="sxs-lookup"><span data-stu-id="29cba-108">Attributes</span></span>  
  
|<span data-ttu-id="29cba-109">attribute</span><span class="sxs-lookup"><span data-stu-id="29cba-109">Attribute</span></span>|<span data-ttu-id="29cba-110">설명</span><span class="sxs-lookup"><span data-stu-id="29cba-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="29cba-111">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="29cba-112">응용 프로그램 도메인 별로 문자열의 해시 코드를 계산할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-112">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="29cba-113">enabled 특성</span><span class="sxs-lookup"><span data-stu-id="29cba-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="29cba-114">값</span><span class="sxs-lookup"><span data-stu-id="29cba-114">Value</span></span>|<span data-ttu-id="29cba-115">설명</span><span class="sxs-lookup"><span data-stu-id="29cba-115">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="29cba-116">공용 언어 런타임은 응용 프로그램 도메인 별로 문자열의 해시 코드를 계산 하지 않습니다. 단일 알고리즘은 문자열 해시 코드를 계산 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-116">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="29cba-117">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-117">This is the default.</span></span>|  
|`1`|<span data-ttu-id="29cba-118">공용 언어 런타임은 응용 프로그램 도메인 별로 문자열의 해시 코드를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-118">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="29cba-119">서로 다른 응용 프로그램 도메인의 동일한 문자열과 다른 프로세스의 해시 코드는 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-119">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29cba-120">자식 요소</span><span class="sxs-lookup"><span data-stu-id="29cba-120">Child Elements</span></span>  

 <span data-ttu-id="29cba-121">없음</span><span class="sxs-lookup"><span data-stu-id="29cba-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29cba-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="29cba-122">Parent Elements</span></span>  
  
|<span data-ttu-id="29cba-123">요소</span><span class="sxs-lookup"><span data-stu-id="29cba-123">Element</span></span>|<span data-ttu-id="29cba-124">설명</span><span class="sxs-lookup"><span data-stu-id="29cba-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29cba-125">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="29cba-126">런타임 초기화 옵션에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29cba-127">설명</span><span class="sxs-lookup"><span data-stu-id="29cba-127">Remarks</span></span>  

 <span data-ttu-id="29cba-128">기본적으로 <xref:System.StringComparer> 클래스와 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 메서드는 응용 프로그램 도메인 간에 일관 된 해시 코드를 생성 하는 단일 해싱 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-128">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="29cba-129">이는 요소의 특성을로 설정 하는 것과 같습니다 `enabled` `<UseRandomizedStringHashAlgorithm>` `0` .</span><span class="sxs-lookup"><span data-stu-id="29cba-129">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="29cba-130">.NET Framework 4에서 사용 되는 해시 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-130">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="29cba-131"><xref:System.StringComparer>클래스와 메서드는 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 응용 프로그램 도메인 별로 해시 코드를 계산 하는 다른 해싱 알고리즘을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-131">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="29cba-132">따라서 동일한 문자열의 해시 코드는 응용 프로그램 도메인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-132">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="29cba-133">이 기능은 옵트인 (opt in) 기능입니다. 이를 활용 하려면 요소의 특성을로 설정 해야 합니다 `enabled` `<UseRandomizedStringHashAlgorithm>` `1` .</span><span class="sxs-lookup"><span data-stu-id="29cba-133">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="29cba-134">해시 테이블의 문자열 조회는 일반적으로 O (1) 연산입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-134">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="29cba-135">그러나 많은 수의 충돌이 발생 하면 조회는 O (n<sup>2</sup>) 작업이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-135">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="29cba-136">구성 요소를 사용 하 여 `<UseRandomizedStringHashAlgorithm>` 응용 프로그램 도메인당 임의의 해싱 알고리즘을 생성할 수 있습니다 .이는 특히 해시 코드를 계산 하는 키가 사용자의 데이터 입력을 기반으로 하는 경우 잠재적 충돌 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-136">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29cba-137">예제</span><span class="sxs-lookup"><span data-stu-id="29cba-137">Example</span></span>  

 <span data-ttu-id="29cba-138">다음 예제에서는 `DisplayString` 전용 문자열 상수를 포함 하는 클래스를 정의 합니다 `s` . 해당 값은 "This is the string"입니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-138">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="29cba-139">메서드를 실행하는 애플리케이션 도메인의 이름과 함께 문자열 값 및 해시 코드를 표시하는 `ShowStringHashCode` 메서드도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-139">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="29cba-140">구성 파일을 지정하지 않고 이 예제를 실행할 경우 다음과 유사한 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-140">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="29cba-141">문자열의 해시 코드는 두 애플리케이션 도메인에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-141">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="29cba-142">하지만 샘플 디렉터리에 다음의 구성을 추가하고 샘플을 실행하는 경우 동일 문자열의 해시 코드는 애플리케이션 도메인에 의해 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-142">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="29cba-143">구성 파일이 있는 경우 예제는 다음과 같은 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="29cba-143">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="29cba-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="29cba-144">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
