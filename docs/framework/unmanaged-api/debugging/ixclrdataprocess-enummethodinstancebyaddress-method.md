---
description: '자세히 알아보기: IXCLRDataProcess:: EnumMethodInstanceByAddress 메서드'
title: 'IXCLRDataProcess:: EnumMethodInstanceByAddress 메서드'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0d59956288e39be188628d10c63a52d09d17638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800697"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="9a117-103">IXCLRDataProcess:: EnumMethodInstanceByAddress 메서드</span><span class="sxs-lookup"><span data-stu-id="9a117-103">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="9a117-104">주소 오프셋에서 시작 하 여이 프로세스의 메서드 인스턴스를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a117-104">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9a117-105">구문</span><span class="sxs-lookup"><span data-stu-id="9a117-105">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="9a117-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9a117-106">Parameters</span></span>

`handle`\
<span data-ttu-id="9a117-107">진행 메서드 인스턴스를 열거 하는 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="9a117-107">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="9a117-108">제한이 열거 된 메서드 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="9a117-108">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a117-109">설명</span><span class="sxs-lookup"><span data-stu-id="9a117-109">Remarks</span></span>

<span data-ttu-id="9a117-110">제공 된 메서드는 인터페이스의 일부 `IXCLRDataProcess` 이며 가상 메서드 테이블의 29 슬롯에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a117-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a117-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9a117-111">Requirements</span></span>

<span data-ttu-id="9a117-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a117-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="9a117-113">**헤더:** None **라이브러리:** 없음 **.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9a117-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9a117-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a117-114">See also</span></span>

- [<span data-ttu-id="9a117-115">CLRDataSourceType 열거형</span><span class="sxs-lookup"><span data-stu-id="9a117-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="9a117-116">디버깅</span><span class="sxs-lookup"><span data-stu-id="9a117-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="9a117-117">IXCLRDataProcess 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9a117-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
