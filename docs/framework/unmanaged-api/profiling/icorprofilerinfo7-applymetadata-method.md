---
description: '자세히 알아보기: ICorProfilerInfo7:: ApplyMetaData 메서드'
title: 'ICorProfilerInfo7:: ApplyMetaData 메서드'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 3a4554357ede85d936e8bf9c87c6b9c096dab188
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737131"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="cb6ce-103">ICorProfilerInfo7:: ApplyMetaData 메서드</span><span class="sxs-lookup"><span data-stu-id="cb6ce-103">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="cb6ce-104">[.NET Framework 4.6.1 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="cb6ce-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="cb6ce-105">메서드에 의해 새로 정의 된 메타 데이터를 `IMetadataEmit::Define*` 지정 된 모듈에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-105">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6ce-106">구문</span><span class="sxs-lookup"><span data-stu-id="cb6ce-106">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb6ce-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cb6ce-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="cb6ce-108">진행 메타 데이터가 변경 된 모듈의 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-108">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb6ce-109">설명</span><span class="sxs-lookup"><span data-stu-id="cb6ce-109">Remarks</span></span>  

 <span data-ttu-id="cb6ce-110">[Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) 콜백을 수행한 후 메타 데이터를 변경 하는 경우 새 메타 데이터를 사용 하기 전에이 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-110">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="cb6ce-111">`ApplyMetaData` 에서는 다음 유형의 메타 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-111">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="cb6ce-112">`AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)를 호출 하 여 만드는 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-112">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="cb6ce-113">메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-113">method.</span></span>  
  
- <span data-ttu-id="cb6ce-114">`TypeRef`[IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) 메서드를 호출 하 여 만드는 레코드.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-114">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="cb6ce-115">`TypeSpec` 레코드는 [IMetaDataEmit:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) 메서드를 호출 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-115">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="cb6ce-116">`MemberRef`[IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md) 메서드를 호출 하 여 만드는 레코드.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-116">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="cb6ce-117">`MemberSpec`[IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) 메서드를 호출 하 여 만드는 레코드.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-117">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="cb6ce-118">`UserString`[IMetaDataEmit::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) 메서드를 호출 하 여 만드는 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-118">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="cb6ce-119">.NET Core 3.0부터는 `ApplyMetaData` 다음 유형도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-119">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="cb6ce-120">`TypeDef`[IMetaDataEmit::D Efin def](../metadata/imetadataemit-definetypedef-method.md) 메서드를 호출 하 여 만드는 레코드.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-120">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="cb6ce-121">`MethodDef`[IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md) 메서드를 호출 하 여 만드는 레코드.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-121">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="cb6ce-122">그러나 기존 형식에 가상 메서드를 추가 하는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-122">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="cb6ce-123">가상 메서드는 [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) 콜백 전에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-123">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb6ce-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cb6ce-124">Requirements</span></span>  

 <span data-ttu-id="cb6ce-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6ce-126">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb6ce-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb6ce-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb6ce-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb6ce-128">**.NET Framework 버전:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6ce-128">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6ce-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb6ce-129">See also</span></span>

- [<span data-ttu-id="cb6ce-130">ICorProfilerInfo7 인터페이스</span><span class="sxs-lookup"><span data-stu-id="cb6ce-130">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
