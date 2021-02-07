---
description: '자세한 정보: 어셈블리 (Visual Basic)'
title: 어셈블리
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 60b8ce4ed2b8b5cb7deeabb702c33d1e561d765f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701185"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="589e7-103">Assembly(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="589e7-103">Assembly (Visual Basic)</span></span>

<span data-ttu-id="589e7-104">소스 파일의 시작 부분에 있는 특성이 전체 어셈블리에 적용 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="589e7-104">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="589e7-105">설명</span><span class="sxs-lookup"><span data-stu-id="589e7-105">Remarks</span></span>  

 <span data-ttu-id="589e7-106">많은 특성은 클래스 또는 속성과 같은 개별 프로그래밍 요소와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="589e7-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="589e7-107">꺾쇠 괄호 () 내에서 선언 문에 직접 특성 블록을 연결 하 여 이러한 특성을 적용 `< >` 합니다.</span><span class="sxs-lookup"><span data-stu-id="589e7-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="589e7-108">특성이 다음 요소 뿐만 아니라 전체 어셈블리에만 관련 되는 경우 특성 블록을 소스 파일의 시작 부분에 놓고 키워드를 사용 하 여 특성을 식별 합니다 `Assembly` .</span><span class="sxs-lookup"><span data-stu-id="589e7-108">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="589e7-109">현재 어셈블리 모듈에 적용 되는 경우 [module](module-keyword.md) 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="589e7-109">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="589e7-110">AssemblyInfo 파일의 어셈블리에 특성을 적용할 수도 있습니다 .이 경우 기본 소스 코드 파일에서 특성 블록을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="589e7-110">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589e7-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="589e7-111">See also</span></span>

- [<span data-ttu-id="589e7-112">모듈 \<keyword></span><span class="sxs-lookup"><span data-stu-id="589e7-112">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="589e7-113">특성 개요</span><span class="sxs-lookup"><span data-stu-id="589e7-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
