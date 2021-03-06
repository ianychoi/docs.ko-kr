---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224340"
---
> [!CAUTION]
> CAS (코드 액세스 보안) 및 부분적으로 신뢰할 수 있는 코드
>
> .NET Framework는 동일한 애플리케이션에서 실행되는 다른 코드에 다양한 신뢰 수준을 적용하기 위한 CAS(코드 액세스 보안)라는 메커니즘을 제공합니다.
>
> **CAS는 .NET Core, .NET 5 이상 버전에서 지원 되지 않습니다. CAS는 7.0 이후의 c # 버전에서 지원 되지 않습니다.**
>
> .NET Framework의 CA는 코드를 통해 또는 다른 id 측면에 따라 보안 경계를 적용 하기 위한 메커니즘으로 사용해 서는 안 됩니다. CAS 및 Security-Transparent 코드는 부분적으로 신뢰할 수 있는 코드, 특히 출처를 알 수 없는 코드의 보안 경계로 지원 되지 않습니다. 대체 보안 조치를 적용하지 않고 출처를 알 수 없는 코드를 로드 및 실행하지 않는 것이 좋습니다. .NET Framework는 CAS 샌드박스에 대해 검색 될 수 있는 권한 상승 악용에 대 한 보안 패치를 발급 하지 않습니다.
>
> 이 정책은 모든 버전의 .NET Framework에 적용되지만 Silverlight에 포함된 .NET Framework에는 적용되지 않습니다.
