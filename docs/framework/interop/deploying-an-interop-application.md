---
title: Interop 애플리케이션 배포
description: 일반적으로 .NET 클라이언트 어셈블리, 고유한 COM 형식 라이브러리의 interop 어셈블리, 등록된 COM 구성 요소를 포함하는 interop 애플리케이션을 배포합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
ms.openlocfilehash: 2a8c94ac482bc16cb373fc694c4610ad42e8f631
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267093"
---
# <a name="deploying-an-interop-application"></a><span data-ttu-id="4ae36-103">Interop 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="4ae36-103">Deploying an Interop Application</span></span>

<span data-ttu-id="4ae36-104">Interop 애플리케이션에는 일반적으로 .NET 클라이언트 어셈블리, 고유한 COM 형식 라이브러리를 나타내는 하나 이상의 interop 어셈블리 및 하나 이상의 등록된 COM 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-104">An interop application typically includes a .NET client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span> <span data-ttu-id="4ae36-105">Visual Studio 및 Windows SDK에서는 [형식 라이브러리를 어셈블리로 가져오기](importing-a-type-library-as-an-assembly.md)에 설명된 대로 형식 라이브러리를 interop 어셈블리로 가져오고 변환하는 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-105">Visual Studio and the Windows SDK provide tools to import and convert a type library to an interop assembly, as discussed in [Importing a Type Library as an Assembly](importing-a-type-library-as-an-assembly.md).</span></span> <span data-ttu-id="4ae36-106">Interop 애플리케이션을 배포하는 두 가지 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-106">There are two ways to deploy an interop application:</span></span>  
  
- <span data-ttu-id="4ae36-107">포함된 interop 형식 사용: .NET Framework 4부터 interop 어셈블리의 형식 정보를 실행 파일에 포함하도록 컴파일러에 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-107">By using embedded interop types: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="4ae36-108">컴파일러는 애플리케이션에서 사용하는 형식 정보만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-108">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="4ae36-109">Interop 어셈블리를 애플리케이션에 배포할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-109">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="4ae36-110">이것이 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-110">This is the recommended technique.</span></span>  
  
- <span data-ttu-id="4ae36-111">Interop 어셈블리 배포: interop 어셈블리에 대한 표준 참조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-111">By deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="4ae36-112">이 경우 interop 어셈블리를 애플리케이션에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-112">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="4ae36-113">이 방법을 적용하는데 전용 COM 구성 요소를 사용하지 않을 경우 관리 코드에 통합하려는 COM 구성 요소의 작성자가 게시한 PIA(주 interop 어셈블리)를 항상 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae36-113">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="4ae36-114">주 interop 어셈블리를 생성 및 사용하는 방법에 대한 자세한 내용은 [주 Interop 어셈블리](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae36-114">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4ae36-115">포함된 interop 형식을 사용할 경우 배포는 간단하고 직관적입니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-115">If you use embedded interop types, deployment is simple and straightforward.</span></span> <span data-ttu-id="4ae36-116">특별히 수행할 작업이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-116">There is nothing special you need to do.</span></span> <span data-ttu-id="4ae36-117">이 문서의 나머지 부분에서는 애플리케이션에 interop 어셈블리를 배포하기 위한 시나리오를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-117">The rest of this article describes the scenarios for deploying interop assemblies with your application.</span></span>  
  
## <a name="deploying-interop-assemblies"></a><span data-ttu-id="4ae36-118">Interop 어셈블리 배포</span><span class="sxs-lookup"><span data-stu-id="4ae36-118">Deploying Interop Assemblies</span></span>  

 <span data-ttu-id="4ae36-119">어셈블리는 강력한 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-119">Assemblies can have strong names.</span></span> <span data-ttu-id="4ae36-120">강력한 이름의 어셈블리에는 고유한 ID를 제공하는 게시자의 공개 키가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-120">A strong-named assembly includes the publisher's public key, which provides a unique identity.</span></span> <span data-ttu-id="4ae36-121">[형식 라이브러리 가져오기(Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)에서 생성되는 어셈블리는 게시자가 **/keyfile** 옵션을 사용하여 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-121">Assemblies that are produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) can be signed by the publisher by using the **/keyfile** option.</span></span> <span data-ttu-id="4ae36-122">서명된 어셈블리를 전역 어셈블리 캐시에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-122">You can install signed assemblies into the global assembly cache.</span></span> <span data-ttu-id="4ae36-123">서명되지 않은 어셈블리는 사용자 컴퓨터에 프라이빗 어셈블리로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-123">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
