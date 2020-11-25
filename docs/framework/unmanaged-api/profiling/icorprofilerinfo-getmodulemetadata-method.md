---
title: ICorProfilerInfo::GetModuleMetaData 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 74df0fb412e7fb3d9f779391ec84f07a0379a2cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724119"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="edd76-102">ICorProfilerInfo::GetModuleMetaData 메서드</span><span class="sxs-lookup"><span data-stu-id="edd76-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>

<span data-ttu-id="edd76-103">지정 된 모듈에 매핑되는 메타 데이터 인터페이스 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edd76-104">구문</span><span class="sxs-lookup"><span data-stu-id="edd76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edd76-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="edd76-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="edd76-106">진행 인터페이스 인스턴스가 매핑될 모듈의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="edd76-107">진행 매니페스트 파일을 여는 모드를 지정 하는 [Coropenflags](../metadata/coropenflags-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="edd76-108">`ofRead`, `ofWrite` 및 `ofNoTransform` 비트만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="edd76-109">진행 해당 인스턴스를 검색할 메타 데이터 인터페이스의 참조 ID (GUID)입니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="edd76-110">인터페이스 목록은 [메타 데이터 인터페이스](../metadata/metadata-interfaces.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="edd76-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="edd76-111">제한이 메타 데이터 인터페이스 인스턴스의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edd76-112">설명</span><span class="sxs-lookup"><span data-stu-id="edd76-112">Remarks</span></span>  

 <span data-ttu-id="edd76-113">메타 데이터를 읽기/쓰기 모드에서 열도록 요청할 수도 있지만이 경우 메타 데이터에 대 한 변경 내용이 컴파일러에서와 같이 최적화 되지 않으므로 프로그램의 메타 데이터 실행 속도가 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="edd76-114">일부 모듈 (예: 리소스 모듈)에는 메타 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="edd76-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="edd76-115">이러한 경우 `GetModuleMetaData` 는 S_FALSE HRESULT 값을 반환 하 고 \*에 null을 반환 합니다 `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="edd76-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edd76-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="edd76-116">Requirements</span></span>  

 <span data-ttu-id="edd76-117">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="edd76-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edd76-118">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="edd76-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edd76-119">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edd76-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edd76-120">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edd76-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd76-121">참조</span><span class="sxs-lookup"><span data-stu-id="edd76-121">See also</span></span>

- [<span data-ttu-id="edd76-122">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="edd76-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
