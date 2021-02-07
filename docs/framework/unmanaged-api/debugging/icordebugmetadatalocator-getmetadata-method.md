---
description: '자세히 알아보기: ICorDebugMetaDataLocator:: GetMetaData 메서드'
title: ICorDebugMetaDataLocator::GetMetaData 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 419a03e42a54057ab70e31a368e918612f3a85f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691694"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="f3cd3-103">ICorDebugMetaDataLocator::GetMetaData 메서드</span><span class="sxs-lookup"><span data-stu-id="f3cd3-103">ICorDebugMetaDataLocator::GetMetaData Method</span></span>

<span data-ttu-id="f3cd3-104">디버거가 요청한 작업을 완료하는 데 필요한 메타데이터가 포함된 모듈의 전체 경로를 반환하도록 디버거에 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-104">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3cd3-105">구문</span><span class="sxs-lookup"><span data-stu-id="f3cd3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3cd3-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f3cd3-106">Parameters</span></span>  

 `wszImagePath`  
 <span data-ttu-id="f3cd3-107">[in] 파일의 전체 경로를 나타내는 null로 종료된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-107">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="f3cd3-108">전체 경로를 사용할 수 없는 경우 파일의 이름 및 *확장명 (파일 이름)* 입니다.*확장*).</span><span class="sxs-lookup"><span data-stu-id="f3cd3-108">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="f3cd3-109">[in] 이미지 PE 파일 헤더의 타임스탬프입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-109">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="f3cd3-110">이 매개 변수는 기호 서버 ([Symsrv](/windows/desktop/debug/using-symsrv)) 조회에 사용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-110">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="f3cd3-111">[in] PE 파일 헤더의 이미지 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-111">[in] The image size from PE file headers.</span></span> <span data-ttu-id="f3cd3-112">이 매개 변수는 SymSrv 조회에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-112">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="f3cd3-113">[in] `wszPathBuffer`의 문자 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-113">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="f3cd3-114">[out] `wszPathBuffer`에 기록된 `WCHAR` 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-114">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="f3cd3-115">메서드가 E_NOT_SUFFICIENT_BUFFER를 반환할 경우 경로를 저장하는 데 필요한 `WCHAR` 개수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-115">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="f3cd3-116">[out] 디버거가 요청된 메타데이터를 포함한 파일의 전체 경로를 복사할 대상 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-116">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="f3cd3-117">`ofReadOnly` [Coropenflags](../metadata/coropenflags-enumeration.md) 열거형의 플래그는이 파일의 메타 데이터에 대 한 읽기 전용 액세스를 요청 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-117">The `ofReadOnly` flag from the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3cd3-118">Return Value</span><span class="sxs-lookup"><span data-stu-id="f3cd3-118">Return Value</span></span>  

 <span data-ttu-id="f3cd3-119">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="f3cd3-120">모든 기타 오류 HRESULT는 파일을 검색할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-120">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="f3cd3-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3cd3-121">HRESULT</span></span>|<span data-ttu-id="f3cd3-122">설명</span><span class="sxs-lookup"><span data-stu-id="f3cd3-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3cd3-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3cd3-123">S_OK</span></span>|<span data-ttu-id="f3cd3-124">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-124">The method completed successfully.</span></span> <span data-ttu-id="f3cd3-125">`wszPathBuffer`는 파일의 전체 경로를 포함하고 null로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-125">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="f3cd3-126">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f3cd3-126">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f3cd3-127">`wszPathBuffer`의 현재 크기는 전체 경로를 포함하기에 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-127">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="f3cd3-128">이 경우 `pcchPathBuffer`는 종료 null 문자를 비롯하여 필요한 `WCHAR` 개수를 포함하고, `GetMetaData`는 요청된 버퍼 크기와 함께 두 번째로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-128">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3cd3-129">설명</span><span class="sxs-lookup"><span data-stu-id="f3cd3-129">Remarks</span></span>  

 <span data-ttu-id="f3cd3-130">`wszImagePath`에 덤프부터 모듈의 전체 경로가 포함되면 이 매개 변수는 덤프가 수집된 컴퓨터의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-130">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="f3cd3-131">이 위치에 파일이 있을 수 없거나 같은 이름을 가진 잘못된 파일이 경로에 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-131">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3cd3-132">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f3cd3-132">Requirements</span></span>  

 <span data-ttu-id="f3cd3-133">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3cd3-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3cd3-134">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3cd3-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3cd3-135">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3cd3-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3cd3-136">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3cd3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cd3-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3cd3-137">See also</span></span>

- [<span data-ttu-id="f3cd3-138">ICorDebugThread4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f3cd3-138">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="f3cd3-139">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f3cd3-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f3cd3-140">디버깅</span><span class="sxs-lookup"><span data-stu-id="f3cd3-140">Debugging</span></span>](index.md)
