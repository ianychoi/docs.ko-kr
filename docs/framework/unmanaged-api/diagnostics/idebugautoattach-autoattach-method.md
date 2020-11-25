---
title: IDebugAutoAttach::AutoAttach 메서드
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 64dd653bb0d4e383075a999e0803e4acfd0fae3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720102"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="5e9bd-102">IDebugAutoAttach::AutoAttach 메서드</span><span class="sxs-lookup"><span data-stu-id="5e9bd-102">IDebugAutoAttach::AutoAttach Method</span></span>

<span data-ttu-id="5e9bd-103">서버에서 호출 하는 디버거 자동 연결을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9bd-104">구문</span><span class="sxs-lookup"><span data-stu-id="5e9bd-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e9bd-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5e9bd-105">Parameters</span></span>  

 `guidPort`  
 <span data-ttu-id="5e9bd-106">진행 항상로 설정 `GUID_NULL` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="5e9bd-107">진행 일반적으로 함수를 사용 하 여 검색 되는 프로세스 ID `GetCurrentProcessId` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="5e9bd-108">진행 프로그램 유형: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` 또는 `AUTOATTACH_PROGRAM_UNKNOWN`</span><span class="sxs-lookup"><span data-stu-id="5e9bd-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="5e9bd-109">진행 프로그램 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="5e9bd-110">진행 디버그 동사에 의해 전달 된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e9bd-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="5e9bd-111">Return Value</span></span>  

 <span data-ttu-id="5e9bd-112">메서드가 성공 하면 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e9bd-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e9bd-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5e9bd-113">Requirements</span></span>  

 <span data-ttu-id="5e9bd-114">**헤더:** DbgAutoAttach</span><span class="sxs-lookup"><span data-stu-id="5e9bd-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9bd-115">참조</span><span class="sxs-lookup"><span data-stu-id="5e9bd-115">See also</span></span>

- [<span data-ttu-id="5e9bd-116">IDebugAutoAttach 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5e9bd-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
