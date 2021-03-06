---
description: '자세한 정보: 형식 디자인 지침'
title: 형식 디자인 지침
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: d2c193d41dda118558cc5e7541f7e2dfbaf1a369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641839"
---
# <a name="type-design-guidelines"></a>형식 디자인 지침

CLR 관점에서는 참조 형식과 값 형식이라는 두 가지 범주의 형식만 있습니다. 그러나 프레임워크 디자인에 대해 설명하기 위해 각각 고유한 특정 디자인 규칙을 사용하는 더 많은 논리 그룹으로 형식을 구분합니다.

 클래스는 참조 형식의 일반적인 사례입니다. 클래스는 대다수 프레임워크에서 대부분의 형식을 구성합니다. 클래스는 지원하는 풍부한 개체 지향 기능 세트와 일반적인 적용 가능성 덕분에 많이 사용됩니다. 기본 클래스와 추상 클래스는 확장성과 관련된 특수한 논리 그룹입니다.

 인터페이스는 참조 형식과 값 형식 둘 다에서 구현할 수 있는 형식입니다. 따라서 참조 형식 및 값 형식의 다형성 계층 구조 루트로 사용될 수 있습니다. 또한 인터페이스를 사용하면 CLR에서 기본적으로 지원하지 않는 다중 상속을 시뮬레이션할 수 있습니다.

 구조체는 값 형식의 일반적인 사례이며 언어 기본 형식과 유사하게 작은 단순 형식용으로 예약해야 합니다.

 열거형은 요일, 콘솔 색상 등의 간단한 값 세트를 정의하는 데 사용되는 값 형식의 특수한 사례입니다.

 정적 클래스는 정적 멤버의 컨테이너로 사용되는 형식입니다. 일반적으로 다른 작업에 대한 바로 가기를 제공하는 데 사용됩니다.

 대리자, 예외, 특성, 배열, 컬렉션은 모두 특정 용도로 사용되는 참조 형식의 특수한 사례이며, 디자인 및 사용 지침은 이 설명서의 다른 부분에서 설명합니다.

 ✔️ 각 형식이 관련되지 않은 기능의 임의 컬렉션이 아니라 잘 정의된 관련 멤버 세트가 되도록 하세요.

## <a name="in-this-section"></a>섹션 내용

 [클래스와 구조체 간의 선택](choosing-between-class-and-struct.md) [추상 클래스 디자인](abstract-class.md) [정적 클래스 디자인](static-class.md) [인터페이스 디자인](interface.md) [구조체 디자인](struct.md) [열거형 디자인](enum.md) [중첩 형식](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*

 *Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>참고 항목

- [프레임워크 디자인 지침](index.md)
