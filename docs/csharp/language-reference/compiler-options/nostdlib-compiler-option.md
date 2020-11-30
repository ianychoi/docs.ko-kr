---
description: -nostdlib(C# 컴파일러 옵션)
title: -nostdlib(C# 컴파일러 옵션)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125100"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="0f828-103">-nostdlib(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="0f828-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="0f828-104">**-nostdlib** 를 사용하면 전체 시스템 네임스페이스를 정의하는 mscorlib.dll을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f828-105">구문</span><span class="sxs-lookup"><span data-stu-id="0f828-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="0f828-106">설명</span><span class="sxs-lookup"><span data-stu-id="0f828-106">Remarks</span></span>

<span data-ttu-id="0f828-107">고유한 시스템 네임스페이스와 개체를 정의하거나 만들려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="0f828-108">**-nostdlib** 를 지정하지 않으면 mscorlib.dll을 프로그램으로 가져옵니다(**-nostdlib-** 지정과 동일함).</span><span class="sxs-lookup"><span data-stu-id="0f828-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="0f828-109">**-nostdlib** 를 지정하는 것은 **-nostdlib+** 를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="0f828-110">Visual Studio에서 이 컴파일러 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0f828-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="0f828-111">다음 지침은 Visual Studio 2015(및 이전 버전)에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="0f828-112">**mscorlib.dll을 참조하지 않음** 빌드 속성은 Visual Studio 최신 버전에 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="0f828-113">프로젝트의 **속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="0f828-114">**빌드** 속성 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="0f828-115">**고급** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="0f828-116">**mscorlib.dll을 참조하지 않음** 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f828-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="0f828-117">프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0f828-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="0f828-118">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f828-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f828-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f828-119">See also</span></span>

- [<span data-ttu-id="0f828-120">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="0f828-120">C# Compiler Options</span></span>](./index.md)
