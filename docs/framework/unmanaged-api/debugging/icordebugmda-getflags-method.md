---
description: '자세히 알아보기: ICorDebugMDA:: GetFlags 메서드'
title: ICorDebugMDA::GetFlags 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 53476da06252771627d4883ef9056eb7f945e1b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801178"
---
# <a name="icordebugmdagetflags-method"></a>ICorDebugMDA::GetFlags 메서드

[ICorDebugMDA](icordebugmda-interface.md)로 표시 된 MDA (관리 디버깅 도우미)와 연결 된 플래그를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pFlags`  
 진행 이 MDA에 대 한 플래그의 설정을 지정 하는 [Cordebugmdaflags](cordebugmdaflags-enumeration.md) 열거형 값의 비트 조합입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugMDA 인터페이스](icordebugmda-interface.md)
- [관리 디버깅 도우미를 사용하여 오류 진단](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
