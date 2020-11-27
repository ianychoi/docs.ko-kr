---
title: 기본 프로그래밍 수명 주기
description: WCF 응용 프로그램을 빌드하는 작업에 대해 알아봅니다. WCF를 사용 하면 앱이 동일한 컴퓨터, 네트워크 또는 다른 응용 프로그램 플랫폼에서 통신할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: f958bd06f617a5648b31332ebe9e7662d45cd241
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294848"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="a3e73-104">기본 프로그래밍 수명 주기</span><span class="sxs-lookup"><span data-stu-id="a3e73-104">Basic Programming Lifecycle</span></span>

<span data-ttu-id="a3e73-105">WCF (Windows Communication Foundation)를 사용 하면 응용 프로그램이 동일한 컴퓨터, 인터넷 또는 다른 응용 프로그램 플랫폼에 있든 간에 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="a3e73-106">이 항목에서는 WCF 응용 프로그램을 빌드하는 데 필요한 작업에 대해 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="a3e73-107">작동 하는 샘플 응용 프로그램은 [시작 자습서](getting-started-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="a3e73-108">기본 작업</span><span class="sxs-lookup"><span data-stu-id="a3e73-108">The Basic Tasks</span></span>  

 <span data-ttu-id="a3e73-109">수행할 기본 작업 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="a3e73-110">서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-110">Define the service contract.</span></span> <span data-ttu-id="a3e73-111">서비스 계약은 서비스 서명, 서비스 교환 날짜 및 계약에 필요한 기타 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="a3e73-112">자세한 내용은 [서비스 계약 디자인](designing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="a3e73-113">계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-113">Implement the contract.</span></span> <span data-ttu-id="a3e73-114">서비스 계약을 구현하려면 계약을 구현하는 클래스를 만들고 런타임에 필요한 사용자 지정 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="a3e73-115">자세한 내용은 [서비스 계약 구현](implementing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="a3e73-116">엔드포인트 및 기타 동작 정보를 지정하여 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="a3e73-117">자세한 내용은 [서비스 구성](configuring-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="a3e73-118">서비스를 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-118">Host the service.</span></span> <span data-ttu-id="a3e73-119">자세한 내용은 [호스팅 서비스](hosting-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="a3e73-120">클라이언트 애플리케이션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-120">Build a client application.</span></span> <span data-ttu-id="a3e73-121">자세한 내용은 [클라이언트 빌드](building-clients.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e73-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="a3e73-122">이 단원의 항목은 이 순서를 따르지만 일부 시나리오에서는 첫 번째 단계부터 시작하지 않는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="a3e73-123">예를 들어 기존 서비스에 대한 클라이언트를 빌드하려면 5단계에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="a3e73-124">다른 사용자가 사용할 서비스를 빌드하는 경우 5단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="a3e73-125">서비스 계약 개발에 대해 잘 알고 있으면 [확장성 소개를](introduction-to-extensibility.md)읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="a3e73-126">서비스에 문제가 있는 경우 [WCF 문제 해결 퀵 스타트](wcf-troubleshooting-quickstart.md) 를 확인 하 여 다른 사용자가 동일 하거나 유사한 문제를 발생 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e73-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e73-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3e73-127">See also</span></span>

- [<span data-ttu-id="a3e73-128">서비스 계약 구현</span><span class="sxs-lookup"><span data-stu-id="a3e73-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
