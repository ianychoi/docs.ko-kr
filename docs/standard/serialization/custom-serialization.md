---
title: 사용자 지정 serialization
description: 사용자 지정 serialization은 형식의 serialization 및 deserialization을 제어합니다. Serialization을 제어하면 serialization 호환성을 보장할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 4ca78c71f464a914c07583825d4a7027ebb11bf6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679041"
---
# <a name="custom-serialization"></a><span data-ttu-id="99019-104">사용자 지정 serialization</span><span class="sxs-lookup"><span data-stu-id="99019-104">Custom serialization</span></span>

<span data-ttu-id="99019-105">사용자 지정 serialization은 형식의 serialization 및 deserialization을 제어하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="99019-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="99019-106">serialization을 제어하면 형식의 핵심 기능에 영향을 주지 않고 다양한 형식 사이에 직렬화 및 역직렬화할 수 있는 기능인 직렬화 호환성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="99019-107">예를 들어 첫 번째 버전의 형식에는 두 개의 필드만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="99019-108">다음 버전의 형식에는 몇 개의 필드가 더 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="99019-109">하지만 애플리케이션의 두 번째 버전에서는 여전히 두 형식을 모두 직렬화 및 역직렬화할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="99019-110">다음 단원에서는 serialization을 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="99019-111">.NET Framework 4.0 이전 버전에서는 부분적으로 신뢰할 수 있는 어셈블리의 사용자 지정 사용자 데이터를 직렬화하는 데 `GetObjectData`가 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using `GetObjectData`.</span></span> <span data-ttu-id="99019-112">버전 4.0부터 이 메서드는 <xref:System.Security.SecurityCriticalAttribute> 특성으로 표시되어 부분적으로 신뢰할 수 있는 어셈블리에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute, which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="99019-113">이 문제를 해결하려면 <xref:System.Runtime.Serialization.ISafeSerializationData> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="99019-114">serialization 도중 및 이후에 사용자 지정 메서드 실행</span><span class="sxs-lookup"><span data-stu-id="99019-114">Running custom methods during and after serialization</span></span>

