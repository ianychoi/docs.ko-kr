---
description: '자세한 정보: AddImport 메서드'
title: AddImport 메서드
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638602"
---
# <a name="addimport-method"></a><span data-ttu-id="5bf2e-103">AddImport 메서드</span><span class="sxs-lookup"><span data-stu-id="5bf2e-103">AddImport Method</span></span>

<span data-ttu-id="5bf2e-104">어셈블리에 가져오기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-104">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf2e-105">구문</span><span class="sxs-lookup"><span data-stu-id="5bf2e-105">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bf2e-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5bf2e-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5bf2e-107">확대할 어셈블리의 고유 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-107">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="5bf2e-108">가져올 파일의 [Importfile 메서드에서](importfile-method.md)검색 된 고유 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-108">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5bf2e-109">및와 같은 COM + FileDef 플래그 `ffContainsNoMetaData` `ffWriteable` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="5bf2e-110">`dwFlags`[DefineFile 메서드에](../metadata/imetadataassemblyemit-definefile-method.md)전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="5bf2e-111">결과 파일에 대 한 ID를 받는 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-111">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bf2e-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="5bf2e-112">Return Value</span></span>  

 <span data-ttu-id="5bf2e-113">메서드가 성공 하면 S_OK을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf2e-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf2e-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5bf2e-114">Requirements</span></span>  

 <span data-ttu-id="5bf2e-115">Alink 필요</span><span class="sxs-lookup"><span data-stu-id="5bf2e-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf2e-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bf2e-116">See also</span></span>

- [<span data-ttu-id="5bf2e-117">IALink 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5bf2e-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5bf2e-118">IALink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5bf2e-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5bf2e-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="5bf2e-119">ALink API</span></span>](index.md)
