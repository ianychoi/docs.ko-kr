---
description: '자세히 알아보기: 방법: COM + 서비스 모델 구성 도구 사용'
title: '방법: COM+ 서비스 모델 구성 도구 사용'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2047604f327cd871629bbdac403e9acd816bbdb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734089"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="6f038-103">방법: COM+ 서비스 모델 구성 도구 사용</span><span class="sxs-lookup"><span data-stu-id="6f038-103">How to: Use the COM+ Service Model Configuration Tool</span></span>

<span data-ttu-id="6f038-104">적절한 호스팅 모드를 선택한 다음 COM+ 서비스 모델 구성 명령줄 도구(ComSvcConfig.exe)를 사용하여 웹 서비스로 노출될 애플리케이션 인터페이스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-104">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="6f038-105">다음 작업을 수행하려면 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-105">You must be an administrator on the machine to perform any of the following tasks.</span></span>

 <span data-ttu-id="6f038-106">Windows 7 컴퓨터에서 ComSvcConfig.exe를 사용하여 웹 서비스가 최신 서비스 모델 버전(현재 v4.5)을 사용하도록 구성하려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="6f038-106">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>

1. <span data-ttu-id="6f038-107">레지스트리 키를  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` DWORD 값 0x00000001로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-107">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>

2. <span data-ttu-id="6f038-108">Comsvcconfig.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-108">Run comsvcconfig.exe</span></span>

3. <span data-ttu-id="6f038-109">1단계에서 추가한 레지스트리 키를 원래 값으로 되돌리거나, 원래 값이 없었던 경우에는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-109">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f038-110">이 레지스트리 키를 되돌리는 것은 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-110">Reverting this registry key is important.</span></span> <span data-ttu-id="6f038-111">이 키는 호환성 키이므로</span><span class="sxs-lookup"><span data-stu-id="6f038-111">This is a compatibility key.</span></span> <span data-ttu-id="6f038-112">변경 내용을 되돌리지 않으면 컴퓨터에서 실행 중인 다른 .NET 애플리케이션에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-112">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>

> [!WARNING]
> <span data-ttu-id="6f038-113">Windows 8 컴퓨터에서 ComSvcConfig.exe/install을 사용 하는 경우 "PC의 앱에 다음 Windows 기능이 필요 합니다. .NET Framework 3.5 (.NET 2.0 및 .NET 3.0 포함) .NET Framework 3.5이 설치 되어 있지 않으면이 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-113">When using ComSvcConfig.exe  /install on a Windows 8 machine, a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="6f038-114">이 대화 상자는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-114">This dialog may be ignored.</span></span> <span data-ttu-id="6f038-115">또는 OnlyUseLatestCLR 레지스트리 키를 DWORD 값 0x00000001로 설정해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-115">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>

## <a name="add-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="6f038-116">COM + 호스팅 모드를 사용 하 여 인터페이스 추가</span><span class="sxs-lookup"><span data-stu-id="6f038-116">Add an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="6f038-117">다음 예제에서처럼 `/install` 및 `/hosting:complus` 옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-117">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     <span data-ttu-id="6f038-118">이 명령은 OnlineStore COM+ 애플리케이션에 있는 `IFinances` 구성 요소의 `ItemOrders.IFinancial` 인터페이스를 웹 서비스로 노출될 인터페이스 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-118">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="6f038-119">이 서비스는 COM+ 호스팅 모드를 사용하므로 명시적으로 애플리케이션을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-119">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>

     <span data-ttu-id="6f038-120">와일드 카드 별표 ( \* ) 문자는 구성 요소와 인터페이스에 사용할 수 있지만 선택한 기능만 웹 서비스로 노출 하려는 경우에는 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6f038-120">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="6f038-121">이 구성 요소의 다음 버전으로 실행하는 경우 와일드카드를 사용하면 구성 구문을 확인했을 때 표시되지 않은 인터페이스를 실수로 노출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-121">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>

     <span data-ttu-id="6f038-122">/verbose 옵션은 도구에 경고와 오류를 표시하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-122">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>

     <span data-ttu-id="6f038-123">노출된 서비스에 대한 계약에 `IFinances` 인터페이스의 모든 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-123">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="6f038-124">COM + 호스팅 모드를 사용 하 여 인터페이스의 특정 메서드 추가</span><span class="sxs-lookup"><span data-stu-id="6f038-124">Add specific methods from an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="6f038-125">다음 예제에서처럼 `/install` 및 `/hosting:complus` 옵션에 필수 메서드의 명시적 명명을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-125">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     <span data-ttu-id="6f038-126">이 명령은 `Credit` 인터페이스의 `Debit` 및 `IFinances` 메서드만 노출된 서비스 계약에 작업으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-126">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="6f038-127">인터페이스의 다른 모든 메서드는 계약에서 생략되고 웹 서비스 클라이언트에서 호출될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-127">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>

## <a name="add-an-interface-using-the-web-hosting-mode"></a><span data-ttu-id="6f038-128">웹 호스팅 모드를 사용 하 여 인터페이스 추가</span><span class="sxs-lookup"><span data-stu-id="6f038-128">Add an interface using the Web hosting mode</span></span>

- <span data-ttu-id="6f038-129">다음 예제에서처럼 `/install` 옵션 및 `/hosting:was` 옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-129">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     <span data-ttu-id="6f038-130">이 명령은 OnlineWarehouse COM+ 애플리케이션에 있는 `IStockLevels` 구성 요소의 `ItemInventory.Warehouse` 인터페이스를 웹 서비스로 노출될 인터페이스의 집합에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-130">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="6f038-131">이 서비스는 COM+가 아닌 IIS의 OnlineWarehouse 가상 디렉터리에서 웹 호스팅되므로 필요한 경우 애플리케이션이 자동으로 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-131">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>

     <span data-ttu-id="6f038-132">웹 호스팅 in-process 구성을 사용하려면 구성 요소 서비스 관리 콘솔을 사용하여 서버 애플리케이션이 아닌 라이브러리 애플리케이션으로 실행되도록 COM+ 애플리케이션을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-132">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="6f038-133">서버 애플리케이션으로 구성된 애플리케이션은 표준 웹 호스팅 모드를 사용하고 프로세스 홉을 수행하여 각 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-133">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>

     <span data-ttu-id="6f038-134">ph x=&quot;1&quot; /&amp;gt; 옵션은 같은 전송을 애플리케이션의 서비스 엔드포인트로 사용하는 MEX(메타데이터 교환) 서비스 엔드포인트를 추가하여 서비스에서 계약 정의를 검색하려는 클라이언트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-134">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>

## <a name="remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="6f038-135">지정 된 인터페이스에 대 한 웹 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-135">Remove a Web service for a specified interface</span></span>

- <span data-ttu-id="6f038-136">다음 예제에서처럼 `/uninstall` 옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-136">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     <span data-ttu-id="6f038-137">이 명령은 OnlineStore COM+ 애플리케이션의 `IFinances` 구성 요소에서 `ItemOrders.Financial` 인터페이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-137">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>

## <a name="list-currently-exposed-interfaces"></a><span data-ttu-id="6f038-138">현재 노출 된 인터페이스 나열</span><span class="sxs-lookup"><span data-stu-id="6f038-138">List currently exposed interfaces</span></span>

- <span data-ttu-id="6f038-139">다음 예제에서처럼 `/list` 옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-139">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list
    ```

     <span data-ttu-id="6f038-140">이 명령은 현재 노출된 인터페이스와 함께 로컬 컴퓨터에 적용되는 해당 주소 및 바인딩 세부 내용을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-140">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>

