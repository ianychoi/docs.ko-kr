---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239902"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="4f161-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="4f161-102">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="4f161-103">속성</span><span class="sxs-lookup"><span data-stu-id="4f161-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f161-104">ID</span><span class="sxs-lookup"><span data-stu-id="4f161-104">ID</span></span>|<span data-ttu-id="4f161-105">1003</span><span class="sxs-lookup"><span data-stu-id="4f161-105">1003</span></span>|  
|<span data-ttu-id="4f161-106">키워드</span><span class="sxs-lookup"><span data-stu-id="4f161-106">Keywords</span></span>|<span data-ttu-id="4f161-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4f161-107">WFRuntime</span></span>|  
|<span data-ttu-id="4f161-108">Level</span><span class="sxs-lookup"><span data-stu-id="4f161-108">Level</span></span>|<span data-ttu-id="4f161-109">정보</span><span class="sxs-lookup"><span data-stu-id="4f161-109">Information</span></span>|  
|<span data-ttu-id="4f161-110">채널</span><span class="sxs-lookup"><span data-stu-id="4f161-110">Channel</span></span>|<span data-ttu-id="4f161-111">Microsoft-Windows-애플리케이션 서버-애플리케이션/디버그</span><span class="sxs-lookup"><span data-stu-id="4f161-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f161-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f161-112">Description</span></span>  

 <span data-ttu-id="4f161-113">워크플로 인스턴스가 Closed 상태에서 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f161-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f161-114">메시지</span><span class="sxs-lookup"><span data-stu-id="4f161-114">Message</span></span>  

 <span data-ttu-id="4f161-115">WorkflowInstance Id: '%1'이(가) Canceled 상태에서 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4f161-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f161-116">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4f161-116">Details</span></span>  
  
|<span data-ttu-id="4f161-117">데이터 항목 이름</span><span class="sxs-lookup"><span data-stu-id="4f161-117">Data Item Name</span></span>|<span data-ttu-id="4f161-118">데이터 항목 형식</span><span class="sxs-lookup"><span data-stu-id="4f161-118">Data Item Type</span></span>|<span data-ttu-id="4f161-119">Description</span><span class="sxs-lookup"><span data-stu-id="4f161-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f161-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4f161-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="4f161-121">워크플로의 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="4f161-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4f161-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f161-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4f161-123">AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="4f161-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
