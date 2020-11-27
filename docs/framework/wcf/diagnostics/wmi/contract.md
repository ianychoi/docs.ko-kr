---
title: 계약
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 0df39bbd0b273f1e898ccbe585be288cc245b7f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274142"
---
# <a name="contract"></a><span data-ttu-id="bf109-102">계약</span><span class="sxs-lookup"><span data-stu-id="bf109-102">Contract</span></span>

<span data-ttu-id="bf109-103">계약</span><span class="sxs-lookup"><span data-stu-id="bf109-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf109-104">구문</span><span class="sxs-lookup"><span data-stu-id="bf109-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bf109-105">메서드</span><span class="sxs-lookup"><span data-stu-id="bf109-105">Methods</span></span>  

 <span data-ttu-id="bf109-106">Contract 클래스는 메서드를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bf109-107">속성</span><span class="sxs-lookup"><span data-stu-id="bf109-107">Properties</span></span>  

 <span data-ttu-id="bf109-108">Contract 클래스에는 다음 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="bf109-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="bf109-109">AppDomainId</span></span>  

 <span data-ttu-id="bf109-110">데이터 형식: sint32</span><span class="sxs-lookup"><span data-stu-id="bf109-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="bf109-111">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-112">계약을 호스팅하는 appdomain의 appdomain ID입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="bf109-113">동작</span><span class="sxs-lookup"><span data-stu-id="bf109-113">Behaviors</span></span>  

 <span data-ttu-id="bf109-114">데이터 형식: Behavior array</span><span class="sxs-lookup"><span data-stu-id="bf109-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="bf109-115">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-116">이 계약과 연결된 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="bf109-117">이름</span><span class="sxs-lookup"><span data-stu-id="bf109-117">Name</span></span>  

 <span data-ttu-id="bf109-118">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="bf109-118">Data type: string</span></span>  
  
 <span data-ttu-id="bf109-119">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-120">WSDL에 있는 계약의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="bf109-121">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="bf109-121">Namespace</span></span>  

 <span data-ttu-id="bf109-122">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="bf109-122">Data type: string</span></span>  
  
 <span data-ttu-id="bf109-123">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-124">WSDL에 있는 `portType` 요소의 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="bf109-125">작업</span><span class="sxs-lookup"><span data-stu-id="bf109-125">Operations</span></span>  

 <span data-ttu-id="bf109-126">데이터 형식: Operation array</span><span class="sxs-lookup"><span data-stu-id="bf109-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="bf109-127">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-128">이 계약의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="bf109-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="bf109-129">ProcessId</span></span>  

 <span data-ttu-id="bf109-130">데이터 형식: sint32</span><span class="sxs-lookup"><span data-stu-id="bf109-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="bf109-131">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-132">계약을 호스팅하는 프로세스의 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="bf109-133">ref</span><span class="sxs-lookup"><span data-stu-id="bf109-133">ref</span></span>  

 <span data-ttu-id="bf109-134">데이터 형식: Contract</span><span class="sxs-lookup"><span data-stu-id="bf109-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="bf109-135">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-136">계약이 이중 계약인 경우 콜백의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="bf109-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="bf109-137">SessionMode</span></span>  

 <span data-ttu-id="bf109-138">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="bf109-138">Data type: string</span></span>  
  
 <span data-ttu-id="bf109-139">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-140">계약에서 채널 세션을 사용하기 위해 이 계약과 연결된 바인딩이 필요한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="bf109-141">유형</span><span class="sxs-lookup"><span data-stu-id="bf109-141">Type</span></span>  

 <span data-ttu-id="bf109-142">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="bf109-142">Data type: string</span></span>  
  
 <span data-ttu-id="bf109-143">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="bf109-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf109-144">계약의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf109-145">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bf109-145">Requirements</span></span>  
  
|<span data-ttu-id="bf109-146">MOF</span><span class="sxs-lookup"><span data-stu-id="bf109-146">MOF</span></span>|<span data-ttu-id="bf109-147">Servicemodel.mof에 선언되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bf109-148">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="bf109-148">Namespace</span></span>|<span data-ttu-id="bf109-149">root\ServiceModel에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf109-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf109-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf109-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
