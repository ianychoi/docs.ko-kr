---
title: 기본 마샬링 동작
description: .NET의 기본 마샬링 동작에 대해 알아봅니다. Interop 마샬링을 사용한 메모리 관리를 살펴보고 클래스, 대리자 및 값 형식에 대한 기본 마샬링을 알아봅니다.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 3e18bb5c4caa43a8e951eed3fc6992ec1b2d2afb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256657"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="00a45-104">기본 마샬링 동작</span><span class="sxs-lookup"><span data-stu-id="00a45-104">Default Marshaling Behavior</span></span>

<span data-ttu-id="00a45-105">Interop 마샬링은 메서드 매개 변수와 연결된 데이터가 관리되는 메모리와 관리되지 않는 메모리 간에 전달될 때 동작하는 방식을 제어하는 규칙에 따라 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-105">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="00a45-106">이러한 기본 제공 규칙은 데이터 형식 변형, 호출 수신자가 전달된 데이터를 변경하고 해당 변경 내용을 호출자에게 반환할 수 있는지 여부 및 마샬러가 성능 최적화를 제공하는 상황과 같은 마샬링 작업을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-106">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="00a45-107">이 섹션에서는 interop 마샬링 서비스의 기본 동작 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-107">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="00a45-108">배열, 부울 형식, char 형식, 대리자, 클래스, 개체, 문자열 및 구조체 마샬링에 대한 자세한 정보를 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-108">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a45-109">제네릭 형식의 마샬링은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-109">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="00a45-110">자세한 내용은 [제네릭 형식을 통한 상호 운용](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00a45-110">For more information see, [Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="00a45-111">Interop 마샬러를 사용한 메모리 관리</span><span class="sxs-lookup"><span data-stu-id="00a45-111">Memory management with the interop marshaler</span></span>  

 <span data-ttu-id="00a45-112">Interop 마샬러는 항상 비관리 코드에 의해 할당된 메모리를 해제하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-112">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="00a45-113">이 동작은 COM 메모리 관리 규칙을 준수하지만 네이티브 C++를 제어하는 규칙과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-113">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="00a45-114">포인터에 대한 메모리를 자동으로 해제하는 플랫폼 호출을 사용하는 경우 네이티브 C++ 동작(메모리 해제 안 함)을 예상하면 혼란이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-114">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="00a45-115">예를 들어 C++ DLL에서 다음 관리되지 않는 메서드를 호출하는 경우 메모리가 자동으로 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-115">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="00a45-116">관리되지 않는 서명</span><span class="sxs-lookup"><span data-stu-id="00a45-116">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="00a45-117">그러나 메서드를 플랫폼 호출 프로토타입으로 정의하고, 각 **BSTR** 형식을 <xref:System.String> 형식으로 바꾼 다음 `MethodOne`을 호출하는 경우 공용 언어 런타임에서 `b`를 해제하려고 두 번 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-117">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="00a45-118">**String** 형식보다 <xref:System.IntPtr> 형식을 사용하여 마샬링 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-118">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="00a45-119">런타임은 항상 **CoTaskMemFree** 메서드를 사용하여 메모리를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-119">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="00a45-120">사용하는 메모리가 **CoTaskMemAlloc** 메서드를 통해 할당되지 않은 경우 **IntPtr** 을 사용하고 적절한 메서드를 통해 수동으로 메모리를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-120">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="00a45-121">마찬가지로, 커널 메모리에 대한 포인터를 반환하는 Kernel32.dll의 **GetCommandLine** 함수를 사용하는 경우와 같이 메모리가 해제되지 않아야 하는 상황에서는 자동 메모리 해제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-121">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="00a45-122">수동으로 메모리를 해제하는 방법에 대한 자세한 내용은 [Buffers 샘플](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00a45-122">For details on manually freeing memory, see the [Buffers Sample](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="00a45-123">클래스에 대한 기본 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-123">Default marshaling for classes</span></span>  

 <span data-ttu-id="00a45-124">클래스는 COM interop에 의해서만 마샬링될 수 있으며 항상 인터페이스로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-124">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="00a45-125">클래스를 마샬링하는 데 사용되는 인터페이스를 클래스 인터페이스라고 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-125">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="00a45-126">선택한 인터페이스로 클래스 인터페이스를 재정의하는 방법에 대한 자세한 내용은 [클래스 인터페이스 소개](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00a45-126">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="00a45-127">COM에 클래스 전달</span><span class="sxs-lookup"><span data-stu-id="00a45-127">Passing Classes to COM</span></span>  

 <span data-ttu-id="00a45-128">관리되는 클래스를 COM에 전달하면 interop 마샬러가 자동으로 클래스를 COM 프록시로 래핑하고 프록시에 의해 생성된 클래스 인터페이스를 COM 메서드 호출에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-128">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="00a45-129">그런 다음 프록시는 클래스 인터페이스에 대한 모든 호출을 관리되는 개체에 다시 위임합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-129">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="00a45-130">또한 프록시는 클래스에 의해 명시적으로 구현되지 않은 다른 인터페이스를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-130">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="00a45-131">프록시는 클래스를 대신하여 **IUnknown** 및 **IDispatch** 와 같은 인터페이스를 자동으로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-131">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="00a45-132">.NET 코드에 클래스 전달</span><span class="sxs-lookup"><span data-stu-id="00a45-132">Passing Classes to .NET Code</span></span>  

 <span data-ttu-id="00a45-133">Coclass는 대개 COM에서 메서드 인수로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-133">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="00a45-134">대신, 일반적으로 기본 인터페이스가 coclass 대신 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-134">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="00a45-135">인터페이스가 관리 코드에 전달되는 경우 interop 마샬러가 인터페이스를 적절한 래퍼로 래핑하고 관리되는 메서드에 래퍼를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-135">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="00a45-136">사용할 래퍼를 결정하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-136">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="00a45-137">COM 개체의 모든 인스턴스에는 개체가 구현하는 인터페이스 수에 관계없이 하나의 고유한 래퍼가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-137">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="00a45-138">예를 들어 서로 다른 인터페이스 5개를 구현하는 단일 COM 개체에는 하나의 래퍼만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-138">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="00a45-139">동일한 래퍼가 5개 인터페이스를 모두 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-139">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="00a45-140">COM 개체 인스턴스를 2개 만들면 래퍼 인스턴스도 2개 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-140">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="00a45-141">래퍼가 전체 수명 동안 동일한 형식을 유지하려면 개체에 의해 노출된 인터페이스가 마샬러를 통해 처음 전달될 때 interop 마샬러가 올바른 래퍼를 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-141">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="00a45-142">마샬러는 개체가 구현하는 인터페이스 중 하나를 확인하여 개체를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-142">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="00a45-143">예를 들어 마샬러는 클래스 래퍼를 사용하여 관리 코드에 전달된 인터페이스를 래핑해야 한다고 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-143">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="00a45-144">인터페이스는 마샬러를 통해 처음 전달될 때 마샬러는 인터페이스가 알려진 개체에서 제공되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-144">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="00a45-145">이 검사는 다음 두 가지 상황에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-145">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="00a45-146">다른 곳에서 COM에 전달된 다른 관리되는 개체에 의해 인터페이스가 구현되는 경우.</span><span class="sxs-lookup"><span data-stu-id="00a45-146">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="00a45-147">마샬러는 관리되는 개체에 의해 노출된 인터페이스를 쉽게 식별할 수 있으며, 구현을 제공하는 관리되는 개체와 인터페이스를 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-147">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="00a45-148">그런 다음 관리되는 개체가 메서드에 전달되며 래퍼는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-148">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="00a45-149">이미 래핑된 개체가 인터페이스를 구현하는 경우.</span><span class="sxs-lookup"><span data-stu-id="00a45-149">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="00a45-150">이러한 경우인지 확인하기 위해 마샬러는 해당 **IUnknown** 인터페이스에 대해 개체를 쿼리하고 반환된 인터페이스를 이미 래핑된 다른 개체의 인터페이스와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-150">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="00a45-151">인터페이스가 다른 래퍼의 인터페이스와 같으면 개체 ID가 동일하고 기존 래퍼가 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-151">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="00a45-152">알려진 개체의 인터페이스가 아닌 경우 마샬러는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-152">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="00a45-153">마샬러가 **IProvideClassInfo2** 인터페이스에 대해 개체를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-153">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="00a45-154">제공되면 마샬러가 **IProvideClassInfo2.GetGUID** 에서 반환된 CLSID를 사용하여 인터페이스를 제공하는 coclass를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-154">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="00a45-155">CLSID를 통해 마샬러는 어셈블리가 이전에 등록된 경우 레지스트리에서 래퍼를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-155">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="00a45-156">마샬러가 **IProvideClassInfo** 인터페이스에 대해 인터페이스를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-156">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="00a45-157">제공되면 마샬러가 **IProvideClassInfo.GetClassinfo** 에서 반환된 **ITypeInfo** 를 사용하여 인터페이스를 노출하는 클래스의 CLSID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-157">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="00a45-158">마샬러는 CLSID를 사용하여 래퍼에 대한 메타데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-158">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="00a45-159">마샬러가 여전히 클래스를 식별할 수 없는 경우 **System.__ComObject** 라는 제네릭 래퍼 클래스로 인터페이스를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-159">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="00a45-160">대리자에 대한 기본 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-160">Default marshaling for delegates</span></span>  

 <span data-ttu-id="00a45-161">관리되는 대리자는 호출 메커니즘에 따라 COM 인터페이스 또는 함수 포인터로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-161">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="00a45-162">플랫폼 호출의 경우 대리자는 기본적으로 관리되지 않는 함수 포인터로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-162">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="00a45-163">COM interop의 경우 대리자는 기본적으로 **_Delegate** 형식의 COM 인터페이스로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-163">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="00a45-164">**_Delegate** 인터페이스는 Mscorlib.tlb 형식 라이브러리에서 정의되며 대리자가 참조하는 메서드를 호출할 수 있게 해주는 <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> 메서드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-164">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="00a45-165">다음 표에서는 관리되는 대리자 데이터 형식에 대한 마샬링 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-165">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="00a45-166"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 특성은 대리자를 마샬링하기 위한 여러 <xref:System.Runtime.InteropServices.UnmanagedType> 열거형 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-166">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="00a45-167">열거형 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-167">Enumeration type</span></span>|<span data-ttu-id="00a45-168">관리되지 않는 형식에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="00a45-168">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="00a45-169">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="00a45-169">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="00a45-170">관리되지 않는 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-170">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="00a45-171">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="00a45-171">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="00a45-172">Mscorlib.tlb에서 정의된 **_Delegate** 형식의 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-172">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="00a45-173">`DelegateTestInterface`의 메서드를 COM 형식 라이브러리로 내보내는 다음 예제 코드를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="00a45-173">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="00a45-174">**ref**(또는 **ByRef**) 키워드로 표시된 대리자만 In/Out 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-174">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="00a45-175">형식 라이브러리 표현</span><span class="sxs-lookup"><span data-stu-id="00a45-175">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="00a45-176">다른 모든 관리되지 않는 함수 포인터를 역참조할 수 있는 것과 마찬가지로 함수 포인터도 역참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-176">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="00a45-177">이 예제에서 두 개의 대리자가 <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>으로 마샬링되면 결과는 `int` 및 `int`에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-177">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="00a45-178">대리자 형식이 마샬링되기 때문에 여기에서 `int`는 void(`void*`)에 대한 포인터를 나타냅니다. 이 항목은 메모리에서 대리자의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-178">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="00a45-179">즉, 여기서 `int`가 함수 포인터의 크기를 나타내므로 이 결과는 32비트 Windows 시스템에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-179">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="00a45-180">비관리 코드에서 보유한 관리되는 대리자에 대한 함수 포인터 참조는 공용 언어 런타임이 관리되는 개체에서 가비지 컬렉션을 수행할 수 없도록 차단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-180">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="00a45-181">예를 들어 다음 코드는 `SetChangeHandler` 메서드에 전달된 `cb` 개체 참조가 `Test` 메서드의 수명을 초과하여 `cb` 연결을 유지하지 않으므로 잘못된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-181">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="00a45-182">`cb` 개체가 가비지 수집되고 나면 `SetChangeHandler`에 전달된 함수 포인터가 더이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-182">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 <span data-ttu-id="00a45-183">예기치 않은 가비지 수집을 보완하기 위해 호출자는 관리되지 않는 함수 포인터가 사용되는 한 `cb` 개체 연결이 유지되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-183">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="00a45-184">필요에 따라 다음 예제와 같이 함수 포인터가 더 이상 필요하지 않을 때 비관리 코드에서 관리 코드에 알리도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-184">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="00a45-185">값 형식에 대한 기본 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-185">Default marshaling for value types</span></span>  

 <span data-ttu-id="00a45-186">정수 및 부동 소수점 숫자와 같은 대부분의 값 형식은 [blittable](blittable-and-non-blittable-types.md)이며 마샬링할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-186">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="00a45-187">다른 [비 blittable](blittable-and-non-blittable-types.md) 형식은 관리되는 메모리와 관리되지 않는 메모리에서 서로 다르게 표현되므로 마샬링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-187">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="00a45-188">다른 형식은 상호 운용 경계 간에 명시적 형식 지정도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-188">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="00a45-189">이 섹션에서는 다음과 같은 서식이 지정된 값 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-189">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="00a45-190">플랫폼 호출에서 사용되는 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-190">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="00a45-191">COM Interop에서 사용되는 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-191">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="00a45-192">이 항목에서는 형식이 지정된 형식을 설명할 뿐 아니라 특별한 마샬링 동작이 있는 [시스템 값 형식](#system-value-types)을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-192">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="00a45-193">형식이 지정된 형식은 메모리에서 해당 멤버의 레이아웃을 명시적으로 제어하는 정보가 포함된 복합 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-193">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="00a45-194">멤버 레이아웃 정보는 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 사용하여 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-194">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="00a45-195">레이아웃은 다음 <xref:System.Runtime.InteropServices.LayoutKind> 열거형 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-195">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="00a45-196">**LayoutKind.Auto**</span><span class="sxs-lookup"><span data-stu-id="00a45-196">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="00a45-197">공용 언어 런타임이 효율성을 위해 형식의 멤버 순서를 자유롭게 조정할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-197">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="00a45-198">그러나 값 형식이 비관리 코드에 전달될 때는 멤버의 레이아웃을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-198">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="00a45-199">이러한 구조체를 자동으로 마샬링하려고 하면 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-199">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="00a45-200">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="00a45-200">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="00a45-201">형식의 멤버가 관리되는 형식 정의에 나타나는 순서대로 관리되지 않는 메모리에 배치됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-201">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="00a45-202">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="00a45-202">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="00a45-203">각 필드에 제공된 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>에 따라 멤버가 배치됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-203">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="00a45-204">플랫폼 호출에서 사용되는 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-204">Value Types Used in Platform Invoke</span></span>  

 <span data-ttu-id="00a45-205">다음 예제에서 `Point` 및 `Rect` 형식은 **StructLayoutAttribute** 를 사용하여 멤버 레이아웃 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-205">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="00a45-206">비관리 코드로 마샬링된 경우 이러한 형식이 지정된 형식은 C 스타일 구조체로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-206">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="00a45-207">이렇게 하면 구조체 인수가 있는 관리되지 않는 API를 쉽게 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-207">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="00a45-208">예를 들어 다음과 같이 Microsoft Windows API **PtInRect** 함수에 `POINT` 및 `RECT` 구조체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-208">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="00a45-209">다음과 같은 플랫폼 호출 정의를 사용하여 구조체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-209">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="00a45-210">관리되지 않는 API는 `RECT`에 대한 포인터가 함수에 전달될 것으로 예상하기 때문에 `Rect` 값 형식은 참조로 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-210">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="00a45-211">관리되지 않는 API는 `POINT`가 스택에서 전달될 것으로 예상하기 때문에 `Point` 값 형식은 값으로 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-211">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="00a45-212">이러한 미묘한 차이가 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-212">This subtle difference is very important.</span></span> <span data-ttu-id="00a45-213">참조는 비관리 코드에 포인터로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-213">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="00a45-214">값은 스택에서 비관리 코드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-214">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a45-215">형식이 지정된 형식이 구조체로 마샬링된 경우 형식 내의 필드에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-215">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="00a45-216">형식에 메서드, 속성 또는 이벤트가 있는 경우 비관리 코드에서 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-216">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="00a45-217">고정된 멤버 레이아웃이 있는 경우 클래스를 비관리 코드에 C 스타일 구조체로 마샬링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-217">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="00a45-218">클래스에 대한 멤버 레이아웃 정보도 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 특성을 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-218">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="00a45-219">고정 레이아웃의 값 형식과 고정 레이아웃의 클래스 간에 주요 차이점은 비관리 코드로 마샬링되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-219">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="00a45-220">값 형식은 스택에서 값으로 전달되므로 호출 수신자가 형식의 멤버를 변경해도 변경 내용이 호출자에게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-220">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="00a45-221">참조 형식은 참조로 전달되므로(스택에서 형식에 대한 참조가 전달됨) 호출 수신자가 형식의 blittable 형식 멤버를 변경할 경우 모든 변경 내용이 호출자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-221">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a45-222">참조 형식에 non-blittable 형식 멤버가 있을 경우 변환이 두 번 필요합니다. 첫 번째는 인수가 관리되지 않는 쪽에 전달될 때이고 두 번째는 호출에서 반환될 때입니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-222">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="00a45-223">이러한 추가 오버헤드로 인해 호출자가 호출 수신자에 의한 변경 내용을 보려는 경우 In/Out 매개 변수를 인수에 명시적으로 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-223">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="00a45-224">다음 예제에서 `SystemTime` 클래스는 순차적 멤버 레이아웃을 사용하며 Windows API **GetSystemTime** 함수에 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-224">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 <span data-ttu-id="00a45-225">**GetSystemTime** 함수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-225">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="00a45-226">**GetSystemTime** 에 해당하는 플랫폼 호출 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-226">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="00a45-227">`SystemTime`이 값 형식이 아니라 클래스이기 때문에 `SystemTime` 인수는 참조 인수로 형식화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-227">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="00a45-228">값 형식과 달리 클래스는 항상 참조로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-228">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="00a45-229">다음 코드 예제에서는 `SetXY`라는 메서드가 있는 다른 `Point` 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-229">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="00a45-230">형식이 순차적 레이아웃을 사용하므로 비관리 코드에 전달되고 구조체로 마샬링될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-230">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="00a45-231">그러나 개체가 참조로 전달되는 경우에도 `SetXY` 멤버는 비관리 코드에서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-231">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="00a45-232">COM Interop에서 사용되는 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-232">Value Types Used in COM Interop</span></span>  

 <span data-ttu-id="00a45-233">형식이 지정된 형식을 COM interop 메서드 호출에 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-233">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="00a45-234">실제로 형식 라이브러리로 내보내는 경우 값 형식이 자동으로 구조체로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-234">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="00a45-235">다음 예제에서 볼 수 있듯이, `Point` 값 형식은 이름이 `Point`인 형식 정의(typedef)가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-235">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="00a45-236">형식 라이브러리의 다른 위치에 있는 `Point` 값 형식에 대한 모든 참조가 `Point` typedef로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-236">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="00a45-237">**형식 라이브러리 표현**</span><span class="sxs-lookup"><span data-stu-id="00a45-237">**Type library representation**</span></span>  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="00a45-238">값과 참조를 플랫폼 호출로 마샬링하는 데 사용되는 것과 동일한 규칙이 COM 인터페이스를 통해 마샬링할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-238">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="00a45-239">예를 들어 `Point` 값 형식의 인스턴스가 .NET Framework에서 COM으로 전달되는 경우 `Point`가 값으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-239">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="00a45-240">`Point` 값 형식이 참조로 전달되는 경우에는 `Point`에 대한 포인터가 스택에서 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-240">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="00a45-241">interop 마샬러는 두 방향에서 모두 더 높은 수준의 간접 참조(**Point** \*\*)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-241">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a45-242">내보낸 형식 라이브러리에서 명시적 레이아웃을 표현할 수 없기 때문에 <xref:System.Runtime.InteropServices.LayoutKind> 열거형 값이 **Explicit** 로 설정된 구조체는 COM interop에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-242">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="00a45-243">시스템 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-243">System Value Types</span></span>  

 <span data-ttu-id="00a45-244"><xref:System> 네임스페이스에는 런타임 기본 형식의 boxed 형식을 나타내는 여러 개의 값 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-244">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="00a45-245">예를 들어 값 형식 <xref:System.Int32?displayProperty=nameWithType> 구조체는 **ELEMENT_TYPE_I4** 의 boxed 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-245">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="00a45-246">다른 형식이 지정된 형식처럼 이러한 형식을 구조체로 마샬링하는 대신 boxing하는 기본 형식과 동일한 방식으로 마샬링합니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-246">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="00a45-247">따라서 **System.Int32** 는 **long** 형식의 단일 멤버를 포함하는 구조체가 아니라 **ELEMENT_TYPE_I4** 로 마샬링됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-247">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="00a45-248">다음 표에는 기본 형식의 boxed 표현인 **System** 네임스페이스의 값 형식 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-248">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="00a45-249">시스템 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-249">System value type</span></span>|<span data-ttu-id="00a45-250">요소 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-250">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="00a45-251">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="00a45-251">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="00a45-252">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="00a45-252">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="00a45-253">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="00a45-253">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="00a45-254">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="00a45-254">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="00a45-255">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="00a45-255">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="00a45-256">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="00a45-256">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="00a45-257">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="00a45-257">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="00a45-258">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="00a45-258">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="00a45-259">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="00a45-259">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="00a45-260">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="00a45-260">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="00a45-261">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="00a45-261">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="00a45-262">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="00a45-262">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="00a45-263">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="00a45-263">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="00a45-264">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="00a45-264">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="00a45-265">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="00a45-265">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="00a45-266">**System** 네임스페이스의 다른 값 형식은 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-266">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="00a45-267">비관리 코드에는 이러한 형식에 대해 잘 설정된 형식이 이미 있으므로 마샬러에 특수 마샬링 규칙이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-267">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="00a45-268">다음 표에서는 **System** 네임스페이스의 특수 값 형식과 마샬링되는 관리되지 않는 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-268">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="00a45-269">시스템 값 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-269">System value type</span></span>|<span data-ttu-id="00a45-270">IDL 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-270">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="00a45-271">**DATE**</span><span class="sxs-lookup"><span data-stu-id="00a45-271">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="00a45-272">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="00a45-272">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="00a45-273">**GUID**</span><span class="sxs-lookup"><span data-stu-id="00a45-273">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="00a45-274">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="00a45-274">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="00a45-275">다음 코드에서는 Stdole2 형식 라이브러리에 있는 관리되지 않는 형식 **DATE**, **GUID**, **DECIMAL** 및 **OLE_COLOR** 의 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-275">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="00a45-276">형식 라이브러리 표현</span><span class="sxs-lookup"><span data-stu-id="00a45-276">Type library representation</span></span>  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="00a45-277">다음 코드에서는 관리되는 `IValueTypes` 인터페이스의 해당 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00a45-277">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="00a45-278">형식 라이브러리 표현</span><span class="sxs-lookup"><span data-stu-id="00a45-278">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="00a45-279">참조</span><span class="sxs-lookup"><span data-stu-id="00a45-279">See also</span></span>

- [<span data-ttu-id="00a45-280">Blittable 형식 및 비 Blittable 형식</span><span class="sxs-lookup"><span data-stu-id="00a45-280">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="00a45-281">복사 및 고정</span><span class="sxs-lookup"><span data-stu-id="00a45-281">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="00a45-282">배열에 대한 기본 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-282">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="00a45-283">개체에 대한 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-283">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="00a45-284">문자열에 대한 기본 마샬링</span><span class="sxs-lookup"><span data-stu-id="00a45-284">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
