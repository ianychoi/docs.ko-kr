---
description: '자세히 알아보기: ICorDebugNativeFrame:: GetLocalDoubleRegisterValue 메서드'
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: a478c51ea7bf04b3fc3faf49fef39f9b29a30599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722427"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="18b08-103">ICorDebugNativeFrame::GetLocalDoubleRegisterValue 메서드</span><span class="sxs-lookup"><span data-stu-id="18b08-103">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>

<span data-ttu-id="18b08-104">이 네이티브 프레임의 지정 된 두 레지스터에 저장 된 인수 또는 지역 변수의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-104">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b08-105">구문</span><span class="sxs-lookup"><span data-stu-id="18b08-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b08-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="18b08-106">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="18b08-107">진행 값의 상위 단어가 포함 된 레지스터를 지정 하는 "CorDebugRegister" 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="18b08-108">진행 `CorDebugRegister` 값의 하위 단어를 포함 하는 레지스터를 지정 하는 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-108">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="18b08-109">진행 매개 변수에서 참조 하는 이진 메타 데이터 시그니처의 크기를 지정 하는 정수입니다 `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="18b08-109">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="18b08-110">진행 `PCCOR_SIGNATURE` 값 형식의 이진 메타 데이터 서명을 가리키는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-110">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="18b08-111">제한이 지정 된 레지스터에 저장 된 검색 된 값을 나타내는 "ICorDebugValue" 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-111">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18b08-112">설명</span><span class="sxs-lookup"><span data-stu-id="18b08-112">Remarks</span></span>  

 <span data-ttu-id="18b08-113">`GetLocalDoubleRegisterValue`메서드는 네이티브 프레임 또는 JIT (just-in-time) 컴파일된 프레임에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b08-113">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b08-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="18b08-114">Requirements</span></span>  

 <span data-ttu-id="18b08-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18b08-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b08-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18b08-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18b08-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18b08-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b08-118">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b08-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b08-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18b08-119">See also</span></span>
