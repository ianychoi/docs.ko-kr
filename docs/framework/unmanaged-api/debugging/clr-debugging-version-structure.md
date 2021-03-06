---
description: '다음에 대 한 자세한 정보: CLR_DEBUGGING_VERSION 구조체'
title: CLR_DEBUGGING_VERSION 구조체
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772785"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION 구조체

디버깅용 CLR(공용 언어 런타임)의 제품 버전을 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`wStructVersion`|구조 버전 번호입니다.|  
|`wMajor`|주 버전 번호입니다.|  
|`wMinor`|부 버전 번호입니다.|  
|`wBuild`|빌드 번호입니다.|  
|`wRevision`|수정 번호입니다.|  
  
## <a name="remarks"></a>설명  

 `CLR_DEBUGGING_VERSION`구조는 COR_VERSION 구조와 동일 하지만 구조는 `CLR_DEBUGGING_VERSION` 추가 구조 버전 필드 ()를 제공 합니다 `wStructVersion` . 현재이 필드는 0으로 설정 해야 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug .idl  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 구조체](debugging-structures.md)
- [디버깅](index.md)
