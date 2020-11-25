---
title: DataSet 및 DataTable 보안 지침
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 8798c4542acc578c8f7f00c9b26cd01a0db20c42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726069"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="9fc4a-102">DataSet 및 DataTable 보안 지침</span><span class="sxs-lookup"><span data-stu-id="9fc4a-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="9fc4a-103">이 문서는 다음에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-103">This article applies to:</span></span>

* <span data-ttu-id="9fc4a-104">.NET Framework(모든 버전)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="9fc4a-105">.NET Core 이상</span><span class="sxs-lookup"><span data-stu-id="9fc4a-105">.NET Core and later</span></span>
* <span data-ttu-id="9fc4a-106">.NET 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="9fc4a-106">.NET 5.0 and later</span></span>

<span data-ttu-id="9fc4a-107">[DataSet](/dotnet/api/system.data.dataset) 및 [DataTable](/dotnet/api/system.data.datatable) 형식은 데이터 집합을 관리 되는 개체로 표현할 수 있도록 하는 레거시 .net 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="9fc4a-108">이러한 구성 요소는 .NET Framework 1.0에서 원래 [ADO.NET 인프라](./index.md)의 일부로 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-108">These components were introduced in .NET Framework 1.0 as part of the original [ADO.NET infrastructure](./index.md).</span></span> <span data-ttu-id="9fc4a-109">이러한 목표는 관계형 데이터 집합에 대 한 관리 되는 뷰를 제공 하 여 데이터의 기본 원본이 XML, SQL 또는 다른 기술 인지 여부를 추상화 하는 것 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="9fc4a-110">최신 데이터 뷰 패러다임을 비롯 한 ADO.NET에 대 한 자세한 내용은 [ADO.NET 설명서](../index.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](../index.md).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="9fc4a-111">XML에서 DataSet 또는 DataTable을 deserialize 할 때의 기본 제한 사항</span><span class="sxs-lookup"><span data-stu-id="9fc4a-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="9fc4a-112">지원 되는 모든 버전의 .NET Framework, .NET Core 및 .NET에서 `DataSet` `DataTable` deserialize 된 데이터에 표시 될 수 있는 개체 형식에 대해 다음과 같은 제한 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="9fc4a-113">기본적으로이 목록은 다음으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="9fc4a-114">기본 형식 및 해당 하는 기본 형식:,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `bool` `char` `sbyte` `byte` `short` `ushort` `int` `uint` `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` 및 `SqlString`</span><span class="sxs-lookup"><span data-stu-id="9fc4a-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="9fc4a-115">일반적으로 사용 되는 기본 형식이 아닌 `Type` , `Uri` 및 `BigInteger` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="9fc4a-116">일반적으로 사용 되는 _system.web_ ,,,,, `Color` `Point` `PointF` `Rectangle` `RectangleF` `Size` 및 `SizeF` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="9fc4a-117">`Enum` 종류.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-117">`Enum` types.</span></span>
* <span data-ttu-id="9fc4a-118">위 형식의 배열 및 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="9fc4a-119">들어오는 XML 데이터에이 목록에 없는 형식의 개체가 포함 된 경우:</span><span class="sxs-lookup"><span data-stu-id="9fc4a-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="9fc4a-120">다음 메시지 및 스택 추적을 사용 하 여 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-120">An exception is thrown with the following message and stack trace.</span></span>
<span data-ttu-id="9fc4a-121">오류 메시지: InvalidOperationException: Type ' \<Type Name\> , Version = \<n.n.n.n\> , Culture = \<culture\> , PublicKeyToken = \<token value\> '는 여기에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-121">Error Message: System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="9fc4a-122">[https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227)자세한 내용은을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-122">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>
<span data-ttu-id="9fc4a-123">스택 추적: System.Data.DataColumn.set_DataType (유형 값)에서 EnsureTypeIsAllowed (type 유형, StorageType typeCode)의 TypeLimiter (형식 유형, TypeLimiter capturedLimiter)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-123">Stack Trace: at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter) at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode) at System.Data.DataColumn.set_DataType(Type value)</span></span>

