---
title: ICorDebugILFrame2 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 3ada9e19bb1a92b3bd7e41340b99bf81b651dd37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725016"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="68589-102">ICorDebugILFrame2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="68589-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="68589-103">ICorDebugILFrame 인터페이스의 논리적 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="68589-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68589-104">메서드</span><span class="sxs-lookup"><span data-stu-id="68589-104">Methods</span></span>  
  
|<span data-ttu-id="68589-105">메서드</span><span class="sxs-lookup"><span data-stu-id="68589-105">Method</span></span>|<span data-ttu-id="68589-106">설명</span><span class="sxs-lookup"><span data-stu-id="68589-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68589-107">EnumerateTypeParameters 메서드</span><span class="sxs-lookup"><span data-stu-id="68589-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="68589-108">이 프레임의 매개 변수를 포함 하는 ICorDebugTypeEnum 개체를 가져옵니다 <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="68589-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="68589-109">RemapFunction 메서드</span><span class="sxs-lookup"><span data-stu-id="68589-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="68589-110">새 MSIL 오프셋을 지정 하 여 편집 된 함수를 다시 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="68589-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68589-111">설명</span><span class="sxs-lookup"><span data-stu-id="68589-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68589-112">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68589-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68589-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="68589-113">Requirements</span></span>  

 <span data-ttu-id="68589-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68589-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68589-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68589-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68589-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68589-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68589-117">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68589-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68589-118">참조</span><span class="sxs-lookup"><span data-stu-id="68589-118">See also</span></span>

- [<span data-ttu-id="68589-119">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="68589-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
