---
description: '자세히 알아보기: ICorDebugVariableHome:: GetSlotIndex 메서드'
title: 'ICorDebugVariableHome:: GetSlotIndex 메서드'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 7f6ee01c2bfcee4c78f8463a7cefac1f90a3295f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790648"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome:: GetSlotIndex 메서드

지역 변수의 관리 되는 슬롯 인덱스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pSlotIndex`  
 제한이 지역 변수의 슬롯 인덱스에 대 한 포인터입니다.  
  
## <a name="return-value"></a>Return Value  

 메서드는 다음 값을 반환 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드 호출이에서 슬롯 인덱스 값을 반환 했습니다 `pSlotIndex` .|  
|`E_FAIL`|현재 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 인스턴스는 함수 인수를 나타냅니다.|  
  
## <a name="remarks"></a>설명  

 슬롯 인덱스를 사용 하 여이 지역 변수에 대 한 메타 데이터를 검색할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugVariableHome 인터페이스](icordebugvariablehome-interface.md)
