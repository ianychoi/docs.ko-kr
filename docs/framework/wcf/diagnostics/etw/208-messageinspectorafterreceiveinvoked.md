---
description: '자세한 정보: 208-MessageInspectorAfterReceiveInvoked'
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 29935f5dc8c5dd53c0bf427bfdc9b3858d7fb8fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728056"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="32962-103">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="32962-103">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="32962-104">속성</span><span class="sxs-lookup"><span data-stu-id="32962-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32962-105">ID</span><span class="sxs-lookup"><span data-stu-id="32962-105">ID</span></span>|<span data-ttu-id="32962-106">208</span><span class="sxs-lookup"><span data-stu-id="32962-106">208</span></span>|  
|<span data-ttu-id="32962-107">키워드</span><span class="sxs-lookup"><span data-stu-id="32962-107">Keywords</span></span>|<span data-ttu-id="32962-108">문제 해결, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32962-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="32962-109">Level</span><span class="sxs-lookup"><span data-stu-id="32962-109">Level</span></span>|<span data-ttu-id="32962-110">정보</span><span class="sxs-lookup"><span data-stu-id="32962-110">Information</span></span>|  
|<span data-ttu-id="32962-111">채널</span><span class="sxs-lookup"><span data-stu-id="32962-111">Channel</span></span>|<span data-ttu-id="32962-112">Microsoft-Windows-애플리케이션 서버-애플리케이션/분석</span><span class="sxs-lookup"><span data-stu-id="32962-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32962-113">설명</span><span class="sxs-lookup"><span data-stu-id="32962-113">Description</span></span>  

 <span data-ttu-id="32962-114">이 이벤트는 서비스 모델이 메시지 검사자에 대해 `AfterReceive` 메서드를 호출한 후에 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="32962-114">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32962-115">메시지</span><span class="sxs-lookup"><span data-stu-id="32962-115">Message</span></span>  

 <span data-ttu-id="32962-116">디스패처가 '%1' 형식의 MessageInspector에 대해 'AfterReceiveReply'를 호출했습니다.</span><span class="sxs-lookup"><span data-stu-id="32962-116">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32962-117">세부 정보</span><span class="sxs-lookup"><span data-stu-id="32962-117">Details</span></span>  
  
|<span data-ttu-id="32962-118">데이터 항목 이름</span><span class="sxs-lookup"><span data-stu-id="32962-118">Data Item Name</span></span>|<span data-ttu-id="32962-119">데이터 항목 형식</span><span class="sxs-lookup"><span data-stu-id="32962-119">Data Item Type</span></span>|<span data-ttu-id="32962-120">설명</span><span class="sxs-lookup"><span data-stu-id="32962-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32962-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="32962-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="32962-122">호출된 `MessageInspector` 형식의 CLR FullName입니다.</span><span class="sxs-lookup"><span data-stu-id="32962-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="32962-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="32962-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="32962-124">웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="32962-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="32962-125">해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName '으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32962-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="32962-126">예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.</span><span class="sxs-lookup"><span data-stu-id="32962-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="32962-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32962-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="32962-128">AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="32962-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
