---
title: CoUninitializeEE 함수
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687849"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="2a276-102">CoUninitializeEE 함수</span><span class="sxs-lookup"><span data-stu-id="2a276-102">CoUninitializeEE Function</span></span>

<span data-ttu-id="2a276-103">`CoUninitializeEE` 는 사용 되지 않으며 기능을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a276-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a276-104">구문</span><span class="sxs-lookup"><span data-stu-id="2a276-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a276-105">설명</span><span class="sxs-lookup"><span data-stu-id="2a276-105">Remarks</span></span>  

 <span data-ttu-id="2a276-106">프로세스에서 공용 언어 런타임 실행 엔진을 언로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a276-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="2a276-107">실행 엔진을 종료 하려면 [Corexitprocess](corexitprocess-function.md)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a276-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a276-108">참조</span><span class="sxs-lookup"><span data-stu-id="2a276-108">See also</span></span>

- [<span data-ttu-id="2a276-109">CoInitializeEE 함수</span><span class="sxs-lookup"><span data-stu-id="2a276-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="2a276-110">메타데이터 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="2a276-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
