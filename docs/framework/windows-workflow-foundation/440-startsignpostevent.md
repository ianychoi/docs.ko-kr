---
title: 440 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 1e0278d665a961afab21445ab8490e3e5a94987c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293457"
---
# <a name="440---startsignpostevent1"></a><span data-ttu-id="7bb87-102">440 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="7bb87-102">440 - StartSignpostEvent1</span></span>

## <a name="properties"></a><span data-ttu-id="7bb87-103">속성</span><span class="sxs-lookup"><span data-stu-id="7bb87-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7bb87-104">ID</span><span class="sxs-lookup"><span data-stu-id="7bb87-104">ID</span></span>|<span data-ttu-id="7bb87-105">440</span><span class="sxs-lookup"><span data-stu-id="7bb87-105">440</span></span>|  
|<span data-ttu-id="7bb87-106">키워드</span><span class="sxs-lookup"><span data-stu-id="7bb87-106">Keywords</span></span>|<span data-ttu-id="7bb87-107">문제 해결</span><span class="sxs-lookup"><span data-stu-id="7bb87-107">Troubleshooting</span></span>|  
|<span data-ttu-id="7bb87-108">Level</span><span class="sxs-lookup"><span data-stu-id="7bb87-108">Level</span></span>|<span data-ttu-id="7bb87-109">정보</span><span class="sxs-lookup"><span data-stu-id="7bb87-109">Information</span></span>|  
|<span data-ttu-id="7bb87-110">채널</span><span class="sxs-lookup"><span data-stu-id="7bb87-110">Channel</span></span>|<span data-ttu-id="7bb87-111">Microsoft-Windows-애플리케이션 서버-애플리케이션/분석</span><span class="sxs-lookup"><span data-stu-id="7bb87-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7bb87-112">Description</span><span class="sxs-lookup"><span data-stu-id="7bb87-112">Description</span></span>  

 <span data-ttu-id="7bb87-113">동작 추적에서 보내거나 받을 메시지가 동작 경계를 넘기 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7bb87-113">In activity tracing, indicates a message has started crossing an activity boundary in send or receive.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7bb87-114">메시지</span><span class="sxs-lookup"><span data-stu-id="7bb87-114">Message</span></span>  

 <span data-ttu-id="7bb87-115">동작 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="7bb87-115">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7bb87-116">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7bb87-116">Details</span></span>  
  
|<span data-ttu-id="7bb87-117">데이터 항목 이름</span><span class="sxs-lookup"><span data-stu-id="7bb87-117">Data Item Name</span></span>|<span data-ttu-id="7bb87-118">데이터 항목 형식</span><span class="sxs-lookup"><span data-stu-id="7bb87-118">Data Item Type</span></span>|<span data-ttu-id="7bb87-119">Description</span><span class="sxs-lookup"><span data-stu-id="7bb87-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7bb87-120">ExtendedData</span><span class="sxs-lookup"><span data-stu-id="7bb87-120">ExtendedData</span></span>|`xs:string`|<span data-ttu-id="7bb87-121">작업의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7bb87-121">The name of the activity.</span></span>|  
|<span data-ttu-id="7bb87-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7bb87-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7bb87-123">AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7bb87-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
