---
description: '자세히 알아보기: ICorDebugModule2:: ApplyChanges 메서드'
title: ICorDebugModule2::ApplyChanges 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 09cbc395c8d656d1dc27de86305432b26308c885
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660078"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="4cd32-103">ICorDebugModule2::ApplyChanges 메서드</span><span class="sxs-lookup"><span data-stu-id="4cd32-103">ICorDebugModule2::ApplyChanges Method</span></span>

<span data-ttu-id="4cd32-104">메타 데이터의 변경 내용과 MSIL (Microsoft 중간 언어) 코드의 변경 내용을 실행 중인 프로세스에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-104">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd32-105">구문</span><span class="sxs-lookup"><span data-stu-id="4cd32-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cd32-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4cd32-106">Parameters</span></span>  

 `cbMetadata`  
 <span data-ttu-id="4cd32-107">진행 델타 메타 데이터의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-107">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="4cd32-108">진행 델타 메타 데이터를 포함 하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-108">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="4cd32-109">버퍼의 주소는 [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) 메서드에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-109">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="4cd32-110">메타 데이터의 Rva (상대 가상 주소)는 MSIL 코드의 시작 부분을 기준으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-110">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="4cd32-111">진행 델타 MSIL 코드의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-111">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="4cd32-112">진행 업데이트 된 MSIL 코드를 포함 하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-112">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cd32-113">설명</span><span class="sxs-lookup"><span data-stu-id="4cd32-113">Remarks</span></span>  

 <span data-ttu-id="4cd32-114">`pbMetadata`매개 변수는 특수 한 델타 메타 데이터 형식 ( [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)에서 출력)입니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-114">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="4cd32-115">`pbMetadata` 이전 메타 데이터를 기본으로 사용 하 고 해당 기준에 적용할 개별 변경 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-115">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="4cd32-116">이와 대조적으로, `pbIL[` ] 매개 변수는 업데이트 된 메서드에 대 한 새 msil을 포함 하며 해당 메서드에 대 한 이전 msil을 완전히 대체 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-116">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="4cd32-117">델타 MSIL 및 메타 데이터를 디버거의 메모리에 만든 경우 디버거는 `ApplyChanges` 를 호출 하 여 변경 내용을 CLR (공용 언어 런타임)에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-117">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="4cd32-118">런타임에서는 메타 데이터 테이블을 업데이트 하 고, 새 MSIL을 프로세스에 배치 하 고, 새 MSIL의 JIT (just-in-time) 컴파일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-118">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="4cd32-119">변경 내용이 적용 되 면 디버거는 [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) 를 호출 하 여 다음 편집 세션을 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-119">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="4cd32-120">그러면 디버거가 프로세스를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-120">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="4cd32-121">디버거가 `ApplyChanges` 델타 메타 데이터를 포함 하는 모듈에 대해를 호출할 때마다 변경 내용을 내보내는 데 사용 되는 복사를 제외 하 고 해당 모듈의 메타 데이터 복사본 모두에 대해 동일한 델타 메타 데이터를 사용 하 여 [IMetaDataEmit:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) 를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-121">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="4cd32-122">메타 데이터의 복사본이 실제 메타 데이터와 동기화 되지 않을 경우 디버거는 항상 새 복사본을 복사 하 고 가져오는 것을 항상 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-122">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="4cd32-123">`ApplyChanges`메서드가 실패 하면 디버그 세션이 잘못 된 상태 이므로 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd32-123">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cd32-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4cd32-124">Requirements</span></span>  

 <span data-ttu-id="4cd32-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cd32-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cd32-126">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cd32-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cd32-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cd32-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cd32-128">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd32-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
