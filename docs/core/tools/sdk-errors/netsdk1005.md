---
title: 'NETSDK1005 및 NETSDK1047: 자산 파일에 대상이 없음'
description: 자산 파일에 대상이 없는 문제를 해결하는 방법입니다.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717905"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="da007-103">NETSDK1005 및 NETSDK1047: 자산 파일에 대상이 없음</span><span class="sxs-lookup"><span data-stu-id="da007-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="da007-104">**이 문서의 적용 대상:** ✔️ .NET Core 2.1.100 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="da007-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="da007-105">.NET SDK가 NETSDK1005 또는 NETSDK1047 오류를 실행하는 경우 프로젝트의 자산 파일에 대상 프레임워크 중 하나의 정보가 누락된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="da007-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="da007-106">일반적으로 복원을 실행하고 누락된 대상 값을 프로젝트의 `TargetFrameworks` 속성에 포함하면 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da007-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="da007-107">이 오류가 발생한 Visual Studio 16.8 미리 보기 버전과 함께 사용할 경우 .NET 5 미리 보기 8 초기 빌드에 알려진 문제가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="da007-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="da007-108">특히, 누락된 대상이 `net5.0-windows7.0` 또는 `net5.0`인 경우 최신 버전의 Visual Studio 및 .NET 5 SDK로 업데이트했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="da007-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