### <a name="private-assemblies"></a><span data-ttu-id="4ae36-124">프라이빗 어셈블리</span><span class="sxs-lookup"><span data-stu-id="4ae36-124">Private Assemblies</span></span>  

 <span data-ttu-id="4ae36-125">전용으로 사용할 어셈블리를 설치하려면 애플리케이션 실행 파일과 가져온 COM 형식을 포함하는 interop 어셈블리가 둘 다 동일한 디렉터리 구조에 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-125">To install an assembly to be used privately, both the application executable and the interop assembly that contains imported COM types must be installed in the same directory structure.</span></span> <span data-ttu-id="4ae36-126">다음 그림에서는 개별 애플리케이션 디렉터리에 있는 Client1.exe 및 Client2.exe에서 전용으로 사용할 서명되지 않은 interop 어셈블리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-126">The following illustration shows an unsigned interop assembly to be used privately by Client1.exe and Client2.exe, which reside in separate application directories.</span></span> <span data-ttu-id="4ae36-127">이 예제에서 LOANLib.dll이라는 interop 어셈블리는 두 번 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-127">The interop assembly, which is called LOANLib.dll in this example, is installed twice.</span></span>  
  
 <span data-ttu-id="4ae36-128">![디렉터리 구조 및 Windows 레지스트리](./media/deploying-an-interop-application/com-private-deployment.gif "전용 배포에 대한 디렉터리 구조 및 레지스트리 항목")</span><span class="sxs-lookup"><span data-stu-id="4ae36-128">![Directory structure and Windows registry](./media/deploying-an-interop-application/com-private-deployment.gif "Directory structure and registry entries for a private deployment")</span></span>  
  
 <span data-ttu-id="4ae36-129">애플리케이션과 연결된 모든 COM 구성 요소는 Windows 레지스트리에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-129">All COM components associated with the application must be installed in the Windows registry.</span></span> <span data-ttu-id="4ae36-130">그림의 Client1.exe 및 Client2.exe가 서로 다른 컴퓨터에 설치된 경우에는 두 컴퓨터에 모두 COM 구성 요소를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-130">If Client1.exe and Client2.exe in the illustration are installed on different computers, you must register the COM components on both computers.</span></span>  
  
### <a name="shared-assemblies"></a><span data-ttu-id="4ae36-131">공유 어셈블리</span><span class="sxs-lookup"><span data-stu-id="4ae36-131">Shared Assemblies</span></span>  

 <span data-ttu-id="4ae36-132">여러 애플리케이션에서 공유되는 어셈블리는 전역 어셈블리 캐시라는 중앙 집중식 리포지토리에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-132">Assemblies that are shared by multiple applications should be installed in a centralized repository called the global assembly cache.</span></span> <span data-ttu-id="4ae36-133">.NET 클라이언트는 전역 어셈블리 캐시에서 시그니처 및 설치된 interop 어셈블리의 동일한 복사본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ae36-133">.NET clients can access the same copy of the interop assembly, which is signed and installed in the global assembly cache.</span></span> <span data-ttu-id="4ae36-134">주 interop 어셈블리를 생성 및 사용하는 방법에 대한 자세한 내용은 [주 Interop 어셈블리](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ae36-134">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae36-135">참조</span><span class="sxs-lookup"><span data-stu-id="4ae36-135">See also</span></span>

- [<span data-ttu-id="4ae36-136">.NET Framework에 COM 구성 요소 노출</span><span class="sxs-lookup"><span data-stu-id="4ae36-136">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="4ae36-137">형식 라이브러리를 어셈블리로 가져오기</span><span class="sxs-lookup"><span data-stu-id="4ae36-137">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- <span data-ttu-id="4ae36-138">[관리 코드에서 COM 형식 사용](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4ae36-138">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="4ae36-139">Interop 프로젝트 컴파일</span><span class="sxs-lookup"><span data-stu-id="4ae36-139">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