## <a name="list-specific-currently-exposed-interfaces"></a><span data-ttu-id="6f038-141">현재 노출 된 특정 인터페이스 나열</span><span class="sxs-lookup"><span data-stu-id="6f038-141">List specific currently exposed interfaces</span></span>

- <span data-ttu-id="6f038-142">다음 예제에서처럼 `/list` 옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-142">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     <span data-ttu-id="6f038-143">이 명령은 현재 노출된 COM+ 호스팅 인터페이스와 함께 로컬 컴퓨터의 OnlineStore COM+ 애플리케이션에 대한 해당 주소 및 바인딩 세부 내용을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-143">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>

## <a name="display-help-for-options"></a><span data-ttu-id="6f038-144">옵션에 대 한 도움말 표시</span><span class="sxs-lookup"><span data-stu-id="6f038-144">Display help for options</span></span>

- <span data-ttu-id="6f038-145">다음 예제에서처럼 /?</span><span class="sxs-lookup"><span data-stu-id="6f038-145">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="6f038-146">옵션을 사용하여 ComSvcConfig를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f038-146">option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a><span data-ttu-id="6f038-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f038-147">See also</span></span>

- [<span data-ttu-id="6f038-148">COM + 응용 프로그램과 통합 개요</span><span class="sxs-lookup"><span data-stu-id="6f038-148">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
