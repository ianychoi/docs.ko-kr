---
title: WCF 개발자를 위한 gRPC gRPC 개요
description: GRPC 개발을 안내 하는 원칙 집합에 대해 알아봅니다.
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938405"
---
# <a name="grpc-overview"></a><span data-ttu-id="1ec3c-103">gRPC 개요</span><span class="sxs-lookup"><span data-stu-id="1ec3c-103">gRPC overview</span></span>

<span data-ttu-id="1ec3c-104">이 장에서는 최종 장의 Windows Communication Foundation (WCF) 및 gRPC의 genesis를 확인 한 후에 gRPC의 주요 기능과 WCF와 비교 하는 방법을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-104">After looking at the genesis of both Windows Communication Foundation (WCF) and gRPC in the last chapter, this chapter considers some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="1ec3c-105">ASP.NET Core 3.0은 Microsoft 팀에서 gRPC의 공식 .NET 구현에 기여 하는 최고 수준의 시민으로 gRPC를 기본적으로 지 원하는 ASP.NET의 첫 번째 릴리스입니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="1ec3c-106">다른 모든 주요 프로그래밍 언어 및 프레임 워크와 상호 운용할 수 있는 .NET을 사용 하 여 분산 응용 프로그램을 빌드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-106">It's recommended for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="1ec3c-107">핵심 원칙</span><span class="sxs-lookup"><span data-stu-id="1ec3c-107">Key principles</span></span>

<span data-ttu-id="1ec3c-108">1 장에서 설명한 것 처럼 Google은 HTTP/2 소개를 사용 하 여 Stubby, 범용 RPC 인프라를 대체 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to replace Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="1ec3c-109">Stubby에 기반한 gRPC는 이제 표준화를 활용할 수 있으며 모바일 컴퓨팅, 클라우드 및 사물 인터넷에 대 한 적용 가능성을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-109">gRPC, based on Stubby, now can take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="1ec3c-110">이 표준화를 위해 [CNCF (Cloud Native 컴퓨팅 Foundation)](https://www.cncf.io/) 에서 grpc를 관리 하는 원칙 집합을 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-110">To achieve this standardization, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="1ec3c-111">다음 목록에서는 주로 접근성 및 유용성을 최대화 하는 데 관심이 있는 가장 관련성이 높은 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-111">The following list shows the most relevant ones, which are primarily concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="1ec3c-112">**무료 및 오픈** – 모든 아티팩트는 개발자가 grpc를 도입 하지 못하도록 제한 하지 않는 라이선스가 있는 오픈 소스 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-112">**Free and open** – All artifacts should be open source, with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="1ec3c-113">**검사 및 단순성** – grpc는 인기 있는 모든 플랫폼에서 사용할 수 있어야 하 고 모든 플랫폼에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-113">**Coverage and simplicity** – gRPC should be available across every popular platform, and simple enough to build on any platform.</span></span>
- <span data-ttu-id="1ec3c-114">**상호 운용성 및 연결** – 광범위 하 게 사용 가능한 네트워크 표준을 사용 하 여 대역폭 또는 대기 시간에 관계 없이 모든 네트워크에서 grpc를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-114">**Interoperability and reach** – It should be possible to use gRPC on any network, regardless of bandwidth or latency, by using widely available network standards.</span></span>
- <span data-ttu-id="1ec3c-115">**일반적** 으로 사용 되는 용도의 프레임 워크는 성능을 저하 시 키 지 않고 가능한 한 광범위 한 사용 사례를 통해 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-115">**General purpose and performant** – The framework should be usable by as broad a range of use-cases as possible, without compromising performance.</span></span>
- <span data-ttu-id="1ec3c-116">**스트리밍** – 프로토콜은 대량 데이터 집합 또는 비동기 메시징에 대 한 스트리밍 의미 체계를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-116">**Streaming** – The protocol should provide streaming semantics for large datasets or asynchronous messaging.</span></span>
- <span data-ttu-id="1ec3c-117">**메타 데이터 교환** – 프로토콜을 사용 하면 인증 토큰과 같은 비 비즈니스 데이터를 실제 비즈니스 데이터와 별도로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-117">**Metadata exchange** – The protocol allows non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="1ec3c-118">**표준화 된 상태 코드** – 오류 처리 결정을 보다 명확 하 게 하기 위해 오류 코드의 가변성을 줄여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-118">**Standardized status codes** – The variability of error codes should be reduced to make error handling decisions clearer.</span></span> <span data-ttu-id="1ec3c-119">더 풍부한 오류 처리가 필요한 경우 메타 데이터 교환 내의 동작을 관리 하기 위한 메커니즘을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec3c-119">Where additional, richer error handling is required, a mechanism should be provided for managing behavior within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ec3c-120">[이전](introduction.md)
>[다음](approach.md)</span><span class="sxs-lookup"><span data-stu-id="1ec3c-120">[Previous](introduction.md)
[Next](approach.md)</span></span>
