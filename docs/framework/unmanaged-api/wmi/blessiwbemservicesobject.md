---
title: BlessIWbemServicesObject 함수 (관리 되지 않는 API 참조)
description: BlessIWbemServicesObject 함수는 사용자 자격 증명이 IWbemServices 개체에 대 한 액세스를 허용 하는지 여부를 나타냅니다.
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1aab2076f57f938715a3e65481a3540dc52279c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719751"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="0a484-103">BlessIWbemServicesObject 함수</span><span class="sxs-lookup"><span data-stu-id="0a484-103">BlessIWbemServicesObject function</span></span>

<span data-ttu-id="0a484-104">사용자 자격 증명이 지정 된 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) 개체에 대 한 액세스를 허용 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0a484-105">구문</span><span class="sxs-lookup"><span data-stu-id="0a484-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="0a484-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a484-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="0a484-107">진행 WMI 서비스 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="0a484-108">진행 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="0a484-109">진행 와 연결 된 암호 `strUser` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="0a484-110">진행 사용자의 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-110">[in] The domain name of the user.</span></span> <span data-ttu-id="0a484-111">자세한 내용은 [Connectserverwmi](connectserverwmi.md) 함수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a484-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="0a484-112">진행 가장 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="0a484-113">진행 권한 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a484-114">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a484-114">Return value</span></span>

<span data-ttu-id="0a484-115">이 함수에서 반환 되는 다음 값은 *winerror.h* 헤더 파일에 정의 되어 있거나 코드에서 상수로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0a484-116">상수</span><span class="sxs-lookup"><span data-stu-id="0a484-116">Constant</span></span>  |<span data-ttu-id="0a484-117">값</span><span class="sxs-lookup"><span data-stu-id="0a484-117">Value</span></span>  |<span data-ttu-id="0a484-118">설명</span><span class="sxs-lookup"><span data-stu-id="0a484-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="0a484-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="0a484-119">0x80070057</span></span> | <span data-ttu-id="0a484-120">하나 이상의 인수가 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="0a484-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="0a484-121">0x80004003</span></span> | <span data-ttu-id="0a484-122">`pIWbemServices`이(가) `null`인 경우.</span><span class="sxs-lookup"><span data-stu-id="0a484-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="0a484-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="0a484-123">0x80000008</span></span> | <span data-ttu-id="0a484-124">알 수 없는 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="0a484-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="0a484-125">0x80000002</span></span> | <span data-ttu-id="0a484-126">작업을 수행 하는 데 사용할 수 있는 메모리가 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="0a484-127">0</span><span class="sxs-lookup"><span data-stu-id="0a484-127">0</span></span> | <span data-ttu-id="0a484-128">함수 호출에 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a484-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="0a484-129">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0a484-129">Requirements</span></span>

 <span data-ttu-id="0a484-130">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a484-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="0a484-131">**헤더:** WMINet_Utils idl</span><span class="sxs-lookup"><span data-stu-id="0a484-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="0a484-132">**.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0a484-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0a484-133">참조</span><span class="sxs-lookup"><span data-stu-id="0a484-133">See also</span></span>

- [<span data-ttu-id="0a484-134">WMI 및 성능 카운터(관리되지 않는 API 참조)</span><span class="sxs-lookup"><span data-stu-id="0a484-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
