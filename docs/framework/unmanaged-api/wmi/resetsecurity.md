---
title: ResetSecurity 함수 (관리 되지 않는 API 참조)
description: ResetSecurity 함수는 현재 스레드에 가장 토큰을 할당 합니다.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 259bef74356f16221f1453dd4086e2fbb26faa83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721116"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="b44fd-103">ResetSecurity 함수</span><span class="sxs-lookup"><span data-stu-id="b44fd-103">ResetSecurity function</span></span>

<span data-ttu-id="b44fd-104">제공된 가장 토큰을 현재 스레드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b44fd-105">구문</span><span class="sxs-lookup"><span data-stu-id="b44fd-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="b44fd-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b44fd-106">Parameters</span></span>

`token`  
<span data-ttu-id="b44fd-107">진행 현재 스레드와 연결할 가장 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="b44fd-108">이 값은 `null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="b44fd-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="b44fd-109">Return value</span></span>

<span data-ttu-id="b44fd-110">함수가 성공 하면 반환 값은 `S_OK` (0)입니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="b44fd-111">함수가 실패 하면 반환 값은 0이 아닌 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="b44fd-112">확장 오류 정보를 가져오려면 [Geterrorinfo](geterrorinfo.md) 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b44fd-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="b44fd-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b44fd-113">Requirements</span></span>  

 <span data-ttu-id="b44fd-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b44fd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b44fd-115">**헤더:** WMINet_Utils idl</span><span class="sxs-lookup"><span data-stu-id="b44fd-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b44fd-116">**.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b44fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44fd-117">참조</span><span class="sxs-lookup"><span data-stu-id="b44fd-117">See also</span></span>

- [<span data-ttu-id="b44fd-118">WMI 및 성능 카운터(관리되지 않는 API 참조)</span><span class="sxs-lookup"><span data-stu-id="b44fd-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
