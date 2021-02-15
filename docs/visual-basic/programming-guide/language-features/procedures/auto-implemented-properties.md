---
description: '자세히 알아보기: 자동 구현 속성 (Visual Basic)'
title: 자동으로 구현된 속성
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 61f6565f9d4e7ea8731bb09c59cd6d942ab8c129
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472698"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="38c11-103">자동 구현 속성(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38c11-103">Auto-Implemented Properties (Visual Basic)</span></span>

<span data-ttu-id="38c11-104">*자동 구현 속성* 을 사용 하면 및 속성에 코드를 작성 하지 않고도 클래스의 속성을 신속 하 게 지정할 수 있습니다 `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="38c11-104">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="38c11-105">자동 구현 속성에 대한 코드를 작성하면 Visual Basic 컴파일러에서 관련 `Get` 및 `Set` 프로시저가 생성될 뿐만 아니라 속성 변수를 저장하는 전용 필드가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-105">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="38c11-106">자동 구현 속성을 사용하면 기본값을 포함한 속성을 한 줄에 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-106">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="38c11-107">다음 예제에서는 3개의 속성 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-107">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="38c11-108">자동 구현 속성은 해당 속성 값이 전용 필드에 저장되는 속성과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-108">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="38c11-109">다음 코드 예제에서는 자동 구현 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-109">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="38c11-110">다음 코드 예제에서는 앞의 자동 구현 속성 예제에 해당하는 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-110">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="38c11-111">다음 코드에서는 읽기 전용 속성 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-111">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="38c11-112">예제처럼 초기화 식을 사용해 속성에 할당할 수 있습니다. 또는 포함하는 형식의 생성자에서 속성에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-112">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="38c11-113">언제든지 읽기 전용 속성의 지원 필드에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-113">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="38c11-114">지원 필드</span><span class="sxs-lookup"><span data-stu-id="38c11-114">Backing Field</span></span>  

 <span data-ttu-id="38c11-115">자동 구현 속성을 선언 하면 Visual Basic는 속성 값을 포함 하기 위해 *지원 필드* 라는 숨겨진 private 필드를 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-115">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="38c11-116">지원 필드 이름은 밑줄(_) 다음에 자동 구현 속성 이름이 나오는 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-116">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="38c11-117">예를 들어 `ID`라는 자동 구현 속성을 선언하는 경우 지원 필드의 이름은 `_ID`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-117">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="38c11-118">이름이 `_ID`인 클래스의 멤버를 포함하는 경우 이름 충돌이 발생하며 Visual Basic에서 컴파일러 오류가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-118">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="38c11-119">지원 필드에는 또한 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-119">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="38c11-120">속성 자체에 `Public`과 같은 다른 액세스 수준이 있는 경우에도, 지원 필드에 대한 액세스 한정자는 항상 `Private`입니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-120">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="38c11-121">속성이 `Shared`로 표시된 경우 지원 필드도 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-121">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="38c11-122">속성에 대해 지정된 특성은 지원 필드에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-122">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="38c11-123">클래스 내의 코드에서, 그리고 조사식 창과 같은 디버깅 도구에서 지원 필드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-123">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="38c11-124">그러나 지원 필드는 IntelliSense 단어 완성 목록에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-124">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="38c11-125">자동 구현 속성 초기화</span><span class="sxs-lookup"><span data-stu-id="38c11-125">Initializing an Auto-Implemented Property</span></span>  

 <span data-ttu-id="38c11-126">필드를 초기화하는 데 사용할 수 있는 모든 식이 자동 구현 속성을 초기화하는 데 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-126">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="38c11-127">자동 구현 속성을 초기화하면 식이 계산되어 속성에 대한 `Set` 프로시저에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-127">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="38c11-128">다음 코드 예제에서는 초기 값이 포함된 일부 자동 구현 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-128">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="38c11-129">`Interface`의 멤버이거나 `MustOverride`로 표시된 자동 구현 속성은 초기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-129">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="38c11-130">자동 구현 속성을 `Structure`의 멤버로 선언하는 경우 `Shared`로 표시된 자동 구현 속성만 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-130">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="38c11-131">자동 구현 속성을 배열로 선언하는 경우 명시적 배열 범위를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-131">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="38c11-132">그러나 다음 예에서와 같이 배열 이니셜라이저를 사용하여 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-132">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="38c11-133">표준 구문이 요구되는 속성 정의</span><span class="sxs-lookup"><span data-stu-id="38c11-133">Property Definitions That Require Standard Syntax</span></span>  

 <span data-ttu-id="38c11-134">자동 구현 속성은 편리하며 많은 프로그래밍 시나리오를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-134">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="38c11-135">그러나 자동으로 구현 된 속성을 사용할 수 없으며 대신 표준 또는 *확장* 된 속성 구문을 사용 해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-135">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="38c11-136">다음 중 하나를 수행하려는 경우 확장된 속성 정의 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-136">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="38c11-137">속성의 `Get` 또는 `Set` 프로시저에 추가합니다. 예를 들어 `Set` 프로시저에 들어오는 값의 유효성을 검사하는 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-137">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="38c11-138">예를 들어 해당 속성 값을 설정하기 전에 전화번호를 나타내는 문자열에 필요한 수의 숫자가 포함되었는지 확인해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-138">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="38c11-139">`Get` 및 `Set` 프로시저에 대해 다른 접근성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-139">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="38c11-140">`Set` 프로시저를 `Private`으로, `Get` 프로시저를 `Public`으로 만들려는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-140">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="38c11-141">`WriteOnly`인 속성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-141">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="38c11-142">매개 변수가 있는 속성을 사용합니다(`Default` 속성 포함).</span><span class="sxs-lookup"><span data-stu-id="38c11-142">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="38c11-143">속성에 대한 매개 변수를 지정하기 위해, 또는 `Set` 프로시저에 대해 추가 매개 변수를 지정하기 위해서는 확장된 속성을 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-143">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="38c11-144">지원 필드에 특성을 배치하거나 지원 필드의 액세스 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-144">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="38c11-145">지원 필드에 대한 XML 주석을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-145">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="38c11-146">자동 구현 속성 확장명</span><span class="sxs-lookup"><span data-stu-id="38c11-146">Expanding an Auto-Implemented Property</span></span>  

 <span data-ttu-id="38c11-147">자동 구현 속성을 `Get` 또는 `Set` 프로시저가 포함된 확장된 속성으로 변환해야 하는 경우 Visual Basic 코드 편집기는 속성에 대한 `Get` 및 `Set` 프로시저와 `End Property` 문을 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-147">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="38c11-148">문 뒤에 있는 빈 줄에 커서를 놓고 `Property` `G` (의 경우 `Get` ) 또는 (의 경우)를 입력 하 `S` `Set` 고 enter 키를 누르면 코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-148">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="38c11-149">`Property` 문 끝에서 Enter 키를 누르면 Visual Basic 코드 편집기에서 읽기 전용 및 쓰기 전용 속성에 대한 `Get` 또는 `Set` 프로시저가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="38c11-149">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c11-150">추가 정보</span><span class="sxs-lookup"><span data-stu-id="38c11-150">See also</span></span>

- [<span data-ttu-id="38c11-151">방법: Visual Basic에서 기본 속성 선언 및 호출</span><span class="sxs-lookup"><span data-stu-id="38c11-151">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="38c11-152">방법: 액세스 수준이 혼합된 속성 선언</span><span class="sxs-lookup"><span data-stu-id="38c11-152">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="38c11-153">Property Statement</span><span class="sxs-lookup"><span data-stu-id="38c11-153">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="38c11-154">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="38c11-154">ReadOnly</span></span>](../../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="38c11-155">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="38c11-155">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="38c11-156">개체 및 클래스</span><span class="sxs-lookup"><span data-stu-id="38c11-156">Objects and Classes</span></span>](../objects-and-classes/index.md)
