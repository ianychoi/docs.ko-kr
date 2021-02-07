---
description: '자세히 알아보기: 방법: 사용자 지정 인증서 유효성 검사기를 활용 하는 서비스 만들기'
title: '방법: 사용자 지정 인증서 유효성 검사기를 사용하는 서비스 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 8ed5d23143b7b69768cc556d9fd5663e46fd7da7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668983"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="8a3bb-103">방법: 사용자 지정 인증서 유효성 검사기를 사용하는 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8a3bb-103">How to: Create a Service that Employs a Custom Certificate Validator</span></span>

<span data-ttu-id="8a3bb-104">이 항목에서는 사용자 지정 인증서 유효성 검사기를 구현하는 방법과 클라이언트 또는 서비스 자격 증명을 구성하여 기본 인증서 유효성 검사 논리를 사용자 지정 인증서 유효성 검사기로 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-104">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="8a3bb-105">X.509 인증서가 클라이언트 또는 서비스를 인증 하는 데 사용 되는 경우 기본적으로 WCF (Windows Communication Foundation)는 Windows 인증서 저장소 및 Crypto API를 사용 하 여 인증서의 유효성을 검사 하 고 신뢰할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-105">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="8a3bb-106">기본 제공 인증서 유효성 검사 기능으로 충분하지 않은 경우에는 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-106">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="8a3bb-107">WCF는 사용자가 사용자 지정 인증서 유효성 검사기를 추가할 수 있도록 하 여 유효성 검사 논리를 쉽게 변경 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-107">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="8a3bb-108">사용자 지정 인증서 유효성 검사기가 지정 된 경우 WCF는 기본 제공 인증서 유효성 검사 논리를 사용 하지 않고 대신 사용자 지정 유효성 검사기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-108">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8a3bb-109">프로시저</span><span class="sxs-lookup"><span data-stu-id="8a3bb-109">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="8a3bb-110">사용자 지정 인증서 유효성 검사기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8a3bb-110">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="8a3bb-111"><xref:System.IdentityModel.Selectors.X509CertificateValidator>에서 파생된 새 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-111">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="8a3bb-112">추상 <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-112">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="8a3bb-113">유효성을 검사해야 하는 인증서는 인수로 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-113">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="8a3bb-114">전달된 인증서가 유효성 검사 논리에 따라 유효하지 않은 경우 이 메서드는 <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-114">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="8a3bb-115">인증서가 유효하면 메서드가 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-115">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8a3bb-116">인증 오류를 다시 클라이언트에 반환하려면 <xref:System.ServiceModel.FaultException> 메서드에서 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-116">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="8a3bb-117">서비스 구성에 사용자 지정 인증서 유효성 검사기를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8a3bb-117">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="8a3bb-118">요소 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 와을 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 요소에 추가 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-118">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="8a3bb-119">를 추가 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 하 고 `name` 특성을 적절 한 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-119">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="8a3bb-120">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)요소에를 추가 `<behavior>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-120">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="8a3bb-121">`<clientCertificate>` 요소를 `<serviceCredentials>` 요소에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-121">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="8a3bb-122">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)요소에를 추가 `<clientCertificate>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-122">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="8a3bb-123">`customCertificateValidatorType` 특성을 유효성 검사기 형식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-123">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="8a3bb-124">다음 예제에서는 특성을 형식의 네임스페이스 및 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-124">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="8a3bb-125">`certificateValidationMode` 특성을 `Custom`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-125">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="8a3bb-126">클라이언트에 구성을 사용하여 사용자 지정 인증서 유효성 검사기를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8a3bb-126">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="8a3bb-127">요소 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 와을 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 요소에 추가 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-127">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="8a3bb-128">요소를 추가 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-128">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="8a3bb-129">`<behavior>` 요소를 추가하고 `name` 특성을 적절한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-129">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="8a3bb-130">요소를 추가 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-130">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="8a3bb-131">을 추가 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-131">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="8a3bb-132">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)다음 예제와 같이를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-132">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="8a3bb-133">`customCertificateValidatorType` 특성을 유효성 검사기 형식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-133">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="8a3bb-134">`certificateValidationMode` 특성을 `Custom`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-134">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="8a3bb-135">다음 예제에서는 특성을 형식의 네임스페이스 및 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-135">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="8a3bb-136">서비스에 코드를 사용하여 사용자 지정 인증서 유효성 검사기를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8a3bb-136">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="8a3bb-137"><xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> 속성에 사용자 지정 인증서 유효성 검사기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-137">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="8a3bb-138"><xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 속성을 사용하여 서비스 자격 증명에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-138">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="8a3bb-139"><xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 속성을 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-139">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="8a3bb-140">클라이언트에 코드를 사용하여 사용자 지정 인증서 유효성 검사기를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8a3bb-140">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="8a3bb-141"><xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> 속성을 사용하여 사용자 지정 인증서 유효성 검사기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-141">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="8a3bb-142"><xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 속성을 사용하여 클라이언트 자격 증명에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-142">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="8a3bb-143">[ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 에서 생성 된 클라이언트 클래스는 항상 클래스에서 파생 <xref:System.ServiceModel.ClientBase%601> 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-143">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="8a3bb-144"><xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 속성을 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-144">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a3bb-145">예제</span><span class="sxs-lookup"><span data-stu-id="8a3bb-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a3bb-146">설명</span><span class="sxs-lookup"><span data-stu-id="8a3bb-146">Description</span></span>  

 <span data-ttu-id="8a3bb-147">다음 샘플에서는 서비스에 사용자 지정 인증서 유효성 검사기를 구현하고 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a3bb-147">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a3bb-148">코드</span><span class="sxs-lookup"><span data-stu-id="8a3bb-148">Code</span></span>  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8a3bb-149">참조</span><span class="sxs-lookup"><span data-stu-id="8a3bb-149">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
