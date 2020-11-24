---
title: ISymUnmanagedWriter::UsingNamespace 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: 6404252f2c1eb14f0cd723451beb82b4c65960fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683487"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="acf2d-102">ISymUnmanagedWriter::UsingNamespace 메서드</span><span class="sxs-lookup"><span data-stu-id="acf2d-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="acf2d-103">지정 된 정규화 된 네임 스페이스 이름이 현재 열려 있는 어휘 범위 내에서 사용 되 고 있음을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acf2d-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="acf2d-104">네임 스페이스는 현재 열려 있는 범위에서 상속 되는 모든 범위 내에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acf2d-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="acf2d-105">현재 범위를 닫으면 네임 스페이스 사용도 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acf2d-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf2d-106">구문</span><span class="sxs-lookup"><span data-stu-id="acf2d-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acf2d-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="acf2d-107">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="acf2d-108">진행 네임 스페이스의 정규화 된 이름에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="acf2d-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acf2d-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="acf2d-109">Return Value</span></span>  

 <span data-ttu-id="acf2d-110">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="acf2d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf2d-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="acf2d-111">Requirements</span></span>  

 <span data-ttu-id="acf2d-112">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="acf2d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf2d-113">참조</span><span class="sxs-lookup"><span data-stu-id="acf2d-113">See also</span></span>

- [<span data-ttu-id="acf2d-114">ISymUnmanagedWriter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="acf2d-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
