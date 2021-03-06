---
description: '다음에 대 한 자세한 정보: 열거형 COR_GC_STAT_TYPES'
title: COR_GC_STAT_TYPES 열거형
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c4ea3175c777d49a5d6cffdf506f42e479784971
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799809"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 열거형

가비지 컬렉션에 대해 기록할 통계를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>설명  

 이 열거형은 [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) 메서드로 설정할 [COR_GC_STATS](cor-gc-stats-structure.md) 구조체의 통계를 지정 합니다.  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`COR_GC_COUNTS`|각 세대에 대해 수행 된 가비지 컬렉션의 수를 기록 합니다.|  
|`COR_GC_MEMORYUSAGE`|메모리 사용 및 가비지 컬렉션 크기 통계를 기록 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** GCHost, GCHost  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [COR_GC_STATS 구조체](cor-gc-stats-structure.md)
- [호스팅 열거형](hosting-enumerations.md)
