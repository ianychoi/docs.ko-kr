---
description: '자세한 정보: 동적 개체 작업 (Visual Basic)'
title: 동적 개체 작업
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 4991ae3deca908fc0b96760f50c85514df92714f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434396"
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="00644-103">동적 개체 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00644-103">Working with Dynamic Objects (Visual Basic)</span></span>

<span data-ttu-id="00644-104">동적 개체는 형식 이외의 다른 방법을 제공 `Object` 하 여 런타임에 개체에 런타임에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="00644-104">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="00644-105">동적 개체는 네임 스페이스에 정의 된 동적 인터페이스를 사용 하 여 런타임에 속성 및 메서드와 같은 멤버를 노출 <xref:System.Dynamic> 합니다.</span><span class="sxs-lookup"><span data-stu-id="00644-105">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="00644-106">네임 스페이스의 클래스를 사용 <xref:System.Dynamic> 하 여 정적 형식 또는 형식과 일치 하지 않는 데이터 구조를 사용 하는 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00644-106">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="00644-107">또한 IronPython 및 IronRuby와 같은 동적 언어에서 정의 된 동적 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00644-107">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="00644-108">동적 개체를 만들거나 동적 언어로 정의 된 동적 개체를 사용 하는 방법을 보여 주는 예제는 [연습: 동적 개체 만들기 및 사용](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), 또는를 참조 하세요 <xref:System.Dynamic.DynamicObject> <xref:System.Dynamic.ExpandoObject> .</span><span class="sxs-lookup"><span data-stu-id="00644-108">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="00644-109">Visual Basic는 인터페이스를 사용 하 여 동적 언어 런타임의 개체와 IronPython 및 IronRuby와 같은 동적 언어에 바인딩합니다 <xref:System.Dynamic.IDynamicMetaObjectProvider> .</span><span class="sxs-lookup"><span data-stu-id="00644-109">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="00644-110">인터페이스를 구현 하는 클래스의 예로는 `IDynamicMetaObjectProvider` <xref:System.Dynamic.DynamicObject> 및 <xref:System.Dynamic.ExpandoObject> 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00644-110">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="00644-111">인터페이스를 구현 하는 개체에 런타임에 바인딩된 호출이 수행 되는 경우 `IDynamicMetaObjectProvider` Visual Basic는 해당 인터페이스를 사용 하 여 동적 개체에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="00644-111">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="00644-112">인터페이스를 구현 하지 않는 개체에 대 한 런타임에 바인딩된 호출이 수행 `IDynamicMetaObjectProvider` 되거나 `IDynamicMetaObjectProvider` 인터페이스 호출이 실패 하면 Visual Basic Visual Basic 런타임의 런타임에 바인딩 기능을 사용 하 여 개체에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="00644-112">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00644-113">추가 정보</span><span class="sxs-lookup"><span data-stu-id="00644-113">See also</span></span>

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [<span data-ttu-id="00644-114">연습: 동적 개체 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="00644-114">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [<span data-ttu-id="00644-115">초기 바인딩 및 런타임에 바인딩</span><span class="sxs-lookup"><span data-stu-id="00644-115">Early and Late Binding</span></span>](index.md)
