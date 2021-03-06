---
description: '다음에 대 한 자세한 정보: 지 속성 참가자'
title: 지속성 참석자
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 66f39bfe5b9efcae5d8377fda9415efd4cab9468
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742058"
---
# <a name="persistence-participants"></a>지속성 참석자

지속성 참가자는 애플리케이션 호스트에서 트리거된 지속성 작업(저장 또는 로드)에 참가할 수 있습니다. 는 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 지 속성 참가자를 만드는 데 사용할 수 있는 두 개의 추상 클래스인 **PersistenceParticipant** 및 **PersistenceIOParticipant** 를 제공 합니다. 지속성 참가자는 이 클래스 중 하나에서 파생되고 관련 메서드를 구현한 다음 클래스의 인스턴스를 <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A>의 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 컬렉션에 추가합니다. 애플리케이션 호스트는 워크플로 인스턴스를 지속할 때 이 워크플로 확장을 검색하고 적당한 시간에 지속성 참가자에서 해당 메서드를 호출합니다.  
  
 다음 목록에서는 유지(저장) 작업의 여러 단계에서 지속성 하위 시스템이 수행하는 작업을 설명합니다. 지속성 참가자는 세 번째 단계와 네 번째 단계에서 사용됩니다. 참가자가 i/o 작업에도 참여 하는 i/o 참가자 인 경우 해당 참가자는 여섯 번째 단계 에서도 사용 됩니다.  
  
1. 워크플로 상태, 책갈피, 매핑된 변수 및 타임스탬프 등 기본 제공 값을 수집합니다.  
  
2. 워크플로 인스턴스와 연결된 확장 수집에 추가된 모든 지속성 참가자를 수집합니다.  
  
3. 모든 지속성 참가자에서 구현된 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 메서드를 호출합니다.  
  
4. 모든 지속성 참가자에서 구현된 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 메서드를 호출합니다.  
  
5. 워크플로를 지속성 저장소에 유지하거나 저장합니다.  
  
6. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A>모든 지 속성 i/o 참가자에 대해 메서드를 호출 합니다. 참가자가 i/o 참가자가 아닌 경우에는이 작업을 건너뜁니다. 지속성 에피소드가 트랜잭션인 경우 이 트랜잭션은 Transaction.Current 속성에서 제공됩니다.  
  
7. 모든 지속성 참가자가 완료될 때까지 기다립니다. 모든 참가자가 인스턴스 데이터 유지에 성공하면 트랜잭션을 커밋합니다.  
  
 지 속성 참가자는 **PersistenceParticipant** 클래스에서 파생 되며 **CollectValues** 및 **mapvalues** 메서드를 구현할 수 있습니다. 지 속성 i/o 참가자는 **PersistenceIOParticipant** 클래스에서 파생 되며 **CollectValues** 및 **mapvalues** 메서드를 구현 하는 것 외에도 **beginonsave로** 메서드를 구현할 수 있습니다.  
  
 각 단계는 다음 단계가 시작되기 전에 완료됩니다. 예를 들어 첫 번째 단계에서 **모든** 지 속성 참가자 로부터 값을 수집 합니다. 두 번째 단계에서는 첫 번째 단계에서 수집한 모든 값을 모든 지속성 참가자에게 제공합니다. 세 번째 단계에서는 첫 번째 단계와 두 번째 단계에서 수집하고 매핑한 모든 값을 지속성 공급자에게 제공하며, 이후에도 같은 방식으로 계속됩니다.  
  
 다음 목록에서는 로드 작업의 여러 단계에서 지속성 하위 시스템이 수행하는 작업을 설명합니다. 지속성 참가자는 네 번째 단계에서 사용됩니다. 지 속성 (i/o) 참가자 (i/o 작업에도 참여 하는 지 속성 참가자)는 세 번째 단계 에서도 사용 됩니다.  
  
1. 워크플로 인스턴스와 연결된 확장 수집에 추가된 모든 지속성 참가자를 수집합니다.  
  
2. 지속성 저장소에서 워크플로를 로드합니다.  
  
3. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A>모든 지 속성 i/o 참가자에 대해를 호출 하 고 모든 지 속성 참가자가 완료 될 때까지 기다립니다. 지속성 에피소드가 트랜잭션인 경우 이 트랜잭션은 Transaction.Current에서 제공됩니다.  
  
4. 지속성 저장소에서 검색한 데이터를 기반으로 메모리에 워크플로 인스턴스를 로드합니다.  
  
5. 각 지속성 참가자에서 <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A>를 호출합니다.  
  
 지 속성 참가자는 **PersistenceParticipant** 클래스에서 파생 되며, 지 속성 **값** 메서드를 구현할 수 있습니다. 지 속성 i/o 참가자는 **PersistenceIOParticipant** 클래스에서 파생 되며, 출력 **값** 메서드를 구현 하는 것 외에도 **beginonload** 메서드를 구현할 수 있습니다.  
  
 워크플로 인스턴스를 로드하면 지속성 공급자는 해당 인스턴스에 잠금을 만듭니다. 그러면 인스턴스가 다중 노드 시나리오에서 둘 이상의 호스트에 로드되는 것이 방지됩니다. 잠겨 있는 워크플로를 로드하려고 시도하면 다음과 같은 예외가 발생합니다. 예외 "System.ServiceModel.Persistence.InstanceLockException: '00000000-0000-0000-0000-000000000000' 인스턴스에 대한 잠금을 수행할 수 없으므로 요청한 작업을 완료할 수 없습니다.". 이 오류는 다음 중 하나가 발생하는 경우 발생합니다.  
  
- 다중 노드 시나리오에서 인스턴스는 다른 호스트에 의해 로드됩니다.  이러한 충돌 유형을 해결하는 방법은 몇 가지가 있습니다. 잠금을 소유하고 있는 노드에 처리를 전송하거나 다른 호스트가 해당 작업을 저장할 수 있도록 강제로 로드합니다.  
  
- 단일 노드 시나리오에서는 호스트가 충돌합니다.  호스트가 다시 시작되면(프로세스 재생 또는 새 지속성 공급자 팩터리 만들기) 새 호스트는 잠금이 아직 만료되지 않았기 때문에 기존 호스트가 아직 잠근 인스턴스를 로드하려고 시도합니다.  
  
- 단일 노드 시나리오에서는 해당 인스턴스가 어느 지점에서 중단되고 다른 호스트 ID를 가진 새 지속성 공급자가 만들어집니다.  
  
 잠금 시간 제한의 기본값은 5분이며 <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>를 호출할 때 다른 시간 제한 값을 지정할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
- [방법: 사용자 지정 지속성 참가자 만들기](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>참고 항목

- [저장소 확장성](store-extensibility.md)
