---
description: '자세히 알아보기: IXCLRDataModule:: GetVersionId 메서드'
title: 'IXCLRDataModule:: GetVersionId 메서드'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b924757f43d106df555ea028270ac873f8f4558
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800762"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="82501-103">IXCLRDataModule:: GetVersionId 메서드</span><span class="sxs-lookup"><span data-stu-id="82501-103">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="82501-104">모듈의 버전 식별자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="82501-104">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="82501-105">구문</span><span class="sxs-lookup"><span data-stu-id="82501-105">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="82501-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="82501-106">Parameters</span></span>

`vid`\
<span data-ttu-id="82501-107">제한이 모듈의 버전 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="82501-107">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="82501-108">설명</span><span class="sxs-lookup"><span data-stu-id="82501-108">Remarks</span></span>

<span data-ttu-id="82501-109">제공 된 메서드는 인터페이스의 일부 `IXCLRDataModule` 이며 가상 메서드 테이블의 4 번째 슬롯에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="82501-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="82501-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="82501-110">Requirements</span></span>

<span data-ttu-id="82501-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82501-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="82501-112">**헤더:** 없음을</span><span class="sxs-lookup"><span data-stu-id="82501-112">**Header:** None</span></span>  
<span data-ttu-id="82501-113">**라이브러리:** 없음을</span><span class="sxs-lookup"><span data-stu-id="82501-113">**Library:** None</span></span>  
<span data-ttu-id="82501-114">**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82501-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="82501-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82501-115">See also</span></span>

- [<span data-ttu-id="82501-116">디버깅</span><span class="sxs-lookup"><span data-stu-id="82501-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="82501-117">IXCLRDataModule 인터페이스</span><span class="sxs-lookup"><span data-stu-id="82501-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
