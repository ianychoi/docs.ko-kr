---
description: '자세히 알아보기: ICorDebugProcess6:: GetCode 메서드'
title: ICorDebugProcess6::GetCode 메서드
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: a7cb71ddb1e65cda37d762a0fba958d413145138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649665"
---
# <a name="icordebugprocess6getcode-method"></a>ICorDebugProcess6::GetCode 메서드

특정 코드 주소에서 관리 코드에 대한 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a>매개 변수  

 `codeAddress`  
 진행 관리 코드 세그먼트의 시작 주소를 지정 하는 [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 값입니다.  
  
 `ppCode`  
 제한이 관리 코드의 세그먼트를 나타내는 "ICorDebugCode" 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugProcess6 인터페이스](icordebugprocess6-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
