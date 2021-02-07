---
description: '자세한 정보: 방법: EdmGen.exe를 사용 하 여 Object-Layer 코드 생성'
title: '방법: EdmGen.exe를 사용하여 개체 계층 코드 생성'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1c1f614247f10c8819709b9494fb1ec04271b634
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697467"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="c3a83-103">방법: EdmGen.exe를 사용하여 개체 계층 코드 생성</span><span class="sxs-lookup"><span data-stu-id="c3a83-103">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>

<span data-ttu-id="c3a83-104">이 항목에서는 [EDM 생성기 (EdmGen.exe)](edm-generator-edmgen-exe.md) 도구를 사용 하 여 csdl 파일을 기반으로 개체 계층 코드를 생성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-104">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="c3a83-105">EdmGen.exe를 사용하여 Visual Basic 프로젝트용 School 모델의 개체 계층 코드를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="c3a83-105">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="c3a83-106">School 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-106">Create the School database.</span></span> <span data-ttu-id="c3a83-107">자세한 내용은 [School 샘플 데이터베이스 만들기](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a83-107">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c3a83-108">School 모델을 생성하거나 School.csdl 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-108">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="c3a83-109">자세한 내용은 [방법: EdmGen.exe를 사용 하 여 모델 및 매핑 파일 생성](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a83-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="c3a83-110">명령 프롬프트에서 줄 바꿈 없이 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="c3a83-111">EdmGen.exe를 사용하여 C# 프로젝트용 School 모델의 개체 계층 코드를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="c3a83-111">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="c3a83-112">School 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-112">Create the School database.</span></span> <span data-ttu-id="c3a83-113">자세한 내용은 [School 샘플 데이터베이스 만들기](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a83-113">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c3a83-114">School 모델을 생성하거나 School.csdl 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-114">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="c3a83-115">자세한 내용은 [방법: EdmGen.exe를 사용 하 여 모델 및 매핑 파일 생성](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a83-115">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="c3a83-116">명령 프롬프트에서 줄 바꿈 없이 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a83-116">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c3a83-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3a83-117">See also</span></span>

- [<span data-ttu-id="c3a83-118">모델링 및 매핑</span><span class="sxs-lookup"><span data-stu-id="c3a83-118">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="c3a83-119">[방법: 수동으로 Entity Framework 프로젝트 구성](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c3a83-119">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="c3a83-120">[ADO.NET 엔터티 데이터 모델 도구](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c3a83-120">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="c3a83-121">[방법: 뷰를 미리 생성하여 쿼리 성능 향상](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c3a83-121">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="c3a83-122">방법: EdmGen.exe를 사용하여 모델 및 매핑 파일 생성</span><span class="sxs-lookup"><span data-stu-id="c3a83-122">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
