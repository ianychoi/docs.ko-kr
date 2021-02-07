---
description: '자세히 알아보기: ICLRRuntimeInfo 인터페이스'
title: ICLRRuntimeInfo 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: d599c743e5a42801321ea487fdd9e52bfcfaf081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753863"
---
# <a name="iclrruntimeinfo-interface"></a><span data-ttu-id="0d9d7-103">ICLRRuntimeInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0d9d7-103">ICLRRuntimeInfo Interface</span></span>

<span data-ttu-id="0d9d7-104">버전, 디렉터리 및 로드 상태를 포함 하 여 특정 CLR (공용 언어 런타임)에 대 한 정보를 반환 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-104">Provides methods that return information about a specific common language runtime (CLR), including version, directory, and load status.</span></span> <span data-ttu-id="0d9d7-105">또한이 인터페이스는 런타임을 초기화 하지 않고 런타임 관련 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-105">This interface also provides runtime-specific functionality without initializing the runtime.</span></span> <span data-ttu-id="0d9d7-106">이 메서드에는 [Getinterface](iclrruntimeinfo-getinterface-method.md) 메서드를 통해 런타임 관련 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) 메서드, 런타임 모듈 관련 [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) 메서드 및 런타임 제공 인터페이스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-106">It includes the runtime-relative [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method, the runtime module-specific [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method, and runtime-provided interfaces through the [GetInterface](iclrruntimeinfo-getinterface-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d9d7-107">메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-107">Methods</span></span>  
  
|<span data-ttu-id="0d9d7-108">메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-108">Method</span></span>|<span data-ttu-id="0d9d7-109">설명</span><span class="sxs-lookup"><span data-stu-id="0d9d7-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d9d7-110">BindAsLegacyV2Runtime 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-110">BindAsLegacyV2Runtime Method</span></span>](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|<span data-ttu-id="0d9d7-111">모든 레거시 CLR 버전 2 활성화 정책 결정에 대해이 런타임을 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-111">Binds this runtime for all legacy CLR version 2 activation policy decisions.</span></span>|  
|[<span data-ttu-id="0d9d7-112">GetDefaultStartupFlags 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-112">GetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-getdefaultstartupflags-method.md)|<span data-ttu-id="0d9d7-113">CLR 시작 플래그 및 호스트 구성 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-113">Gets the CLR startup flags and host configuration file.</span></span>|  
|[<span data-ttu-id="0d9d7-114">GetInterface 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-114">GetInterface Method</span></span>](iclrruntimeinfo-getinterface-method.md)|<span data-ttu-id="0d9d7-115">CLR을 현재 프로세스로 로드 하 고 [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) 및 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)와 같은 런타임 인터페이스 포인터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-115">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) and [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md).</span></span> <span data-ttu-id="0d9d7-116">이 메서드는 모든 함수를 대체 `CorBindTo*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-116">This method supersedes all the `CorBindTo*` functions.</span></span>|  
|[<span data-ttu-id="0d9d7-117">GetProcAddress 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-117">GetProcAddress Method</span></span>](iclrruntimeinfo-getprocaddress-method.md)|<span data-ttu-id="0d9d7-118">이 인터페이스와 연결 된 CLR에서 내보낸 지정 된 함수의 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-118">Gets the address of a specified function that was exported from the CLR associated with this interface.</span></span> <span data-ttu-id="0d9d7-119">이 메서드는 [GetRealProcAddress](getrealprocaddress-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-119">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) method.</span></span>|  
|[<span data-ttu-id="0d9d7-120">GetRuntimeDirectory 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-120">GetRuntimeDirectory Method</span></span>](iclrruntimeinfo-getruntimedirectory-method.md)|<span data-ttu-id="0d9d7-121">이 인터페이스와 연결 된 CLR의 설치 디렉터리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-121">Gets the installation directory of the CLR associated with this interface.</span></span> <span data-ttu-id="0d9d7-122">이 메서드는 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-122">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) method.</span></span>|  
|[<span data-ttu-id="0d9d7-123">GetVersionString 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-123">GetVersionString Method</span></span>](iclrruntimeinfo-getversionstring-method.md)|<span data-ttu-id="0d9d7-124">지정 된 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR (공용 언어 런타임) 버전 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-124">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="0d9d7-125">이 메서드는 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) 및 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-125">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) and [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) methods.</span></span>|  
|[<span data-ttu-id="0d9d7-126">IsLoadable 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-126">IsLoadable Method</span></span>](iclrruntimeinfo-isloadable-method.md)|<span data-ttu-id="0d9d7-127">프로세스에 이미 로드 되어 있을 수 있는 다른 런타임을 고려 하 여이 인터페이스와 연결 된 런타임을 현재 프로세스에 로드할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-127">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>|  
|[<span data-ttu-id="0d9d7-128">IsLoaded 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-128">IsLoaded Method</span></span>](iclrruntimeinfo-isloaded-method.md)|<span data-ttu-id="0d9d7-129">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR이 프로세스에 로드 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-129">Indicates whether the CLR associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span>|  
|[<span data-ttu-id="0d9d7-130">IsStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-130">IsStarted Method</span></span>](iclrruntimeinfo-isstarted-method.md)|<span data-ttu-id="0d9d7-131">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR이 시작 되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-131">Indicates whether the CLR that is associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface has been started.</span></span>|  
|[<span data-ttu-id="0d9d7-132">LoadErrorString 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-132">LoadErrorString Method</span></span>](iclrruntimeinfo-loaderrorstring-method.md)|<span data-ttu-id="0d9d7-133">HRESULT 값을 지정 된 문화권에 대 한 적절 한 오류 메시지로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-133">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span> <span data-ttu-id="0d9d7-134">이 메서드는 [LoadStringRC](loadstringrc-function.md) 및 [LoadStringRCEx](loadstringrcex-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-134">This method supersedes the [LoadStringRC](loadstringrc-function.md) and [LoadStringRCEx](loadstringrcex-function.md) methods.</span></span>|  
|[<span data-ttu-id="0d9d7-135">LoadLibrary 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-135">LoadLibrary Method</span></span>](iclrruntimeinfo-loadlibrary-method.md)|<span data-ttu-id="0d9d7-136">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스로 표시 되는 CLR의 프레임 워크 디렉터리에서 라이브러리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-136">Loads a library from the framework directory of the CLR represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="0d9d7-137">이 메서드는 [LoadLibraryShim](loadlibraryshim-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-137">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) method.</span></span>|  
|[<span data-ttu-id="0d9d7-138">SetDefaultStartupFlags 메서드</span><span class="sxs-lookup"><span data-stu-id="0d9d7-138">SetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-setdefaultstartupflags-method.md)|<span data-ttu-id="0d9d7-139">CLR 시작 플래그 및 호스트 구성 파일을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-139">Sets the CLR startup flags and host configuration file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d9d7-140">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0d9d7-140">Requirements</span></span>  

 <span data-ttu-id="0d9d7-141">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d9d7-142">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="0d9d7-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d9d7-143">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d9d7-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d9d7-144">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d9d7-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9d7-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d9d7-145">See also</span></span>

- [<span data-ttu-id="0d9d7-146">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0d9d7-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0d9d7-147">호스팅</span><span class="sxs-lookup"><span data-stu-id="0d9d7-147">Hosting</span></span>](index.md)