<span data-ttu-id="99019-115">권장되는 방법은 직렬화 도중과 이후에 사용자 지정 메서드를 실행하여 직렬화 도중과 이후에 데이터를 수정하는 데 사용되는 메서드에 다음 특성을 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99019-115">The recommended way to run custom methods during and after serialization is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="99019-116">이러한 특성을 통해 형식은 serialization 및 deserialization 프로세스의 네 단계 중 하나 또는 모두에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="99019-117">특성은 각 단계에서 호출되어야 하는 형식의 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="99019-118">메서드는 serialization 스트림에 액세스할 수 없지만 대신 serialization 이전과 이후 또는 deserialization 이전과 이후에 개체를 변경할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="99019-119">특성은 형식 상속 계층의 모든 수준에 적용될 수 있으며 각 메서드는 계층 구조의 기본부터 가장 많이 파생된 단계까지 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="99019-120">이 메커니즘에서는 가장 많이 파생된 구현에서 serialization 및 deserialization을 담당하도록 하여 <xref:System.Runtime.Serialization.ISerializable> 인터페이스의 구현으로 인한 모든 문제와 복잡성을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="99019-121">또한 포맷터는 이 메커니즘을 통해 필드의 입력과 serialization 스트림에서의 검색을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="99019-122">serialization 및 deserialization 제어에 대한 자세한 내용과 예제를 보려면 이전 링크를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="99019-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="99019-123">또한 새 필드를 기존 serialize 가능한 형식에 추가할 때 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 특성을 필드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="99019-124"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 및 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>는 새 필드가 없는 스트림이 처리될 때 필드가 없어도 이를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="99019-125">ISerializable 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="99019-125">Implementing the ISerializable interface</span></span>  

 <span data-ttu-id="99019-126">serialization을 제어하는 다른 방법은 개체에 <xref:System.Runtime.Serialization.ISerializable> 인터페이스를 구현하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99019-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="99019-127">하지만 이전 단원의 메서드가 이 메서드를 대체하여 serialization을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="99019-128">또한 [Serializable](xref:System.SerializableAttribute) 특성으로 표시되어 있으며 클래스 수준 또는 생성자에 선언적 또는 명령적 보안이 있는 클래스에는 기본 serialization을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="99019-129">대신 이러한 클래스는 항상 <xref:System.Runtime.Serialization.ISerializable> 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="99019-130"><xref:System.Runtime.Serialization.ISerializable> 구현에는 개체가 역직렬화될 때 사용되는 특별한 생성자 및 `GetObjectData` 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="99019-131">다음 샘플 코드에서는 이전 단원의 <xref:System.Runtime.Serialization.ISerializable> 클래스에서 `MyObject`을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99019-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="99019-132">serialization 도중 **GetObjectData** 가 호출될 때는 메서드 호출과 함께 제공된 <xref:System.Runtime.Serialization.SerializationInfo>를 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="99019-133">이름 및 값 쌍으로 serialize될 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="99019-134">모든 텍스트를 이름으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-134">Any text can be used as the name.</span></span> <span data-ttu-id="99019-135">deserialization 도중 개체를 복원하기 위한 충분한 데이터가 serialize된 경우 <xref:System.Runtime.Serialization.SerializationInfo>에 추가되는 멤버 변수를 자유롭게 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="99019-136">이 멤버 변수가 <xref:System.Runtime.Serialization.ISerializable>을 구현하는 경우 파생 클래스는 기본 개체의 **GetObjectData** 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="99019-137">serialization을 통해 다른 코드가 일반적으로 액세스할 수 없는 개체 인스턴스 데이터를 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="99019-138">따라서 serialization을 수행하는 코드에는 <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 플래그가 지정된 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="99019-139">기본 정책에 따라 이 권한은 인터넷에서 다운로드한 코드나 인트라넷 코드에는 부여되지 않고 로컬 컴퓨터에 있는 코드에만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="99019-140"><xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 플래그가 지정된 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)을 요청하거나 전용 데이터 보호에 특별히 도움이 되는 다른 권한을 요청하여 **GetObjectData** 메서드를 명시적으로 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="99019-141">전용 필드에 민감한 정보가 저장된 경우 데이터를 보호하려면 **GetObjectData** 에 대한 적절한 권한을 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="99019-142">**SerializationFormatter** 플래그가 지정된 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)이 부여된 코드는 전용 필드에 저장된 데이터를 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="99019-143">이 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)이 부여된 악의적 호출자가 숨겨진 디렉터리 위치나 부여된 권한 등의 데이터를 볼 수 있으며 데이터를 사용하여 컴퓨터의 보안 취약성을 악용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="99019-144">지정할 수 있는 보안 권한 플래그의 전체 목록은 [SecurityPermissionFlag 열거형](xref:System.Security.Permissions.SecurityPermissionFlag)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99019-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="99019-145"><xref:System.Runtime.Serialization.ISerializable>을 클래스에 추가한 경우 **GetObjectData** 및 특수 생성자를 모두 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="99019-146">**GetObjectData** 가 누락되면 컴파일러가 이를 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="99019-147">하지만 생성자의 구현을 강제할 수 없기 때문에 생성자가 없는 경우에는 경고가 제공되지 않으며 생성자 없이 클래스를 역직렬화하려고 하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="99019-148">잠재적 보안 문제와 버전 관리 문제를 해결하기 위해 <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> 메서드 대신 현재 디자인을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="99019-149">예를 들어 `SetObjectData` 메서드는 인터페이스의 일부로 정의된 경우 public이어야 합니다. 따라서 사용자는 **SetObjectData** 메서드가 여러 번 호출되는 것을 막기 위한 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="99019-150">그러지 않으면 작업을 실행하는 프로세스에서 개체에 대해 **SetObjectData** 메서드를 호출하는 악의적 애플리케이션으로 인해 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="99019-151">deserialization 도중 <xref:System.Runtime.Serialization.SerializationInfo>가 이런 목적으로 제공되는 생성자를 사용하여 클래스로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="99019-152">생성자에 적용된 모든 표시 제약 조건은 개체가 역직렬화될 때 무시됩니다. 따라서 클래스를 public, protected, internal 또는 private로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="99019-153">하지만 클래스가 sealed가 아니면 생성자를 보호하는 것이 좋으며, 이 경우 생성자를 private로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="99019-154">또한 생성자는 엄격한 입력 유효성 검사를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="99019-155">악의적 코드에 의해 오용되는 것을 피하기 위해 생성자는 다른 모든 생성자를 사용하여 클래스의 인스턴스를 얻는 데 필요한 것과 동일한 보안 검사 및 권한을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="99019-156">이 권장 사항을 따르지 않으면 악의적 코드가 개체를 미리 직렬화하고, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 플래그가 지정된 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)을 가진 컨트롤을 가져오고, public 생성자를 사용한 표준 인스턴스 생성 도중 적용된 모든 보안을 우회하여 클라이언트 컴퓨터의 개체를 역직렬화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="99019-157">개체의 상태를 복원하려면 serialization 도중 사용된 이름을 사용하여 <xref:System.Runtime.Serialization.SerializationInfo>에서 변수의 값을 검색하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="99019-158">기본 클래스가 <xref:System.Runtime.Serialization.ISerializable>을 구현하는 경우 기본 생성자를 호출하여 기본 개체가 변수를 복원할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="99019-159"><xref:System.Runtime.Serialization.ISerializable>을 구현하는 클래스에서 새 클래스를 파생하는 경우 파생 클래스는 직렬화되어야 하는 변수가 있는 경우 **GetObjectData** 메서드뿐만 아니라 생성자도 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="99019-160">다음 코드 예제에서는 이전에 보여 준 `MyObject` 클래스를 사용하여 이 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99019-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="99019-161">deserialization 생성자에서 반드시 기본 클래스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99019-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="99019-162">이렇게 하지 않으면 기본 클래스의 생성자가 호출되지 않으며 deserialization 후 개체가 완전히 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="99019-163">개체는 내부에서 외부로 재생성됩니다. deserialization 도중 메서드를 호출하면 원하지 않는 파생 효과가 발생할 수 있습니다. 호출된 메서드가 호출 시점에서 역직렬화되지 않은 개체 참조를 참조할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="99019-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="99019-164">역직렬화되는 클래스가 <xref:System.Runtime.Serialization.IDeserializationCallback>을 구현하는 경우 전체 개체 그래프가 역직렬화될 때 <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> 메서드가 자동으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="99019-165">이 시점에서 참조된 모든 자식 개체가 완전히 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="99019-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="99019-166">해시 테이블은 이벤트 수신기를 사용하지 않고 역직렬화하기 어려운 클래스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="99019-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="99019-167">deserialization 도중 키와 값 쌍을 검색하는 것은 쉽지만, 해시 테이블에서 파생된 클래스가 역직렬화되었다는 보장이 없기 때문에 해당 개체를 다시 해시 테이블에 추가하면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="99019-168">따라서 이 단계에서 해시 테이블에 대해 메서드를 호출하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="99019-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99019-169">참조</span><span class="sxs-lookup"><span data-stu-id="99019-169">See also</span></span>

- [<span data-ttu-id="99019-170">이진 serialization</span><span class="sxs-lookup"><span data-stu-id="99019-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="99019-171">XML 및 SOAP serialization</span><span class="sxs-lookup"><span data-stu-id="99019-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="99019-172">보안 및 Serialization</span><span class="sxs-lookup"><span data-stu-id="99019-172">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
