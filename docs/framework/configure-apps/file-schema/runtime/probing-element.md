---
description: '다음에 대 한 자세한 정보: <probing> 요소'
title: <probing> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: 404e53f735ce02c2a3d7911216f834d38e309789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726106"
---
# <a name="probing-element"></a><span data-ttu-id="141eb-103">\<probing> 요소</span><span class="sxs-lookup"><span data-stu-id="141eb-103">\<probing> Element</span></span>

<span data-ttu-id="141eb-104">어셈블리를 로드할 때 검색할 공용 언어 런타임에 대 한 응용 프로그램 기본 하위 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-104">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="141eb-105">구문</span><span class="sxs-lookup"><span data-stu-id="141eb-105">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="141eb-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="141eb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="141eb-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="141eb-108">특성</span><span class="sxs-lookup"><span data-stu-id="141eb-108">Attributes</span></span>  
  
|<span data-ttu-id="141eb-109">attribute</span><span class="sxs-lookup"><span data-stu-id="141eb-109">Attribute</span></span>|<span data-ttu-id="141eb-110">설명</span><span class="sxs-lookup"><span data-stu-id="141eb-110">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="141eb-111">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="141eb-112">어셈블리를 포함할 수 있는 응용 프로그램 기본 디렉터리의 하위 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-112">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="141eb-113">각 하위 디렉터리를 세미콜론으로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-113">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="141eb-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="141eb-114">Child Elements</span></span>  

<span data-ttu-id="141eb-115">없음</span><span class="sxs-lookup"><span data-stu-id="141eb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="141eb-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="141eb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="141eb-117">요소</span><span class="sxs-lookup"><span data-stu-id="141eb-117">Element</span></span>|<span data-ttu-id="141eb-118">설명</span><span class="sxs-lookup"><span data-stu-id="141eb-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="141eb-119">어셈블리 버전 리디렉션 및 어셈블리 위치에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="141eb-120">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="141eb-121">어셈블리 바인딩 및 가비지 컬렉션에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="141eb-122">예제</span><span class="sxs-lookup"><span data-stu-id="141eb-122">Example</span></span>  

 <span data-ttu-id="141eb-123">다음 예제에서는 런타임에서 어셈블리를 검색 해야 하는 응용 프로그램 기본 하위 디렉터리를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="141eb-123">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="141eb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="141eb-124">See also</span></span>

- [<span data-ttu-id="141eb-125">런타임 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="141eb-125">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="141eb-126">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="141eb-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="141eb-127">어셈블리 위치 지정</span><span class="sxs-lookup"><span data-stu-id="141eb-127">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="141eb-128">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="141eb-128">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
