---
title: XML Serializer 생성기 도구(Sgen.exe)
description: XML Serializer Generator는 특정 어셈블리의 형식에 대한 XML serialization 어셈블리를 만들어 XmlSerializer의 시작 성능을 향상시킵니다.
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: c2f33236e39f61638118f45f0d5ab5385df27ac3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676519"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="b67ab-103">XML Serializer 생성기 도구(Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="b67ab-103">XML Serializer Generator Tool (Sgen.exe)</span></span>

<span data-ttu-id="b67ab-104">XML Serializer 생성기는 지정된 어셈블리의 형식에 대한 XML 직렬화 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-104">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly.</span></span> <span data-ttu-id="b67ab-105">직렬화 어셈블리는 지정된 형식의 개체를 직렬화하거나 역직렬화할 때 <xref:System.Xml.Serialization.XmlSerializer>의 시작 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-105">The serialization assembly improves the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b67ab-106">구문</span><span class="sxs-lookup"><span data-stu-id="b67ab-106">Syntax</span></span>

<span data-ttu-id="b67ab-107">명령줄에서 도구를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-107">Run the tool from the command line.</span></span>
  
```console  
sgen [options]  
```
  
> [!TIP]
> <span data-ttu-id="b67ab-108">.NET Framework 도구가 제대로 작동하려면 `Path`, `Include` 및 `Lib` 환경 변수를 올바르게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-108">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="b67ab-109">\<SDK>\\\<version>\Bin 디렉터리에 있는 SDKVars.bat를 실행하여 이러한 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-109">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\\\<version>\Bin directory.</span></span> <span data-ttu-id="b67ab-110">SDKVars.bat를 모든 명령 셸에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-110">SDKVars.bat must be executed in every command shell.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="b67ab-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b67ab-111">Parameters</span></span>  
  
