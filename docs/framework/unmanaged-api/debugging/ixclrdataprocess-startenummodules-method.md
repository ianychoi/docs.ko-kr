---
description: '자세히 알아보기: IXCLRDataProcess:: StartEnumModules 메서드'
title: 'IXCLRDataProcess:: StartEnumModules 메서드'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e90c646ee8815ec10ce0bbd7538f13d7b5dcf8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800584"
---
# <a name="ixclrdataprocessstartenummodules-method"></a>IXCLRDataProcess:: StartEnumModules 메서드

프로세스의 모듈을 열거 하는 핸들을 제공 합니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>매개 변수

`handle`\
제한이 모듈을 열거 하는 핸들입니다.

## <a name="remarks"></a>설명

제공 된 메서드는 인터페이스의 일부 이며 `IXCLRDataProcess` 가상 메서드 테이블의 24 일 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
**헤더:** 없음을  
**라이브러리:** 없음을  
**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [CLRDataSourceType 열거형](clrdatasourcetype-enumeration.md)
- [디버깅](index.md)
- [IXCLRDataProcess 인터페이스](ixclrdataprocess-interface.md)
