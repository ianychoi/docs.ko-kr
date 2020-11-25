---
title: CreateAssemblyNameObject 함수
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 995f1064c2f40005c4a19ef034d7edfd668b5d51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704164"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="08120-102">CreateAssemblyNameObject 함수</span><span class="sxs-lookup"><span data-stu-id="08120-102">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="08120-103">지정 된 이름을 사용 하 여 어셈블리의 고유 id를 나타내는 [IAssemblyName](iassemblyname-interface.md) 인스턴스에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="08120-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08120-104">구문</span><span class="sxs-lookup"><span data-stu-id="08120-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="08120-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="08120-105">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="08120-106">제한이 반환 된 `IAssemblyName` 입니다.</span><span class="sxs-lookup"><span data-stu-id="08120-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="08120-107">진행 새 인스턴스를 만들 어셈블리의 이름입니다 `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="08120-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="08120-108">진행 개체 생성자에 전달할 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="08120-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="08120-109">진행 향후 확장성을 위해 예약 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="08120-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="08120-110">`pvReserved` 는 null 참조 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08120-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08120-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="08120-111">Requirements</span></span>  

 <span data-ttu-id="08120-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08120-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08120-113">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="08120-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="08120-114">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08120-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08120-115">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08120-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08120-116">참조</span><span class="sxs-lookup"><span data-stu-id="08120-116">See also</span></span>

- [<span data-ttu-id="08120-117">IAssemblyName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="08120-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="08120-118">Fusion 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="08120-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
