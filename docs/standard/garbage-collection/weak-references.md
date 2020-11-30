---
title: 약한 참조
description: 애플리케이션에서 개체에 계속 액세스할 수 있는 동안 .NET 가비지 수집기에서 개체를 수집할 수 있도록 하는 약한 참조에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: 1eb5e57f5cc1065f1b8510e4fb0a980a85abca29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714213"
---
# <a name="weak-references"></a><span data-ttu-id="d82b0-103">약한 참조</span><span class="sxs-lookup"><span data-stu-id="d82b0-103">Weak References</span></span>

<span data-ttu-id="d82b0-104">애플리케이션의 코드가 해당 개체에 연결될 수 있는 반면 가비지 수집기는 애플리케이션에서 사용 중인 개체를 수집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-104">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="d82b0-105">애플리케이션은 개체에 대한 강력한 참조를 가진다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-105">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="d82b0-106">Weak references는 애플리케이션에서 개체에 계속 액세스할 수 있는 동안 가비지 수집기에서 해당 개체를 수집할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-106">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="d82b0-107">강한 참조가 없을 경우 Weak references는 개체가 수집되기 전까지 임의의 시간 동안에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-107">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="d82b0-108">Weak references를 사용하면 애플리케이션은 여전히 개체에 대한 강한 참조를 유지할 수 있으며 이로 인해 개체가 수집되지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-108">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="d82b0-109">그러나 강력한 참조를 다시 설정하기 전에 가비지 수집기가 먼저 개체에 연결될 위험이 항상 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-109">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="d82b0-110">Weak references는 많은 메모리를 사용하는 개체에 유용하지만 가비지 수집에서 회수될 경우 쉽게 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-110">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="d82b0-111">Windows Forms 애플리케이션의 트리 뷰에서는 사용자에게 복잡한 계층적 선택 옵션을 표시한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-111">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="d82b0-112">기본 데이터가 크다면 사용자가 애플리케이션에서 다른 작업을 수행하는 경우 트리를 메모리에 유지하는 것은 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-112">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="d82b0-113">사용자가 애플리케이션의 다른 부분으로 전환할 때 <xref:System.WeakReference> 클래스를 사용하여 트리에 대한 약한 참조를 만들고 모든 강력한 참조를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-113">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="d82b0-114">사용자가 트리로 다시 전환할 때 애플리케이션은 트리에 대한 강한 참조를 가지려고 하며 이 시도가 성공할 경우 트리를 다시 생성하지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-114">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="d82b0-115">개체를 사용하여 약한 참조를 설정하려면 추적할 개체의 인스턴스를 사용하여 <xref:System.WeakReference>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-115">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="d82b0-116">그런 다음 <xref:System.WeakReference.Target%2A> 속성을 해당 개체로 설정하고 해당 개체에 대한 원래 참조를 `null`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-116">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="d82b0-117">코드 예제는 클래스 라이브러리의 <xref:System.WeakReference>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d82b0-117">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="d82b0-118">Short 및 Long Weak References</span><span class="sxs-lookup"><span data-stu-id="d82b0-118">Short and Long Weak References</span></span>  

 <span data-ttu-id="d82b0-119">Short Weak Reference 또는 Long Weak References를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-119">You can create a short weak reference or a long weak reference:</span></span>  
  
- <span data-ttu-id="d82b0-120">Short</span><span class="sxs-lookup"><span data-stu-id="d82b0-120">Short</span></span>  
  
     <span data-ttu-id="d82b0-121">가비지 수집에서 개체를 회수하는 경우 Short Weak Reference의 대상은 `null`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-121">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="d82b0-122">Weak Reference는 자체 관리되는 개체이며 다른 관리되는 개체와 마찬가지로 가비지 수집의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-122">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="d82b0-123">짧은 약한 참조는 <xref:System.WeakReference>의 매개 변수 없는 생성자입니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-123">A short weak reference is the parameterless constructor for <xref:System.WeakReference>.</span></span>  
  
- <span data-ttu-id="d82b0-124">Long</span><span class="sxs-lookup"><span data-stu-id="d82b0-124">Long</span></span>  
  
     <span data-ttu-id="d82b0-125">개체의 <xref:System.Object.Finalize%2A> 메서드가 호출된 후에 긴 약한 참조는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-125">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="d82b0-126">이렇게 하면 개체를 다시 만들 수 있지만 개체의 상태는 예측할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-126">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="d82b0-127">긴 참조를 사용하려면 <xref:System.WeakReference> 생성자에서 `true`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-127">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="d82b0-128">개체의 형식에 <xref:System.Object.Finalize%2A> 메서드가 없는 경우 짧은 약한 참조 기능이 적용되며 약한 참조는 대상이 수집될 때까지만 유효합니다. 이는 종료자가 실행된 후에 언제든지 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-128">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="d82b0-129">강한 참조를 설정하고 개체를 다시 사용하려면 <xref:System.WeakReference>의 <xref:System.WeakReference.Target%2A> 속성을 개체의 형식에 캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-129">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="d82b0-130"><xref:System.WeakReference.Target%2A> 속성이 `null`을 반환하는 경우 개체가 수집되었습니다. 그러지 않으면, 애플리케이션이 해당 개체에 대한 강한 참조를 회복하기 때문에 개체를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-130">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="d82b0-131">Weak References를 사용하기 위한 지침</span><span class="sxs-lookup"><span data-stu-id="d82b0-131">Guidelines for Using Weak References</span></span>  

 <span data-ttu-id="d82b0-132">종료된 후에 개체의 상태를 예측할 수 없기 때문에 필요한 경우에만 Long Weak Referencs를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-132">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="d82b0-133">포인터 자체는 이상일 수 있기 때문에 작은 개체에 Weak Referencs를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-133">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="d82b0-134">메모리 관리 문제에 대한 자동 솔루션으로 Weak Referencs를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-134">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="d82b0-135">대신, 애플리케이션의 개체를 처리하기 위한 효과적인 캐싱 정책을 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="d82b0-135">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82b0-136">참조</span><span class="sxs-lookup"><span data-stu-id="d82b0-136">See also</span></span>

- [<span data-ttu-id="d82b0-137">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="d82b0-137">Garbage Collection</span></span>](index.md)
