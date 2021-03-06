---
description: '다음에 대 한 자세한 정보: COR_IL_MAP 구조체'
title: COR_IL_MAP 구조체
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: ff3d636429f51119342baea5d71163eb9d764e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712326"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP 구조체

함수의 상대 오프셋 변경 내용을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`oldOffset`|함수의 시작 부분을 기준으로 하는 이전 MSIL (Microsoft 중간 언어) 오프셋입니다.|  
|`newOffset`|함수의 시작 부분을 기준으로 하는 새 MSIL 오프셋입니다.|  
|`fAccurate`|`true` 매핑이 정확한 것으로 알려져 있으면이 고, 그렇지 않으면입니다. 그렇지 않으면 `false` 입니다.|  
  
## <a name="remarks"></a>설명  

 맵의 형식은 다음과 같습니다. 디버거는가 수정 되지 않은 `oldOffset` 원래 msil 코드 내에서 msil 오프셋을 참조 한다고 가정 합니다. `newOffset`매개 변수는 계측 된 새 코드 내에서 해당 MSIL 오프셋을 참조 합니다.  
  
 단계별 실행이 제대로 작동 하려면 다음 요구 사항을 충족 해야 합니다.  
  
- 맵은 오름차순으로 정렬 되어야 합니다.  
  
- 계측 된 MSIL 코드는 다시 정렬 하면 안 됩니다.  
  
- 원래 MSIL 코드는 제거 하면 안 됩니다.  
  
- 맵에는 PDB (프로그램 데이터베이스) 파일의 모든 시퀀스 위치를 매핑하는 항목이 포함 되어야 합니다.  
  
 지도는 누락 된 항목을 보간 하지 않습니다. 다음 예에서는 맵과 해당 결과를 보여 줍니다.  
  
 매핑할  
  
- 0 이전 오프셋, 0 새 오프셋  
  
- 5 이전 오프셋, 10 개의 새 오프셋  
  
- 9 이전 오프셋, 20 개의 새 오프셋  
  
 결과:  
  
- 0, 1, 2, 3 또는 4의 이전 오프셋은 0의 새 오프셋에 매핑됩니다.  
  
- 5, 6, 7 또는 8의 이전 오프셋은 새 오프셋 10에 매핑됩니다.  
  
- 이전 오프셋 9 이상은 새 오프셋 20에 매핑됩니다.  
  
- 0, 1, 2, 3, 4, 5, 6, 7, 8 또는 9의 새 오프셋은 이전 오프셋 0에 매핑됩니다.  
  
- 새 오프셋 10, 11, 12, 13, 14, 15, 16, 17, 18 또는 19는 이전 오프셋 5에 매핑됩니다.  
  
- 새 오프셋 20 이상은 이전 오프셋 9에 매핑됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug .idl, Corprof.idl  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 구조체](debugging-structures.md)
- [디버깅](index.md)
