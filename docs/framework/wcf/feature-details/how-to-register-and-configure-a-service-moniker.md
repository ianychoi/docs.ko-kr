---
description: '자세한 정보: 방법: 서비스 모니커 등록 및 구성'
title: '방법: 서비스 모니커 등록 및 구성'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 9c6867941a5b96c6ced0f8e371e10697144bd121
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643464"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="2a57e-103">방법: 서비스 모니커 등록 및 구성</span><span class="sxs-lookup"><span data-stu-id="2a57e-103">How to: Register and Configure a Service Moniker</span></span>

<span data-ttu-id="2a57e-104">형식화 된 계약을 사용 하 여 COM 응용 프로그램 내에서 WCF (Windows Communication Foundation) 서비스 모니커를 사용 하려면 먼저 필요한 특성을 사용 하는 형식을 COM에 등록 하 고 필요한 바인딩 구성을 사용 하 여 COM 응용 프로그램 및 모니커를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-104">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>

## <a name="register-the-required-attributed-types-with-com"></a><span data-ttu-id="2a57e-105">필요한 특성 사용 형식을 COM에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-105">Register the required attributed types with COM</span></span>

1. <span data-ttu-id="2a57e-106">[ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 도구를 사용 하 여 WCF 서비스에서 메타 데이터 계약을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-106">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="2a57e-107">이렇게 하면 WCF 클라이언트 어셈블리와 클라이언트 응용 프로그램 구성 파일에 대 한 소스 코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-107">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>

2. <span data-ttu-id="2a57e-108">어셈블리의 형식이 `ComVisible`로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-108">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="2a57e-109">이렇게 하려면 Visual Studio 프로젝트의 *AssemblyInfo.cs* 파일에 다음 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-109">To do so, add the following attribute to the *AssemblyInfo.cs* file in your Visual Studio project.</span></span>

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. <span data-ttu-id="2a57e-110">관리 되는 WCF 클라이언트를 강력한 이름의 어셈블리로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-110">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="2a57e-111">이렇게 하려면 암호화된 키 쌍으로 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-111">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="2a57e-112">자세한 내용은 [강력한 이름으로 어셈블리 서명](../../../standard/assembly/sign-strong-name.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a57e-112">For more information, see [Signing an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

4. <span data-ttu-id="2a57e-113">어셈블리 등록(Regasm.exe) 도구에 `-tlb` 옵션을 사용하여 어셈블리의 형식을 COM에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-113">Use the Assembly Registration (Regasm.exe) tool with the `-tlb` option to register the types in the assembly with COM.</span></span>

5. <span data-ttu-id="2a57e-114">전역 어셈블리 캐시(Gacutil.exe) 도구를 사용하여 어셈블리를 전역 어셈블리 캐시에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-114">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a57e-115">어셈블리에 서명하고 전역 어셈블리 캐시에 추가하는 것은 선택적 단계이지만 런타임에 올바른 위치에서 어셈블리를 로드하는 프로세스를 단순화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-115">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="2a57e-116">필요한 바인딩 구성을 사용 하 여 COM 응용 프로그램 및 모니커 구성</span><span class="sxs-lookup"><span data-stu-id="2a57e-116">Configure the COM application and the moniker with the required binding configuration</span></span>

- <span data-ttu-id="2a57e-117">클라이언트 응용 프로그램 구성 파일에서 [ServiceModel 메타 데이터 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 에 의해 생성 된 바인딩 정의를 클라이언트 응용 프로그램 구성 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-117">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="2a57e-118">예를 들어 이름이 CallCenterClient.exe인 Visual Basic 6.0 실행 파일에 대해 실행 파일과 동일한 디렉터리 내의 CallCenterConfig.exe.config 파일에 구성을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-118">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="2a57e-119">이제 클라이언트 애플리케이션에서 모니커를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-119">The client application can now use the moniker.</span></span> <span data-ttu-id="2a57e-120">WCF에서 제공 하는 표준 바인딩 형식 중 하나를 사용 하는 경우에는 바인딩 구성이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-120">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>

     <span data-ttu-id="2a57e-121">다음 형식이 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-121">The following type is registered.</span></span>

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     <span data-ttu-id="2a57e-122">애플리케이션은 `wsHttpBinding` 바인딩을 사용하여 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-122">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="2a57e-123">지정된 형식과 애플리케이션 구성에 대해 다음 예제 모니커 문자열이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-123">For the given type and application configuration, the following example moniker strings are used.</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     <span data-ttu-id="2a57e-124">or</span><span class="sxs-lookup"><span data-stu-id="2a57e-124">or</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     <span data-ttu-id="2a57e-125">다음 샘플 코드와 같이 `IMathService` 형식을 포함하는 어셈블리에 대한 참조를 추가한 후 Visual Basic 6.0 애플리케이션 내에서 이러한 모니커 문자열 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-125">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     <span data-ttu-id="2a57e-126">이 예제에서는 바인딩 구성의 정의가 `Binding1` 클라이언트 응용 프로그램에 대 한 적절 한 이름의 구성 파일에 저장 됩니다 (예: *vb6appname.exe.config*).</span><span class="sxs-lookup"><span data-stu-id="2a57e-126">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as *vb6appname.exe.config*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a57e-127">C#, C++ 또는 다른 모든 .NET 언어 애플리케이션으로 유사한 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-127">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a57e-128">모니커의 형식이 잘못 되었거나 서비스를 사용할 수 없는 경우를 호출 하면 `GetObject` "구문이 잘못 되었습니다" 라는 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-128">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="2a57e-129">이 오류가 발생하면 사용하고 있는 모니커가 올바르고 서비스를 사용할 수 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2a57e-129">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>

     <span data-ttu-id="2a57e-130">이 항목에서는 Visual Basic 6.0 코드에서 서비스 모니커를 사용 하는 방법을 중점적으로 설명 하지만 다른 언어의 서비스 모니커를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-130">Although this topic focuses on using the service moniker from Visual Basic 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="2a57e-131">C++ 코드에서 모니커를 사용하는 경우 다음 코드와 같이 "no_namespace named_guids raw_interfaces_only"를 사용하여 Svcutil.exe에서 생성된 어셈블리를  가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-131">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     <span data-ttu-id="2a57e-132">모든 메서드에서 `HResult`를 반환하도록 가져온 인터페이스 정의를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-132">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="2a57e-133">다른 모든 반환 값은 출력 매개 변수로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-133">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="2a57e-134">전체 메서드 실행은 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-134">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="2a57e-135">이 경우 프록시에서 메서드를 호출할 때 예외의 원인을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-135">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="2a57e-136">이 기능은 C++ 코드에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a57e-136">This functionality is only available from C++ code.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a57e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a57e-137">See also</span></span>

- [<span data-ttu-id="2a57e-138">ServiceModel Metadata 유틸리티 도구(Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="2a57e-138">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
