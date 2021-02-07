---
description: '자세히 알아보기: ADO.NET 응용 프로그램 보안'
title: 애플리케이션 보안
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 4e4d219d1f4249846943d019e174abd6d43687c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718878"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="83984-103">ADO.NET 응용 프로그램 보안</span><span class="sxs-lookup"><span data-stu-id="83984-103">Securing ADO.NET applications</span></span>

<span data-ttu-id="83984-104">보안 ADO.NET 애플리케이션을 작성하려면 사용자 입력의 유효성을 확인하지 않는 것과 같은 일반적인 코딩 문제를 피하는 것 외에도 여러 부분을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-104">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="83984-105">데이터에 액세스하는 애플리케이션에는 공격자가 주요한 데이터를 검색, 조작 또는 파괴하는 데 사용할 수 있는 수많은 잠재적인 오류 지점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83984-105">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="83984-106">따라서 애플리케이션 디자인 단계의 위협 모델링 과정에서부터 최종 배포와 진행 중인 유지 관리에 이르기까지 보안의 모든 측면을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-106">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="83984-107">.NET Framework에서는 데이터베이스 애플리케이션을 보호하고 관리할 수 있는 여러 유용한 클래스, 서비스 및 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-107">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="83984-108">CLR(공용 언어 런타임)은 관리 코드의 권한을 더 제한하는 CAS(코드 액세스 보안)를 사용하여 실행될 코드에 형식 안전 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-108">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="83984-109">다음 보안 데이터 액세스 코딩 연습에서는 잠재적인 공격자에 의해 발생할 수 있는 손상을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-109">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="83984-110">보안 코드를 작성하면 데이터베이스와 같은 관리되지 않는 리소스 작업을 할 때 자초한 보안 허점을 막지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-110">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="83984-111">SQL Server와 같은 대부분의 서버 데이터베이스는 제대로 구현되는 경우 보안을 강화하는 자체 보안 시스템을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="83984-111">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="83984-112">그러나 제대로 구성되지 않은 경우 강력한 보안 시스템으로 구성된 데이터 소스라 할지라도 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83984-112">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83984-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="83984-113">In this section</span></span>

 [<span data-ttu-id="83984-114">보안 개요</span><span class="sxs-lookup"><span data-stu-id="83984-114">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="83984-115">보안 ADO.NET 애플리케이션 디자인에 대한 권장 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-115">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="83984-116">보안 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="83984-116">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="83984-117">안전한 데이터 소스의 데이터로 작업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-117">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="83984-118">안전한 클라이언트 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="83984-118">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="83984-119">클라이언트 애플리케이션 보안을 위한 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-119">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="83984-120">코드 액세스 보안 및 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83984-120">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="83984-121">CAS를 사용하여 ADO.NET 코드를 보호하는 방법 및</span><span class="sxs-lookup"><span data-stu-id="83984-121">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="83984-122">부분 신뢰를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-122">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="83984-123">개인 정보 및 데이터 보안</span><span class="sxs-lookup"><span data-stu-id="83984-123">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="83984-124">ADO.NET 애플리케이션의 암호화 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-124">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83984-125">관련 단원</span><span class="sxs-lookup"><span data-stu-id="83984-125">Related sections</span></span>

 [<span data-ttu-id="83984-126">DataSet 및 DataTable 보안 지침</span><span class="sxs-lookup"><span data-stu-id="83984-126">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="83984-127">및에 대 한 보안 지침을 제공 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-127">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="83984-128">SQL Server 보안</span><span class="sxs-lookup"><span data-stu-id="83984-128">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="83984-129">개발자 관점에서 SQL Server 보안 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-129">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="83984-130">Security Considerations</span><span class="sxs-lookup"><span data-stu-id="83984-130">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="83984-131">Entity Framework 애플리케이션의 보안에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-131">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="83984-132">보안</span><span class="sxs-lookup"><span data-stu-id="83984-132">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="83984-133">.NET의 모든 보안 측면을 설명 하는 문서에 대 한 링크를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-133">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="83984-134">[보안 도구](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83984-134">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="83984-135">보안 정책을 보호하고 관리하는 .NET Framework 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="83984-135">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="83984-136">[보안 애플리케이션을 만들기 위한 리소스](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83984-136">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="83984-137">보안 응용 프로그램을 만들기 위한 아티클에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-137">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="83984-138">보안 참고 자료</span><span class="sxs-lookup"><span data-stu-id="83984-138">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="83984-139">온라인 및 인쇄 작업에서 사용 가능한 외부 리소스의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83984-139">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83984-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83984-140">See also</span></span>

- [<span data-ttu-id="83984-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83984-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="83984-142">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="83984-142">ADO.NET Overview</span></span>](ado-net-overview.md)
