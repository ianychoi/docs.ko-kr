---
description: '자세한 정보: 방법: 데이터 서비스 쿼리 실행 (WCF Data Services)'
title: '방법: 데이터 서비스 쿼리 실행(WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: 0d78a5a82f23bb6035d21bd45d68a0b1bb76f34b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765323"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>방법: 데이터 서비스 쿼리 실행(WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services를 사용 하면 생성 된 클라이언트 데이터 서비스 클래스를 사용 하 여 .NET Framework 기반 클라이언트 응용 프로그램에서 데이터 서비스를 쿼리할 수 있습니다. 다음 방법 중 하나를 사용하여 쿼리를 실행할 수 있습니다.  
  
- <xref:System.Data.Services.Client.DataServiceQuery%601> 도구가 생성하는 <xref:System.Data.Services.Client.DataServiceContext>에서 가져온 명명된 `Add Data Service Reference`에 대해 LINQ 쿼리 실행  
  
- <xref:System.Data.Services.Client.DataServiceQuery%601> 도구가 생성하는 <xref:System.Data.Services.Client.DataServiceContext>에서 가져온 명명된 `Add Data Service Reference`를 열거하여 암시적으로  
  
- <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>의 <xref:System.Data.Services.Client.DataServiceQuery%601> 메서드를 호출하거나 비동기 실행의 경우 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 메서드를 호출하여 명시적으로  
  
 자세한 내용은 [데이터 서비스 쿼리](querying-the-data-service-wcf-data-services.md)를 참조 하세요.  
  
 이 항목의 예제에서는 Northwind 샘플 데이터 서비스 및 자동 생성된 클라이언트 데이터 서비스 클래스를 사용합니다. 이 서비스 및 클라이언트 데이터 클래스는 [WCF Data Services 빠른](quickstart-wcf-data-services.md)시작을 완료 하면 생성 됩니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 Northwind 데이터 서비스에 대해 모든 `Customers`를 반환하는 LINQ 쿼리를 정의하고 실행하는 방법을 보여 줍니다.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>예제  

 다음 예제에서는 `Add Data Service Reference` 도구가 생성하는 컨텍스트를 사용하여 Northwind 데이터 서비스에 대해 모든 `Customers`를 반환하는 쿼리를 암시적으로 실행하는 방법을 보여 줍니다. 요청 된 엔터티 집합의 URI는 `Customers` 컨텍스트에 의해 자동으로 결정 됩니다. 열거형이 발생 하면 쿼리가 암시적으로 실행 됩니다.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>예제  

 다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext>를 사용하여 Northwind 데이터 서비스에 대해 모든 `Customers`를 반환하는 쿼리를 명시적으로 실행하는 방법을 보여 줍니다.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>참고 항목

- [방법: 데이터 서비스 쿼리에 쿼리 옵션 추가](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
