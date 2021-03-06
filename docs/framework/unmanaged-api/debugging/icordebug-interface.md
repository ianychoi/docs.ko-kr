---
description: '자세히 알아보기: ICorDebug 인터페이스'
title: ICorDebug 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: b989013f7eb54e163feeb965e10448a3a1756e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772525"
---
# <a name="icordebug-interface"></a>ICorDebug 인터페이스

개발자가 CLR (공용 언어 런타임) 환경에서 응용 프로그램을 디버그할 수 있도록 하는 메서드를 제공 합니다.  
  
> [!NOTE]
> 혼합 모드 (관리 코드 및 네이티브 코드) 디버깅은 Windows 95, Windows 98, Windows ME 또는 비 x86 플랫폼 (예: IA64 및 AMD64)에서 지원 되지 않습니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[CanLaunchOrAttach 메서드](icordebug-canlaunchorattach-method.md)|현재 컴퓨터 및 런타임 구성의 컨텍스트 내에서 새 프로세스를 시작 하거나 지정 된 프로세스에 연결할 수 있는지 여부를 결정 합니다.|  
|[CreateProcess 메서드](icordebug-createprocess-method.md)|디버거를 제어할 때 프로세스 및 해당 기본 스레드를 시작 합니다.|  
|[DebugActiveProcess 메서드](icordebug-debugactiveprocess-method.md)|디버거를 기존 프로세스에 연결 합니다.|  
|[EnumerateProcesses 메서드](icordebug-enumerateprocesses-method.md)|디버깅 중인 프로세스에 대 한 열거자를 가져옵니다.|  
|[GetProcess 메서드](icordebug-getprocess-method.md)|지정 된 프로세스 ID를 사용 하 여 "ICorDebugProcess" 개체를 반환 합니다.|  
|[Initialize 메서드](icordebug-initialize-method.md)|초기화는 `ICorDebug` 개체입니다.|  
|[SetManagedHandler 메서드](icordebug-setmanagedhandler-method.md)|관리 되는 이벤트에 대 한 이벤트 처리기 개체를 지정 합니다.|  
|[SetUnmanagedHandler 메서드](icordebug-setunmanagedhandler-method.md)|관리 되지 않는 이벤트에 대 한 이벤트 처리기 개체를 지정 합니다.|  
|[Terminate 메서드](icordebug-terminate-method.md)|개체를 종료 `ICorDebug` 합니다.|  
  
## <a name="remarks"></a>설명  

 `ICorDebug` 디버거 프로세스에 대 한 이벤트 처리 루프를 나타냅니다. 디버거는이 인터페이스를 해제 하기 전에 디버깅 중인 모든 프로세스에서 [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) 콜백이 대기 해야 합니다.  
  
 `ICorDebug`개체는 모든 추가 관리 디버깅을 제어 하는 초기 개체입니다. .NET Framework 버전 1.0 및 1.1에서이 개체는 `CoClass` COM에서 만든 개체 였습니다. .NET Framework 버전 2.0에서이 개체는 더 이상 `CoClass` 개체가 아닙니다. 버전을 인식 하는 [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) 함수를 통해 만들어야 합니다. 이 새 생성 함수를 사용 하면 클라이언트는 특정 버전의 디버깅 API를 에뮬레이션 하는의 특정 구현을 가져올 수 있습니다 `ICorDebug` .  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 인터페이스](debugging-interfaces.md)
