---
description: '자세히 알아보기: ICorDebugMergedAssemblyRecord:: GetCulture 메서드'
title: ICorDebugMergedAssemblyRecord::GetCulture 메서드
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f530bb68a1e7e4c4bff53b8f3046f6ae9ca42aab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754006"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture 메서드

어셈블리의 문화권 이름 문자열을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cchCulture`  
 [in] `szCulture` 버퍼의 문자 수입니다.  
  
 `pcchCulture`  
 [out] 실제로 `szCulture` 버퍼에 기록되는 문자 수입니다.  
  
 `szCulture`  
 [out] 문화권 이름을 포함하는 문자 배열입니다.  
  
## <a name="remarks"></a>설명  

 문화권 이름은 문화권을 식별하는 고유 문자열입니다(예: 영어(미국) 문화권 "en-US" 또는 중립 문화권 "neutral").  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugMergedAssemblyRecord 인터페이스](icordebugmergedassemblyrecord-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
