---
description: '자세한 정보: 구성 섹션 스키마'
title: 구성 섹션 스키마
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: f16ca16417da0b3ee7a7d0a5ebdd1a446ec0714a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698962"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="28f77-103">구성 섹션 스키마</span><span class="sxs-lookup"><span data-stu-id="28f77-103">Configuration sections schema</span></span>

<span data-ttu-id="28f77-104">구성 섹션 스키마에는 구성 파일의 사용자 지정 설정을 정의 하는 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28f77-104">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="28f77-105">구성 파일 및 스키마에 대 한 일반적인 내용은 [.NET Framework 구성 파일 스키마](index.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28f77-105">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="28f77-106">설명</span><span class="sxs-lookup"><span data-stu-id="28f77-106">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="28f77-107">구성 섹션과 네임 스페이스 선언을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f77-107">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="28f77-108">**\<section>** 및의 경우 **\<configSections>\*\*\*\*\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="28f77-108">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="28f77-109">구성 섹션 선언을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f77-109">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="28f77-110">**\<sectionGroup>** 에 대 한 **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="28f77-110">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="28f77-111">구성 섹션에 대 한 네임 스페이스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f77-111">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="28f77-112">구현 되지 않은 요소</span><span class="sxs-lookup"><span data-stu-id="28f77-112">Unimplemented elements</span></span>

<span data-ttu-id="28f77-113">다음 요소는 영향을 주지 않으며 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28f77-113">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
