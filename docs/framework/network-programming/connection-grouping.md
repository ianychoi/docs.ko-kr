---
title: 연결 그룹화
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 8bd4412a4c13dd490fce3118f59b5bb1f0d3ea85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250569"
---
# <a name="connection-grouping"></a><span data-ttu-id="8a411-102">연결 그룹화</span><span class="sxs-lookup"><span data-stu-id="8a411-102">Connection Grouping</span></span>

<span data-ttu-id="8a411-103">연결 그룹화는 단일 애플리케이션 내의 특정 요청을 정의된 연결 풀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="8a411-104">이 기능은 사용자 대신 백 엔드 서버에 연결되고 Kerberos와 같은 위임을 지원하는 인증 프로토콜을 사용하는 중간 계층 애플리케이션에 필요하거나 다음 예제와 같이 자체적인 자격 증명을 제공하는 중간 계층 애플리케이션에 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="8a411-105">예를 들어 사용자인 Joe가 급여 정보를 표시하는 내부 웹 사이트를 방문한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="8a411-106">Joe를 인증한 후 중간 계층 애플리케이션 서버는 Joe의 자격 증명을 사용하여 백 엔드 서버에 연결하고 급여 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="8a411-107">다음으로 Susan은 사이트를 방문하고 급여 정보를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="8a411-108">중간 계층 애플리케이션은 Joe의 자격 증명으로 이미 연결을 설정했으므로 백 엔드 서버는 Joe의 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="8a411-109">그러나 애플리케이션이 백 엔드 서버로 보낸 각 요청을 사용자 이름에서 형성된 연결 그룹에 할당하면 각 사용자는 개별 연결 풀에 속하고 실수로 다른 사용자와 인증 정보를 공유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="8a411-110">요청을 특정 연결 그룹에 할당하려면 요청을 만들기 전에 <xref:System.Net.WebRequest>의 <xref:System.Net.WebRequest.ConnectionGroupName%2A> 속성에 이름을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a411-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a411-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a411-111">See also</span></span>

- [<span data-ttu-id="8a411-112">연결 관리</span><span class="sxs-lookup"><span data-stu-id="8a411-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="8a411-113">방법: 그룹 연결에 사용자 정보 할당</span><span class="sxs-lookup"><span data-stu-id="8a411-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
