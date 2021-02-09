---
description: '자세한 정보: 사용자 지정 My 확장 패키징 및 배포(Visual Basic)'
title: 사용자 지정 My 확장 패키징 및 배포
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 7037cc72951fc5228ae47998f39dca3455bf57de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775411"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="99607-103">사용자 지정 My 확장 패키징 및 배포(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99607-103">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="99607-104">Visual Basic은 Visual Studio 템플릿을 사용하여 사용자 지정 `My` 네임스페이스 확장을 쉽게 배포할 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-104">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="99607-105">`My` 확장이 새 프로젝트 형식의 정수 부분인 프로젝트 템플릿을 만드는 경우 템플릿을 내보낼 때 프로젝트에 사용자 지정 `My` 확장 코드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-105">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="99607-106">프로젝트 템플릿 내보내기에 대한 자세한 내용은 [방법: 프로젝트 템플릿 만들기](/visualstudio/ide/how-to-create-project-templates)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99607-106">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="99607-107">사용자 지정 `My` 확장이 단일 코드 파일에 있는 경우 사용자가 Visual Basic 프로젝트의 모든 형식에 추가할 수 있는 항목 템플릿으로 파일을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-107">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="99607-108">그런 다음, Visual Basic 프로젝트에서 사용자 지정 `My` 확장에 대한 추가 기능 및 동작을 사용하도록 항목 템플릿을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-108">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="99607-109">이러한 기능에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="99607-109">Those capabilities include the following:</span></span>

- <span data-ttu-id="99607-110">사용자가 Visual Basic 프로젝트 디자이너의 **My 확장** 페이지에서 사용자 지정 `My` 확장을 관리할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-110">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="99607-111">지정된 어셈블리에 대한 참조가 프로젝트에 추가될 때 사용자 지정 `My` 확장을 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-111">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="99607-112">프로젝트 항목 목록에 포함되지 않도록 **항목 추가** 대화 상자에서 `My` 확장 항목 템플릿을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="99607-112">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="99607-113">이 항목에서는 Visual Basic 프로젝트 디자이너의 **My 확장** 페이지에서 관리할 수 있는 숨겨진 항목 템플릿으로 사용자 지정 `My` 확장을 패키징하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-113">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99607-114">지정된 어셈블리에 대한 참조가 프로젝트에 추가될 때 사용자 지정 `My` 확장을 자동으로 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-114">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="99607-115">My 네임스페이스 확장 만들기</span><span class="sxs-lookup"><span data-stu-id="99607-115">Create a My namespace extension</span></span>

<span data-ttu-id="99607-116">사용자 지정 `My` 확장에 대한 배포 패키지를 만드는 첫 번째 단계는 확장을 단일 코드 파일로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-116">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="99607-117">사용자 지정 `My` 확장을 만드는 방법에 대한 자세한 내용과 지침은 [Visual Basic에서 My 네임스페이스 확장](extending-the-my-namespace.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99607-117">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="99607-118">My 네임스페이스 확장을 항목 템플릿으로 내보내기</span><span class="sxs-lookup"><span data-stu-id="99607-118">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="99607-119">`My` 네임스페이스 확장을 포함하는 코드 파일을 만든 후에는 코드 파일을 Visual Studio 항목 템플릿으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-119">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="99607-120">Visual Studio 항목 템플릿으로 파일을 내보내는 방법에 대한 자세한 내용은 [방법: 항목 템플릿 만들기](/visualstudio/ide/how-to-create-item-templates)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99607-120">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="99607-121">`My` 네임스페이스 확장이 특정 어셈블리에 종속되어 있는 경우 해당 어셈블리에 대한 참조가 추가되면 `My` 네임스페이스 확장을 자동으로 설치하도록 항목 템플릿을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-121">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="99607-122">결과적으로 코드 파일을 Visual Studio 항목 템플릿으로 내보낼 때 해당 어셈블리 참조를 제외하려고 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-122">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="99607-123">항목 템플릿 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="99607-123">Customize the item template</span></span>

<span data-ttu-id="99607-124">Visual Basic 프로젝트 디자이너의 **My 확장** 페이지에서 항목 템플릿을 관리할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-124">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99607-125">지정된 어셈블리에 대한 참조가 프로젝트에 추가될 때 항목 템플릿을 자동으로 추가하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-125">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="99607-126">이러한 사용자 지정을 사용하려면 CustomData 파일이라는 새 파일을 템플릿에 추가한 다음, .vstemplate 파일의 XML에 새 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-126">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="99607-127">CustomData 파일 추가</span><span class="sxs-lookup"><span data-stu-id="99607-127">Add the CustomData file</span></span>

