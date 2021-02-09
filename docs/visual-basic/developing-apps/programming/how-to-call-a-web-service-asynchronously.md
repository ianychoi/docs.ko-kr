---
description: '자세한 정보: 방법: 비동기적으로 웹 서비스 호출(Visual Basic)'
title: '방법: 비동기적으로 웹 서비스 호출'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: a702177f60ac598f624676072116bd3ce78da0bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775255"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="dce91-103">방법: 비동기적으로 웹 서비스 호출(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dce91-103">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="dce91-104">이 예제에서는 비동기 메서드 호출의 결과를 검색할 수 있도록 웹 서비스의 비동기 처리기 이벤트에 처리기를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-104">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="dce91-105">여기에는 `http://www.xmethods.net`에 DemoTemperatureService 웹 서비스가 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-105">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="dce91-106">Visual Studio IDE(통합 개발 환경)에서 프로젝트의 웹 서비스를 참조하면, `My.WebServices` 개체에 해당 웹 서비스가 추가되며 IDE에서 지정된 웹 서비스에 액세스하기 위해 클라이언트 프록시 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-106">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="dce91-107">프록시 클래스를 통해 웹 서비스 메서드를 동기식으로 호출할 수 있습니다. 이 경우 애플리케이션은 함수가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-107">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="dce91-108">또한 프록시는 추가 멤버를 만들어 메서드를 비동기식으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-108">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="dce91-109">각 웹 서비스 함수(*NameOfWebServiceFunction*)에 대해 프록시는 *NameOfWebServiceFunction*`Async` 서브루틴, *NameOfWebServiceFunction*`Completed` 이벤트 및 *NameOfWebServiceFunction*`CompletedEventArgs` 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-109">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="dce91-110">이 예제에서는 비동기 멤버를 사용하여 DemoTemperatureService 웹 서비스의 `getTemp` 함수에 액세스하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-110">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="dce91-111">ASP.NET은 `My.WebServices` 개체를 지원하지 않으므로 웹 애플리케이션에서는 이 코드가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-111">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="dce91-112">비동기적으로 웹 서비스 호출</span><span class="sxs-lookup"><span data-stu-id="dce91-112">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="dce91-113">`http://www.xmethods.net`에서 DemoTemperatureService 웹 서비스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-113">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="dce91-114">해당 주소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-114">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="dce91-115">`getTempCompleted` 이벤트에 대한 이벤트 처리기를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-115">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="dce91-116">`Handles` 문을 사용하여 이벤트 처리기를 `My.WebServices` 개체의 이벤트와 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-116">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="dce91-117">이벤트 처리기가 `getTempCompleted` 이벤트에 추가되었는지를 추적할 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-117">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="dce91-118">필요한 경우 이벤트 처리기를 `getTempCompleted` 이벤트에 추가하고 `getTempAsync` 메서드를 호출하는 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-118">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

    ```vb
    Sub CallGetTempAsync(ByVal zipCode As Integer)
        If Not handlerAttached Then
            AddHandler My.WebServices.
                TemperatureService.getTempCompleted,
                AddressOf Me.TS_getTempCompleted
            handlerAttached = True
        End If
        My.WebServices.TemperatureService.getTempAsync(zipCode)
    End Sub
    ```

    <span data-ttu-id="dce91-119">`getTemp` 웹 메서드를 비동기식으로 호출하려면 `CallGetTempAsync` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-119">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="dce91-120">웹 메서드가 완료되면 해당 반환 값이 `getTempCompletedHandler` 이벤트 처리기로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce91-120">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="dce91-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dce91-121">See also</span></span>

- [<span data-ttu-id="dce91-122">애플리케이션 웹 서비스 액세스</span><span class="sxs-lookup"><span data-stu-id="dce91-122">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="dce91-123">My.WebServices 개체</span><span class="sxs-lookup"><span data-stu-id="dce91-123">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
