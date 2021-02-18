---
description: '자세한 정보: @(지시 파일 지정)(Visual Basic)'
title: '@(지시 파일 지정)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 7a28be0d0bf6da177d9cfe85ecdb40eccf8a339f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473916"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="b541e-103">@(지시 파일 지정)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b541e-103">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="b541e-104">컴파일러 옵션과 컴파일할 소스 코드 파일이 포함된 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-104">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="b541e-105">구문</span><span class="sxs-lookup"><span data-stu-id="b541e-105">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="b541e-106">인수</span><span class="sxs-lookup"><span data-stu-id="b541e-106">Arguments</span></span>

`response_file`  
<span data-ttu-id="b541e-107">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="b541e-107">Required.</span></span> <span data-ttu-id="b541e-108">컴파일러 옵션이나 컴파일할 소스 코드 파일이 나열된 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-108">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="b541e-109">공백이 있으면 파일 이름을 따옴표(" ")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-109">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="b541e-110">설명</span><span class="sxs-lookup"><span data-stu-id="b541e-110">Remarks</span></span>

<span data-ttu-id="b541e-111">컴파일러는 지시 파일에 지정된 컴파일러 옵션 및 소스 코드 파일을 명령줄에 지정된 것처럼 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-111">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="b541e-112">컴파일에 지시 파일을 둘 이상 지정하려면 다음과 같이 여러 지시 파일 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-112">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="b541e-113">지시 파일에서 여러 컴파일러 옵션과 소스 코드 파일이 한 줄에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-113">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="b541e-114">단일 컴파일러 옵션 사양은 한 줄에 표시되어야 합니다(여러 줄에 걸쳐 있을 수 없음).</span><span class="sxs-lookup"><span data-stu-id="b541e-114">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="b541e-115">지시 파일은 `#` 기호로 시작하는 주석을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-115">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="b541e-116">명령줄에 지정된 옵션을 하나 이상의 지시 파일에 지정된 옵션과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-116">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="b541e-117">명령 옵션이 발견되면 컴파일러에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-117">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="b541e-118">따라서, 명령줄 인수는 지시 파일에서 이전에 나열된 옵션을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-118">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="b541e-119">반대로 지시 파일의 옵션은 명령줄 또는 다른 지시 파일에서 이전에 나열된 옵션을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-119">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="b541e-120">Visual Basic에서는 Vbc.exe 파일과 동일한 디렉터리에 있는 Vbc.rsp 파일을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-120">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="b541e-121">Vbc.rsp 파일은 `-noconfig` 옵션을 사용하지 않는 한 기본적으로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-121">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="b541e-122">자세한 내용은 [-noconfig](noconfig.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b541e-122">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b541e-123">Visual Studio 개발 환경 내에서는 `@` 옵션을 사용할 수 없습니다. 명령줄에서 컴파일하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-123">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="b541e-124">예제</span><span class="sxs-lookup"><span data-stu-id="b541e-124">Example</span></span>

<span data-ttu-id="b541e-125">다음 줄은 샘플 지시 파일에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-125">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="b541e-126">예제</span><span class="sxs-lookup"><span data-stu-id="b541e-126">Example</span></span>

<span data-ttu-id="b541e-127">다음 예제에서는 `File1.rsp`이라는 지시 파일에 `@` 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b541e-127">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="b541e-128">참조</span><span class="sxs-lookup"><span data-stu-id="b541e-128">See also</span></span>

- [<span data-ttu-id="b541e-129">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="b541e-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b541e-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="b541e-130">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="b541e-131">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="b541e-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
