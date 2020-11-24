---
title: ICorDebugProcess::WriteMemory 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 18416954517c3cac09d013b8075bd097305a1dca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673971"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="9b2a7-102">ICorDebugProcess::WriteMemory 메서드</span><span class="sxs-lookup"><span data-stu-id="9b2a7-102">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="9b2a7-103">이 프로세스의 메모리 영역에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2a7-104">구문</span><span class="sxs-lookup"><span data-stu-id="9b2a7-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b2a7-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9b2a7-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="9b2a7-106">진행 `CORDB_ADDRESS` 데이터가 기록 되는 메모리 영역의 기준 주소인 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="9b2a7-107">데이터 전송이 발생 하기 전에 시스템에서는 기본 주소에서 시작 하 여 지정 된 크기의 메모리 영역을 쓰기 위해 액세스할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="9b2a7-108">액세스할 수 없는 경우 메서드가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="9b2a7-109">진행 메모리 영역에 쓸 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9b2a7-110">진행 쓸 데이터를 포함 하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="9b2a7-111">제한이 이 프로세스의 메모리 영역에 쓴 바이트 수를 받는 변수에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="9b2a7-112">`written`가 NULL 이면이 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b2a7-113">설명</span><span class="sxs-lookup"><span data-stu-id="9b2a7-113">Remarks</span></span>  

 <span data-ttu-id="9b2a7-114">데이터는 모든 중단점 뒤에 자동으로 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="9b2a7-115">.NET Framework 버전 2.0에서 네이티브 디버거는이 메서드를 사용 하 여 중단점을 명령 스트림에 삽입 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="9b2a7-116">대신 [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="9b2a7-117">`WriteMemory`메서드는 관리 코드 외부 에서만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="9b2a7-118">이 메서드는 부적절 하 게 사용 되는 경우 런타임을 손상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2a7-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9b2a7-119">Requirements</span></span>  

 <span data-ttu-id="9b2a7-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b2a7-121">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b2a7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b2a7-122">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b2a7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b2a7-123">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b2a7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
