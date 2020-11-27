---
title: 메시지 큐에 대한 메시지 보안
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 1b262a5f4343e07aecf5eebda32cc995f86ec77b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248935"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="d334a-102">메시지 큐에 대한 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="d334a-102">Message Security over Message Queuing</span></span>

<span data-ttu-id="d334a-103">이 샘플에서는 클라이언트에 대해 X.509v3 인증서를 통한 WS-Security 인증을 사용하며 MSMQ를 통해 서버의 X.509v3 인증서를 사용한 서버 인증을 수행해야 하는 애플리케이션의 구현 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="d334a-104">메시지 보안에서는 MSMQ 스토리지에 있는 메시지의 암호화가 유지되며 애플리케이션에서 메시지의 자체 인증을 수행할 수 있도록 하는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="d334a-105">이 샘플은 [트랜잭션 된 MSMQ 바인딩](transacted-msmq-binding.md) 샘플을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-105">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="d334a-106">메시지가 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d334a-107">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d334a-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d334a-108">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d334a-109">서비스가 처음 실행되는 경우 서비스에서는 큐가 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="d334a-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="d334a-110">큐가 없으면 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="d334a-111">서비스를 처음 실행하여 큐를 만들거나 MSMQ 큐 관리자를 통해 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="d334a-112">Windows 2008에서 큐를 만들려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="d334a-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="d334a-113">Visual Studio 2012에서 서버 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="d334a-114">**기능** 탭을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="d334a-115">**개인 메시지 큐** 를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**, **개인 큐** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="d334a-116">**트랜잭션** 상자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="d334a-117">`ServiceModelSamplesTransacted`새 큐의 이름으로을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="d334a-118">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d334a-119">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d334a-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="d334a-120">Makecert.exe 및 FindPrivateKey.exe가 포함된 폴더가 경로에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="d334a-121">샘플 설치 폴더에서 Setup.bat를 실행하여</span><span class="sxs-lookup"><span data-stu-id="d334a-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d334a-122">이 작업은 샘플 실행에 필요한 모든 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d334a-123">샘플 사용을 마쳤으면 Cleanup.bat를 실행하여 인증서를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="d334a-124">다른 보안 샘플에도 동일한 인증서가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="d334a-125">\service\bin에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="d334a-126">\client\bin에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="d334a-127">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="d334a-128">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d334a-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d334a-129">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d334a-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="d334a-130">Setup.bat, Cleanup.bat 및 ImportClientCert.bat 파일을 서비스 컴퓨터에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="d334a-131">클라이언트 컴퓨터에 클라이언트 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="d334a-132">클라이언트 프로그램 파일을 클라이언트 컴퓨터의 클라이언트 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="d334a-133">Setup.bat, Cleanup.bat 및 ImportServiceCert.bat 파일도 클라이언트로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="d334a-134">서버에서 `setup.bat service`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="d334a-135">`setup.bat`인수를 사용 하 여를 실행 하면 컴퓨터의 정규화 된 `service` 도메인 이름으로 서비스 인증서가 생성 되 고 서비스 인증서가 이름이 .cer 인 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="d334a-136">`findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 컴퓨터의 정규화 된 도메인 이름과 같은 새 인증서 이름 (의 특성)이 반영 되도록 서비스의 service.exe.config를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="d334a-137">서비스 디렉터리에서 클라이언트 컴퓨터의 클라이언트 디렉터리로 Service.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="d334a-138">클라이언트에서 `setup.bat client`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="d334a-139">`setup.bat` 인수를 사용하여 `client`를 실행하면 client.com이라는 클라이언트 인증서가 생성되어 Client.cer이라는 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="d334a-140">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="d334a-141">이렇게 하려면 localhost를 서버의 정규화된 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="d334a-142">서비스의 인증서 이름도 서비스 컴퓨터의 정규화된 도메인 이름과 일치하게 변경해야 합니다(`findValue`에 있는 `defaultCertificate`의 `serviceCertificate` 요소에 있는 `clientCredentials` 특성).</span><span class="sxs-lookup"><span data-stu-id="d334a-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="d334a-143">클라이언트 디렉터리에서 서버의 서비스 디렉터리로 Client.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="d334a-144">클라이언트에서 `ImportServiceCert.bat`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="d334a-145">이 작업은 Service.cer 파일의 서비스 인증서를 CurrentUser - TrustedPeople 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="d334a-146">서버에서 `ImportClientCert.bat`를 실행하여 Client.cer 파일에서 LocalMachine - TrustedPeople 저장소로 클라이언트 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="d334a-147">서비스 컴퓨터의 명령 프롬프트에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="d334a-148">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="d334a-149">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d334a-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d334a-150">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d334a-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d334a-151">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d334a-152">다중 컴퓨터 구성에서 이 샘플을 실행할 경우에는 이 스크립트로 클라이언트의 서비스 인증서를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="d334a-153">컴퓨터에서 인증서를 사용 하는 WCF (Windows Communication Foundation) 샘플을 실행 한 경우에는 CurrentUser-비트 사용자 저장소에 설치 된 서비스 인증서를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d334a-154">이를 수행하려면 `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 명령을 사용합니다(예: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="d334a-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="d334a-155">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d334a-155">Requirements</span></span>

 <span data-ttu-id="d334a-156">이 샘플을 실행하려면 MSMQ가 설치되어 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d334a-157">데모</span><span class="sxs-lookup"><span data-stu-id="d334a-157">Demonstrates</span></span>

 <span data-ttu-id="d334a-158">클라이언트는 서비스의 공개 키를 사용하여 메시지를 암호화하고 자체 인증서로 메시지에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="d334a-159">큐로부터 메시지를 읽는 서비스는 신뢰할 수 있는 사용자 저장소에 포함된 인증서를 사용하여 클라이언트 인증서를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="d334a-160">그리고 메시지를 해독한 후 서비스 작업에 디스패치합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="d334a-161">Windows Communication Foundation (WCF) 메시지는 MSMQ 메시지 본문에서 페이로드로 전달 되기 때문에 본문은 MSMQ 저장소에서 암호화 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="d334a-162">그러면 원치 않는 노출로부터 메시지를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="d334a-163">MSMQ 자체에서는 전달하는 메시지의 암호화 여부를 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="d334a-164">샘플에서는 MSMQ에서 메시지 수준의 상호 인증을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="d334a-165">인증서는 out-of-band로 교환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="d334a-166">대기 중인 애플리케이션의 경우에는 서비스와 클라이언트가 동시에 실행 중이어야 할 필요가 없기 때문에 항상 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="d334a-167">Description</span><span class="sxs-lookup"><span data-stu-id="d334a-167">Description</span></span>

 <span data-ttu-id="d334a-168">샘플 클라이언트 및 서비스 코드는 한 가지 차이점이 있는 [트랜잭션 된 MSMQ 바인딩](transacted-msmq-binding.md) 샘플과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-168">The sample client and service code are the same as the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="d334a-169">작업 계약에는 보호 수준에서 주석을 달아야 하기 때문에 메시지에 서명과 암호화가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="d334a-170">필수 토큰을 사용하여 서비스 및 클라이언트를 식별하는 방식으로 메시지를 보호할 수 있도록 App.config에는 자격 증명 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="d334a-171">클라이언트 구성에서는 서비스를 인증할 서비스 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="d334a-172">여기서는 LocalMachine 저장소를 서비스의 유효성에 의존하는 신뢰할 수 있는 저장소로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="d334a-173">여기서는 클라이언트의 서비스 인증을 위해 메시지와 함께 첨부되는 클라이언트 인증서도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="d334a-174">보안 모드는 Message로 설정되며 ClientCredentialType은 Certificate로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="d334a-175">서비스 구성에는 클라이언트에서 서비스를 인증할 때 사용된 서비스의 자격 증명을 지정하는 서비스 동작이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="d334a-176">서버 인증서 주체 이름은의 특성에 지정 됩니다 `findValue` [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="d334a-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="d334a-177">이 샘플에서는 다음 샘플 코드에서와 같이 구성을 이용하여 인증을 제어하는 방법과 보안 컨텍스트에서 호출자의 ID를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="d334a-178">서비스 코드를 실행하면 클라이언트 ID가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="d334a-179">다음은 서비스 코드의 출력 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-179">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="d334a-180">의견</span><span class="sxs-lookup"><span data-stu-id="d334a-180">Comments</span></span>

- <span data-ttu-id="d334a-181">클라이언트 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="d334a-181">Creating the client certificate.</span></span>

     <span data-ttu-id="d334a-182">배치 파일의 다음 줄에서는 클라이언트 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="d334a-183">지정된 클라이언트 이름은 만든 인증서의 제목 이름에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="d334a-184">인증서는 `My` 저장소 위치에 있는 `CurrentUser` 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="d334a-185">서버의 신뢰할 수 있는 인증서 저장소에 클라이언트 인증서 설치.</span><span class="sxs-lookup"><span data-stu-id="d334a-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="d334a-186">배치 파일의 다음 줄에서는 서버에서 관련된 신뢰 여부를 결정할 수 있도록 서버의 TrustedPeople 저장소에 클라이언트 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="d334a-187">신뢰할 수 있는 사용자 저장소에 설치 된 인증서를 WCF (Windows Communication Foundation) 서비스에서 신뢰할 수 있도록 하려면 클라이언트 인증서 유효성 검사 모드를 또는 값으로 설정 해야 합니다 `PeerOrChainTrust` `PeerTrust` .</span><span class="sxs-lookup"><span data-stu-id="d334a-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="d334a-188">구성 파일을 사용하여 이런 작업을 수행하는 방법을 보려면 앞서 소개된 서비스 구성 샘플을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d334a-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="d334a-189">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="d334a-189">Creating the server certificate.</span></span>

     <span data-ttu-id="d334a-190">Setup.bat 배치 파일에서 다음 줄은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="d334a-191">%SERVER_NAME% 변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="d334a-192">인증서는 LocalMachine 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="d334a-193">서비스의 인수 (예:)를 사용 하 여 설치 일괄 처리 파일을 실행 하는 경우 `setup.bat service` % SERVER_NAME%에는 컴퓨터의 정규화 된 도메인 이름이 포함 됩니다. 그렇지 않은 경우 기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="d334a-194">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치</span><span class="sxs-lookup"><span data-stu-id="d334a-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="d334a-195">다음 줄은 클라이언트의 신뢰할 수 있는 사용자 저장소에 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="d334a-196">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="d334a-197">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="d334a-198">가 아닌를 사용 하는 경우 영어 버전의 Microsoft Windows Setup.bat 파일을 편집 하 고 "NT AUTHORITY\NETWORK SERVICE" 계정 이름을 해당 지역으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d334a-199">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d334a-200">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d334a-200">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d334a-201">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d334a-202">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d334a-202">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`