* <span data-ttu-id="9fc4a-124">Deserialization 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-124">The deserialization operation fails.</span></span>

<span data-ttu-id="9fc4a-125">XML `DataSet` 을 기존 또는 인스턴스로 로드할 때 `DataTable` 기존 열 정의도 고려 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-125">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="9fc4a-126">테이블에 사용자 지정 형식의 열 정의가 이미 포함 되어 있으면 해당 형식이 XML deserialization 작업 기간 동안 허용 목록에 일시적으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-126">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="9fc4a-127">에 열을 추가 하면가 `DataTable` `ReadXml` XML에서 스키마를 읽지 않으며 스키마가 일치 하지 않는 경우에도 레코드에서 읽지 않으므로이 메서드를 사용 하려면 모든 열을 직접 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-127">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

```csharp
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="9fc4a-128">를 사용 하 여 `XmlSerializer` 또는의 인스턴스를 deserialize 하는 경우에도 개체 형식 제한이 적용 됩니다 `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-128">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="9fc4a-129">그러나를 사용 하 여 `BinaryFormatter` 또는의 인스턴스를 deserialize 하는 경우에는 적용 되지 않을 수 있습니다 `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-129">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="9fc4a-130">를 사용 하는 경우 ( `DataAdapter.Fill` 예: `DataTable` XML deserialization api를 사용 하지 않고 인스턴스를 데이터베이스에서 직접 채우는 경우)에는 개체 유형 제한이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-130">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="9fc4a-131">허용 되는 형식 목록 확장</span><span class="sxs-lookup"><span data-stu-id="9fc4a-131">Extend the list of allowed types</span></span>

<span data-ttu-id="9fc4a-132">앱은 위에 나열 된 기본 제공 유형 외에도 사용자 지정 유형을 포함 하도록 허용 된 유형 목록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-132">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="9fc4a-133">허용 되는 유형 목록을 확장 하면 변경 내용이 _all_ `DataSet` 앱 내의 모든 및 인스턴스에 영향을 줍니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-133">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="9fc4a-134">형식은 기본 제공 허용 형식 목록에서 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-134">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="9fc4a-135">구성을 통해 확장 (.NET Framework 4.0-4.8)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-135">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="9fc4a-136">_App.config_ 를 사용 하 여 허용 되는 형식 목록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-136">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="9fc4a-137">허용 되는 유형 목록을 확장 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-137">To extend the allowed types list:</span></span>

