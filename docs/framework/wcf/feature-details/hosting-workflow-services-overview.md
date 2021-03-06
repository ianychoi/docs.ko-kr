---
description: '자세한 정보: 워크플로 서비스 호스팅 개요'
title: 워크플로 서비스 호스팅 개요
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: e183dfd7428c11cf20e731ab4a9975a7388b6f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743085"
---
# <a name="hosting-workflow-services-overview"></a>워크플로 서비스 호스팅 개요

워크플로 서비스를 실행하려면 호스팅해야 합니다. <xref:System.ServiceModel.WorkflowServiceHost>는 여러 인스턴스, 구성 및 WCF 메시징(워크플로가 호스팅되기 위해 메시징을 사용할 필요는 없지만)을 지원하는 즉시 사용 가능한 워크플로 호스트로,  서비스 동작의 집합을 통해 지속성, 추적 및 인스턴스 제어와 통합됩니다.  WCF의 <xref:System.ServiceModel.ServiceHost>와 마찬가지로 <xref:System.ServiceModel.WorkflowServiceHost>는 모든 관리되는 .NET 애플리케이션에서 자체 호스팅되거나 IIS/WAS에서 .xamlx 파일로 웹 호스팅될 수 있습니다.  이 단원의 항목에서는 워크플로 서비스를 호스팅하는 방법에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [워크플로 서비스 호스팅](hosting-workflow-services.md)  
 워크플로 서비스 호스팅에 대해 설명합니다.  
  
 [워크플로 서비스 호스트 내부 기능](workflow-service-host-internals.md)  
 <xref:System.ServiceModel.WorkflowServiceHost>가 들어오는 메시지를 처리하는 방법에 대해 설명합니다.  
  
 [워크플로 서비스 호스트 확장](workflow-service-host-extensibility.md)  
 워크플로 서비스 호스트의 기능을 확장하는 방법에 대해 설명합니다.  
  
 [워크플로 제어 엔드포인트](workflow-control-endpoint.md)  
 워크플로 인스턴스를 만들 수 있는 엔드포인트를 정의하는 방법에 대해 설명합니다.
  
 [방법: Windows Server App Fabric을 사용하여 워크플로 서비스 호스팅](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Windows Server AppFabric에서 기존 워크플로 서비스를 호스팅하는 방법을 보여 줍니다.  
  
 [WorkflowServiceHost 구성](configuring-workflowservicehost.md)  
 지속성, 추적, 유휴 상태 및 처리되지 않은 예외 동작을 제어하는 방법에 대해 설명합니다.  
  
## <a name="reference"></a>참고  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>관련 단원  

 [워크플로 서비스](workflow-services.md)
