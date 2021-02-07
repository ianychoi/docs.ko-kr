---
description: '자세한 정보: DataContract 서로게이트'
title: DataContract 서로게이트
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 739471efcea1d04752f3065c7a28f55f9ff9a0f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755826"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="b24fe-103">DataContract 서로게이트</span><span class="sxs-lookup"><span data-stu-id="b24fe-103">DataContract Surrogate</span></span>

<span data-ttu-id="b24fe-104">이 샘플에서는 데이터 계약 서로게이트 클래스를 사용하여 serialization, deserialization, 스키마 내보내기 및 스키마 가져오기와 같은 프로세스를 사용자 지정할 수 있는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-104">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="b24fe-105">이 샘플에서는 클라이언트 및 서버 시나리오에서 데이터를 serialize 하 고 Windows Communication Foundation (WCF) 클라이언트와 서비스 간에 전송 하는 서로게이트를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-105">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b24fe-106">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b24fe-107">이 샘플에는 다음 서비스 계약이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-107">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="b24fe-108">`AddEmployee` 작업을 통해 사용자는 새 직원에 대한 데이터를 추가할 수 있으며 `GetEmployee` 작업은 이름을 기준으로 한 직원 검색을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-108">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="b24fe-109">이러한 작업에는 다음 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-109">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="b24fe-110">`Employee` 형식에서는 다음 샘플 코드의 `Person` 클래스가 유효한 데이터 계약 클래스가 아니므로 <xref:System.Runtime.Serialization.DataContractSerializer>에 의해 serialize될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-110">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="b24fe-111"><xref:System.Runtime.Serialization.DataContractAttribute> 특성을 `Person` 클래스에 적용할 수 있지만 항상 가능한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-111">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="b24fe-112">예를 들어, `Person` 클래스는 제어할 수 없는 별개의 어셈블리에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-112">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="b24fe-113">이 제한 사항이 있을 경우 `Person` 클래스를 serialize하는 한 가지 방법은 <xref:System.Runtime.Serialization.DataContractAttribute>로 표시된 다른 클래스로 대체하고 필요한 데이터를 새 클래스에 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-113">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="b24fe-114">이렇게 하는 것은 `Person` 클래스를 <xref:System.Runtime.Serialization.DataContractSerializer>에 대해 DataContract로 표시하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-114">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="b24fe-115">이것은 데이터 계약 클래스가 아닌 클래스를 serialize하는 한 방법이라는 것에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b24fe-115">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="b24fe-116">이 샘플에서는 `Person` 클래스를 `PersonSurrogated`라는 다른 클래스로 논리적으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-116">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="b24fe-117">데이터 계약 서로게이트는 이 대체를 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-117">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="b24fe-118">데이터 계약 서로게이트는 <xref:System.Runtime.Serialization.IDataContractSurrogate>를 구현하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-118">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="b24fe-119">이 샘플에서는 `AllowNonSerializableTypesSurrogate` 클래스가 이 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-119">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="b24fe-120">인터페이스 구현에서 첫 번째 작업은 `Person`에서 `PersonSurrogated`로의 형식 매핑을 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-120">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="b24fe-121">이 매핑은 serialization이 발생할 때 뿐만 아니라 스키마 내보내기를 수행할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-121">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="b24fe-122">이 매핑은 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> 메서드를 구현하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-122">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="b24fe-123">다음 샘플 코드와 같이 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> 메서드는 serialization 도중에 `Person` 인스턴스를 `PersonSurrogated` 인스턴스에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="b24fe-124">다음 샘플 코드와 같이 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> 메서드는 deserialization을 위한 역방향 매핑을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-124">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="b24fe-125">스키마 가져오기 도중에 `PersonSurrogated` 데이터 계약을 기존 `Person` 클래스에 매핑하기 위해 이 샘플에서는 다음 샘플 코드와 같이 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-125">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="b24fe-126">다음 샘플 코드에서는 <xref:System.Runtime.Serialization.IDataContractSurrogate> 인터페이스의 구현을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-126">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="b24fe-127">이 샘플에서는 `AllowNonSerializableTypesAttribute`라는 특성에 의해 ServiceModel에서 서로게이트가 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-127">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="b24fe-128">개발자는 위의 `IPersonnelDataService` 서비스 계약과 같이 해당 서비스 계약에서 이 특성을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-128">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="b24fe-129">이 특성은 `IContractBehavior`를 구현하고 해당 `ApplyClientBehavior` 및 `ApplyDispatchBehavior` 메서드의 작업에서 서로게이트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-129">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="b24fe-130">이 경우에 이 특성이 필요하지 않지만 이 샘플에서는 이해를 돕기 위해 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-130">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="b24fe-131">사용자는 코드나 구성을 사용해 비슷한 `IContractBehavior``IEndpointBehavior` 또는 `IOperationBehavior`를 추가하여 수동으로 서로게이트를 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-131">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="b24fe-132">`IContractBehavior` 구현은 등록된 `DataContractSerializerOperationBehavior`가 있는지 확인하여 DataContract를 사용하는 작업을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-132">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="b24fe-133">작업에 이 동작이 있는 경우 해당 동작에서 `DataContractSurrogate` 속성이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-133">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="b24fe-134">다음 샘플 코드에서는 이를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-134">The following sample code shows how this is done.</span></span> <span data-ttu-id="b24fe-135">이 작업 동작에서 서로게이트를 설정하면 serialization 및 deserialization에 대해 사용할 수 있도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-135">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="b24fe-136">메타데이터 생성 도중 사용할 서로게이트를 플러그 인하기 위해 추가 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-136">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="b24fe-137">이를 수행하는 한 가지 메커니즘은 이 샘플에서 보여 주는 `IWsdlExportExtension`을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-137">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="b24fe-138">또 다른 방법은 `WsdlExporter`를 직접 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-138">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="b24fe-139">`AllowNonSerializableTypesAttribute`특성은 및를 구현 `IWsdlExportExtension` `IContractBehavior` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-139">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="b24fe-140">이 경우 확장은 또는 중 하나일 수 있습니다 `IContractBehavior` `IEndpointBehavior` .</span><span class="sxs-lookup"><span data-stu-id="b24fe-140">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="b24fe-141">해당 `IWsdlExportExtension.ExportContract` 메서드 구현은 DataContract에 대한 스키마 생성 도중 사용되는 `XsdDataContractExporter`에 추가하여 서로게이트를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-141">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="b24fe-142">다음 코드 조각에서는 이를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-142">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="b24fe-143">샘플을 실행하려면 클라이언트는 AddEmployee를 호출한 다음 GetEmployee를 호출하여 첫 번째 호출이 성공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-143">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="b24fe-144">GetEmployee 작업 요청의 결과는 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-144">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="b24fe-145">GetEmployee 작업은 직원을 찾고 "found"를 인쇄 하는 데 성공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-145">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b24fe-146">이 샘플에서는 직렬화, 역직렬화 및 메타데이터 생성을 위해 서로게이트를 플러그 인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-146">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="b24fe-147">메타데이터에서의 코드 생성을 위해 서로게이트를 플러그 인하는 방법을 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-147">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="b24fe-148">서로게이트를 사용 하 여 클라이언트 코드 생성을 연결 하는 방법에 대 한 샘플을 보려면 [사용자 지정 WSDL 게시](custom-wsdl-publication.md) 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b24fe-148">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b24fe-149">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="b24fe-149">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b24fe-150">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b24fe-151">C # 버전의 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b24fe-151">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b24fe-152">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b24fe-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b24fe-153">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b24fe-154">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b24fe-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b24fe-155">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b24fe-156">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b24fe-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
