---
description: '자세한 정보: 인터페이스 디버깅'
title: 디버깅 인터페이스
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717968"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="8f669-103">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8f669-103">Debugging Interfaces</span></span>

<span data-ttu-id="8f669-104">이 단원에서는 CLR(공용 언어 런타임)에서 실행되는 프로그램의 디버깅을 처리하는 관리되지 않는 인터페이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-104">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f669-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8f669-105">In This Section</span></span>  

 <span data-ttu-id="8f669-106">[ICLRDataEnumMemoryRegions 인터페이스](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-106">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="8f669-107">호출자가 지정하는 메모리 영역을 열거하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-107">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="8f669-108">[ICLRDataEnumMemoryRegionsCallback 인터페이스](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-108">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="8f669-109">지정된 메모리 영역을 열거하려고 시도한 결과를 디버거에 보고하는 콜백 메서드를 `EnumMemoryRegions`에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-109">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="8f669-110">[ICLRDataTarget 인터페이스](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-110">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="8f669-111">대상 CLR 프로세스와 상호 작용하기 위한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-111">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="8f669-112">[ICLRDataTarget2 인터페이스](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-112">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="8f669-113">데이터 액세스 서비스 계층에서 대상 프로세스의 가상 메모리 영역을 조작하는 데 사용하는 `ICLRDataTarget`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-113">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="8f669-114">[ICLRDataTarget3 인터페이스](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-114">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="8f669-115">예외 정보에 대 한 액세스를 제공 하는 [ICLRDataTarget2](iclrdatatarget2-interface.md) 의 서브 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-115">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="8f669-116">[ICLRDebugging 인터페이스](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-116">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="8f669-117">디버깅을 위해 모듈을 로드 및 언로드하는 작업을 처리하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-117">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="8f669-118">[ICLRDebuggingLibraryProvider 인터페이스](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-118">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="8f669-119">요청 시 공용 언어 런타임 버전별 디버깅 라이브러리를 찾고 로드 하는 데 사용할 수 있는 라이브러리 공급자 콜백 인터페이스를 가져오는 [ProvideLibrary method](iclrdebugginglibraryprovider-providelibrary-method.md) 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-119">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="8f669-120">[ICLRMetadataLocator 인터페이스](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-120">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="8f669-121">데이터 액세스 서비스 계층에서 대상 프로세스의 어셈블리 메타데이터를 찾는 데 사용되는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-121">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="8f669-122">[ICorDebug 인터페이스](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-122">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="8f669-123">개발자가 CLR 환경에서 애플리케이션을 디버깅하는 데 사용할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-123">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="8f669-124">[ICorDebugAppDomain 인터페이스](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-124">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="8f669-125">애플리케이션 도메인 디버깅에 사용하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-125">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="8f669-126">[ICorDebugAppDomain2 인터페이스](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-126">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="8f669-127">배열, 포인터, 함수 포인터 및 ByRef 형식에 사용할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-127">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="8f669-128">이 인터페이스는 `ICorDebugAppDomain` 인터페이스의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-128">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="8f669-129">[ICorDebugAppDomain3 인터페이스](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-129">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="8f669-130">응용 프로그램 도메인에서 Windows 런타임 형식으로 작업 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-130">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="8f669-131">이 인터페이스는 `ICorDebugAppDomain` 및 `ICorDebugAppDomain2` 인터페이스의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-131">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="8f669-132">[ICorDebugAppDomain4 인터페이스](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-132">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="8f669-133">[ICorDebugAppDomain](icordebugappdomain-interface.md) 인터페이스를 논리적으로 확장 하 여 COM 호출 가능 래퍼에서 관리 되는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-133">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="8f669-134">[ICorDebugAppDomainEnum 인터페이스](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-134">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-135">열거형의 다음 위치에서 시작하여 지정된 수만큼 `ICorDebugAppDomain` 값을 반환하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-135">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="8f669-136">[ICorDebugArrayValue 인터페이스](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-136">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-137">1차원 배열이나 다차원 배열을 나타내는 `ICorDebugHeapValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-137">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="8f669-138">[ICorDebugAssembly 인터페이스](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-138">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="8f669-139">어셈블리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-139">Represents an assembly.</span></span>  
  
 <span data-ttu-id="8f669-140">[ICorDebugAssembly2 인터페이스](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-140">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="8f669-141">어셈블리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-141">Represents an assembly.</span></span> <span data-ttu-id="8f669-142">이 인터페이스는 `ICorDebugAssembly` 인터페이스의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-142">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="8f669-143">[ICorDebugAssembly3 인터페이스](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-143">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="8f669-144">[ICorDebugAssembly](icordebugassembly-interface.md) 인터페이스를 논리적으로 확장 하 여 컨테이너 어셈블리 및 포함 된 어셈블리에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-144">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="8f669-145">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-145">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-146">[ICorDebugAssemblyEnum 인터페이스](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-146">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-147">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugAssembly` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-147">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="8f669-148">[ICorDebugBlockingObjectEnum 인터페이스](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-148">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-149">[CorDebugBlockingObject](cordebugblockingobject-structure.md) 구조체의 목록에 대 한 열거자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-149">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="8f669-150">[ICorDebugBoxValue 인터페이스](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-150">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-151">boxed 값 클래스 개체를 나타내는 `ICorDebugHeapValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-151">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="8f669-152">[ICorDebugBreakpoint 인터페이스](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-152">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="8f669-153">함수의 중단점 또는 값에 대한 조사식 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-153">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="8f669-154">[ICorDebugBreakpointEnum 인터페이스](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-154">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-155">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugBreakpoint` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-155">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="8f669-156">[ICorDebugChain 인터페이스](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-156">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="8f669-157">실제 또는 논리 호출 스택의 세그먼트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-157">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="8f669-158">[ICorDebugChainEnum 인터페이스](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-158">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-159">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugChain` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-159">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="8f669-160">[ICorDebugClass 인터페이스](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-160">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="8f669-161">기본 또는 복합(즉, 사용자 정의) 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-161">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="8f669-162">형식이 제네릭이면 `ICorDebugClass`는 인스턴스화되지 않은 제네릭 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-162">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="8f669-163">[ICorDebugClass2 인터페이스](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-163">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="8f669-164">제네릭 클래스나 <xref:System.Type> 형식의 메서드 매개 변수를 사용하는 클래스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-164">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="8f669-165">이 인터페이스는 `ICorDebugClass`를 확장한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-165">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="8f669-166">[ICorDebugCode 인터페이스](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-166">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="8f669-167">MSIL(Microsoft Intermediate Language) 코드나 네이티브 코드의 세그먼트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-167">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="8f669-168">[ICorDebugCode2 인터페이스](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-168">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="8f669-169">`ICorDebugCode`의 기능을 확장하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-169">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="8f669-170">[ICorDebugCode3 인터페이스](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-170">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="8f669-171">관리 되는 반환 값에 대 한 정보를 제공 하기 위해 [ICorDebugCode](icordebugcode-interface1.md) 및 [ICorDebugCode2](icordebugcode2-interface.md) 를 확장 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-171">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="8f669-172">[ICorDebugCode4 인터페이스](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-172">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="8f669-173">디버거가 함수의 지역 변수 및 인수를 열거할 수 있도록 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-173">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="8f669-174">[ICorDebugCodeEnum 인터페이스](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-174">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-175">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugCode` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-175">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="8f669-176">[ICorDebugComObjectValue 인터페이스](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-176">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-177">캐시된 인터페이스 개체를 검색하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-177">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="8f669-178">[ICorDebugContext 인터페이스](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-178">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="8f669-179">컨텍스트 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-179">Represents a context object.</span></span> <span data-ttu-id="8f669-180">이 인터페이스는 아직 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-180">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="8f669-181">[ICorDebugController 인터페이스](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-181">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="8f669-182"><xref:System.Diagnostics.Process>나 <xref:System.AppDomain> 같이 코드 실행 컨텍스트를 제어할 수 있는 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-182">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="8f669-183">[ICorDebugDataTarget 인터페이스](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-183">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="8f669-184">특정 대상 프로세스에 대한 액세스를 제공하는 콜백 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-184">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="8f669-185">[ICorDebugDataTarget2 인터페이스](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-185">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="8f669-186">[ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스를 논리적으로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-186">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="8f669-187">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-187">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-188">[ICorDebugDataTarget3 인터페이스](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-188">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="8f669-189">[ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스를 논리적으로 확장 하 여 로드 된 모듈에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-189">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="8f669-190">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-190">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-191">[ICorDebugDebugEvent 인터페이스](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-191">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="8f669-192">모든 `ICorDebug` 디버그 이벤트가 파생되는 기본 인터페이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-192">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="8f669-193">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-193">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-194">[ICorDebugEditAndContinueErrorInfo 인터페이스](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-194">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="8f669-195">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-195">Obsolete.</span></span> <span data-ttu-id="8f669-196">이 인터페이스를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8f669-196">Do not use this interface.</span></span>  
  
 <span data-ttu-id="8f669-197">[ICorDebugEditAndContinueSnapshot 인터페이스](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-197">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="8f669-198">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-198">Obsolete.</span></span> <span data-ttu-id="8f669-199">이 인터페이스를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8f669-199">Do not use this interface.</span></span>  
  
 <span data-ttu-id="8f669-200">[ICorDebugEnum 인터페이스](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-200">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="8f669-201">열거자를 디버깅할 수 있는 추상 기본 인터페이스로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-201">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="8f669-202">[ICorDebugErrorInfoEnum 인터페이스](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-202">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-203">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-203">Obsolete.</span></span> <span data-ttu-id="8f669-204">이 인터페이스를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8f669-204">Do not use this interface.</span></span>  
  
 <span data-ttu-id="8f669-205">[ICorDebugEval 인터페이스](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-205">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="8f669-206">디버깅 중인 코드의 컨텍스트 내에서 디버거가 코드를 실행할 수 있도록 하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-206">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="8f669-207">[ICorDebugEval2 인터페이스](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-207">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="8f669-208">제네릭 형식을 지원하도록 `ICorDebugEval`을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-208">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="8f669-209">[ICorDebugExceptionDebugEvent 인터페이스](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-209">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="8f669-210">[ICorDebugDebugEvent](icordebugdebugevent-interface.md) 인터페이스를 확장 하 여 예외 이벤트를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-210">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="8f669-211">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-211">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-212">[ICorDebugExceptionObjectCallStackEnum 인터페이스](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-212">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-213">예외 개체에 포함된 호출 스택 정보에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-213">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="8f669-214">[ICorDebugExceptionObjectValue 인터페이스](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-214">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-215">[ICorDebugObjectValue](icordebugobjectvalue-interface.md) 인터페이스를 확장 하 여 관리 되는 예외 개체의 스택 추적 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-215">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="8f669-216">[ICorDebugFrame 인터페이스](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-216">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="8f669-217">현재 스택의 프레임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-217">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="8f669-218">[ICorDebugFrameEnum 인터페이스](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-218">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-219">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugFrame` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-219">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="8f669-220">[ICorDebugFunction 인터페이스](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-220">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="8f669-221">관리되는 함수 또는 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-221">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="8f669-222">[ICorDebugFunction2 인터페이스](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-222">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="8f669-223">`ICorDebugFunction`의 기능을 논리적으로 확장하여 "내 코드만" 단계별 실행 디버깅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-223">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="8f669-224">[ICorDebugFunction3 인터페이스](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-224">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="8f669-225">[ICorDebugFunction](icordebugfunction-interface1.md) 인터페이스를 논리적으로 확장 하 여 ReJIT 요청에서 코드에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-225">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="8f669-226">[ICorDebugFunctionBreakpoint 인터페이스](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-226">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="8f669-227">함수에서 중단점을 지원하기 위해 `ICorDebugBreakpoint`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-227">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="8f669-228">[ICorDebugGCReferenceEnum 인터페이스](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-228">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-229">가비지 수집되는 개체에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-229">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="8f669-230">[ICorDebugGenericValue 인터페이스](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-230">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-231">모든 값에 적용되는 `ICorDebugValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-231">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="8f669-232">이 인터페이스에서는 값의 Get 및 Set 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-232">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="8f669-233">[ICorDebugGuidToTypeEnum 인터페이스](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-233">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-234">GUID를 매핑하는 개체와 그에 해당하는 `ICorDebugType` 개체에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-234">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="8f669-235">[ICorDebugHandleValue 인터페이스](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-235">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-236">디버거에서 가비지 수집을 위해 핸들을 만든 대상 참조 값을 나타내는 `ICorDebugReferenceValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-236">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="8f669-237">[ICorDebugHeapEnum 인터페이스](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-237">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-238">관리되는 힙의 개체에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-238">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="8f669-239">[ICorDebugHeapSegmentEnum 인터페이스](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-239">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-240">관리되는 힙 메모리 영역에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-240">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="8f669-241">[ICorDebugHeapValue 인터페이스](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-241">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-242">CLR 가비지 수집기에서 수집한 개체를 나타내는 `ICorDebugValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-242">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="8f669-243">[ICorDebugHeapValue2 인터페이스](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-243">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="8f669-244">런타임 핸들에 대한 지원을 제공하는 `ICorDebugHeapValue`의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-244">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="8f669-245">[ICorDebugHeapValue3 인터페이스](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-245">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="8f669-246">개체의 모니터 잠금 속성을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-246">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="8f669-247">[ICorDebugILCode 인터페이스](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-247">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="8f669-248">IL(중간 언어) 코드 세그먼트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-248">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="8f669-249">[ICorDebugILCode2 인터페이스](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-249">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="8f669-250">는 [ICorDebugILCode](icordebugilcode-interface.md) 인터페이스를 논리적으로 확장 하 여 함수의 지역 변수 시그니처에 대 한 토큰을 반환 하는 메서드를 제공 하 고 프로파일러 계측 된 il (중간 언어) 오프셋을 원래 메서드 il 오프셋에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-250">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="8f669-251">[ICorDebugILFrame 인터페이스](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-251">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="8f669-252">MSIL 코드의 스택 프레임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-252">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="8f669-253">[ICorDebugILFrame2 인터페이스](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-253">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="8f669-254">`ICorDebugILFrame`에서 논리적으로 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-254">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="8f669-255">[ICorDebugILFrame3 인터페이스](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-255">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="8f669-256">함수의 반환 값을 캡슐화하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-256">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="8f669-257">[ICorDebugILFrame4 인터페이스](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-257">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="8f669-258">IL(중간 언어) 코드의 스택 프레임에서 로컬 변수 및 코드에 액세스하는 데 사용할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-258">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="8f669-259">디버거가 프로파일러 ReJIT 계측에 추가된 변수와 코드에 액세스할 수 있는지는 매개 변수를 통해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-259">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="8f669-260">[ICorDebugInstanceFieldSymbol 인터페이스](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-260">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="8f669-261">인스턴스 필드에 대한 디버그 기호 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-261">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="8f669-262">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-262">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-263">[ICorDebugInternalFrame 인터페이스](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-263">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="8f669-264">디버거의 프레임 형식을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-264">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="8f669-265">[ICorDebugInternalFrame2 인터페이스](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-265">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="8f669-266">[ICorDebugFrame](icordebugframe-interface.md) 개체와 관련 하 여 스택 주소 및 위치를 포함 하 여 내부 프레임에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-266">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="8f669-267">[ICorDebugLoadedModule 인터페이스](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-267">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="8f669-268">로드된 모듈에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-268">Provides information about a loaded module.</span></span> <span data-ttu-id="8f669-269">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-269">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-270">[ICorDebugManagedCallback 인터페이스](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-270">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="8f669-271">디버거 콜백을 처리하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-271">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="8f669-272">[ICorDebugManagedCallback2 인터페이스](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-272">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="8f669-273">디버거 예외 처리 및 MDA(관리 디버깅 도우미)를 지원하기 위한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-273">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="8f669-274">`ICorDebugManagedCallback2`은 `ICorDebugManagedCallback`에서 논리적으로 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-274">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="8f669-275">[ICorDebugManagedCallback3 인터페이스](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-275">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="8f669-276">활성화된 사용자 지정 디버거 알림이 발생했음을 나타내는 콜백 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-276">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="8f669-277">[ICorDebugMDA 인터페이스](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-277">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="8f669-278">MDA(관리 디버깅 도우미) 메시지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-278">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="8f669-279">[ICorDebugMemoryBuffer 인터페이스](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-279">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="8f669-280">메모리 내 버퍼를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-280">Represents an in-memory buffer.</span></span> <span data-ttu-id="8f669-281">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-281">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-282">[ICorDebugMergedAssemblyRecord 인터페이스](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-282">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="8f669-283">병합된 어셈블리에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-283">Provides information about a merged assembly.</span></span> <span data-ttu-id="8f669-284">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-284">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-285">[ICorDebugMetaDataLocator 인터페이스](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-285">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="8f669-286">디버거에 메타데이터 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-286">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="8f669-287">[ICorDebugModule 인터페이스](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-287">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="8f669-288">실행 파일이나 DLL(동적 연결 라이브러리)인 CLR 모듈을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-288">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="8f669-289">[ICorDebugModule2 인터페이스](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-289">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="8f669-290">`ICorDebugModule`에서 논리적으로 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-290">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="8f669-291">[ICorDebugModule3 인터페이스](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-291">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="8f669-292">동적 모듈에 대한 기호 판독기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-292">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="8f669-293">[ICorDebugModuleBreakpoint 인터페이스](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-293">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="8f669-294">특정 모듈에 액세스할 수 있도록 `ICorDebugBreakpoint`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-294">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="8f669-295">[ICorDebugModuleDebugEvent 인터페이스](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-295">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="8f669-296">모듈 수준 이벤트를 지원 하기 위해 [ICorDebugDebugEvent](icordebugdebugevent-interface.md) 인터페이스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-296">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="8f669-297">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-297">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-298">[ICorDebugModuleEnum 인터페이스](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-298">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-299">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugModule` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-299">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="8f669-300">[ICorDebugMutableDataTarget 인터페이스](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-300">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="8f669-301">[ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스를 확장 하 여 변경 가능한 데이터 대상을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-301">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="8f669-302">[ICorDebugNativeFrame 인터페이스](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-302">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="8f669-303">네이티브 프레임에 사용되는 특수화된 `ICorDebugFrame` 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-303">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="8f669-304">[ICorDebugNativeFrame2 인터페이스](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-304">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="8f669-305">자식 및 부모 프레임 관계를 테스트하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-305">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="8f669-306">[ICorDebugObjectEnum 인터페이스](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-306">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-307">`ICorDebugEnum` 메서드를 구현하고 RVA(Relative Virtual Address)로 개체의 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-307">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="8f669-308">[ICorDebugObjectValue 인터페이스](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-308">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-309">개체가 들어 있는 값을 나타내는 `ICorDebugValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-309">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="8f669-310">[ICorDebugObjectValue2 인터페이스](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-310">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="8f669-311">상속 및 재정의 기능을 지원하도록 `ICorDebugObjectValue`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-311">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="8f669-312">[ICorDebugProcess 인터페이스](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-312">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="8f669-313">관리 코드를 실행하는 프로세스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-313">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="8f669-314">[ICorDebugProcess2 인터페이스](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-314">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="8f669-315">`ICorDebugProcess`에서 논리적으로 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-315">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="8f669-316">[ICorDebugProcess3 인터페이스](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-316">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="8f669-317">사용자 지정 디버거 알림을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-317">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="8f669-318">[ICorDebugProcess4 인터페이스](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-318">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="8f669-319">Out-of-process 실행 제어에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-319">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="8f669-320">[ICorDebugProcess5 인터페이스](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-320">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="8f669-321">관리 되는 힙에 대 한 액세스를 지원 하 고, 관리 되는 개체의 가비지 수집에 대 한 정보를 제공 하 고, 디버거가 응용 프로그램의 로컬 네이티브 이미지 캐시에서 이미지를 로드할지 여부를 결정 하기 위해 [ICorDebugProcess](icordebugprocess-interface.md) 인터페이스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-321">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="8f669-322">[ICorDebugProcess6 인터페이스](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-322">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="8f669-323">는 [ICorDebugProcess](icordebugprocess-interface.md) 인터페이스를 논리적으로 확장 하 여 네이티브 예외 디버그 이벤트에서 인코딩된 관리 되는 디버그 이벤트와 가상 모듈 분할을 디코딩하는 등의 기능을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-323">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="8f669-324">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-324">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-325">[ICorDebugProcess7 인터페이스](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-325">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="8f669-326">대상 프로세스에서 디버거가 메모리 내 메타데이터 업데이트를 처리하도록 구성하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-326">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="8f669-327">[ICorDebugProcess8 인터페이스](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-327">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="8f669-328">[ICorDebugProcess](icordebugprocess-interface.md) 인터페이스를 논리적으로 확장 하 여 특정 형식의 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 예외 콜백을 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-328">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="8f669-329">[ICorDebugProcessEnum 인터페이스](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-329">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-330">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugProcess` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-330">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="8f669-331">[ICorDebugReferenceValue 인터페이스](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-331">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-332">참조 형식을 지원하는 `ICorDebugValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-332">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="8f669-333">[ICorDebugRegisterSet 인터페이스](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-333">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="8f669-334">코드가 실행되고 있는 컴퓨터에서 사용할 수 있는 레지스터 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-334">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="8f669-335">[ICorDebugRegisterSet2 인터페이스](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-335">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="8f669-336">64개 이상의 레지스터가 있는 하드웨어 플랫폼의 `ICorDebugRegisterSet` 기능을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-336">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="8f669-337">[ICorDebugRemote 인터페이스](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-337">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="8f669-338">시작할 수 있거나 원격 대상 프로세스에 관리되는 디버거를 연결할 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-338">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="8f669-339">[ICorDebugRemoteTarget 인터페이스](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-339">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="8f669-340">CLR 환경에서 Silverlight 기반 애플리케이션을 디버깅하는 데 사용할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-340">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="8f669-341">[ICorDebugRuntimeUnwindableFrame 인터페이스](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-341">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="8f669-342">프레임을 해제하는 데 CLR(공용 언어 런타임)을 필요로 하는 관리되지 않는 메서드에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-342">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="8f669-343">[ICorDebugStackWalk 인터페이스](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-343">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="8f669-344">스레드 스택에서 관리되는 메서드나 프레임을 가져오기 위한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-344">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="8f669-345">[ICorDebugStaticFieldSymbol 인터페이스](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-345">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="8f669-346">정적 필드에 대한 디버그 기호 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-346">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="8f669-347">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-347">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-348">[ICorDebugStepper 인터페이스](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-348">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="8f669-349">디버거에서 수행하는 코드 실행 단계를 나타내며, 명령의 실행/완료를 구분하는 식별자로 사용되고, 단계를 취소하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-349">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="8f669-350">[ICorDebugStepper2 인터페이스](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-350">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="8f669-351">JMC(내 코드만) 디버깅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-351">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="8f669-352">[ICorDebugStepperEnum 인터페이스](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-352">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-353">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugStepper` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-353">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="8f669-354">[ICorDebugStringValue 인터페이스](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-354">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-355">문자열 값에 적용되는 `ICorDebugHeapValue`의 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-355">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="8f669-356">[ICorDebugSymbolProvider 인터페이스](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-356">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="8f669-357">디버그 기호 정보를 검색하는 데 사용할 수 있는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-357">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="8f669-358">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-358">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-359">[ICorDebugSymbolProvider2 인터페이스](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-359">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="8f669-360">[ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) 인터페이스를 논리적으로 확장 하 여 추가 디버그 기호 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-360">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="8f669-361">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-361">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-362">[ICorDebugThread 인터페이스](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-362">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="8f669-363">프로세스의 스레드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-363">Represents a thread in a process.</span></span> <span data-ttu-id="8f669-364">`ICorDebugThread` 인스턴스의 수명은 이 인스턴스가 나타내는 스레드의 수명과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-364">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="8f669-365">[ICorDebugThread2 인터페이스](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-365">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="8f669-366">`ICorDebugThread`에서 논리적으로 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-366">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="8f669-367">[ICorDebugThread3 인터페이스](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-367">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="8f669-368">[ICorDebugStackWalk](icordebugstackwalk-interface.md) 및 해당 인터페이스에 대 한 진입점을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-368">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="8f669-369">[ICorDebugThread4 인터페이스](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-369">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="8f669-370">스레드 차단 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-370">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="8f669-371">[ICorDebugThreadEnum 인터페이스](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-371">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="8f669-372">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugThread` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-372">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="8f669-373">[ICorDebugType 인터페이스](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-373">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="8f669-374">기본 또는 복합(즉, 사용자 정의) 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-374">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="8f669-375">형식이 제네릭이면 `ICorDebugType`는 인스턴스화된 제네릭 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-375">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="8f669-376">[ICorDebugType2 인터페이스](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-376">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="8f669-377">[ICorDebugType](icordebugtype-interface.md) 인터페이스를 확장 하 여 기본 형식 또는 복합 (사용자 정의) 형식의 형식 식별자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-377">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="8f669-378">[ICorDebugTypeEnum 인터페이스](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-378">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-379">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugType` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-379">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="8f669-380">[ICorDebugUnmanagedCallback 인터페이스](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-380">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="8f669-381">CLR에 직접적으로 관련되지 않은 네이티브 이벤트에 대한 알림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-381">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="8f669-382">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-382">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="8f669-383">디버깅 중인 프로세스의 읽기 또는 쓰기 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-383">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="8f669-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="8f669-385">`ICorDebugValue`을 지원하기 위해 `ICorDebugType`에서 확장된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-385">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="8f669-386">[ICorDebugValue3 인터페이스](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-386">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="8f669-387">"ICorDebugValue" 및 "ICorDebugValue2" 인터페이스를 확장 하 여 2gb 보다 큰 배열에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-387">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="8f669-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="8f669-389">특정 값에 액세스할 수 있도록 `ICorDebugBreakpoint`를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-389">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="8f669-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-391">`ICorDebugEnum` 메서드를 구현하고 `ICorDebugValue` 배열을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-391">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="8f669-392">[ICorDebugVariableHome 인터페이스](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-392">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="8f669-393">함수의 지역 변수 또는 인수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-393">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="8f669-394">[ICorDebugVariableHomeEnum 인터페이스](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-394">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-395">함수의 지역 변수 및 인수에 대 한 열거자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-395">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="8f669-396">[ICorDebugVariableSymbol 인터페이스](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-396">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="8f669-397">변수에 대한 디버그 기호 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-397">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="8f669-398">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-398">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-399">[ICorDebugVirtualUnwinder 인터페이스](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-399">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="8f669-400">스택 해제에 도움이 되는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-400">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="8f669-401">**.NET 네이티브에서만 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8f669-401">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="8f669-402">[ICorPublish 인터페이스](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-402">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="8f669-403">게시 프로세스에 대한 일반적인 인터페이스로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-403">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="8f669-404">[ICorPublishAppDomain 인터페이스](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-404">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="8f669-405">애플리케이션 도메인을 나타내고 애플리케이션 도메인에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-405">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="8f669-406">[ICorPublishAppDomainEnum 인터페이스](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-406">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-407">프로세스 내에 현재 있는 `ICorPublishAppDomain` 개체의 컬렉션을 이동하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-407">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="8f669-408">[ICorPublishEnum 인터페이스](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-408">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-409">열거자를 게시하기 위한 추상 기본 열거형으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-409">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="8f669-410">[ICorPublishProcess 인터페이스](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-410">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="8f669-411">프로세스에 대한 정보에 액세스하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-411">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="8f669-412">[ICorPublishProcessEnum 인터페이스](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-412">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="8f669-413">`ICorPublishProcess` 개체의 컬렉션을 이동하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-413">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="8f669-414">[ISOSDacInterface 인터페이스](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-414">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="8f669-415">에서 데이터에 액세스 하는 도우미 메서드를 제공 `SOS` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-415">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="8f669-416">[IXCLRDataMethodDefinition 인터페이스](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-416">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="8f669-417">메서드 정의에 대 한 정보를 쿼리 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-417">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="8f669-418">[IXCLRDataMethodInstance 인터페이스](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-418">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="8f669-419">메서드 인스턴스에 대 한 정보를 쿼리 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-419">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="8f669-420">[IXCLRDataModule 인터페이스](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-420">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="8f669-421">로드 된 모듈에 대 한 정보를 쿼리 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-421">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="8f669-422">[IXCLRDataProcess 인터페이스](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-422">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="8f669-423">프로세스에 대 한 정보를 쿼리 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f669-423">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="8f669-424">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="8f669-424">Related Sections</span></span>  

 <span data-ttu-id="8f669-425">[디버깅 Coclass](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-425">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="8f669-426">[디버깅 전역 정적 함수](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-426">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="8f669-427">[디버깅 열거형](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-427">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="8f669-428">[디버깅 구조체](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="8f669-428">[Debugging Structures](debugging-structures.md)</span></span>\
