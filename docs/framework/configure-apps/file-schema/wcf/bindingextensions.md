---
description: 다음에 대해 자세히 알아보세요. <bindingExtensions>
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: e568c7dd2da509709e5c85d3181d1808b1c636df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639408"
---
# \<bindingExtensions>

<span data-ttu-id="0dd09-102">이 섹션은 시스템 또는 애플리케이션 구성 파일의 사용자 정의 바인딩을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="0dd09-103">`add` 키워드를 사용하고 요소의 `type` 특성을 사용자 정의 바인딩으로 설정하고 `name` 특성을 사용자 정의 바인딩의 이름으로 설정하여 사용자 정의 바인딩을 이 컬렉션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="0dd09-104">바인딩 확장을 사용하면 엔드포인트 구성의 일부로 사용할 사용자 정의 바인딩을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="0dd09-105">프로그래밍에서 바인딩 확장은 추상 클래스 <xref:System.ServiceModel.Channels.Binding>을 구현하는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="0dd09-106">다음 예제에서는 요소 및 특성을 사용 하 여 `add` `name` `bindingExtensions` 구성 파일의 섹션에 바인딩 확장을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

```xml
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```

<span data-ttu-id="0dd09-107">요소에 구성 기능을 추가하려면 `bindingSection` 요소를 작성하고 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="0dd09-108">이에 대한 자세한 내용은 <xref:System.Configuration> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0dd09-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="0dd09-109">요소와 해당 구성 형식을 정의한 후에는 다음 예제와 같이 확장을 끝점의 일부로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dd09-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="0dd09-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0dd09-110">See also</span></span>

- [<span data-ttu-id="0dd09-111">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="0dd09-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
