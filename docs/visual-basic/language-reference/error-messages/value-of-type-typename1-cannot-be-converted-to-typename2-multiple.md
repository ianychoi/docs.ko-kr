---
description: "자세한 정보: BC30961: ' ' 형식의 값 <typename1> 을 ' ' (으)로 변환할 수 없습니다 <typename2> (여러 파일 참조)."
title: "'<typename1>' 형식의 값을 '<typename2>'(으)로 변환할 수 없습니다.(여러 파일 참조)"
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 77f8f3c500f9f395d3998261a218175e49f0f52b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640864"
---
# <a name="bc30961-value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="2d436-103">BC30961: ' ' 형식의 값 \<typename1> 을 ' ' (으)로 변환할 수 없습니다 \<typename2> (여러 파일 참조).</span><span class="sxs-lookup"><span data-stu-id="2d436-103">BC30961: Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="2d436-104">' ' 형식의 값 \<typename1> 을 ' ' (으)로 변환할 수 없습니다 \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="2d436-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="2d436-105">' ' 프로젝트의 ' '에 대 한 파일 참조와 ' ' 프로젝트의 ' '에 대 한 파일 참조를 혼합 했기 때문에 형식이 일치 하지 않을 수 있습니다 \<filepath1> \<projectname1> \<filepath2> \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="2d436-105">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="2d436-106">두 어셈블리가 동일하면 동일한 대상을 참조하도록 두 참조를 바꿔 보세요.</span><span class="sxs-lookup"><span data-stu-id="2d436-106">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>

 <span data-ttu-id="2d436-107">프로젝트에서 어셈블리에 대 한 파일 참조를 두 개 이상 만드는 경우 컴파일러는 한 형식을 다른 형식으로 변환할 수 있음을 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-107">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="2d436-108">각 파일 참조는 프로젝트의 출력 파일에 대 한 파일 경로와 이름을 지정 합니다 (일반적으로 DLL 파일).</span><span class="sxs-lookup"><span data-stu-id="2d436-108">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="2d436-109">컴파일러가 출력 파일을 동일한 소스에서 제공 하거나 동일한 어셈블리의 동일한 버전을 나타낸다는 것을 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-109">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="2d436-110">따라서 다른 참조의 형식이 동일한 형식이 나 다른 참조로 변환 될 수 있음을 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-110">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>

 <span data-ttu-id="2d436-111">참조 된 어셈블리의 어셈블리 id가 동일 하다는 것을 알고 있는 경우 단일 파일 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-111">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="2d436-112">*어셈블리 id* 에는 어셈블리 이름, 버전, 공개 키 (있는 경우) 및 문화권이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-112">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="2d436-113">이 정보는 어셈블리를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-113">This information uniquely identifies the assembly.</span></span>

 <span data-ttu-id="2d436-114">**오류 ID:** BC30961</span><span class="sxs-lookup"><span data-stu-id="2d436-114">**Error ID:** BC30961</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2d436-115">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="2d436-115">To correct this error</span></span>

- <span data-ttu-id="2d436-116">참조 된 어셈블리의 어셈블리 id가 같은 경우 파일 참조 중 하나를 제거 하거나 바꿔서 파일 참조가 하나만 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-116">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>

- <span data-ttu-id="2d436-117">참조 된 어셈블리의 어셈블리 id가 같지 않은 경우 한 형식에서 다른 형식으로 변환 하려고 시도 하지 않도록 코드를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d436-117">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d436-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d436-118">See also</span></span>

- [<span data-ttu-id="2d436-119">Visual Basic의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="2d436-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="2d436-120">프로젝트의 참조 관리</span><span class="sxs-lookup"><span data-stu-id="2d436-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
