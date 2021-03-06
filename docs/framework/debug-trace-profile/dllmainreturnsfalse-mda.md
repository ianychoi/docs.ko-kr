---
title: dllMainReturnsFalse MDA
description: .NET의 dllMainReturnsFalse 관리 디버깅 도우미에 대해 읽어 보세요. DLL 초기화에 실패 한 경우이 MDA가 활성화 됩니다.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 83f38c4918c1354477627b70a62e60cbdc7de275
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273518"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA

DLL_PROCESS_ATTACH로 인해 호출된 사용자 어셈블리의 관리되는 `DllMain` 함수가 FALSE를 반환하면 `dllMainReturnsFalse` MDA(관리 디버깅 도우미)가 활성화됩니다.  
  
## <a name="symptoms"></a>증상  

 `DllMain` 함수가 FALSE를 반환했고 이는 함수가 제대로 실행되지 않았음을 나타냅니다. `DllMain` 함수에는 일반적으로 중요한 초기화 코드가 포함되므로 이로 인해 결정되지 않은 문제가 발생할 수 있습니다.  
  
## <a name="cause"></a>원인  

 로드 시 DLL 초기화에 대한 DLL_PROCESS_ATTACH로 인해 `DllMain` 함수가 호출됩니다. 함수가 FALSE를 반환하면 DLL 초기화가 실패했음을 의미합니다.  
  
## <a name="resolution"></a>해결 방법  

 실패한 DLL의 `DllMain` 함수 코드를 분석하고 초기화 실패의 원인을 식별합니다.  
  
## <a name="effect-on-the-runtime"></a>런타임에 대한 영향  

 이 MDA는 CLR에 아무런 영향을 미치지 않습니다. `DllMain`의 반환 값에 대한 데이터만 보고합니다.  
  
## <a name="output"></a>출력  

 DLL_PROCESS_ATTACH로 인해 호출되는 `DllMain` 함수가 FALSE를 반환했음을 나타내는 메시지입니다. 이 MDA는 `DllMain`이 관리 코드에서 구현된 경우에만 활성화됩니다.  
  
## <a name="configuration"></a>구성  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>참고 항목

- [관리 디버깅 도우미를 사용하여 오류 진단](diagnosing-errors-with-managed-debugging-assistants.md)
