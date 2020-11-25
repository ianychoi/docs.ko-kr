---
title: GetHashFromAssemblyFile 함수
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: caefc9773b0d208f8b20847b664f7bc017d2c076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730996"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="92f01-102">GetHashFromAssemblyFile 함수</span><span class="sxs-lookup"><span data-stu-id="92f01-102">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="92f01-103">지정된 해시 알고리즘을 사용하여 지정된 어셈블리 파일의 해시를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="92f01-104">이 함수는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-104">This function has been deprecated.</span></span> <span data-ttu-id="92f01-105">대신 [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f01-106">구문</span><span class="sxs-lookup"><span data-stu-id="92f01-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92f01-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="92f01-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="92f01-108">진행 해시할 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="92f01-109">[in, out] 해시 알고리즘을 지정 하는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="92f01-110">기본 해시 알고리즘에 대해 0을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="92f01-111">제한이 반환 된 해시 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="92f01-112">진행 요청 된 최대 크기 `pbHash` 입니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="92f01-113">제한이 반환 된 크기 (바이트)입니다 `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="92f01-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f01-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="92f01-114">Requirements</span></span>  

 <span data-ttu-id="92f01-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92f01-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f01-116">**헤더:** StrongName</span><span class="sxs-lookup"><span data-stu-id="92f01-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="92f01-117">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92f01-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92f01-118">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f01-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f01-119">참조</span><span class="sxs-lookup"><span data-stu-id="92f01-119">See also</span></span>

- [<span data-ttu-id="92f01-120">GetHashFromAssemblyFile 메서드</span><span class="sxs-lookup"><span data-stu-id="92f01-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="92f01-121">GetHashFromAssemblyFileW 메서드</span><span class="sxs-lookup"><span data-stu-id="92f01-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="92f01-122">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="92f01-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
