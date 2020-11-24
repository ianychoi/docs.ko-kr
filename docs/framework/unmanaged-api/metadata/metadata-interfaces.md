---
title: 메타데이터 인터페이스
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 5d9b48df740668797a7c901219401e9ea304a8f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672883"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="f7daf-102">메타데이터 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-102">Metadata Interfaces</span></span>

<span data-ttu-id="f7daf-103">이 섹션에서는 .NET Framework 형식, 메서드, 필드 등이 노출하는 메타데이터에 대한 액세스를 제공하는 관리되지 않는 인터페이스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7daf-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f7daf-104">In This Section</span></span>  

 [<span data-ttu-id="f7daf-105">ICeeGen 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-105">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="f7daf-106">동적 코드 컴파일에 대한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="f7daf-107">IHostFilter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-107">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="f7daf-108">처리할 메타데이터 토큰을 표시하기 위한 런타임 호스트에 대한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="f7daf-109">IMapToken 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-109">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="f7daf-110">가져온 메타데이터 서명과 내보낸 메타데이터 서명 간 매핑 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="f7daf-111">IMetaDataAssemblyEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-111">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="f7daf-112">CLR(공용 언어 런타임)에서 리소스를 확인하고 소비하는 데 사용되는 자체 설명 모델을 지원하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="f7daf-113">IMetaDataAssemblyImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="f7daf-114">어셈블리 매니페스트에 액세스하여 이를 검사하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="f7daf-115">IMetaDataConverter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="f7daf-116">형식 라이브러리를 메타데이터 서명에 매핑하고 서로 변환하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="f7daf-117">IMetaDataDispenser 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-117">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="f7daf-118">`IMetaDataDispenser`는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="f7daf-119">대신 `IMetaDataDispenserEx`를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f7daf-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="f7daf-120">IMetaDataDispenserEx 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="f7daf-121">메타데이터를 만들거나 수정할 메모리 영역을 매핑하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="f7daf-122">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="f7daf-123">현재 정의된 범위에서 어셈블리에 대한 메타데이터를 만들고 수정 및 저장하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="f7daf-124">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="f7daf-125"><xref:System.Type?displayProperty=nameWithType> 형식 매개 변수가 있는 메서드와 생성자의 메타데이터 서명을 정의 및 수정하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="f7daf-126">IMetaDataError 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-126">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="f7daf-127">어셈블리에 대한 메타데이터 서명을 확인하는 동안 오류를 보고하는 콜백 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="f7daf-128">IMetaDataFilter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-128">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="f7daf-129">이미 수행된 반복 작업을 방지하려고 메타데이터 토큰을 표시 및 필터링하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="f7daf-130">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="f7daf-131">다른 어셈블리에서 형식을 가져오고 조작하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="f7daf-132">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="f7daf-133">제네릭 형식 작업 기능을 제공하도록 `IMetaDataImport`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="f7daf-134">IMetaDataInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-134">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="f7daf-135">디스크에 있는 파일에서 메모리로의 메타데이터 매핑에 대한 정보를 가져오는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="f7daf-136">IMetaDataTables 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-136">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="f7daf-137">테이블에서 메타데이터 정보를 스토리지 및 검색하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="f7daf-138">IMetaDataTables2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-138">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="f7daf-139">메타데이터 스트림 작업을 수행하는 메서드를 포함하도록 `IMetaDataTables`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="f7daf-140">IMetaDataValidate 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7daf-140">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="f7daf-141">메타데이터 서명의 유효성을 검사하는 데 사용할 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7daf-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7daf-142">관련 단원</span><span class="sxs-lookup"><span data-stu-id="f7daf-142">Related Sections</span></span>  

 [<span data-ttu-id="f7daf-143">메타데이터 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="f7daf-143">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="f7daf-144">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="f7daf-144">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="f7daf-145">메타데이터 구조체</span><span class="sxs-lookup"><span data-stu-id="f7daf-145">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="f7daf-146">메타데이터 공용 구조체</span><span class="sxs-lookup"><span data-stu-id="f7daf-146">Metadata Unions</span></span>](metadata-unions.md)
