---
description: IMetaDataEmit::D efineMethodImpl 메서드에 대해 자세히 알아보세요.
title: IMetaDataEmit::DefineMethodImpl 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 9c79d713e61bfcc7b3191e570ed727b128422bf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753408"
---
# <a name="imetadataemitdefinemethodimpl-method"></a>IMetaDataEmit::DefineMethodImpl 메서드

인터페이스에서 상속 된 메서드의 구현에 대 한 정의를 만들고 해당 메서드 구현 정의에 대 한 토큰을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `td`  
 진행 `mdTypedef` 구현 하는 클래스의 토큰입니다.  
  
 `tkBody`  
 진행 `mdMethodDef` `mdMemberRef` 코드 본문의 또는 토큰입니다.  
  
 `tkDecl`  
 진행 `mdMethodDef` `mdMemberRef` 구현 중인 인터페이스 메서드의 또는 토큰입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataEmit 인터페이스](imetadataemit-interface.md)
- [IMetaDataEmit2 인터페이스](imetadataemit2-interface.md)