|<span data-ttu-id="b67ab-112">옵션</span><span class="sxs-lookup"><span data-stu-id="b67ab-112">Option</span></span>|<span data-ttu-id="b67ab-113">설명</span><span class="sxs-lookup"><span data-stu-id="b67ab-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b67ab-114">**/a\[ssembly\]:** _filename_</span><span class="sxs-lookup"><span data-stu-id="b67ab-114">**/a\[ssembly\]:**_filename_</span></span>|<span data-ttu-id="b67ab-115">*filename* 에서 지정한 어셈블리 또는 실행 파일에 있는 모든 형식에 대해 serialization 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-115">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="b67ab-116">파일 이름은 하나만 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-116">Only one file name can be provided.</span></span> <span data-ttu-id="b67ab-117">이 인수가 반복되면 마지막 파일 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-117">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="b67ab-118">**/c\[ompiler\]:** _options_</span><span class="sxs-lookup"><span data-stu-id="b67ab-118">**/c\[ompiler\]:**_options_</span></span>|<span data-ttu-id="b67ab-119">C# 컴파일러로 전달될 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-119">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="b67ab-120">모든 csc.exe 옵션이 컴파일러로 전달되어 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-120">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="b67ab-121">이 옵션은 어셈블리에서 서명되도록 지정할 때와 키 파일을 지정할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-121">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="b67ab-122">**/d\[ebug\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-122">**/d\[ebug\]**</span></span>|<span data-ttu-id="b67ab-123">디버거에서 사용할 수 있는 이미지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-123">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="b67ab-124">**/f\[orce\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-124">**/f\[orce\]**</span></span>|<span data-ttu-id="b67ab-125">이름이 같은 기존 어셈블리를 덮어쓰게 합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-125">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="b67ab-126">기본값은 **false** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-126">The default is **false**.</span></span>|  
|<span data-ttu-id="b67ab-127">**/help 또는 /?**</span><span class="sxs-lookup"><span data-stu-id="b67ab-127">**/help or /?**</span></span>|<span data-ttu-id="b67ab-128">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-128">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b67ab-129">**/k\[eep\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-129">**/k\[eep\]**</span></span>|<span data-ttu-id="b67ab-130">생성된 소스 파일 및 기타 임시 파일이 serialization 어셈블리로 컴파일된 후에는 이 파일을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-130">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="b67ab-131">이 도구에서 특정 형식에 대해 serialization 코드를 생성하는지 여부를 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-131">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="b67ab-132">**/n\[ologo\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-132">**/n\[ologo\]**</span></span>|<span data-ttu-id="b67ab-133">Microsoft 시작 배너를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-133">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="b67ab-134">**/o\[ut\]:** _path_</span><span class="sxs-lookup"><span data-stu-id="b67ab-134">**/o\[ut\]:**_path_</span></span>|<span data-ttu-id="b67ab-135">생성된 어셈블리를 저장할 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-135">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="b67ab-136">**참고:**  생성된 어셈블리의 이름은 입력 어셈블리의 이름과 "xmlSerializers.dll"로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-136">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="b67ab-137">**/p\[roxytypes\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-137">**/p\[roxytypes\]**</span></span>|<span data-ttu-id="b67ab-138">XML Web services 프록시 형식에 대해서만 serialization 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-138">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="b67ab-139">**/r\[eference\]:** _assemblyfiles_</span><span class="sxs-lookup"><span data-stu-id="b67ab-139">**/r\[eference\]:**_assemblyfiles_</span></span>|<span data-ttu-id="b67ab-140">XML serialization이 필요한 형식에서 참조하는 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-140">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="b67ab-141">여러 개의 어셈블리 파일을 쉼표로 구분할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-141">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="b67ab-142">**/s\[ilent\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-142">**/s\[ilent\]**</span></span>|<span data-ttu-id="b67ab-143">성공 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-143">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="b67ab-144">**/t\[ype\]:** _type_</span><span class="sxs-lookup"><span data-stu-id="b67ab-144">**/t\[ype\]:**_type_</span></span>|<span data-ttu-id="b67ab-145">지정된 형식에 대해서만 serialization 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-145">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="b67ab-146">**/v\[erbose\]**</span><span class="sxs-lookup"><span data-stu-id="b67ab-146">**/v\[erbose\]**</span></span>|<span data-ttu-id="b67ab-147">디버깅에 대한 자세한 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-147">Displays verbose output for debugging.</span></span> <span data-ttu-id="b67ab-148">대상 어셈블리에서 <xref:System.Xml.Serialization.XmlSerializer>로 serialize할 수 없는 형식을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-148">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="b67ab-149">**/?**</span><span class="sxs-lookup"><span data-stu-id="b67ab-149">**/?**</span></span>|<span data-ttu-id="b67ab-150">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b67ab-151">설명</span><span class="sxs-lookup"><span data-stu-id="b67ab-151">Remarks</span></span>  

 <span data-ttu-id="b67ab-152">XML Serializer 생성기를 사용하지 않을 경우, <xref:System.Xml.Serialization.XmlSerializer>는 애플리케이션이 실행될 때마다 각 형식에 대해 serialization 코드 및 serialization 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-152">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="b67ab-153">XML 직렬화 시작 성능을 높이려면 Sgen.exe 도구를 사용하여 해당 어셈블리를 미리 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-153">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="b67ab-154">그런 다음 애플리케이션과 함께 이 어셈블리를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-154">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="b67ab-155">XML Serializer 생성기는 해당 형식이 맨 처음 로드될 때 serialization 프로세스에서 성능 손실을 유발하지 않으므로, 서버와의 통신에서 XML Web services 프록시를 사용하는 클라이언트의 성능도 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-155">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="b67ab-156">이렇게 생성된 어셈블리는 웹 서비스의 서버측에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-156">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="b67ab-157">이 도구는 웹 서비스 클라이언트 및 수동 serialization 시나리오에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-157">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="b67ab-158">serialize할 형식을 포함하는 어셈블리의 이름이 MyType.dll이라면 연결된 serialization 어셈블리의 이름은 MyType.XmlSerializers.dll이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-158">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b67ab-159">예</span><span class="sxs-lookup"><span data-stu-id="b67ab-159">Examples</span></span>  

 <span data-ttu-id="b67ab-160">다음 명령에서는 Data.dll이라는 어셈블리에 포함된 모든 형식을 serialize하기 위해 Data.XmlSerializers.dll이라는 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-160">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```console  
sgen Data.dll
```  
  
 <span data-ttu-id="b67ab-161">Data.XmlSerializers.dll 어셈블리는 Data.dll의 형식을 직렬화/역직렬화해야 하는 코드에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b67ab-161">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67ab-162">참조</span><span class="sxs-lookup"><span data-stu-id="b67ab-162">See also</span></span>

- [<span data-ttu-id="b67ab-163">도구</span><span class="sxs-lookup"><span data-stu-id="b67ab-163">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="b67ab-164">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="b67ab-164">Command Prompts</span></span>](../../framework/tools/developer-command-prompt-for-vs.md)
