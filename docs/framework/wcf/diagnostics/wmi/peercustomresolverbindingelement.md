---
description: '자세히 알아보기: PeerCustomResolverBindingElement'
title: PeerCustomResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 9ccc2770-a20e-4dff-9970-f56ad8aec2b5
ms.openlocfilehash: f4277c04818eec69c1041eee30282d3111421eaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803050"
---
# <a name="peercustomresolverbindingelement"></a>PeerCustomResolverBindingElement

PeerCustomResolverBindingElement

## <a name="syntax"></a>Syntax

```csharp
class PeerCustomResolverBindingElement : PeerResolverBindingElement
{
    string Address;
    string Binding;
};
```

## <a name="methods"></a>메서드

PeerCustomResolverBindingElement 클래스는 메서드를 정의하지 않습니다.

## <a name="properties"></a>속성

 PeerCustomResolverBindingElement 클래스에는 다음과 같은 속성이 있습니다.

### <a name="address"></a>주소

데이터 형식: 문자열

액세스 형식: 읽기 전용

피어 사용자 지정 확인자의 주소입니다.

### <a name="binding"></a>바인딩

데이터 형식: 문자열

액세스 형식: 읽기 전용

바인딩의 구성 이름입니다.

## <a name="requirements"></a>요구 사항

|MOF|Servicemodel.mof에 선언되어 있습니다.|
|---------|-----------------------------------|
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|

## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement>
