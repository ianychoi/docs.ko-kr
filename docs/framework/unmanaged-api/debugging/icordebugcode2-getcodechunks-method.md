---
description: '자세히 알아보기: ICorDebugCode2:: GetCodeChunks 메서드'
title: ICorDebugCode2::GetCodeChunks 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: 371d077466ff2390293d9d4e320d4c95a992fe54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764972"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="38aa3-103">ICorDebugCode2::GetCodeChunks 메서드</span><span class="sxs-lookup"><span data-stu-id="38aa3-103">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="38aa3-104">이 코드 개체가 구성 된 코드의 청크를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-104">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="38aa3-105">구문</span><span class="sxs-lookup"><span data-stu-id="38aa3-105">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="38aa3-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38aa3-106">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="38aa3-107">진행 `chunks` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-107">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="38aa3-108">제한이 배열에 반환 된 청크의 수 `chunks` 입니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-108">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="38aa3-109">제한이 각각 단일 코드 청크를 나타내는 "CodeChunkInfo" 구조체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-109">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="38aa3-110">의 값 `cbufSize` 이 0 이면이 매개 변수는 null 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-110">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="38aa3-111">설명</span><span class="sxs-lookup"><span data-stu-id="38aa3-111">Remarks</span></span>

<span data-ttu-id="38aa3-112">코드 청크가 겹치면 안 되며, [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md)에 의해 연결 된 순서를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-112">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="38aa3-113">.NET Framework 버전 2.0의 MSIL (Microsoft 중간 언어) 코드 개체는 단일 코드 청크로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38aa3-113">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="38aa3-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="38aa3-114">Requirements</span></span>

<span data-ttu-id="38aa3-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38aa3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="38aa3-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38aa3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="38aa3-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38aa3-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="38aa3-118">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38aa3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
