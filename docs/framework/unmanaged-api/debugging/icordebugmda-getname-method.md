---
title: ICorDebugMDA::GetName 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 516fcf8a97b92eac8dfff9eae34199caa97c2d2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710937"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="e6047-102">ICorDebugMDA::GetName 메서드</span><span class="sxs-lookup"><span data-stu-id="e6047-102">ICorDebugMDA::GetName Method</span></span>

<span data-ttu-id="e6047-103">[ICorDebugMDA](icordebugmda-interface.md)로 표시 된 MDA (관리 디버깅 도우미)의 이름을 포함 하는 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6047-104">구문</span><span class="sxs-lookup"><span data-stu-id="e6047-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6047-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6047-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="e6047-106">[in] `szName` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e6047-107">제한이 이름 길이에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e6047-108">제한이 이름을 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6047-109">설명</span><span class="sxs-lookup"><span data-stu-id="e6047-109">Remarks</span></span>  

 <span data-ttu-id="e6047-110">MDA 이름은 고유한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-110">MDA names are unique values.</span></span> <span data-ttu-id="e6047-111">`GetName`메서드는 XML 스트림을 가져오고 스키마에 따라 스트림에서 이름을 추출 하는 데 편리한 성능 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="e6047-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6047-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e6047-112">Requirements</span></span>  

 <span data-ttu-id="e6047-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6047-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6047-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6047-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6047-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6047-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6047-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6047-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6047-117">참조</span><span class="sxs-lookup"><span data-stu-id="e6047-117">See also</span></span>

- [<span data-ttu-id="e6047-118">ICorDebugMDA 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6047-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="e6047-119">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="e6047-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
