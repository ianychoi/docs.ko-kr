---
title: WCF 개발자를 위한 ASP.NET Core gRPC - WCF 개발자를 위한 gRPC
description: ASP.NET Core 3.0에서 WCF 개발자를 위한 gRPC 서비스를 구축하는 방법 소개
ms.date: 09/02/2019
ms.openlocfilehash: c9cc5ef9c06d5262fb85850f8a3b178d46e5c6fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689279"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="e4274-103">WCF 개발자를 위한 ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="e4274-103">ASP.NET Core gRPC for WCF Developers</span></span>

![표지 이미지](./media/cover.png)

<span data-ttu-id="e4274-105">게시자:</span><span class="sxs-lookup"><span data-stu-id="e4274-105">PUBLISHED BY</span></span>

<span data-ttu-id="e4274-106">Microsoft 개발자 사업부, .NET 및 Visual Studio 제품 팀</span><span class="sxs-lookup"><span data-stu-id="e4274-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e4274-107">Microsoft Corporation의 사업부</span><span class="sxs-lookup"><span data-stu-id="e4274-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e4274-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e4274-108">One Microsoft Way</span></span>

<span data-ttu-id="e4274-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e4274-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e4274-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4274-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="e4274-111">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="e4274-111">All rights reserved.</span></span> <span data-ttu-id="e4274-112">이 가이드의 내용 중 어떤 부분도 게시자의 서면 허가 없이는 어떠한 형식이나 방법으로도 복제하거나 전송할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e4274-113">이 가이드는 작성자의 견해와 의견을 "있는 그대로" 제공하고 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="e4274-114">URL 및 기타 인터넷 웹 사이트 참조를 비롯하여 이 가이드에 제공된 견해, 의견 및 정보는 예고 없이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e4274-115">여기에 설명된 일부 예제는 예시 용도로만 제공되며 실제 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e4274-116">실제로 연관시키거나 관련시키려고 의도하거나 추론해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e4274-117">"상표" 웹 페이지의 <https://www.microsoft.com> 에 나열된 Microsoft 및 상표는 Microsoft 그룹 계열사의 상표입니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e4274-118">Docker 고래 로고는 Docker, Inc.의 등록 상표로, 허가하에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e4274-119">기타 모든 표시와 로고는 해당 소유자의 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="e4274-120">작성자:</span><span class="sxs-lookup"><span data-stu-id="e4274-120">Authors:</span></span>

> <span data-ttu-id="e4274-121">**Mark Rendle** - 최고 기술 책임자 - [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="e4274-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="e4274-122">**Miranda Steiner** - 기술 작성자</span><span class="sxs-lookup"><span data-stu-id="e4274-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="e4274-123">편집기:</span><span class="sxs-lookup"><span data-stu-id="e4274-123">Editor:</span></span>

> <span data-ttu-id="e4274-124">**Maira Wenzel** - 선임 콘텐츠 개발자 - Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4274-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="e4274-125">소개</span><span class="sxs-lookup"><span data-stu-id="e4274-125">Introduction</span></span>

<span data-ttu-id="e4274-126">gRPC는 네트워크 서비스와 분산 애플리케이션을 빌드하기 위한 최신 프레임워크입니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="e4274-127">SOAP의 플랫폼 간 상호 운용성과 결합된 WCF(Windows Communication Foundation) NetTCP 바인딩의 성능을 상상해 보세요.</span><span class="sxs-lookup"><span data-stu-id="e4274-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="e4274-128">gRPC는 HTTP/2 및 Protobuf 메시지 인코딩 프로토콜을 기반으로 하여 애플리케이션과 서비스 간에 뛰어난 성능의 저대역폭 통신을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="e4274-129">.NET, Java, Python, Node.js, Go, C++ 등을 비롯한 가장 인기 있는 프로그래밍 언어 및 플랫폼에서 서버 및 클라이언트 코드 생성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="e4274-130">.NET Framework 4.x용 기존 gRPC 도구 및 라이브러리와 함께 ASP.NET Core 3.0에서 gRPC에 대한 최고 수준의 지원을 제공하므로 조직에서 .NET Core를 도입하려는 개발 팀을 위한 WCF의 훌륭한 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="e4274-131">이 가이드의 대상 사용자</span><span class="sxs-lookup"><span data-stu-id="e4274-131">Who should use this guide</span></span>

<span data-ttu-id="e4274-132">이 가이드는 이전에 WCF를 사용했으며 .NET Core 3.0 이상 버전용 최신 RPC 환경으로 애플리케이션을 마이그레이션하려는 .NET Framework 또는 .NET Core에서 작업하는 개발자를 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="e4274-133">더 일반적으로는 .NET Core 3.0로 업그레이드하거나 업그레이드를 고려 중이고 기본 제공 gRPC 도구를 사용하려는 경우에도 이 가이드가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="e4274-134">이 가이드를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="e4274-134">How you can use this guide</span></span>

<span data-ttu-id="e4274-135">다음은 WCF에 대한 특정 참조를 유사한 플랫폼으로 사용하여 ASP.NET Core 3.0에서 gRPC 서비스를 빌드하는 방법을 간략히 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="e4274-136">여기서는 각 개념을 WCF의 해당 기능과 연계하여 gRPC의 원칙을 설명하고 기존 WCF 애플리케이션을 gRPC로 마이그레이션하기 위한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="e4274-137">또한 WCF를 경험하고 새 서비스를 빌드하기 위해 gRPC를 알아보려는 개발자에게 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="e4274-138">애플리케이션 예제를 사용자 프로젝트를 위한 템플릿 또는 참조로 사용하고, 가이드 또는 샘플에서 코드를 복사하여 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="e4274-139">이 가이드를 팀에서 자유롭게 공유하고 이러한 여러가지 고려 사항과 기회에 대한 이해를 도모하세요.</span><span class="sxs-lookup"><span data-stu-id="e4274-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="e4274-140">모든 사람이 공통적인 용어와 기본 원칙으로 작업하도록 하면 아키텍처 패턴 및 사례를 일관성 있게 적용하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4274-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="e4274-141">참조 항목</span><span class="sxs-lookup"><span data-stu-id="e4274-141">References</span></span>

- <span data-ttu-id="e4274-142">**gRPC 웹 사이트**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="e4274-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="e4274-143">**서버 앱에 대해 .NET Core와 .NET Framework 중에 선택**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="e4274-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="e4274-144">다음</span><span class="sxs-lookup"><span data-stu-id="e4274-144">Next</span></span>](introduction.md)
