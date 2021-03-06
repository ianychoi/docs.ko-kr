---
description: '자세한 정보: 확장성을 위한 디자인'
title: 확장성을 위한 디자인
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642268"
---
# <a name="designing-for-extensibility"></a>확장성을 위한 디자인

프레임워크 설계에서 한 가지 중요한 측면은 프레임워크의 확장성이 신중하게 고려되도록 하는 것입니다. 이렇게 하려면 다양한 확장성 메커니즘과 관련된 비용 및 혜택을 이해해야 합니다. 이 장은 프레임워크의 요구 사항에 가장 잘 맞는 확장성 메커니즘(서브클래싱, 이벤트, 가상 멤버, 콜백 등)을 결정하는 데 도움이 됩니다.  
  
 여러 가지 방법으로 프레임워크에서 확장성을 허용할 수 있습니다. 덜 강력하지만 비용이 저렴한 방법부터 매우 강력하지만 비용이 많이 드는 방법까지 다양합니다. 지정된 확장성 요구 사항에 따라 요구 사항을 충족하는 비용이 가장 저렴한 확장성 메커니즘을 선택해야 합니다. 일반적으로 나중에 확장성을 더 추가할 수 있지만 제거하려면 반드시 호환성이 손상되는 변경이 필요할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [봉인되지 않은 클래스](unsealed-classes.md)  
 [보호된 멤버](protected-members.md)  
 [이벤트 및 콜백](events-and-callbacks.md)  
 [가상 멤버](virtual-members.md)  
 [추상화(추상 형식 및 인터페이스)](abstractions-abstract-types-and-interfaces.md)  
 [추상화 구현을 위한 기본 클래스](base-classes-for-implementing-abstractions.md)  
 [봉인](sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
  
 *Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>참고 항목

- [프레임워크 디자인 지침](index.md)
