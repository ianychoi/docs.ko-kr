---
description: '자세히 알아보기: ICorDebugVariableHome:: GetRegister 메서드'
title: 'ICorDebugVariableHome:: GetRegister 메서드'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: c394d455048cf7451b8320ed72a6aa7adfb3518e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790661"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome:: GetRegister 메서드

위치 형식이 인 변수가 포함 된 레지스터 `VLT_REGISTER` 와 위치 형식이 인 변수에 대 한 기본 레지스터를 가져옵니다 `VLT_REGISTER_RELATIVE` .  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pRegister`  
 제한이 의 위치 형식이 있는 변수의 등록을 나타내는 CorDebugRegister 열거형 값 `VLT_REGISTER` 과 위치 형식이 인 변수에 대 한 기본 레지스터입니다 `VLT_REGISTER_RELATIVE` .  
  
## <a name="return-value"></a>Return Value  

 메서드는 다음 값을 반환 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|변수가 인수가 나타내는 레지스터에 `pRegister` 있습니다.|  
|`E_FAIL`|변수가 레지스터 또는 레지스터 상대 위치에 있지 않습니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [VariableLocationType 열거형](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome 인터페이스](icordebugvariablehome-interface.md)
