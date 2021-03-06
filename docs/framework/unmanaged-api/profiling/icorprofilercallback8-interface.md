---
description: '자세히 알아보기: ICorProfilerCallback8 인터페이스'
title: ICorProfilerCallback8 인터페이스
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 8dd9b8eea82f38b7598d578bd718743af826070d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781677"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 인터페이스

[.NET Framework 4.7 이상 버전에서 지원 됨]  

 공용 언어 런타임에서 동적 메서드의 JIT 컴파일이 시작 및 완료 되었음을 프로파일러에 알리기 위해 사용 하는 콜백 메서드를 제공 하는 [ICorProfilerCallback7](icorprofilercallback7-interface.md) 의 서브 클래스입니다.
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted 메서드](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|동적 메서드의 JIT 컴파일이 시작 되었음을 프로파일러에 알립니다.|  
|[DynamicMethodJITCompilationFinished 메서드](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|동적 메서드의 JIT 컴파일이 완료 되었음을 프로파일러에 알립니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [프로파일링 인터페이스](profiling-interfaces.md)
- [ICorProfilerCallback9 인터페이스](icorprofilercallback9-interface.md)
