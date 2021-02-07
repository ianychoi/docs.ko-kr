---
description: '자세히 알아보기: SetAssemblyFile2 메서드'
title: SetAssemblyFile2 메서드
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 890646b718c211b476d013daf021f8889198c1ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662405"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="31fff-103">SetAssemblyFile2 메서드</span><span class="sxs-lookup"><span data-stu-id="31fff-103">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="31fff-104">새 어셈블리에 대 한 및 옵션의 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-104">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="31fff-105">바인딩되지 않은 모듈을 생성할 때이 메서드를 호출 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="31fff-105">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fff-106">구문</span><span class="sxs-lookup"><span data-stu-id="31fff-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="31fff-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="31fff-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="31fff-108">매니페스트 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-108">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="31fff-109">이 파일에 대 한 [IMetaDataEmit2 interface](../metadata/imetadataemit2-interface.md) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-109">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="31fff-110">[Assemblyflags 열거형](../metadata/assemblyflags-enumeration.md)으로 표시 되는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-110">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="31fff-111">생성 되는 어셈블리에 대 한 고유 ID를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-111">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31fff-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="31fff-112">Return Value</span></span>  

 <span data-ttu-id="31fff-113">메서드가 성공 하면 S_OK을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fff-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="31fff-114">Requirements</span></span>  

 <span data-ttu-id="31fff-115">Alink가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="31fff-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fff-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31fff-116">See also</span></span>

- [<span data-ttu-id="31fff-117">IALink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="31fff-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="31fff-118">IALink 인터페이스</span><span class="sxs-lookup"><span data-stu-id="31fff-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="31fff-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="31fff-119">ALink API</span></span>](index.md)
