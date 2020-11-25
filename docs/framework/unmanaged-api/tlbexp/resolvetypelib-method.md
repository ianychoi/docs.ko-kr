---
title: ResolveTypeLib 메서드
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: 84eea78b9c2e73e24238a5ecbc9442f3d63dbd4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719790"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="becad-102">ResolveTypeLib 메서드</span><span class="sxs-lookup"><span data-stu-id="becad-102">ResolveTypeLib Method</span></span>

<span data-ttu-id="becad-103">정규화 된 경로를 반환 하 여 형식 라이브러리의 단순 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="becad-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becad-104">구문</span><span class="sxs-lookup"><span data-stu-id="becad-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="becad-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="becad-105">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="becad-106">진행 형식 라이브러리의 단순한 이름을 포함 하는 [BSTR](/previous-versions/windows/desktop/automat/bstr) 입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-106">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="becad-107">진행 레지스트리의 형식 라이브러리에 할당 된 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="becad-108">진행 형식 라이브러리의 지역화 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="becad-109">진행 형식 라이브러리의 주 버전 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="becad-110">예를 들어 버전 *x. y* 의 경우 주 버전 번호는 *x* 입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="becad-111">진행 형식 라이브러리의 부 버전 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="becad-112">예를 들어 버전 *x. y* 의 경우 부 버전 번호는 *y* 입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="becad-113">진행 운영 환경을 식별 하는 [Syskind](/windows/win32/api/oaidl/ne-oaidl-syskind) 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-113">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="becad-114">공통 값은 SYS_WIN32 및 SYS_WIN64입니다.</span><span class="sxs-lookup"><span data-stu-id="becad-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="becad-115">제한이 매개 변수에 이름이 지정 된 형식 라이브러리의 전체 경로를 포함 하는 [BSTR](/previous-versions/windows/desktop/automat/bstr) 에 대 한 포인터입니다 `bstrSimpleName` .</span><span class="sxs-lookup"><span data-stu-id="becad-115">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="becad-116">설명</span><span class="sxs-lookup"><span data-stu-id="becad-116">Remarks</span></span>  

 <span data-ttu-id="becad-117">`ResolveTypeLib`메서드는 [Tlbexp.exe (형식 라이브러리 내보내기)](../../tools/tlbexp-exe-type-library-exporter.md) 를 처리 하는 동안 [LoadTypeLibWithResolver 함수](loadtypelibwithresolver-function.md) 에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="becad-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="becad-118">이 인터페이스의 사용자 지정 구현은 매개 변수에서 이름이 인 형식 라이브러리의 전체 경로를 포함 하는 [BSTR](/previous-versions/windows/desktop/automat/bstr) 을 반환 해야 합니다 `bstrSimpleName` .</span><span class="sxs-lookup"><span data-stu-id="becad-118">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="becad-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="becad-119">Requirements</span></span>  

 <span data-ttu-id="becad-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becad-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="becad-121">**헤더:** TlbRef, TlbRef</span><span class="sxs-lookup"><span data-stu-id="becad-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="becad-122">**라이브러리:** TlbRef</span><span class="sxs-lookup"><span data-stu-id="becad-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="becad-123">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="becad-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becad-124">참조</span><span class="sxs-lookup"><span data-stu-id="becad-124">See also</span></span>

- [<span data-ttu-id="becad-125">Tlbexp 도우미 함수</span><span class="sxs-lookup"><span data-stu-id="becad-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="becad-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="becad-126">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
