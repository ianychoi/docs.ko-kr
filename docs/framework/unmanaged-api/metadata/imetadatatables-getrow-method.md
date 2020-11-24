---
title: IMetaDataTables::GetRow 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 01c4c1734aa0701f787a2b73787e9e4781901d42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672658"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="1e484-102">IMetaDataTables::GetRow 메서드</span><span class="sxs-lookup"><span data-stu-id="1e484-102">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="1e484-103">지정 된 테이블 인덱스에 있는 테이블의 지정 된 행 인덱스에 있는 행을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e484-104">구문</span><span class="sxs-lookup"><span data-stu-id="1e484-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e484-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e484-105">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="1e484-106">진행 행을 검색할 테이블의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="1e484-107">진행 가져올 행의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="1e484-108">제한이 행에 대 한 포인터에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e484-109">설명</span><span class="sxs-lookup"><span data-stu-id="1e484-109">Remarks</span></span>  

  <span data-ttu-id="1e484-110">이 메서드를 사용 하는 것은 일관 된 결과를 반환 하지 않기 때문에 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="1e484-111">GUID 테이블에 대 한 자세한 내용은 CLI (공용 언어 인프라) 설명서, 특히 "Partition II: 메타 데이터 정의 및 의미 체계"를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e484-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="1e484-112">설명서는 온라인으로 제공 됩니다. [Ecma c # 및 공용 언어 인프라 표준](../../../standard/components.md#applicable-standards) 및 [표준 ECMA-335-CLI (공용 언어 인프라)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e484-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e484-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1e484-113">Requirements</span></span>  

 <span data-ttu-id="1e484-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e484-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e484-115">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="1e484-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e484-116">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e484-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e484-117">**.NET Framework 버전**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e484-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e484-118">참조</span><span class="sxs-lookup"><span data-stu-id="1e484-118">See also</span></span>

- [<span data-ttu-id="1e484-119">IMetaDataTables 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1e484-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1e484-120">IMetaDataTables2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1e484-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
