---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700864"
---
### <a name="include-specific-api-surfaces"></a>특정 API 화면 포함

액세스 가능성에 따라이 규칙을 실행할 코드 베이스의 부분을 구성할 수 있습니다. 예를 들어 public이 아닌 API 화면에 대해서만 규칙을 실행 하도록 지정 하려면 프로젝트의 *editorconfig* 파일에 다음 키-값 쌍을 추가 합니다.

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