<span data-ttu-id="99607-128">CustomData 파일은 .CustomData의 파일 이름 확장명을 가진 텍스트 파일이며(파일 이름은 템플릿에 의미 있는 값으로 설정할 수 있음) XML이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-128">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="99607-129">CustomData 파일의 XML은 사용자가 Visual Basic 프로젝트 디자이너의 **My 확장** 페이지를 사용할 때 `My` 확장을 포함하도록 Visual Basic을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-129">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="99607-130">필요에 따라 <`AssemblyFullName>` 특성을 CustomData 파일 XML에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-130">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="99607-131">이렇게 하면 특정 어셈블리에 대한 참조가 프로젝트에 추가될 때 Visual Basic에서 사용자 지정 `My` 확장을 자동으로 설치하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-131">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="99607-132">모든 텍스트 편집기나 XML 편집기를 사용하여 CustomData 파일을 만든 다음, 항목 템플릿의 압축 폴더(.zip 파일)에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-132">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="99607-133">예를 들어 다음 XML에서는 Microsoft.VisualBasic.PowerPacks.Vs.dll 어셈블리에 대한 참조가 프로젝트에 추가될 때 Visual Basic 프로젝트의 My Extensions 폴더에 템플릿 항목을 추가하는 CustomData 파일의 콘텐츠를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99607-133">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="99607-134">CustomData 파일에는 다음 표에 나열된 특성을 포함하는 <`VBMyExtensionTemplate>` 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-134">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="99607-135">특성</span><span class="sxs-lookup"><span data-stu-id="99607-135">Attribute</span></span>|<span data-ttu-id="99607-136">Description</span><span class="sxs-lookup"><span data-stu-id="99607-136">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="99607-137">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="99607-137">Required.</span></span> <span data-ttu-id="99607-138">확장에 대한 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-138">A unique identifier for the extension.</span></span> <span data-ttu-id="99607-139">이 ID를 가진 확장이 프로젝트에 이미 추가된 경우 사용자에게 다시 추가하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-139">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="99607-140">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="99607-140">Required.</span></span> <span data-ttu-id="99607-141">항목 템플릿에 대한 버전 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-141">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="99607-142">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-142">Optional.</span></span> <span data-ttu-id="99607-143">어셈블리 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="99607-143">An assembly name.</span></span> <span data-ttu-id="99607-144">이 어셈블리에 대한 참조가 프로젝트에 추가되면 사용자에게 이 항목 템플릿에서 `My` 확장을 추가할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="99607-144">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="99607-145">.vstemplate 파일에 \<CustomDataSignature> 요소 추가</span><span class="sxs-lookup"><span data-stu-id="99607-145">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="99607-146">Visual Studio 항목 템플릿을 `My` 네임스페이스 확장으로 식별하려면 항목 템플릿에 대한 .vstemplate 파일도 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-146">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="99607-147">`<CustomDataSignature>` 요소를 `<TemplateData>` 요소에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-147">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="99607-148">`<CustomDataSignature>` 요소는 다음 예제와 같이 `Microsoft.VisualBasic.MyExtension` 텍스트를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-148">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="99607-149">압축된 폴더(.zip 파일)의 파일은 직접 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-149">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="99607-150">압축된 폴더에서 .vstemplate 파일을 복사하고 수정한 다음, 압축된 폴더의 .vstemplate 파일을 업데이트된 복사본으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99607-150">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="99607-151">다음 예제에서는 `<CustomDataSignature>` 요소가 추가된 .vstemplate 파일의 콘텐츠를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99607-151">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="99607-152">템플릿 설치</span><span class="sxs-lookup"><span data-stu-id="99607-152">Install the template</span></span>

<span data-ttu-id="99607-153">템플릿을 설치하려면 압축된 폴더( *.zip* 파일)를 Visual Basic 항목 템플릿 폴더에 복사하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99607-153">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="99607-154">기본적으로 사용자 항목 템플릿은 *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic* 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-154">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="99607-155">또는 템플릿을 Visual Studio 설치 관리자( *.vsi*) 파일로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99607-155">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="99607-156">참조</span><span class="sxs-lookup"><span data-stu-id="99607-156">See also</span></span>

- [<span data-ttu-id="99607-157">Visual Basic의 내 네임스페이스 확장</span><span class="sxs-lookup"><span data-stu-id="99607-157">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)
- [<span data-ttu-id="99607-158">Visual Basic 애플리케이션 모델 확장</span><span class="sxs-lookup"><span data-stu-id="99607-158">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="99607-159">My에 사용할 수 있는 개체 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="99607-159">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="99607-160">내 확장명 페이지, 프로젝트 디자이너</span><span class="sxs-lookup"><span data-stu-id="99607-160">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
