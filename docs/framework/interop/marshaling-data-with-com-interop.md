---
title: COM Interop를 사용하여 데이터 마샬링
description: COM interop을 사용한 데이터 마샬링에 대해 설명하는 문서를 읽습니다. Tlbimp.exe 및 Tlbexp.exe 도구는 COM 형식 라이브러리와 interop 어셈블리 간을 변환합니다.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: bcbd2c50fcbd9af3f2eead57ac2e26f8db0c6ad6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275946"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="a9bf7-104">COM Interop를 사용하여 데이터 마샬링</span><span class="sxs-lookup"><span data-stu-id="a9bf7-104">Marshaling Data with COM Interop</span></span>

<span data-ttu-id="a9bf7-105">COM interop는 관리 코드에서 COM 개체를 사용하고 관리되는 개체를 COM에 노출하는 기능을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="a9bf7-106">COM과의 데이터 마샬링 지원은 광범위하며 거의 항상 올바른 마샬링 동작을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="a9bf7-107">Windows SDK에는 다음과 같은 COM interop 도구가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="a9bf7-108">[형식 라이브러리 가져오기(Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) - COM 형식 라이브러리를 interop 어셈블리로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="a9bf7-109">이 어셈블리에서 interop 마샬링 서비스는 관리되는 메모리와 관리되지 않는 메모리 간에 데이터 마샬링을 수행하는 래퍼를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="a9bf7-110">[형식 라이브러리 내보내기(Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) - 어셈블리에서 COM 형식 라이브러리를 생성하고 메서드 호출 중 마샬링을 수행하는 래퍼를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="a9bf7-111">다음 섹셕은 마샬러에 추가 형식 정보를 제공할 수 있는(제공해야 하는) 경우 interop 래퍼를 사용자 지정하는 프로세스를 설명하는 항목으로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9bf7-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a9bf7-112">In This Section</span></span>  

<span data-ttu-id="a9bf7-113">[방법: 수동으로 래퍼 만들기](how-to-create-wrappers-manually.md) - 관리형 소스 코드에서 COM 래퍼를 수동으로 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="a9bf7-114">방법: 관리 코드 DCOM을 WCF로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="a9bf7-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="a9bf7-115">보다 안전한 솔루션을 위해 관리되는 DCOM 코드를 WCF로 마이그레이션하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a9bf7-116">관련 단원</span><span class="sxs-lookup"><span data-stu-id="a9bf7-116">Related Sections</span></span>  

 <span data-ttu-id="a9bf7-117">[COM 데이터 형식](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-117">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-118">해당 관리되는 데이터 형식과 관리되지 않는 데이터 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="a9bf7-119">[COM 호출 가능 래퍼 사용자 지정](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-119">[Customizing COM Callable Wrappers](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-120">디자인 타임에 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 특성을 사용하여 데이터 형식을 명시적으로 마샬링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="a9bf7-121">[런타임 호출 가능 래퍼 사용자 지정](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-121">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-122">interop 어셈블리에서 형식의 마샬링 동작을 조정하는 방법 및 COM 형식을 수동으로 조정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="a9bf7-123">[고급 COM 상호 운용성](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-123">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-124">COM 구성 요소를 .NET Framework 애플리케이션으로 통합하는 방법에 대한 추가정보 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="a9bf7-125">[어셈블리와 형식 라이브러리 간 변환 요약](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-125">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-126">어셈블리에서 형식 라이브러리로 내보내기 변환 프로세스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="a9bf7-127">[형식 라이브러리를 어셈블리로 변환 요약](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-127">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-128">형식 라이브러리에서 어셈블리 가져오기 변환 프로세스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="a9bf7-129">[제네릭 형식을 통한 상호 운용](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9bf7-129">[Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="a9bf7-130">COM 상호 운용성을 위해 제네릭 형식을 사용할 때 지원되는 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9bf7-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
