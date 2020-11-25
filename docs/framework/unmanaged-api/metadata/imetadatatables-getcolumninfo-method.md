---
title: IMetaDataTables::GetColumnInfo 메서드
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 227d9ab67ab3091508232be3018ca520a6b5dcc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711054"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="9c973-102">IMetaDataTables::GetColumnInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="9c973-102">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="9c973-103">지정 된 테이블의 지정 된 열에 대 한 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c973-104">구문</span><span class="sxs-lookup"><span data-stu-id="9c973-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c973-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9c973-105">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="9c973-106">진행 원하는 테이블의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="9c973-107">진행 원하는 열의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="9c973-108">제한이 행에 있는 열의 오프셋에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="9c973-109">제한이 열의 크기 (바이트)에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="9c973-110">제한이 열에 있는 값의 형식에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9c973-111">제한이 열 이름에 대 한 포인터에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="9c973-112">설명</span><span class="sxs-lookup"><span data-stu-id="9c973-112">Remarks</span></span>

<span data-ttu-id="9c973-113">반환 된 열 유형은 값 범위 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="9c973-114">pType</span><span class="sxs-lookup"><span data-stu-id="9c973-114">pType</span></span>                    | <span data-ttu-id="9c973-115">설명</span><span class="sxs-lookup"><span data-stu-id="9c973-115">Description</span></span>   | <span data-ttu-id="9c973-116">도우미 함수</span><span class="sxs-lookup"><span data-stu-id="9c973-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="9c973-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="9c973-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="9c973-118">(0, 63)</span><span class="sxs-lookup"><span data-stu-id="9c973-118">(0..63)</span></span>   | <span data-ttu-id="9c973-119">없앨</span><span class="sxs-lookup"><span data-stu-id="9c973-119">Rid</span></span>           | <span data-ttu-id="9c973-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="9c973-120">**IsRidType**</span></span><br><span data-ttu-id="9c973-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="9c973-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="9c973-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="9c973-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="9c973-123">(64.95)</span><span class="sxs-lookup"><span data-stu-id="9c973-123">(64..95)</span></span> | <span data-ttu-id="9c973-124">코딩 된 토큰</span><span class="sxs-lookup"><span data-stu-id="9c973-124">Coded token</span></span> | <span data-ttu-id="9c973-125">**Iscoded Tokentype**</span><span class="sxs-lookup"><span data-stu-id="9c973-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="9c973-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="9c973-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="9c973-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="9c973-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="9c973-128">Int16</span><span class="sxs-lookup"><span data-stu-id="9c973-128">Int16</span></span>         | <span data-ttu-id="9c973-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="9c973-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="9c973-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="9c973-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="9c973-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="9c973-131">UInt16</span></span>        | <span data-ttu-id="9c973-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="9c973-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="9c973-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="9c973-133">`iLONG` (98)</span></span>             | <span data-ttu-id="9c973-134">Int32</span><span class="sxs-lookup"><span data-stu-id="9c973-134">Int32</span></span>         | <span data-ttu-id="9c973-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="9c973-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="9c973-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="9c973-136">`iULONG` (99)</span></span>            | <span data-ttu-id="9c973-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="9c973-137">UInt32</span></span>        | <span data-ttu-id="9c973-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="9c973-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="9c973-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="9c973-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="9c973-140">Byte</span><span class="sxs-lookup"><span data-stu-id="9c973-140">Byte</span></span>          | <span data-ttu-id="9c973-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="9c973-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="9c973-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="9c973-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="9c973-143">String</span><span class="sxs-lookup"><span data-stu-id="9c973-143">String</span></span>        | <span data-ttu-id="9c973-144">**I박 Aptype**</span><span class="sxs-lookup"><span data-stu-id="9c973-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="9c973-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="9c973-145">`iGUID` (102)</span></span>            | <span data-ttu-id="9c973-146">GUID</span><span class="sxs-lookup"><span data-stu-id="9c973-146">Guid</span></span>          | <span data-ttu-id="9c973-147">**I박 Aptype**</span><span class="sxs-lookup"><span data-stu-id="9c973-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="9c973-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="9c973-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="9c973-149">Blob</span><span class="sxs-lookup"><span data-stu-id="9c973-149">Blob</span></span>          | <span data-ttu-id="9c973-150">**I박 Aptype**</span><span class="sxs-lookup"><span data-stu-id="9c973-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="9c973-151">다음을 사용 하 여 *힙에* 저장 된 값 (즉, `IsHeapType == true` )을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="9c973-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="9c973-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="9c973-153">`iGUID`: **IMetadataTables**</span><span class="sxs-lookup"><span data-stu-id="9c973-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="9c973-154">`iBLOB`: **IMetadataTables**</span><span class="sxs-lookup"><span data-stu-id="9c973-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c973-155">위의 표에 정의 된 상수를 사용 하려면 `#define _DEFINE_META_DATA_META_CONSTANTS` *cor* 헤더 파일에서 제공 하는 지시문을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c973-156">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9c973-156">Requirements</span></span>  

 <span data-ttu-id="9c973-157">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9c973-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c973-158">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="9c973-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c973-159">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c973-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c973-160">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c973-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c973-161">참조</span><span class="sxs-lookup"><span data-stu-id="9c973-161">See also</span></span>

- [<span data-ttu-id="9c973-162">IMetaDataTables 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9c973-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9c973-163">IMetaDataTables2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9c973-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
