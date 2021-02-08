---
description: '자세히 알아보기: ConfigurationCodeGenerator'
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f65a32b6e9eadfed8dc8d1066086908c4b9a3396
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778362"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="2dbd8-103">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="2dbd8-103">ConfigurationCodeGenerator</span></span>

<span data-ttu-id="2dbd8-104">ConfigurationCodeGenerator는 구성 시스템에 사용자 지정 채널 구현을 노출하는 데 사용할 수 있는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-104">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="2dbd8-105">이를 통해 사용자 지정 채널의 사용자가 `NetTcpBinding`을 사용하여 `TcpTransportBindingElement` 등의 시스템 제공 바인딩이나 사용자 지정 바인딩을 구성하는 것과 같은 방법으로 .config 파일을 사용하여 채널을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-105">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="2dbd8-106">사용자 지정 채널을 써서 새 `BindingElement` 또는 `Binding`을 통해 프로그래밍 모델에 노출할 때에는 일련의 클래스를 만들어 .config 파일을 통해 `BindingElement` 또는 `Binding`을 구성 가능하게 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-106">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="2dbd8-107">ConfigurationCodeGenerator 도구를 사용하여 이런 클래스를 생성하고 고객의 경험을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-107">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="2dbd8-108">도구를 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="2dbd8-108">To build the tool</span></span>  
  
1. <span data-ttu-id="2dbd8-109">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-109">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2dbd8-110">솔루션을 빌드하면 ConfigurationCodeGenerator.exe 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-110">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="2dbd8-111">SampleRun 파일에는이 도구를 사용 하 여 [전송: UDP](transport-udp.md) 샘플에 대 한 클래스를 생성 하는 방법을 보여 주는 샘플 명령줄이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-111">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="2dbd8-112">도구를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="2dbd8-112">To run the tool</span></span>  
  
1. <span data-ttu-id="2dbd8-113">사용자 지정 `BindingElement` 형식과 사용자 지정 `Binding` 형식이 모두 있는 경우 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-113">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="2dbd8-114">또는 사용자 지정 `BindingElement` 형식만 있는 경우 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-114">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="2dbd8-115">또는 사용자 지정 `Binding` 형식만 있는 경우 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-115">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="2dbd8-116">명령에서는 `BindingElement`(/be: 옵션을 설정한 경우)에 사용할 3개의 .cs 파일, 표준 `Binding`(/sb: 옵션을 지정한 경우)에 사용할 5개의 .cs 파일, 그리고 한 개의 .xml 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-116">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="2dbd8-117">/be 옵션을 사용한 경우 .cs 파일 중 하나에서 바인딩 요소의 `BindingElementExtensionSection`을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-117">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="2dbd8-118">이 코드에서는 다른 사용자 지정 바인딩에서 바인딩 요소를 사용할 수 있도록 구성 시스템에 `BindingElement`를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-118">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="2dbd8-119">다른 파일에는 기본값과 상수를 나타내는 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-119">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="2dbd8-120">파일에는 기본값을 업데이트하도록 상기시키기 위한 `//TODO` 주석이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-120">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="2dbd8-121">/sb 옵션을 지정한 경우 2개의 .cs 파일을 각각 구성 시스템에 표준 바인딩을 노출하는 `StandardBindingElement` 및 `StandardBindingCollectionElement`를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-121">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="2dbd8-122">다른 파일에는 기본값과 상수를 나타내는 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-122">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="2dbd8-123">파일에는 기본값을 업데이트하도록 상기시키기 위한 `//TODO` 주석이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-123">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="2dbd8-124">/Sb: 옵션을 지정한 경우 CodeToAddTo에는 \<*YourStdBinding*> 표준 바인딩을 구현 하는 클래스에 수동으로 추가 해야 하는 코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-124">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="2dbd8-125">SampleConfig.xml 파일에는 이전의 1단계 또는 2단계에 정의된 처리기를 등록하는 구성 파일에 추가해야 할 구성 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dbd8-125">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