* <span data-ttu-id="9fc4a-138">요소를 사용 `<configSections>` 하 여 _system.web_ 구성 섹션에 대 한 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-138">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="9fc4a-139">`<system.data.dataset.serialization>` / `<allowedTypes>` 를 사용 하 여 추가 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-139">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="9fc4a-140">각 `<add>` 요소는 해당 어셈블리의 정규화 된 형식 이름을 사용 하 여 하나의 형식만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-140">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="9fc4a-141">허용 되는 형식 목록에 다른 형식을 추가 하려면 여러 요소를 사용 `<add>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-141">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="9fc4a-142">다음 샘플에서는 사용자 지정 형식을 추가 하 여 허용 되는 형식 목록을 확장 하는 방법을 보여 줍니다 `Fabrikam.CustomType` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-142">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="9fc4a-143">형식의 어셈블리 정규화 된 이름을 검색 하려면 다음 코드에 나와 있는 것 처럼 [AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-143">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="9fc4a-144">구성을 통해 확장 (.NET Framework 2.0-3.5)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-144">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="9fc4a-145">앱이 2.0 또는 3.5 .NET Framework를 대상으로 하는 경우에도 위의 _App.config_ 메커니즘을 사용 하 여 허용 되는 유형 목록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-145">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="9fc4a-146">그러나 `<configSections>` 다음 코드와 같이 요소는 약간 다르게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-146">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="9fc4a-147">프로그래밍 방식으로 확장 (.NET Framework, .NET Core, .NET 5.0 이상)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-147">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="9fc4a-148">다음 코드에 표시 된 것 처럼 잘 _알려진 키를_ 사용 하는 경우에는 [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) 를 사용 하 여 허용 되는 형식 목록을 프로그래밍 방식으로 확장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-148">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```csharp
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="9fc4a-149">확장 메커니즘을 사용 하는 경우에는 key _system.object_ 와 연결 된 값 `Type[]` 이 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-149">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="9fc4a-150">.NET Framework에서 허용 되는 형식 목록은 _App.config_ 및를 사용 하 여 확장할 수 있습니다 `AppDomain.SetData` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-150">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="9fc4a-151">이 경우 `DataSet` 및 `DataTable` 는 해당 형식이 두 목록에 모두 있는 경우 데이터의 일부로 개체를 deserialize 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-151">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="9fc4a-152">감사 모드에서 앱 실행 (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-152">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="9fc4a-153">.NET Framework에서 `DataSet` 및 `DataTable` 는 감사 모드 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-153">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="9fc4a-154">감사 모드를 사용 하는 `DataSet` 경우 `DataTable` 들어오는 개체의 형식을 허용 되는 형식 목록과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-154">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="9fc4a-155">그러나 형식이 허용 되지 않는 개체를 볼 수 있는 경우에는 예외가 throw **되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-155">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="9fc4a-156">대신, `DataSet` 및 `DataTable` `TraceListener` 의심 스러운 형식이 존재 하는 연결 된 인스턴스를 모두 알리고에서 `TraceListener` 이 정보를 기록할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-156">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="9fc4a-157">예외가 throw 되지 않고 deserialization 작업이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-157">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="9fc4a-158">"감사 모드"에서 응용 프로그램을 실행 하는 것은 테스트에 사용 되는 임시 측정값이 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-158">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="9fc4a-159">감사 모드를 사용 하도록 설정 하 `DataSet` 고 `DataTable` 형식 제한을 적용 하지 않습니다 .이 경우 앱 내부에 보안 허점이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-159">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="9fc4a-160">자세한 내용은 [신뢰할 수 없는 입력과 관련 하 여](#swr) [모든 형식 제한](#ratr) 및 안전 제거 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-160">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="9fc4a-161">_App.config_ 를 통해 감사 모드를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-161">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="9fc4a-162">요소에 대 한 적절 한 값에 대 한 자세한 내용은이 문서의 [구성으로 확장](#etc) 섹션을 참조 하세요 `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-162">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="9fc4a-163">`<allowedTypes auditOnly="true">`다음 태그와 같이를 사용 하 여 감사 모드를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-163">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="9fc4a-164">감사 모드를 사용 하는 경우 _App.config_ 를 사용 하 여 기본 제공 `TraceListener` `DataSet` `TraceSource.` 추적 소스의 _System.Data.DataSet_ 이름을 system.string으로 기본 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-164">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="9fc4a-165">다음 샘플에서는 콘솔 _및_ 디스크의 로그 파일에 추적 이벤트를 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-165">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="9fc4a-166">및에 대 한 자세한 내용은 `TraceSource` `TraceListener` [방법: 추적 수신기와 함께 TraceSource 및 필터 사용](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-166">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9fc4a-167">감사 모드에서 응용 프로그램을 실행 하는 것은 .NET Core 또는 .NET 5.0 이상에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-167">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="9fc4a-168">모든 형식 제한 제거</span><span class="sxs-lookup"><span data-stu-id="9fc4a-168">Remove all type restrictions</span></span>

