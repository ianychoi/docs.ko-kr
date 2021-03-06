---
description: '자세한 정보: 서비스 계약 구현'
title: 서비스 계약 구현
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 4510c9e7b9ea3a98a37d528af4064f0e73bea89b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752498"
---
# <a name="implementing-service-contracts"></a>서비스 계약 구현

서비스는 클라이언트에서 사용할 수 있는 기능을 하나 이상의 엔드포인트에 노출하는 클래스입니다. 서비스를 만들려면 WCF (Windows Communication Foundation) 계약을 구현 하는 클래스를 작성 합니다. 이 작업은 다음 두 가지 방법 중 한 가지로 수행할 수 있습니다. 계약을 인터페이스로 따로 정의한 다음 해당 인터페이스를 구현하는 클래스를 만들 수 있습니다. 또는 클래스 자체에 <xref:System.ServiceModel.ServiceContractAttribute> 특성을 두고 서비스 클라이언트에서 사용할 수 있는 메서드에 <xref:System.ServiceModel.OperationContractAttribute> 특성을 두어 클래스와 계약을 직접 만들 수도 있습니다.  
  
## <a name="creating-a-service-class"></a>서비스 클래스 만들기  

 다음은 별도로 정의된 `IMath` 계약을 구현하는 서비스의 예입니다.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 또는 서비스에서 직접 계약을 노출할 수도 있습니다. 다음은 `MathService` 계약을 정의 및 구현하는 서비스 클래스의 예입니다.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 계약 이름이 다르기 때문에 앞의 서비스에서 다른 계약을 노출한다는 것에 주의하십시오. 첫째 경우에서 노출되는 계약의 이름은 "`IMath`"인데 둘째 경우에서 계약의 이름은 "`MathService`"입니다.  
  
 서비스 및 작업 구현 수준에서 동시성 및 인스턴스 등을 설정할 수 있습니다. 자세한 내용은 [서비스 디자인 및 구현](designing-and-implementing-services.md)을 참조 하세요.  
  
 서비스 계약을 구현하고 나면 서비스에 하나 이상의 엔드포인트를 만들어야 합니다. 자세한 내용은 [끝점 만들기 개요](endpoint-creation-overview.md)를 참조 하세요. 서비스를 실행 하는 방법에 대 한 자세한 내용은 [호스팅 서비스](hosting-services.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- [서비스 디자인 및 구현](designing-and-implementing-services.md)
- [방법: Contract 클래스를 사용하여 서비스 만들기](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [방법: Contract 인터페이스를 사용하여 서비스 만들기](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [서비스 런타임 동작 지정](specifying-service-run-time-behavior.md)
