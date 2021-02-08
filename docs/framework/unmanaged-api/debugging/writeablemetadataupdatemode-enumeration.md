---
description: '자세히 알아보기: WriteableMetadataUpdateMode 열거형'
title: WriteableMetadataUpdateMode 열거형
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800515"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="94c50-103">WriteableMetadataUpdateMode 열거형</span><span class="sxs-lookup"><span data-stu-id="94c50-103">WriteableMetadataUpdateMode Enumeration</span></span>

<span data-ttu-id="94c50-104">[.NET Framework 4.5.2 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="94c50-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="94c50-105">메타데이터에 대한 메모리 내 업데이트가 디버거에 표시되는지 여부를 지정하는 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-105">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c50-106">구문</span><span class="sxs-lookup"><span data-stu-id="94c50-106">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="94c50-107">구성원</span><span class="sxs-lookup"><span data-stu-id="94c50-107">Members</span></span>  
  
|<span data-ttu-id="94c50-108">멤버 이름</span><span class="sxs-lookup"><span data-stu-id="94c50-108">Member name</span></span>|<span data-ttu-id="94c50-109">설명</span><span class="sxs-lookup"><span data-stu-id="94c50-109">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="94c50-110">메타데이터에 대한 메모리 내 업데이트를 표시할 때 .NET Framework 이전 버전과의 호환성을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-110">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="94c50-111">자세한 내용은 설명 부분을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94c50-111">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="94c50-112">메타데이터에 대한 메모리 내 업데이트를 디버거에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-112">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94c50-113">설명</span><span class="sxs-lookup"><span data-stu-id="94c50-113">Remarks</span></span>  

 <span data-ttu-id="94c50-114">열거형의 멤버를 `WriteableMetadataUpdateMode` [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) 메서드에 전달 하 여 대상 프로세스에서 메타 데이터에 대 한 메모리 내 업데이트가 디버거에 표시 되는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-114">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="94c50-115">`LegacyCompatPolicy` 옵션은 .NET Framework 4.5.2 이전 버전에서와 같은 동작을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-115">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="94c50-116">이로 인해 업데이트의 메타데이터가 표시되지 않는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-116">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="94c50-117">그러나 여러 디버깅 메서드를 호출하면 디버거가 업데이트를 표시하도록 암시적으로 강제 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-117">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="94c50-118">예를 들어, 디버거가 [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) 을 전달 하는 경우 메서드의 원래 메타 데이터에 없는 변수의 인덱스는 모듈에 대 한 모든 메타 데이터가 프로세스의 현재 상태와 일치 하는 스냅숏으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-118">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="94c50-119">다시 말해서, `LegacyCompatPolicy` 옵션을 사용하는 경우에는 디버거가 관리되지 않는 디버깅 API의 다른 부분을 사용하는 방식에 따라 사용 가능한 메타데이터 업데이트가 표시되지 않을 수도 있고 일부 또는 모든 업데이트가 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94c50-119">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c50-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="94c50-120">Requirements</span></span>  

 <span data-ttu-id="94c50-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94c50-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c50-122">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94c50-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94c50-123">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94c50-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94c50-124">**.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c50-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c50-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94c50-125">See also</span></span>

- [<span data-ttu-id="94c50-126">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="94c50-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="94c50-127">SetWriteableMetadataUpdateMode 메서드</span><span class="sxs-lookup"><span data-stu-id="94c50-127">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
