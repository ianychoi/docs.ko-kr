---
title: 리플렉션을 사용하는 API
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 2c361962f4570200d63037a68ef39b0c982bd5f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251141"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="51472-102">리플렉션을 사용하는 API</span><span class="sxs-lookup"><span data-stu-id="51472-102">APIs That Rely on Reflection</span></span>

<span data-ttu-id="51472-103">경우에 따라 코드에서 리플렉션을 사용 하는 것은 명확 하지 않으므로 .NET 네이티브 도구 체인은 런타임에 필요한 메타 데이터를 유지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="51472-104">이 항목에서는 리플렉션 API의 일부로는 간주되지 않지만 리플렉션을 사용해야 정상적으로 실행되는 몇 가지 일반적인 API 또는 프로그래밍 패턴에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="51472-105">소스 코드에서 이러한 API를 사용하는 경우 해당 API 호출 시 런타임에 [MissingMetadataException](missingmetadataexception-class-net-native.md) 예외 또는 일부 기타 예외가 발생하지 않도록 API에 대한 정보를 런타임 지시문(.rd.xml) 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="51472-106">Type.MakeGenericType 메서드</span><span class="sxs-lookup"><span data-stu-id="51472-106">Type.MakeGenericType method</span></span>  

 <span data-ttu-id="51472-107">다음과 같은 코드를 사용해 `AppClass<T>` 메서드를 호출하여 제네릭 형식 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>를 동적으로 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="51472-108">이 코드가 런타임에 정상적으로 실행되려면 여러 메타데이터 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="51472-109">그 중 첫 번째는 인스턴스화되지 않은 제네릭 형식 `Browse`에 대한 `AppClass<T>` 메타데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="51472-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="51472-110">이 메타데이터가 있으면 <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 메서드가 정상적으로 호출되며 유효한 <xref:System.Type> 개체가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="51472-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="51472-111">그러나 인스턴스화되지 않은 제네릭 형식에 대한 메타데이터를 추가하더라도 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 메서드를 호출하면 [MissingMetadataException](missingmetadataexception-class-net-native.md) 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="51472-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="51472-112">성능상의 이유로 다음 형식의 메타 데이터가 제거 되었으므로이 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="51472-113">`App1.AppClass`1<>'.</span><span class="sxs-lookup"><span data-stu-id="51472-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="51472-114">다음 런타임 지시문을 런타임 지시문 파일에 추가하여 `Activate`를 통한 `AppClass<T>`의 특정 인스턴스화에 대해 <xref:System.Int32?displayProperty=nameWithType> 메타데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="51472-115">`AppClass<T>`를 통한 각 인스턴스화에서는 별도의 지시문이 필요합니다(<xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 메서드를 사용하여 작성되며 정적으로 사용되지 않는 경우).</span><span class="sxs-lookup"><span data-stu-id="51472-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="51472-116">MethodInfo.MakeGenericMethod 메서드</span><span class="sxs-lookup"><span data-stu-id="51472-116">MethodInfo.MakeGenericMethod method</span></span>  

 <span data-ttu-id="51472-117">`Class1` 클래스에 제네릭 메서드 `GetMethod<T>(T t)`가 포함되어 있는 경우 다음과 같은 코드를 사용하여 리플렉션을 통해 `GetMethod`를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="51472-118">이 코드를 정상적으로 실행하려면 다음과 같은 여러 메타데이터 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="51472-119">해당 메서드를 호출할 형식에 대한 `Browse` 메타데이터</span><span class="sxs-lookup"><span data-stu-id="51472-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="51472-120">호출하려는 메서드에 대한 `Browse` 메타데이터.</span><span class="sxs-lookup"><span data-stu-id="51472-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="51472-121">public 메서드의 경우 포함 형식에 대한 public `Browse` 메타데이터를 추가하면 메서드도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="51472-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="51472-122">.NET 네이티브 도구 체인에 의해 리플렉션 호출 대리자가 제거 되지 않도록 호출 하려는 메서드에 대 한 동적 메타 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="51472-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="51472-123">메서드에 대한 동적 메타데이터가 누락되면 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 메서드 호출 시 다음 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="51472-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="51472-124">다음 런타임 지시문을 사용하면 필요한 모든 메타데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="51472-125">동적으로 호출되는 메서드의 서로 다른 각 인스턴스화에는 `MethodInstantiation` 지시문이 필요하며, 각 인스턴스화 인수를 반영하기 위해 `Arguments` 요소가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="51472-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="51472-126">Array.CreateInstance 및 Type.MakeTypeArray 메서드</span><span class="sxs-lookup"><span data-stu-id="51472-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  

 <span data-ttu-id="51472-127">다음 예제에서는 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 형식에 대해 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 및 `Class1` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="51472-128">배열 메타데이터가 없으면 다음 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="51472-129">배열 형식을 동적으로 인스턴스화하려면 해당 형식에 대한 `Browse` 메타데이터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51472-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="51472-130">다음 런타임 지시문을 사용하면 `Class1[]`을 동적으로 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51472-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="51472-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51472-131">See also</span></span>

- [<span data-ttu-id="51472-132">시작</span><span class="sxs-lookup"><span data-stu-id="51472-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="51472-133">런타임 지시문(rd.xml) 구성 파일 참조</span><span class="sxs-lookup"><span data-stu-id="51472-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
