---
description: '다음에 대해 자세히 알아보세요. BC30145: 어셈블리를 내보낼 수 없습니다. <error message>'
title: 어셈블리를 생성할 수 없습니다. <error message>
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 015ab6e1d186495d72bddd65678ab15088c0f1b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674885"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="fceaa-103">BC30145: 어셈블리를 내보낼 수 없습니다. \<error message></span><span class="sxs-lookup"><span data-stu-id="fceaa-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="fceaa-104">Visual Basic 컴파일러는 어셈블리 링커 *Al.exe*(Alink 라고도 함)를 호출 하 여 매니페스트를 사용 하 여 어셈블리를 생성 하 고, 링커가 어셈블리 만들기의 내보내기 단계에서 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="fceaa-105">**오류 ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="fceaa-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fceaa-106">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="fceaa-106">To correct this error</span></span>

1. <span data-ttu-id="fceaa-107">따옴표 붙은 오류 메시지를 검사 하 고 자세한 설명과 조언을 보려면 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fceaa-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="fceaa-108">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 또는 [Sn.exe (강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md)중 하나를 사용 하 여 어셈블리에 수동으로 서명 하세요.</span><span class="sxs-lookup"><span data-stu-id="fceaa-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="fceaa-109">오류가 계속 발생하면 해당 상황에 대한 정보를 수집하여 Microsoft 기술 지원 서비스에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="fceaa-110">어셈블리에 수동으로 서명하려면</span><span class="sxs-lookup"><span data-stu-id="fceaa-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="fceaa-111">[Sn.exe (강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md))를 사용 하 여 공개/개인 키 쌍 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="fceaa-112">이 파일의 확장명은 *.snk* 입니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="fceaa-113">프로젝트에서 오류를 생성하는 COM 참조를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="fceaa-114">[Visual Studio에 대 한 개발자 명령 프롬프트](../../../framework/tools/developer-command-prompt-for-vs.md)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-114">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="fceaa-115">Windows 10에서 작업 표시줄의 검색 상자에 **개발자 명령 프롬프트** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-115">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="fceaa-116">그런 다음 결과 목록에서 **VS 2017에 대 한 개발자 명령 프롬프트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-116">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="fceaa-117">어셈블리 래퍼를 저장 하려는 디렉터리로 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-117">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="fceaa-118">다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-118">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="fceaa-119">입력할 수 있는 실제 명령의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-119">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="fceaa-120">경로 또는 파일에 공백이 있는 경우 큰따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-120">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="fceaa-121">Visual Studio에서 방금 만든 파일에 .NET 어셈블리 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fceaa-121">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="fceaa-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fceaa-122">See also</span></span>

- [<span data-ttu-id="fceaa-123">Al.exe</span><span class="sxs-lookup"><span data-stu-id="fceaa-123">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="fceaa-124">Sn.exe(강력한 이름 도구)</span><span class="sxs-lookup"><span data-stu-id="fceaa-124">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="fceaa-125">방법: 퍼블릭/프라이빗 키 쌍 만들기</span><span class="sxs-lookup"><span data-stu-id="fceaa-125">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="fceaa-126">의견 보내기</span><span class="sxs-lookup"><span data-stu-id="fceaa-126">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
