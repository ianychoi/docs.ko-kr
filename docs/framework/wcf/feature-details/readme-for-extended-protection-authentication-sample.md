---
description: '자세히 알아보기: 확장 된 보호 인증 샘플 추가 정보'
title: 인증에 대한 확장된 보호 ReadMe 샘플
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: edab04c7762bf8964f634107debd3de35a7702ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733309"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="3f7b4-103">인증에 대한 확장된 보호 ReadMe 샘플</span><span class="sxs-lookup"><span data-stu-id="3f7b4-103">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="3f7b4-104">확장 된 보호는 공격자 (MITM) 공격을 방지 하기 위한 보안 이니셔티브입니다. 공격자 ("중간자")는 클라이언트의 자격 증명을 가로채서이를 사용 하 여 클라이언트의 의도 된 서버에 있는 보안 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-104">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="3f7b4-105">자세한 내용은 [인증에 대한 확장된 보호 개요](extended-protection-for-authentication-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-105">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3f7b4-106">이 샘플은 IIS에서 호스팅하는 경우에만 작동하며,</span><span class="sxs-lookup"><span data-stu-id="3f7b4-106">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="3f7b4-107">HTTPS를 지원하지 않는 Visual Studio 개발 서버에서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-107">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f7b4-108">샘플 설치, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="3f7b4-108">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="3f7b4-109">프로그램 추가/제거-> Windows 기능에서 컴퓨터에 IIS를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-109">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="3f7b4-110">Windows 기능에서 Windows 인증을 사용 하도록 설정 합니다. 인터넷 정보 서비스-> World Wide Web 서비스-> Security-Windows 인증을 > 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-110">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="3f7b4-111">Windows 기능에서 HTTP 활성화 설정: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation HTTP Activation.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-111">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="3f7b4-112">이 샘플을 사용하려면 클라이언트에서 서버와의 보안 채널을 설정해야 하므로, IIS(인터넷 정보 서비스) 관리자에서 설치할 수 있는 서버 인증서가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-112">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="3f7b4-113">기능 보기 탭에서 IIS 관리자 > 서버 인증서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-113">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="3f7b4-114">이 샘플을 테스트하기 위해 자체 서명된 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-114">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="3f7b4-115">Internet Explorer에서 인증서가 안전하지 않다는 메시지가 표시되지 않도록 하려면 인증서를 신뢰할 수 있는 인증서 루트 인증 기관 저장소에 설치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-115">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="3f7b4-116">기본 웹 사이트의 작업 창으로 이동하여</span><span class="sxs-lookup"><span data-stu-id="3f7b4-116">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="3f7b4-117">사이트 > 바인딩 편집을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-117">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="3f7b4-118">그런 다음 HTTPS 유형이 없으면 포트 번호 443으로 추가하고 위 단계에서 만든 SSL 인증서를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-118">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="3f7b4-119">서비스를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-119">Build the service.</span></span> <span data-ttu-id="3f7b4-120">그러면 프로젝트 속성에 지정된 빌드 후 작업을 통해 IIS에 가상 디렉터리가 자동으로 만들어지며, 필요에 따라 웹에서 호스팅할 서비스에 대해 dll, .svc 및 config 파일이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-120">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="3f7b4-121">IIS 관리자를 열고</span><span class="sxs-lookup"><span data-stu-id="3f7b4-121">Open the IIS Manager.</span></span> <span data-ttu-id="3f7b4-122">앞 단계에서 만든 가상 디렉터리(ExtendedProtection)를 마우스 오른쪽 단추로 클릭한 다음 애플리케이션으로 변환을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-122">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="3f7b4-123">IIS 관리자에서 이 가상 디렉터리에 대한 인증 모듈을 열고 Windows 인증을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-123">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="3f7b4-124">샘플에서는 해당 ExtendedProtection 설정이 항상으로 설정되므로, 이 가상 디렉터리에 대해 Windows 인증의 고급 설정을 열고 필수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-124">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="3f7b4-125">브라우저 창에서 URL에 액세스해 서비스를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-125">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="3f7b4-126">다중 컴퓨터 구성에서 이 URL에 액세스하려면 들어오는 모든 HTTP 및 HTTPS 연결에 대해 방화벽이 열려 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-126">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="3f7b4-127">클라이언트 구성 파일을 열고-address 특성의 전체 컴퓨터 이름을 입력 \<client>  -  \<endpoint> 하 여를 바꿉니다 \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="3f7b4-127">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="3f7b4-128">클라이언트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-128">Run the client.</span></span> <span data-ttu-id="3f7b4-129">클라이언트가 보안 채널을 설정하고 자동으로 확장된 보호를 사용하여 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="3f7b4-129">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
