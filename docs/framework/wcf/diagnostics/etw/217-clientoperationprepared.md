---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: e8aaf65bdff0718e932d07937e052541b7134f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278884"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="b572d-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="b572d-102">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="b572d-103">속성</span><span class="sxs-lookup"><span data-stu-id="b572d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b572d-104">ID</span><span class="sxs-lookup"><span data-stu-id="b572d-104">ID</span></span>|<span data-ttu-id="b572d-105">217</span><span class="sxs-lookup"><span data-stu-id="b572d-105">217</span></span>|  
|<span data-ttu-id="b572d-106">키워드</span><span class="sxs-lookup"><span data-stu-id="b572d-106">Keywords</span></span>|<span data-ttu-id="b572d-107">문제 해결, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b572d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b572d-108">Level</span><span class="sxs-lookup"><span data-stu-id="b572d-108">Level</span></span>|<span data-ttu-id="b572d-109">정보</span><span class="sxs-lookup"><span data-stu-id="b572d-109">Information</span></span>|  
|<span data-ttu-id="b572d-110">채널</span><span class="sxs-lookup"><span data-stu-id="b572d-110">Channel</span></span>|<span data-ttu-id="b572d-111">Microsoft-Windows-애플리케이션 서버-애플리케이션/분석</span><span class="sxs-lookup"><span data-stu-id="b572d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b572d-112">Description</span><span class="sxs-lookup"><span data-stu-id="b572d-112">Description</span></span>  

 <span data-ttu-id="b572d-113">이 이벤트는 서비스에 작업을 보내기 바로 전에 클라이언트에서 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b572d-114">메시지</span><span class="sxs-lookup"><span data-stu-id="b572d-114">Message</span></span>  

 <span data-ttu-id="b572d-115">클라이언트가 '%2' 계약과 연결된 '%1' 작업을 실행하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="b572d-116">메시지를 '%3'(으)로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b572d-117">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b572d-117">Details</span></span>  
  
|<span data-ttu-id="b572d-118">데이터 항목 이름</span><span class="sxs-lookup"><span data-stu-id="b572d-118">Data Item Name</span></span>|<span data-ttu-id="b572d-119">데이터 항목 형식</span><span class="sxs-lookup"><span data-stu-id="b572d-119">Data Item Type</span></span>|<span data-ttu-id="b572d-120">설명</span><span class="sxs-lookup"><span data-stu-id="b572d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b572d-121">작업</span><span class="sxs-lookup"><span data-stu-id="b572d-121">Action</span></span>|`xs:string`|<span data-ttu-id="b572d-122">보내는 메시지의 SOAP 동작 헤더입니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="b572d-123">Contract Name</span><span class="sxs-lookup"><span data-stu-id="b572d-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="b572d-124">계약 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-124">The name of the contract.</span></span> <span data-ttu-id="b572d-125">예를 들면 ICalculator와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="b572d-126">대상</span><span class="sxs-lookup"><span data-stu-id="b572d-126">Destination</span></span>|`xs:string`|<span data-ttu-id="b572d-127">메시지를 받는 서비스 엔드포인트의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="b572d-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="b572d-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="b572d-129">웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b572d-130">해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName '으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b572d-131">예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.</span><span class="sxs-lookup"><span data-stu-id="b572d-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b572d-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b572d-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b572d-133">AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="b572d-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
