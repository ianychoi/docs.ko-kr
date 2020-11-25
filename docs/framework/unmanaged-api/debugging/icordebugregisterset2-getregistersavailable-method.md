---
title: ICorDebugRegisterSet2::GetRegistersAvailable 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: cb56ea817d4045c19793a6290d68ae8b6236f14a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712322"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="0515f-102">ICorDebugRegisterSet2::GetRegistersAvailable 메서드</span><span class="sxs-lookup"><span data-stu-id="0515f-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>

<span data-ttu-id="0515f-103">사용 가능한 레지스터의 비트맵을 제공 하는 바이트 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0515f-104">구문</span><span class="sxs-lookup"><span data-stu-id="0515f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0515f-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0515f-105">Parameters</span></span>  

 `numChunks`  
 <span data-ttu-id="0515f-106">[in] `availableRegChunks` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="0515f-107">제한이 각 비트가 레지스터에 해당 하는 바이트 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="0515f-108">레지스터를 사용할 수 있는 경우 레지스터의 해당 비트가 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0515f-109">설명</span><span class="sxs-lookup"><span data-stu-id="0515f-109">Remarks</span></span>  

 <span data-ttu-id="0515f-110">CorDebugRegister 열거형의 값은 다른 마이크로프로세서의 레지스터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="0515f-111">각 값의 상위 5 비트는 `availableRegChunks` 바이트 배열에 대 한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="0515f-112">각 값의 하위 3 비트는 인덱싱된 바이트 내의 비트 위치를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="0515f-113">`CorDebugRegister`특정 레지스터를 지정 하는 값을 지정 하는 경우 마스크의 레지스터 위치는 다음과 같이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="0515f-114">배열의 올바른 바이트에 액세스 하는 데 필요한 인덱스를 추출 합니다 `availableRegChunks` .</span><span class="sxs-lookup"><span data-stu-id="0515f-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="0515f-115">`CorDebugRegister` 값 >> 3</span><span class="sxs-lookup"><span data-stu-id="0515f-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="0515f-116">인덱싱된 바이트 내에서 비트 위치를 추출 합니다. 여기서 bit 0은 최하위 비트입니다.</span><span class="sxs-lookup"><span data-stu-id="0515f-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="0515f-117">`CorDebugRegister` 값 & 7</span><span class="sxs-lookup"><span data-stu-id="0515f-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0515f-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0515f-118">Requirements</span></span>  

 <span data-ttu-id="0515f-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0515f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0515f-120">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0515f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0515f-121">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0515f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0515f-122">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0515f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0515f-123">참조</span><span class="sxs-lookup"><span data-stu-id="0515f-123">See also</span></span>

- [<span data-ttu-id="0515f-124">ICorDebugRegisterSet2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0515f-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="0515f-125">ICorDebugRegisterSet 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0515f-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
