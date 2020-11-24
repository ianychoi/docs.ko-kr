---
title: _CorExeMain2 함수
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: a3fb9d87b6433d46dad081619e0692a42219408d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673626"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="1d444-102">_CorExeMain2 함수</span><span class="sxs-lookup"><span data-stu-id="1d444-102">_CorExeMain2 Function</span></span>

<span data-ttu-id="1d444-103">지정 된 메모리 매핑된 코드에서 진입점을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="1d444-104">이 함수는 운영 체제 로더에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d444-105">구문</span><span class="sxs-lookup"><span data-stu-id="1d444-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d444-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1d444-106">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="1d444-107">진행 메모리 매핑된 코드에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="1d444-108">진행 포함할 수 있는 요소 수 `pUnmappedPE` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="1d444-109">진행 실행 가능 이미지의 이름에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="1d444-110">진행 로더 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="1d444-111">진행 명령줄 매개 변수 (있는 경우).</span><span class="sxs-lookup"><span data-stu-id="1d444-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d444-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1d444-112">Requirements</span></span>  

 <span data-ttu-id="1d444-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d444-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d444-114">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="1d444-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d444-115">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d444-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d444-116">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d444-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d444-117">참조</span><span class="sxs-lookup"><span data-stu-id="1d444-117">See also</span></span>

- [<span data-ttu-id="1d444-118">메타데이터 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="1d444-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
