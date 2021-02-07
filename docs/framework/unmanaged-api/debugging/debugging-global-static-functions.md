---
description: '자세한 정보: 디버깅 전역 정적 함수'
title: 디버깅 전역 정적 함수
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: efee1bfb6eb61ae2311320a4c12bf08ec0f9534b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661456"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="ceb3f-103">디버깅 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-103">Debugging Global Static Functions</span></span>

<span data-ttu-id="ceb3f-104">이 섹션에서는 디버깅 API에서 사용하는 관리되지 않는 전역 정적 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-104">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ceb3f-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ceb3f-105">In This Section</span></span>  

 [<span data-ttu-id="ceb3f-106">_EFN_GetManagedExcepStack 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-106">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="ceb3f-107">관리되는 예외 개체 주소를 제공하면 내부에 포함된 스택 추적의 문자열 버전을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-107">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="ceb3f-108">_EFN_GetManagedObjectFieldInfo 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-108">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="ceb3f-109">제공된 개체 포인터와 필드 이름을 사용하여 개체 시작부터 필드 및 필드 값까지의 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-109">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="ceb3f-110">_EFN_GetManagedObjectName 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-110">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="ceb3f-111">제공된 관리되는 개체 포인터를 사용하여 형식 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-111">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="ceb3f-112">_EFN_StackTrace 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-112">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="ceb3f-113">비관리 코드와 관리 코드 간 각 전환에 대해 하나씩, `CONTEXT` 레코드 배열 및 관리되는 스택 추적의 텍스트 표시를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-113">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="ceb3f-114">CLRDataCreateInstance 함수</span><span class="sxs-lookup"><span data-stu-id="ceb3f-114">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="ceb3f-115">지정된 대상 프로세스에 대한 지정된 인터페이스 개체를 만들려고 CLR(공용 언어 런타임) 데이터 액세스 서비스에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-115">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="ceb3f-116">PFN_CLRDataCreateInstance 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="ceb3f-116">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="ceb3f-117">지정된 대상 프로세스에 대한 지정된 인터페이스 개체를 만들려고 CLR 데이터 액세스 서비스에 의해 호출되는 함수를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="ceb3f-117">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ceb3f-118">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="ceb3f-118">Related Sections</span></span>  

 [<span data-ttu-id="ceb3f-119">디버깅 Coclass</span><span class="sxs-lookup"><span data-stu-id="ceb3f-119">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="ceb3f-120">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ceb3f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="ceb3f-121">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="ceb3f-121">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="ceb3f-122">디버깅 구조체</span><span class="sxs-lookup"><span data-stu-id="ceb3f-122">Debugging Structures</span></span>](debugging-structures.md)
