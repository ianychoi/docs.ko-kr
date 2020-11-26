---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239836"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="44391-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="44391-102">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="44391-103">속성</span><span class="sxs-lookup"><span data-stu-id="44391-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44391-104">ID</span><span class="sxs-lookup"><span data-stu-id="44391-104">ID</span></span>|<span data-ttu-id="44391-105">1006</span><span class="sxs-lookup"><span data-stu-id="44391-105">1006</span></span>|  
|<span data-ttu-id="44391-106">키워드</span><span class="sxs-lookup"><span data-stu-id="44391-106">Keywords</span></span>|<span data-ttu-id="44391-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="44391-107">WFRuntime</span></span>|  
|<span data-ttu-id="44391-108">Level</span><span class="sxs-lookup"><span data-stu-id="44391-108">Level</span></span>|<span data-ttu-id="44391-109">오류</span><span class="sxs-lookup"><span data-stu-id="44391-109">Error</span></span>|  
|<span data-ttu-id="44391-110">채널</span><span class="sxs-lookup"><span data-stu-id="44391-110">Channel</span></span>|<span data-ttu-id="44391-111">Microsoft-Windows-애플리케이션 서버-애플리케이션/디버그</span><span class="sxs-lookup"><span data-stu-id="44391-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44391-112">Description</span><span class="sxs-lookup"><span data-stu-id="44391-112">Description</span></span>  

 <span data-ttu-id="44391-113">워크플로 애플리케이션에서 처리되지 않은 예외가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44391-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44391-114">메시지</span><span class="sxs-lookup"><span data-stu-id="44391-114">Message</span></span>  

 <span data-ttu-id="44391-115">WorkflowInstance Id: ' %1 '에서 처리 되지 않은 예외가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="44391-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="44391-116">작업 ' %2 ', DisplayName: ' %3 '에서 예외가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="44391-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="44391-117">다음 작업이 수행 됩니다. %4.</span><span class="sxs-lookup"><span data-stu-id="44391-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44391-118">세부 정보</span><span class="sxs-lookup"><span data-stu-id="44391-118">Details</span></span>  
  
|<span data-ttu-id="44391-119">데이터 항목 이름</span><span class="sxs-lookup"><span data-stu-id="44391-119">Data Item Name</span></span>|<span data-ttu-id="44391-120">데이터 항목 형식</span><span class="sxs-lookup"><span data-stu-id="44391-120">Data Item Type</span></span>|<span data-ttu-id="44391-121">Description</span><span class="sxs-lookup"><span data-stu-id="44391-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44391-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="44391-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="44391-123">워크플로의 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="44391-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="44391-124">예외</span><span class="sxs-lookup"><span data-stu-id="44391-124">Exception</span></span>|`xs:string`|<span data-ttu-id="44391-125">예외에 대한 예외 정보</span><span class="sxs-lookup"><span data-stu-id="44391-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="44391-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44391-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="44391-127">AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="44391-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
