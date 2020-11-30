---
title: XML Schema Definition Tool (Xsd.exe)
description: XML Serializer Generator는 지정된 어셈블리의 형식에 대한 XML serialization 어셈블리를 만들어 XmlSerializer의 시작 성능을 향상시킵니다.
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: a66ebfee3a461bb800e61e4f1d789f497da2f9d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676610"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="decea-103">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="decea-103">XML Schema Definition Tool (Xsd.exe)</span></span>

<span data-ttu-id="decea-104">XML 스키마 정의 도구(Xsd.exe)를 사용하면 XDR, XML 및 XSD 파일 또는 런타임 어셈블리의 클래스에서 XML 스키마 또는 공용 언어 런타임 클래스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-104">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>

<span data-ttu-id="decea-105">XML 스키마 정의 도구(Xsd.exe)는 일반적으로 다음 path:\에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-105">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:\</span></span>
<span data-ttu-id="decea-106">_C:\\Program Files(x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="decea-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

## <a name="syntax"></a><span data-ttu-id="decea-107">구문</span><span class="sxs-lookup"><span data-stu-id="decea-107">Syntax</span></span>

<span data-ttu-id="decea-108">명령줄에서 도구를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-108">Run the tool from the command line.</span></span>

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> <span data-ttu-id="decea-109">.NET Framework 도구가 제대로 작동하려면 `Path`, `Include` 및 `Lib` 환경 변수를 올바르게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-109">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="decea-110">\<SDK>\\\<version>\Bin 디렉터리에 있는 SDKVars.bat를 실행하여 이러한 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-110">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\\\<version>\Bin directory.</span></span> <span data-ttu-id="decea-111">SDKVars.bat를 모든 명령 셸에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-111">SDKVars.bat must be executed in every command shell.</span></span>

## <a name="argument"></a><span data-ttu-id="decea-112">인수</span><span class="sxs-lookup"><span data-stu-id="decea-112">Argument</span></span>

|<span data-ttu-id="decea-113">인수</span><span class="sxs-lookup"><span data-stu-id="decea-113">Argument</span></span>|<span data-ttu-id="decea-114">설명</span><span class="sxs-lookup"><span data-stu-id="decea-114">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="decea-115">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="decea-115">*file.extension*</span></span>|<span data-ttu-id="decea-116">변환할 입력 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-116">Specifies the input file to convert.</span></span> <span data-ttu-id="decea-117">확장명을 .xdr, .xml, .xsd, .dll 또는 .exe 중 하나로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-117">You must specify the extension as one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="decea-118">XDR 스키마 파일(.xdr 확장명)을 지정하면 Xsd.exe는 XDR 스키마를 XSD 스키마로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-118">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="decea-119">출력 파일의 이름은 XDR 스키마와 동일하지만 확장명은 .xsd입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-119">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="decea-120">XML 파일(.xml 확장명)을 지정하면 Xsd.exe는 해당 파일에 있는 데이터에서 스키마를 유추하여 XSD 스키마가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-120">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="decea-121">출력 파일의 이름은 XML 파일과 동일하지만 확장명은 .xsd입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-121">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="decea-122">XML 스키마 파일(.xsd 확장명)을 지정하면 해당 XML 스키마에 해당하는 런타임 개체에 대한 소스 코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-122">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="decea-123">런타임 어셈블리 파일(.exe 또는 .dll 확장명)을 지정하면 해당 어셈블리에 있는 하나 이상의 형식에 대해 스키마가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-123">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="decea-124">`/type` 옵션을 사용하면 스키마를 생성할 대상 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-124">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="decea-125">출력 스키마의 이름은 schema0.xsd, schema1.xsd 등과 같이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-125">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="decea-126">지정된 형식에서 `XMLRoot` 사용자 지정 특성을 사용하여 네임스페이스를 지정하는 경우에만 여러 개의 스키마가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-126">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|

## <a name="general-options"></a><span data-ttu-id="decea-127">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="decea-127">General Options</span></span>

|<span data-ttu-id="decea-128">옵션</span><span class="sxs-lookup"><span data-stu-id="decea-128">Option</span></span>|<span data-ttu-id="decea-129">설명</span><span class="sxs-lookup"><span data-stu-id="decea-129">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="decea-130">**/h\[elp\]**</span><span class="sxs-lookup"><span data-stu-id="decea-130">**/h\[elp\]**</span></span>|<span data-ttu-id="decea-131">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-131">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="decea-132">**/o\[utputdir\]:** _directory_</span><span class="sxs-lookup"><span data-stu-id="decea-132">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="decea-133">출력 파일의 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-133">Specifies the directory for output files.</span></span> <span data-ttu-id="decea-134">이 인수는 한 번만 나타날 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="decea-134">This argument can appear only once.</span></span> <span data-ttu-id="decea-135">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-135">The default is the current directory.</span></span>|
|<span data-ttu-id="decea-136">**/?**</span><span class="sxs-lookup"><span data-stu-id="decea-136">**/?**</span></span>|<span data-ttu-id="decea-137">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-137">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="decea-138">**/p\[arameters\]:** _file.xml_</span><span class="sxs-lookup"><span data-stu-id="decea-138">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="decea-139">지정한 .xml 파일의 여러 가지 작동 모드에 대한 읽기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-139">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="decea-140">약식 표현은 `/p:`입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-140">The short form is `/p:`.</span></span> <span data-ttu-id="decea-141">자세한 내용은 [설명](#remarks) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="decea-141">For more information, see the [Remarks](#remarks) section.</span></span>|

## <a name="xsd-file-options"></a><span data-ttu-id="decea-142">XSD 파일 옵션</span><span class="sxs-lookup"><span data-stu-id="decea-142">XSD File Options</span></span>

 <span data-ttu-id="decea-143">.xsd 파일에는 다음 옵션 중 하나만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-143">You must specify only one of the following options for .xsd files.</span></span>

|<span data-ttu-id="decea-144">옵션</span><span class="sxs-lookup"><span data-stu-id="decea-144">Option</span></span>|<span data-ttu-id="decea-145">설명</span><span class="sxs-lookup"><span data-stu-id="decea-145">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="decea-146">**/c\[lasses\]**</span><span class="sxs-lookup"><span data-stu-id="decea-146">**/c\[lasses\]**</span></span>|<span data-ttu-id="decea-147">지정된 스키마에 해당하는 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-147">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="decea-148">XML 데이터를 개체로 읽어오려면 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-148">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="decea-149">**/d\[ataset\]**</span><span class="sxs-lookup"><span data-stu-id="decea-149">**/d\[ataset\]**</span></span>|<span data-ttu-id="decea-150">지정된 스키마에 해당하는 <xref:System.Data.DataSet>에서 파생된 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-150">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="decea-151">XML 데이터를 파생 클래스로 읽어오려면 <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-151">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|

 <span data-ttu-id="decea-152">.xsd 파일에는 다음 옵션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-152">You can also specify any of the following options for .xsd files.</span></span>

|<span data-ttu-id="decea-153">옵션</span><span class="sxs-lookup"><span data-stu-id="decea-153">Option</span></span>|<span data-ttu-id="decea-154">설명</span><span class="sxs-lookup"><span data-stu-id="decea-154">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="decea-155">**/e\[lement\]:** _element_</span><span class="sxs-lookup"><span data-stu-id="decea-155">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="decea-156">코드를 생성할 대상 스키마 요소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-156">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="decea-157">기본적으로 모든 요소가 입력되며,</span><span class="sxs-lookup"><span data-stu-id="decea-157">By default all elements are typed.</span></span> <span data-ttu-id="decea-158">이 인수는 한 번 이상 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-158">You can specify this argument more than once.</span></span>|
|<span data-ttu-id="decea-159">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="decea-159">**/enableDataBinding**</span></span>|<span data-ttu-id="decea-160">생성된 모든 형식에 <xref:System.ComponentModel.INotifyPropertyChanged> 인터페이스를 구현하여 데이터 바인딩을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-160">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="decea-161">약식 표현은 `/edb`입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-161">The short form is `/edb`.</span></span>|
|<span data-ttu-id="decea-162">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="decea-162">**/enableLinqDataSet**</span></span>|<span data-ttu-id="decea-163">(약식: `/eld`.) 생성된 DataSet을 LINQ to DataSet을 사용하여 쿼리할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-163">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="decea-164">이 옵션은 /dataset 옵션이 지정된 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-164">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="decea-165">자세한 내용은 [LINQ to DataSet 개요](../../framework/data/adonet/linq-to-dataset-overview.md) 및 [형식화된 데이터 세트 쿼리](../../framework/data/adonet/querying-typed-datasets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="decea-165">For more information, see [LINQ to DataSet Overview](../../framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="decea-166">LINQ 사용에 대한 일반적인 정보는 [LINQ(Language-Integrated Query) - C# ](../../csharp/programming-guide/concepts/linq/index.md) 또는 [LINQ(Language-Integrated Query) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="decea-166">For general information about using LINQ, see [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>|
|<span data-ttu-id="decea-167">**/f\[ields\]**</span><span class="sxs-lookup"><span data-stu-id="decea-167">**/f\[ields\]**</span></span>|<span data-ttu-id="decea-168">속성 대신 필드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-168">Generates fields instead of properties.</span></span> <span data-ttu-id="decea-169">기본적으로 속성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-169">By default, properties are generated.</span></span>|
|<span data-ttu-id="decea-170">**/l\[anguage\]:** _language_</span><span class="sxs-lookup"><span data-stu-id="decea-170">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="decea-171">사용할 프로그래밍 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-171">Specifies the programming language to use.</span></span> <span data-ttu-id="decea-172">`CS`(C#, 기본값), `VB`(Visual Basic), `JS`(JScript) 또는 `VJS`(Visual J#) 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-172">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="decea-173"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>를 구현하는 클래스의 정규화된 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-173">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|
|<span data-ttu-id="decea-174">**/n\[amespace\]:** _namespace_</span><span class="sxs-lookup"><span data-stu-id="decea-174">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="decea-175">생성된 형식에 대한 런타임 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-175">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="decea-176">기본 네임스페이스는 `Schemas`입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-176">The default namespace is `Schemas`.</span></span>|
|<span data-ttu-id="decea-177">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="decea-177">**/nologo**</span></span>|<span data-ttu-id="decea-178">배너를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-178">Suppresses the banner.</span></span>|
|<span data-ttu-id="decea-179">**/order**</span><span class="sxs-lookup"><span data-stu-id="decea-179">**/order**</span></span>|<span data-ttu-id="decea-180">모든 파티클 멤버에 대해 명시적인 순서 식별자를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-180">Generates explicit order identifiers on all particle members.</span></span>|
|<span data-ttu-id="decea-181">**/o\[ut\]:** _directoryName_</span><span class="sxs-lookup"><span data-stu-id="decea-181">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="decea-182">파일을 배치할 출력 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-182">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="decea-183">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-183">The default is the current directory.</span></span>|
|<span data-ttu-id="decea-184">**/u\[ri\]:** _uri_</span><span class="sxs-lookup"><span data-stu-id="decea-184">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="decea-185">코드를 생성할 대상 스키마 요소의 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-185">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="decea-186">이 URI가 존재하는 경우 `/element` 옵션을 사용하여 지정된 모든 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-186">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|

## <a name="dll-and-exe-file-options"></a><span data-ttu-id="decea-187">DLL 및 EXE 파일 옵션</span><span class="sxs-lookup"><span data-stu-id="decea-187">DLL and EXE File Options</span></span>

|<span data-ttu-id="decea-188">옵션</span><span class="sxs-lookup"><span data-stu-id="decea-188">Option</span></span>|<span data-ttu-id="decea-189">설명</span><span class="sxs-lookup"><span data-stu-id="decea-189">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="decea-190">**/t\[ype\]:** _typename_</span><span class="sxs-lookup"><span data-stu-id="decea-190">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="decea-191">스키마를 생성할 대상 형식의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-191">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="decea-192">여러 개의 형식 인수를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-192">You can specify multiple type arguments.</span></span> <span data-ttu-id="decea-193">*typename* 에서 네임스페이스를 지정하지 않으면 Xsd.exe는 해당 어셈블리의 모든 형식과 지정된 형식을 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="decea-193">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="decea-194">*typename* 에서 네임스페이스를 지정하면 지정한 형식만 일치됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-194">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="decea-195">*typename* 이 별표(\*)로 끝나는 경우에는 \* 앞의 문자열로 시작하는 모든 형식이 일치됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-195">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="decea-196">`/type` 옵션을 생략하면 Xsd.exe는 해당 어셈블리의 모든 형식에 대해 스키마가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-196">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|

## <a name="remarks"></a><span data-ttu-id="decea-197">설명</span><span class="sxs-lookup"><span data-stu-id="decea-197">Remarks</span></span>

<span data-ttu-id="decea-198">다음 표에서는 Xsd.exe에서 수행되는 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="decea-198">The following table shows the operations that Xsd.exe performs.</span></span>

| | |
|------------|-----------------|
|<span data-ttu-id="decea-199">XDR에서 XSD로</span><span class="sxs-lookup"><span data-stu-id="decea-199">XDR to XSD</span></span>|<span data-ttu-id="decea-200">XDR 스키마 파일에서 XML 스키마를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-200">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="decea-201">XDR은 XML 기반 스키마의 초기 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-201">XDR is an early XML-based schema format.</span></span>|
|<span data-ttu-id="decea-202">XML에서 XSD로</span><span class="sxs-lookup"><span data-stu-id="decea-202">XML to XSD</span></span>|<span data-ttu-id="decea-203">XML 파일에서 XML 스키마를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-203">Generates an XML schema from an XML file.</span></span>|
|<span data-ttu-id="decea-204">XSD에서 DataSet으로</span><span class="sxs-lookup"><span data-stu-id="decea-204">XSD to DataSet</span></span>|<span data-ttu-id="decea-205">XSD 스키마 파일에서 공용 언어 런타임 <xref:System.Data.DataSet> 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-205">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="decea-206">이렇게 생성된 클래스에서는 일반 XML 데이터에 대한 강력한 개체 모델이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-206">The generated classes provide a rich object model for regular XML data.</span></span>|
|<span data-ttu-id="decea-207">XSD에서 클래스로</span><span class="sxs-lookup"><span data-stu-id="decea-207">XSD to Classes</span></span>|<span data-ttu-id="decea-208">XSD 스키마 파일에서 런타임 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-208">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="decea-209">이렇게 생성된 클래스를 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>와 함께 사용하면 해당 스키마를 따르는 XML 코드를 읽고 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-209">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>|
|<span data-ttu-id="decea-210">클래스를 XSD로</span><span class="sxs-lookup"><span data-stu-id="decea-210">Classes to XSD</span></span>| <span data-ttu-id="decea-211">런타임 어셈블리 파일의 형식에서 XML 스키마를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-211">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="decea-212">생성된 스키마는 <xref:System.Xml.Serialization.XmlSerializer>에서 사용하는 XML 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-212">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|

 <span data-ttu-id="decea-213">Xsd.exe를 사용하면 W3C(World Wide Web 컨소시엄)에서 제시하는 XSD(XML Schema Definition) 언어를 따르는 XML 스키마만 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-213">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="decea-214">XML 스키마 정의 제안 또는 XML 표준에 대한 자세한 내용은 <https://w3.org>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="decea-214">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>

## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="decea-215">XML 파일로 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="decea-215">Setting Options with an XML File</span></span>

<span data-ttu-id="decea-216">`/parameters` 스위치를 사용하여 여러 가지 옵션을 설정하는 단일 XML 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-216">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="decea-217">설정할 수 있는 옵션은 XSD.exe 도구를 사용하는 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="decea-217">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="decea-218">스키마 생성, 코드 파일 생성 또는 `DataSet` 기능이 있는 코드 파일 생성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-218">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="decea-219">예를 들면, 스키마는 생성하지만 코드 파일은 생성하지 않을 때 `<assembly>` 요소를 실행 파일(.exe) 또는 형식 라이브러리 파일(.dll) 이름으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-219">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="decea-220">다음 XML에서는 지정된 실행 파일에 `<generateSchemas>` 요소를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="decea-220">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

<span data-ttu-id="decea-221">위의 XML이 GenerateSchemas.xml이라는 파일에 포함된 경우 명령 프롬프트에서 다음을 입력하고 **Enter** 키를 눌러 `/parameters` 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-221">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing **Enter**:</span></span>

```console
 xsd /p:GenerateSchemas.xml
```

<span data-ttu-id="decea-222">그러나 어셈블리에 있는 단일 형식의 스키마를 생성하는 경우 다음 XML을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-222">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

<span data-ttu-id="decea-223">위의 코드를 사용하려면 명령 프롬프트에서 어셈블리의 이름도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-223">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="decea-224">명령 프롬프트에서 다음을 입력합니다. 이 경우 XML 파일 이름이 GenerateSchemaFromType.xml이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-224">Enter the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

<span data-ttu-id="decea-225">`<generateSchemas>` 요소에 대해 다음 옵션 중 하나만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-225">You must specify only one of the following options for the `<generateSchemas>` element.</span></span>

|<span data-ttu-id="decea-226">요소</span><span class="sxs-lookup"><span data-stu-id="decea-226">Element</span></span>|<span data-ttu-id="decea-227">설명</span><span class="sxs-lookup"><span data-stu-id="decea-227">Description</span></span>|
|-------------|-----------------|
|\<assembly>|<span data-ttu-id="decea-228">스키마를 생성하는 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-228">Specifies an assembly to generate the schema from.</span></span>|
|\<type>|<span data-ttu-id="decea-229">스키마를 생성할 대상 어셈블리에 있는 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-229">Specifies a type found in an assembly to generate a schema for.</span></span>|
|\<xml>|<span data-ttu-id="decea-230">스키마를 생성할 대상 XML 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-230">Specifies an XML file to generate a schema for.</span></span>|
|\<xdr>|<span data-ttu-id="decea-231">스키마를 생성할 대상 XDR 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-231">Specifies an XDR file to generate a schema for.</span></span>|

<span data-ttu-id="decea-232">코드 파일을 생성하려면 `<generateClasses>` 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-232">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="decea-233">다음 예제는 코드 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-233">The following example generates a code file.</span></span> <span data-ttu-id="decea-234">또한 생성된 파일의 프로그래밍 언어 및 네임스페이스를 설정할 수 있는 두 개의 특성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="decea-234">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 <span data-ttu-id="decea-235">`<generateClasses>` 요소에 대해 설정할 수 있는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-235">Options you can set for the `<generateClasses>` element include the following.</span></span>

|<span data-ttu-id="decea-236">요소</span><span class="sxs-lookup"><span data-stu-id="decea-236">Element</span></span>|<span data-ttu-id="decea-237">설명</span><span class="sxs-lookup"><span data-stu-id="decea-237">Description</span></span>|
|-------------|-----------------|
|\<element>|<span data-ttu-id="decea-238">코드를 생성할 대상 .xsd 파일의 요소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-238">Specifies an element in the .xsd file to generate code for.</span></span>|
|\<schemaImporterExtensions>|<span data-ttu-id="decea-239"><xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 클래스에서 파생된 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-239">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|
|\<schema>|<span data-ttu-id="decea-240">코드를 생성할 XML 스키마 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-240">Specifies a XML Schema file to generate code for.</span></span> <span data-ttu-id="decea-241">여러 \<schema> 요소를 사용하여 XML 스키마 파일을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

<span data-ttu-id="decea-242">다음 표에서는 `<generateClasses>` 요소에도 사용할 수 있는 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="decea-242">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>

|<span data-ttu-id="decea-243">특성</span><span class="sxs-lookup"><span data-stu-id="decea-243">Attribute</span></span>|<span data-ttu-id="decea-244">설명</span><span class="sxs-lookup"><span data-stu-id="decea-244">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="decea-245">language</span><span class="sxs-lookup"><span data-stu-id="decea-245">language</span></span>|<span data-ttu-id="decea-246">사용할 프로그래밍 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-246">Specifies the programming language to use.</span></span> <span data-ttu-id="decea-247">`CS`(C#, 기본값), `VB`(Visual Basic), `JS`(JScript) 또는 `VJS`(Visual J#) 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="decea-248"><xref:System.CodeDom.Compiler.CodeDomProvider>를 구현하는 클래스의 정규화된 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="decea-249">namespace</span><span class="sxs-lookup"><span data-stu-id="decea-249">namespace</span></span>|<span data-ttu-id="decea-250">생성된 코드에 대한 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="decea-251">네임스페이스는 CLR 표준(예: 공백 없음 또는 백슬래시 문자)에 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|
|<span data-ttu-id="decea-252">옵션</span><span class="sxs-lookup"><span data-stu-id="decea-252">options</span></span>|<span data-ttu-id="decea-253">`none`, `properties`(public 필드 대신 속성 생성), `order` 또는 `enableDataBinding`(위의 XSD 파일 옵션 섹션의 `/order` 및 `/enableDataBinding` 스위치 참조) 값 중 하나</span><span class="sxs-lookup"><span data-stu-id="decea-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|

 <span data-ttu-id="decea-254">`DataSet` 요소를 사용하여 `<generateDataSet>` 코드를 생성하는 방식을 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-254">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="decea-255">다음 XML은 생성된 코드가 `DataSet` 구조체(예: <xref:System.Data.DataTable> 클래스)를 사용하여 지정된 요소에 대한 Visual Basic 코드를 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-255">The following XML specifies that the generated code uses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="decea-256">생성된 DataSet 구조체는 LINQ 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-256">The generated DataSet structures will support LINQ queries.</span></span>

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

<span data-ttu-id="decea-257">`<generateDataSet>` 요소에 대해 설정할 수 있는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-257">Options you can set for the `<generateDataSet>` element include the following.</span></span>

|<span data-ttu-id="decea-258">요소</span><span class="sxs-lookup"><span data-stu-id="decea-258">Element</span></span>|<span data-ttu-id="decea-259">설명</span><span class="sxs-lookup"><span data-stu-id="decea-259">Description</span></span>|
|-------------|-----------------|
|\<schema>|<span data-ttu-id="decea-260">코드를 생성할 XML 스키마 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-260">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="decea-261">여러 \<schema> 요소를 사용하여 XML 스키마 파일을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-261">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

 <span data-ttu-id="decea-262">다음 표에서는 `<generateDataSet>` 요소에 사용할 수 있는 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="decea-262">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>

|<span data-ttu-id="decea-263">특성</span><span class="sxs-lookup"><span data-stu-id="decea-263">Attribute</span></span>|<span data-ttu-id="decea-264">설명</span><span class="sxs-lookup"><span data-stu-id="decea-264">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="decea-265">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="decea-265">enableLinqDataSet</span></span>|<span data-ttu-id="decea-266">생성된 DataSet을 LINQ to DataSet을 사용하여 쿼리할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-266">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="decea-267">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-267">The default value is false.</span></span>|
|<span data-ttu-id="decea-268">language</span><span class="sxs-lookup"><span data-stu-id="decea-268">language</span></span>|<span data-ttu-id="decea-269">사용할 프로그래밍 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-269">Specifies the programming language to use.</span></span> <span data-ttu-id="decea-270">`CS`(C#, 기본값), `VB`(Visual Basic), `JS`(JScript) 또는 `VJS`(Visual J#) 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-270">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="decea-271"><xref:System.CodeDom.Compiler.CodeDomProvider>를 구현하는 클래스의 정규화된 이름을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-271">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="decea-272">namespace</span><span class="sxs-lookup"><span data-stu-id="decea-272">namespace</span></span>|<span data-ttu-id="decea-273">생성된 코드에 대한 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-273">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="decea-274">네임스페이스는 CLR 표준(예: 공백 없음 또는 백슬래시 문자)에 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-274">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|

 <span data-ttu-id="decea-275">이러한 특성은 최상위 수준의 `<xsd>` 요소에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-275">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="decea-276">이러한 옵션은 자식 요소(`<generateSchemas>`, `<generateClasses>` 또는 `<generateDataSet>`)에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-276">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="decea-277">다음 XML 코드는 "MyOutputDirectory"라는 출력 디렉터리에 "IDItems" 요소에 대한 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-277">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

<span data-ttu-id="decea-278">다음 표에서는 `<xsd>` 요소에도 사용할 수 있는 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="decea-278">The following table shows the attributes that can also be used with the `<xsd>` element.</span></span>

|<span data-ttu-id="decea-279">특성</span><span class="sxs-lookup"><span data-stu-id="decea-279">Attribute</span></span>|<span data-ttu-id="decea-280">설명</span><span class="sxs-lookup"><span data-stu-id="decea-280">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="decea-281">출력</span><span class="sxs-lookup"><span data-stu-id="decea-281">output</span></span>|<span data-ttu-id="decea-282">생성된 스키마 또는 코드 파일을 지정할 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="decea-282">The name of a directory where the generated schema or code file will be placed.</span></span>|
|<span data-ttu-id="decea-283">nologo</span><span class="sxs-lookup"><span data-stu-id="decea-283">nologo</span></span>|<span data-ttu-id="decea-284">배너를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="decea-284">Suppresses the banner.</span></span> <span data-ttu-id="decea-285">`true` 또는 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-285">Set to `true` or `false`.</span></span>|
|<span data-ttu-id="decea-286">도움말</span><span class="sxs-lookup"><span data-stu-id="decea-286">help</span></span>|<span data-ttu-id="decea-287">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-287">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="decea-288">`true` 또는 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-288">Set to `true` or `false`.</span></span>|

## <a name="examples"></a><span data-ttu-id="decea-289">예</span><span class="sxs-lookup"><span data-stu-id="decea-289">Examples</span></span>

 <span data-ttu-id="decea-290">다음 명령을 사용하여 `myFile.xdr` 에서 XML 스키마를 생성한 다음 현재 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-290">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>

```console
xsd myFile.xdr
```

<span data-ttu-id="decea-291">다음 명령을 사용하여 `myFile.xml` 스키마를 생성한 다음 지정된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-291">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>

```console
xsd myFile.xml /outputdir:myOutputDir
```

<span data-ttu-id="decea-292">다음 명령은 C# 언어로 된 지정된 스키마와 일치하는 데이터 집합을 생성한 다음 현재 디렉터리에 `XSDSchemaFile.cs`로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-292">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

<span data-ttu-id="decea-293">다음 명령을 사용하여 어셈블리 `myAssembly.dll`에 있는 모든 형식에 대해 XML 스키마를 생성한 다음 현재 디렉터리에 `schema0.xsd`로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="decea-293">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>

```console
xsd myAssembly.dll
```

## <a name="see-also"></a><span data-ttu-id="decea-294">참조</span><span class="sxs-lookup"><span data-stu-id="decea-294">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="decea-295">도구</span><span class="sxs-lookup"><span data-stu-id="decea-295">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="decea-296">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="decea-296">Command Prompts</span></span>](../../framework/tools/developer-command-prompt-for-vs.md)
- [<span data-ttu-id="decea-297">LINQ to DataSet 개요</span><span class="sxs-lookup"><span data-stu-id="decea-297">LINQ to DataSet Overview</span></span>](../../framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="decea-298">형식화된 데이터 세트 쿼리</span><span class="sxs-lookup"><span data-stu-id="decea-298">Querying Typed DataSets</span></span>](../../framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="decea-299">LINQ(Language-Integrated Query)(C#)</span><span class="sxs-lookup"><span data-stu-id="decea-299">LINQ (Language-Integrated Query) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="decea-300">LINQ(Language-Integrated Query)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="decea-300">LINQ (Language-Integrated Query) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
