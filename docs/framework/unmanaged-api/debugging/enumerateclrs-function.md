---
title: EnumerateCLRs 함수
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 8fe0df3ee08f9915ed43990b6f9686e25b183a0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676103"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="7f93f-102">EnumerateCLRs 함수</span><span class="sxs-lookup"><span data-stu-id="7f93f-102">EnumerateCLRs Function</span></span>

<span data-ttu-id="7f93f-103">프로세스의 CLR을 열거하기 위한 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f93f-104">구문</span><span class="sxs-lookup"><span data-stu-id="7f93f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f93f-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7f93f-105">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="7f93f-106">[in] 로드된 CLR이 열거되는 소스 프로세스의 프로세스 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="7f93f-107">[out] CLR 시작을 계속하는 데 사용되는 이벤트 핸들이 포함된 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="7f93f-108">배열의 각 핸들이 유효한지는 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="7f93f-109">유효하면 핸들이 `ppStringArrayOut`의 같은 인덱스에 있는 해당 런타임에 대한 계속-시작 이벤트로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="7f93f-110">[out] 프로세스에 로드된 CLR의 전체 경로를 지정하는 문자열 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="7f93f-111">[out] 크기가 같은 `ppHandleArrayOut` 및 `pdwArrayLengthOut`의 길이가 포함된 DWORD에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f93f-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="7f93f-112">Return Value</span></span>  

 <span data-ttu-id="7f93f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f93f-113">S_OK</span></span>  
 <span data-ttu-id="7f93f-114">프로세스의 CLR 수가 성공적으로 확인되었으며 해당 핸들 및 경로 배열이 제대로 채워졌습니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="7f93f-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7f93f-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="7f93f-116">`ppHandleArrayOut` 또는 `ppStringArrayOut`이 null이거나 `pdwArrayLengthOut`이 null입니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="7f93f-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7f93f-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7f93f-118">함수에서 핸들 및 경로 배열에 충분한 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="7f93f-119">E_FAIL(또는 다른 E_ 반환 코드)</span><span class="sxs-lookup"><span data-stu-id="7f93f-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7f93f-120">로드된 CLR을 열거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f93f-121">설명</span><span class="sxs-lookup"><span data-stu-id="7f93f-121">Remarks</span></span>  

 <span data-ttu-id="7f93f-122">`debuggeePID`로 식별되는 대상 프로세스의 경우 함수에서는 프로세스에 로드된 CLR의 경로 배열 `ppStringArrayOut`, 같은 인덱스에서 CLR에 대한 계속-시작 이벤트가 포함될 수 있는 이벤트 핸들 배열 `ppHandleArrayOut`, 로드된 CLR 수를 지정하는 배열 크기 `pdwArrayLengthOut`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="7f93f-123">Windows 운영 체제에서 `debuggeePID`는 OS 프로세스 식별자에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="7f93f-124">`ppHandleArrayOut` 및 `ppStringArrayOut`용 메모리는 이 함수를 통해 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="7f93f-125">할당 된 메모리를 해제 하려면 [CloseCLREnumeration 함수](closeclrenumeration-function.md)를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-125">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="7f93f-126">대상 프로세스의 CLR 개수를 반환하려면 null로 설정된 두 배열 매개 변수와 함께 이 함수를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f93f-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="7f93f-127">이 개수에서 호출자는 만들어질 버퍼 크기를 유추할 수 있습니다. `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="7f93f-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f93f-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7f93f-128">Requirements</span></span>  

 <span data-ttu-id="7f93f-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f93f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f93f-130">**헤더:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7f93f-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7f93f-131">**라이브러리:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7f93f-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7f93f-132">**.NET Framework 버전:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7f93f-132">**.NET Framework Versions:** 3.5 SP1</span></span>
