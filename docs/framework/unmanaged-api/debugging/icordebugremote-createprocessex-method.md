---
title: ICorDebugRemote::CreateProcessEx 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
ms.openlocfilehash: 37bf800f27754d1bf80aece962b7cbb85b1cbedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712185"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="c1ef8-102">ICorDebugRemote::CreateProcessEx 메서드</span><span class="sxs-lookup"><span data-stu-id="c1ef8-102">ICorDebugRemote::CreateProcessEx Method</span></span>

<span data-ttu-id="c1ef8-103">디버거의 원격 컴퓨터에서 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ef8-104">구문</span><span class="sxs-lookup"><span data-stu-id="c1ef8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1ef8-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c1ef8-105">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="c1ef8-106">진행 [ICorDebugRemoteTarget 인터페이스](icordebugremotetarget-interface.md)에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c1ef8-107">프로세스가 시작 되는 원격 컴퓨터를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="c1ef8-108">진행 시작 된 프로세스에서 실행할 모듈을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="c1ef8-109">모듈은 호출 프로세스의 보안 컨텍스트에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="c1ef8-110">진행 시작 된 프로세스에서 실행할 명령줄을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="c1ef8-111">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="c1ef8-112">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="c1ef8-113">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="c1ef8-114">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="c1ef8-115">진행 새 프로세스에 대 한 환경 블록에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="c1ef8-116">진행 프로세스의 현재 디렉터리에 대 한 전체 경로를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="c1ef8-117">이 매개 변수가 null 이면 새 프로세스는 호출 프로세스와 동일한 현재 드라이브 및 디렉터리를 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="c1ef8-118">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="c1ef8-119">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="c1ef8-120">진행 원격 디버깅에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c1ef8-121">제한이 프로세스를 나타내는 "ICorDebugProcess Interface" 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1ef8-122">반환 값</span><span class="sxs-lookup"><span data-stu-id="c1ef8-122">Return Value</span></span>  

 <span data-ttu-id="c1ef8-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1ef8-123">S_OK</span></span>  
 <span data-ttu-id="c1ef8-124">원격 컴퓨터에서 프로세스를 시작 하 고 디버깅을 위해 "ICorDebugProcess Interface"를 반환 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="c1ef8-125">E_FAIL(또는 다른 E_ 반환 코드)</span><span class="sxs-lookup"><span data-stu-id="c1ef8-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c1ef8-126">원격 컴퓨터에서 프로세스를 시작 하 고 디버깅을 위해 "ICorDebugProcess Interface"를 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1ef8-127">설명</span><span class="sxs-lookup"><span data-stu-id="c1ef8-127">Remarks</span></span>  

 <span data-ttu-id="c1ef8-128">Silverlight에서는 혼합 모드 디버깅이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ef8-129">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1ef8-129">Requirements</span></span>  

 <span data-ttu-id="c1ef8-130">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1ef8-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ef8-131">**헤더:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="c1ef8-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c1ef8-132">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1ef8-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1ef8-133">**.NET Framework 버전:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c1ef8-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ef8-134">참조</span><span class="sxs-lookup"><span data-stu-id="c1ef8-134">See also</span></span>

- [<span data-ttu-id="c1ef8-135">ICorDebugRemote 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c1ef8-135">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="c1ef8-136">ICorDebug 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c1ef8-136">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="c1ef8-137">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c1ef8-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