<span data-ttu-id="9fc4a-169">앱이 및에서 모든 형식 제한 제한을 제거 해야 `DataSet` 하는 경우 `DataTable` 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-169">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="9fc4a-170">형식 제한 제한을 표시 하지 않는 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-170">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="9fc4a-171">사용할 수 있는 옵션은 앱이 대상으로 하는 프레임 워크에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-171">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="9fc4a-172">모든 형식 제한을 제거 하면 앱 내에 보안 허점이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-172">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="9fc4a-173">이 메커니즘을 사용 하는 경우 앱에서 **not** `DataSet` 또는를 사용 `DataTable` 하 여 신뢰할 수 없는 입력을 읽지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-173">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="9fc4a-174">자세한 내용은 [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) 및 [신뢰할 수 없는 입력과 관련 하 여](#swr)다음 섹션의 안전성을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-174">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="9fc4a-175">AppContext 구성 (.NET Framework 4.6-4.8, .NET Core 2.1 이상, .NET 5.0 이상)을 통해</span><span class="sxs-lookup"><span data-stu-id="9fc4a-175">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="9fc4a-176">`AppContext`스위치를 `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 로 설정 하면 `true` 및에서 모든 형식 제한 제한이 제거 됩니다 `DataSet` `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-176">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="9fc4a-177">.NET Framework에서 다음 구성에 표시 된 것 처럼 _App.config_ 를 통해이 스위치를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-177">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="9fc4a-178">ASP.NET에서는 요소를 `<AppContextSwitchOverrides>` 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-178">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="9fc4a-179">대신 다음 구성에 표시 된 것 처럼 _Web.config_ 를 통해 스위치를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-179">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="9fc4a-180">자세한 내용은 요소를 참조 하세요 [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-180">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="9fc4a-181">.NET Core, .NET 5 및 ASP.NET Core에서이 설정은 다음 JSON에 표시 된 것 처럼 _runtimeconfig.js에_ 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-181">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="9fc4a-182">자세한 내용은 [".Net Core 런타임 구성 설정"](../../../../core/run-time-config/index.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-182">For more information, see [".NET Core run-time configuration settings"](../../../../core/run-time-config/index.md).</span></span>

<span data-ttu-id="9fc4a-183">`AllowArbitraryDataSetTypeInstantiation` 는 다음 코드와 같이 구성 파일을 사용 하는 대신 [Appcontext. SetSwitch](/dotnet/api/system.appcontext.setswitch) 를 통해 프로그래밍 방식으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-183">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```csharp
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="9fc4a-184">위의 프로그래밍 방식을 선택 하는 경우에 대 한 호출은 `AppContext.SetSwitch` 앱 시작 초기에 발생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-184">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="9fc4a-185">시스템 수준 레지스트리를 통해 (.NET Framework 2.0-4.8)</span><span class="sxs-lookup"><span data-stu-id="9fc4a-185">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="9fc4a-186">`AppContext`을 사용할 수 없는 경우 Windows 레지스트리를 사용 하 여 형식 제한 검사를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-186">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="9fc4a-187">관리자가 레지스트리를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-187">An administrator must configure the registry.</span></span>
* <span data-ttu-id="9fc4a-188">레지스트리를 사용 하는 것은 시스템 전체에서 변경 되며 컴퓨터에서 실행 되는 _모든_ 앱에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-188">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="9fc4a-189">Type</span><span class="sxs-lookup"><span data-stu-id="9fc4a-189">Type</span></span>  |  <span data-ttu-id="9fc4a-190">값</span><span class="sxs-lookup"><span data-stu-id="9fc4a-190">Value</span></span> |
|---|---|
| <span data-ttu-id="9fc4a-191">**레지스트리 키**</span><span class="sxs-lookup"><span data-stu-id="9fc4a-191">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="9fc4a-192">**값 이름**</span><span class="sxs-lookup"><span data-stu-id="9fc4a-192">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="9fc4a-193">**값 유형**</span><span class="sxs-lookup"><span data-stu-id="9fc4a-193">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="9fc4a-194">**값 데이터**</span><span class="sxs-lookup"><span data-stu-id="9fc4a-194">**Value data**</span></span> | `true` |

<span data-ttu-id="9fc4a-195">64 비트 운영 체제에서이 값은 64 비트 키 (위에 표시 됨) 및 32 비트 키 모두에 대해 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-195">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="9fc4a-196">32 비트 키는에 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-196">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="9fc4a-197">를 구성 하는 데 레지스트리를 사용 하는 방법에 대 한 자세한 내용은 `AppContext` ["라이브러리 소비자를 위한 appcontext"](/dotnet/api/system.appcontext#appcontext-for-library-consumers)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-197">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="9fc4a-198">신뢰할 수 없는 입력과 관련 된 안전</span><span class="sxs-lookup"><span data-stu-id="9fc4a-198">Safety with regard to untrusted input</span></span>

<span data-ttu-id="9fc4a-199">`DataSet`및는 `DataTable` XML 페이로드를 deserialize 하는 동안 나타날 수 있는 형식에 대 한 기본 제한 사항을 적용 하며, 신뢰할 수 없는 __`DataSet` `DataTable` 입력으로 채워질 때 일반적으로 안전 하지 않습니다.__</span><span class="sxs-lookup"><span data-stu-id="9fc4a-199">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="9fc4a-200">다음은 `DataSet` 또는 `DataTable` 인스턴스가 신뢰할 수 없는 입력을 읽을 수 있는 방법에 대 한 완전 하지 않은 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-200">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="9fc4a-201">는 `DataAdapter` 데이터베이스를 참조 하 고 `DataAdapter.Fill` 메서드는를 `DataSet` 데이터베이스 쿼리의 내용으로 채우는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-201">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="9fc4a-202">`DataSet.ReadXml`또는 `DataTable.ReadXml` 메서드는 열 및 행 정보를 포함 하는 XML 파일을 읽는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-202">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="9fc4a-203">`DataSet`또는 `DataTable` 인스턴스는 ASP.NET (SOAP) 웹 서비스 또는 WCF 끝점의 일부로 serialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-203">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="9fc4a-204">와 같은 serializer는 `XmlSerializer` `DataSet` XML 스트림에서 또는 인스턴스를 deserialize 하는 데 사용 됩니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-204">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="9fc4a-205">와 같은 serializer는 `JsonConvert` `DataSet` JSON 스트림에서 또는 인스턴스를 deserialize 하는 데 사용 됩니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-205">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="9fc4a-206">`JsonConvert` 는 라이브러리의 인기 있는 타사 [Newtonsoft.Js](https://www.newtonsoft.com/json) 의 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-206">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="9fc4a-207">와 같은 serializer는 `BinaryFormatter` `DataSet` 원시 바이트 스트림에서 또는 인스턴스를 deserialize 하는 데 사용 됩니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-207">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="9fc4a-208">이 문서에서는 위의 시나리오에 대 한 안전 고려 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-208">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="9fc4a-209">를 사용 `DataAdapter.Fill` 하 여 `DataSet` 신뢰할 수 없는 데이터 소스에서를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-209">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="9fc4a-210">`DataSet` `DataAdapter` 다음 예제와 같이 [ `DataAdapter.Fill` 메서드](/dotnet/api/system.data.common.dataadapter.fill)를 사용 하 여에서 인스턴스를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-210">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```csharp
// Assumes that connection is a valid SqlConnection object.
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);

DataSet customers = new DataSet();
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="9fc4a-211">위의 코드 샘플은 [DataAdapter에서 데이터 집합을 채울](../populating-a-dataset-from-a-dataadapter.md)때 발견 되는 더 큰 샘플의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-211">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="9fc4a-212">대부분의 앱은 데이터베이스 계층이 신뢰 되는 것으로 단순화 하 고 가정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-212">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="9fc4a-213">그러나 앱을 [모델링](https://www.microsoft.com/securityengineering/sdl/threatmodeling) 하는 것이 습관 인 경우 위협 모델은 응용 프로그램 (클라이언트)과 데이터베이스 계층 (서버) 간에 트러스트 경계가 될 것으로 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-213">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="9fc4a-214">클라이언트와 서버 간의 [상호 인증](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) 또는 [AAD 인증](/azure/azure-sql/database/authentication-aad-overview) 을 사용 하는 것은이와 관련 된 위험을 해결 하는 한 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-214">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="9fc4a-215">이 섹션의 나머지 부분에서는 신뢰할 수 없는 서버에 연결 하는 클라이언트의 가능한 결과에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-215">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="9fc4a-216">`DataAdapter`신뢰할 수 없는 데이터 소스에서를 가리키는 경우의 결과는 자체의 구현에 따라 달라 집니다 `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-216">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="9fc4a-217">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="9fc4a-217">SqlDataAdapter</span></span>

<span data-ttu-id="9fc4a-218">기본 제공 형식 [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)의 경우 신뢰할 수 없는 데이터 원본을 참조 하면 dos (서비스 거부) 공격이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-218">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="9fc4a-219">DoS 공격으로 인해 앱이 응답 하지 않거나 작동이 중단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-219">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="9fc4a-220">공격자가 응용 프로그램과 함께 DLL을 공장 화 하는 경우 로컬 코드 실행을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-220">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="9fc4a-221">기타 DataAdapter 형식</span><span class="sxs-lookup"><span data-stu-id="9fc4a-221">Other DataAdapter types</span></span>

<span data-ttu-id="9fc4a-222">타사 구현에서는 `DataAdapter` 신뢰할 수 없는 입력을 통해 제공 되는 보안 보증에 대 한 자체 평가를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-222">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="9fc4a-223">.NET에서는 이러한 구현과 관련 된 안전을 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-223">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="9fc4a-224">ReadXml 및 DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="9fc4a-224">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="9fc4a-225">`DataSet.ReadXml`및 `DataTable.ReadXml` 메서드는 신뢰할 수 없는 입력과 함께 사용할 경우 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-225">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="9fc4a-226">대신이 문서의 뒷부분에서 설명 하는 대체 방법 중 하나를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-226">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="9fc4a-227">및의 구현은 `DataSet.ReadXml` `DataTable.ReadXml` serialization 취약점이 잘 이해 된 위협 범주 였습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-227">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="9fc4a-228">따라서 코드는 현재 보안 모범 사례를 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-228">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="9fc4a-229">이러한 Api는 공격자가 웹 앱에 대해 DoS 공격을 수행할 수 있는 벡터로 사용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-229">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="9fc4a-230">이러한 공격으로 인해 웹 서비스가 응답 하지 않거나 예기치 않은 프로세스가 종료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-230">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="9fc4a-231">프레임 워크는 이러한 공격 범주에 대 한 완화를 제공 하지 않으며 .NET은이 동작을 "의도적으로" 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-231">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="9fc4a-232">.NET은 및에서 정보 공개 또는 원격 코드 실행과 같은 일부 문제를 완화 하기 위해 보안 업데이트를 릴리스 했습니다 `DataSet.ReadXml` `DataTable.ReadXml` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-232">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="9fc4a-233">.NET 보안 업데이트는 이러한 위협 범주에 대 한 완전 한 보호를 제공 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-233">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="9fc4a-234">소비자는 개별 시나리오를 평가하고 이러한 위험에 노출될 가능성을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-234">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="9fc4a-235">소비자는 이러한 Api에 대 한 보안 업데이트가 일부 상황에서 응용 프로그램 호환성에 영향을 줄 수 있음을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-235">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="9fc4a-236">또한 이러한 Api의 novel 취약성은 .NET에서 실제로 보안 업데이트를 게시할 수 없는 것으로 검색 될 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-236">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="9fc4a-237">이러한 Api의 소비자는 다음 중 하나를 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-237">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="9fc4a-238">이 문서의 뒷부분에 설명 된 대체 방법 중 하나를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-238">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="9fc4a-239">앱에서 개별 위험 평가를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-239">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="9fc4a-240">이러한 Api를 활용할 지 여부를 결정 하는 것은 소비자의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-240">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="9fc4a-241">소비자는 이러한 Api를 사용 하 여 제공할 수 있는 규정 요구 사항을 비롯 하 여 보안, 기술 및 법적 위험을 평가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-241">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="9fc4a-242">ASP.NET 웹 서비스 또는 WCF를 통한 DataSet 및 DataTable</span><span class="sxs-lookup"><span data-stu-id="9fc4a-242">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="9fc4a-243">`DataSet` `DataTable` 다음 코드에서 보여 주는 것 처럼 ASP.NET (SOAP) 웹 서비스에서 또는 인스턴스를 받아들일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-243">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```csharp
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="9fc4a-244">이에 대 한 변형은 `DataSet` `DataTable` 다음 코드에 표시 된 것 처럼 전체 SOAP 직렬화 된 개체 그래프의 일부로이를 허용 하는 대신 또는 매개 변수로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-244">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```csharp
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="9fc4a-245">또는 ASP.NET 웹 서비스 대신 WCF를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-245">Or, using WCF instead of ASP.NET web services:</span></span>

```csharp
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="9fc4a-246">이러한 모든 경우에 위협 모델 및 보안 보장은 [ReadXml 및 ReadXml 섹션과](#dsrdtr)동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-246">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="9fc4a-247">XmlSerializer를 통해 데이터 집합 또는 DataTable Deserialize</span><span class="sxs-lookup"><span data-stu-id="9fc4a-247">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="9fc4a-248">개발자는 `XmlSerializer` 다음 코드와 같이를 사용 하 여 `DataSet` 및 인스턴스를 deserialize 할 수 있습니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-248">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```csharp
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="9fc4a-249">이러한 경우 위협 모델 및 보안 보장은 [ReadXml 및 ReadXml 섹션과](#dsrdtr) 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-249">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="9fc4a-250">JsonConvert를 통해 데이터 집합 또는 DataTable Deserialize</span><span class="sxs-lookup"><span data-stu-id="9fc4a-250">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="9fc4a-251">다음 코드에 표시 된 것 처럼 인기 있는 타사 Newtonsoft.json library [JSON.NET](https://www.newtonsoft.com/json) 를 사용 하 여 `DataSet` 및 인스턴스를 deserialize 할 수 있습니다 `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-251">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```csharp
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObject<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObject<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="9fc4a-252">`DataSet` `DataTable` 트러스트 되지 않은 JSON blob에서 또는를이 방식으로 deserialize 하는 것은 안전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-252">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="9fc4a-253">이 패턴은 서비스 거부 공격에 취약 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-253">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="9fc4a-254">이러한 공격으로 인해 앱이 중단 되거나 응답 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-254">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="9fc4a-255">Microsoft는 _Newtonsoft.Js_ 와 같은 타사 라이브러리의 구현을 보증 하거나 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-255">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="9fc4a-256">이 정보는 완전성을 위해 제공 되며이 정보를 작성 하는 시간을 정확 하 게 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-256">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="9fc4a-257">BinaryFormatter를 통해 데이터 집합 또는 DataTable Deserialize</span><span class="sxs-lookup"><span data-stu-id="9fc4a-257">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="9fc4a-258">개발자 `BinaryFormatter` `NetDataContractSerializer` 는,, `SoapFormatter` 또는 관련 \***unsafe** _ 포맷터를 사용 하 여 `DataSet` `DataTable` 신뢰할 수 없는 페이로드에서 또는 인스턴스를 deserialize 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-258">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related \***unsafe** _ formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

<span data-ttu-id="9fc4a-259">_이는 전체 원격 코드 실행 공격에 취약 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-259">_ This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="9fc4a-260">`SerializationBinder`이러한 공격을 방지 하기 위해 사용자 지정을 사용 하는 것 만으로는 충분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-260">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="9fc4a-261">안전한 대체</span><span class="sxs-lookup"><span data-stu-id="9fc4a-261">Safe replacements</span></span>

<span data-ttu-id="9fc4a-262">다음 중 하나에 해당 하는 앱:</span><span class="sxs-lookup"><span data-stu-id="9fc4a-262">For apps that either:</span></span>

* <span data-ttu-id="9fc4a-263">`DataSet` `DataTable` .Asmx SOAP 끝점 또는 WCF 끝점을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-263">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="9fc4a-264">신뢰할 수 없는 데이터를 또는 인스턴스로 `DataSet` Deserialize `DataTable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-264">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="9fc4a-265">[Entity Framework](/ef)사용 하려면 개체 모델을 대체 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-265">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="9fc4a-266">Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="9fc4a-266">Entity Framework:</span></span>

* <span data-ttu-id="9fc4a-267">는 관계형 데이터를 나타낼 수 있는 풍부 하 고 현대적인 개체 지향 프레임 워크입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-267">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="9fc4a-268">는 데이터베이스 공급자의 [다양 한 에코 시스템](/ef/core/providers/) 을 제공 하 여 Entity Framework 개체 모델을 통해 쉽게 데이터베이스 쿼리를 수행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-268">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="9fc4a-269">는 신뢰할 수 없는 소스의 데이터를 deserialize 할 때 기본 제공 보호 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-269">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="9fc4a-270">SOAP 끝점을 사용 하는 앱의 경우 `.aspx` [WCF](../../../wcf/index.md)를 사용 하도록 해당 끝점을 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-270">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](../../../wcf/index.md).</span></span> <span data-ttu-id="9fc4a-271">WCF는 웹 서비스에 대 한 보다 완전 한 기능을 갖춘 대체 기능입니다 `.asmx` .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-271">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="9fc4a-272">WCF 끝점은 기존 호출자와의 호환성을 위해 [SOAP를 통해 노출 될 수 있습니다](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) .</span><span class="sxs-lookup"><span data-stu-id="9fc4a-272">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="9fc4a-273">코드 분석기</span><span class="sxs-lookup"><span data-stu-id="9fc4a-273">Code analyzers</span></span>

<span data-ttu-id="9fc4a-274">소스 코드를 컴파일할 때 실행 되는 코드 분석기 보안 규칙은 c # 및 Visual Basic 코드에서이 보안 문제와 관련 된 취약성을 찾는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-274">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="9fc4a-275">FxCopAnalyzers는 [nuget.org](https://www.nuget.org/)에 배포 되는 코드 분석기의 NuGet 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-275">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="9fc4a-276">코드 분석기의 개요는 [소스 코드 분석기 개요](/visualstudio/code-quality/roslyn-analyzers-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-276">For an overview of code analyzers, see [Overview of source code analyzers](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="9fc4a-277">다음 FxCopAnalyzers 규칙을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-277">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="9fc4a-278">[CA2350](/visualstudio/code-quality/ca2350): 신뢰할 수 없는 데이터와 함께 ReadXml ()를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-278">[CA2350](/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="9fc4a-279">[CA2351](/visualstudio/code-quality/ca2351): 신뢰할 수 없는 데이터와 ReadXml ()를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-279">[CA2351](/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="9fc4a-280">[CA2352](/visualstudio/code-quality/ca2352): 안전 하지 않은 데이터 집합 또는 serialize 할 수 있는 형식의 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-280">[CA2352](/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="9fc4a-281">[CA2353](/visualstudio/code-quality/ca2353): serializable 형식의 안전 하지 않은 데이터 집합 또는 DataTable</span><span class="sxs-lookup"><span data-stu-id="9fc4a-281">[CA2353](/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="9fc4a-282">[CA2354](/visualstudio/code-quality/ca2354): deserialize 된 개체 그래프의 안전 하지 않은 데이터 집합 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-282">[CA2354](/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="9fc4a-283">[CA2355](/visualstudio/code-quality/ca2355): deserialize 가능한 개체 그래프에 안전 하지 않은 데이터 집합 또는 DataTable 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-283">[CA2355](/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="9fc4a-284">[CA2356](/visualstudio/code-quality/ca2356): web deserialize 가능한 개체 그래프의 안전 하지 않은 데이터 집합 또는 DataTable 형식</span><span class="sxs-lookup"><span data-stu-id="9fc4a-284">[CA2356](/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="9fc4a-285">[CA2361](/visualstudio/code-quality/ca2361): ReadXml ()를 포함 하는 자동 생성 된 클래스가 신뢰할 수 없는 데이터와 함께 사용 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-285">[CA2361](/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="9fc4a-286">[CA2362](/visualstudio/code-quality/ca2362): 자동 생성 serialize 할 수 있는 형식에서 안전 하지 않은 데이터 집합 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-286">[CA2362](/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="9fc4a-287">규칙을 구성 하는 방법에 대 한 자세한 내용은 [코드 분석기 사용](/visualstudio/code-quality/use-roslyn-analyzers)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-287">For more information about configuring rules, see [Use code analyzers](/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="9fc4a-288">새 보안 규칙은 다음 NuGet 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc4a-288">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="9fc4a-289">FxCopAnalyzers 3.3.0: Visual Studio 2019 버전 16.3 이상</span><span class="sxs-lookup"><span data-stu-id="9fc4a-289">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="9fc4a-290">FxCopAnalyzers 2.9.11: Visual Studio 2017 버전 15.9 이상</span><span class="sxs-lookup"><span data-stu-id="9fc4a-290">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
