---
description: '자세한 정보: 연습: 관계 간 쿼리 (Visual Basic)'
title: '연습: 관계 간 쿼리(Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 002ec53c5a56d988dcd71af658a546d199473425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650575"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="45cc9-103">연습: 관계 간 쿼리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45cc9-103">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>

<span data-ttu-id="45cc9-104">이 연습에서는 연결을 사용 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  하 여 데이터베이스에서 외래 키 관계를 나타내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-104">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="45cc9-105">이 연습은 Visual Basic 개발 설정을 사용하여 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="45cc9-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="45cc9-106">Prerequisites</span></span>  

 <span data-ttu-id="45cc9-107">[연습: 간단한 개체 모델 및 쿼리 (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-107">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="45cc9-108">이 연습은 c:\linqtest에 있는 northwnd.mdf 파일을 비롯하여 해당 연습의 단순 개체 모델 및 쿼리를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-108">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="45cc9-109">개요</span><span class="sxs-lookup"><span data-stu-id="45cc9-109">Overview</span></span>  

 <span data-ttu-id="45cc9-110">이 연습은 다음과 같은 세 가지 주요 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-110">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="45cc9-111">Northwind 샘플 데이터베이스의 Orders 테이블을 나타내는 엔터티 클래스 추가</span><span class="sxs-lookup"><span data-stu-id="45cc9-111">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="45cc9-112">`Customer` 및 `Customer` 클래스 간의 관계를 향상시키기 위해 `Order` 클래스에 주석 추가</span><span class="sxs-lookup"><span data-stu-id="45cc9-112">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="45cc9-113">`Order` 클래스를 사용하여 `Customer` 정보를 가져오는 과정을 테스트하는 쿼리 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="45cc9-113">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="45cc9-114">테이블 간 관계 매핑</span><span class="sxs-lookup"><span data-stu-id="45cc9-114">Mapping Relationships across Tables</span></span>  

 <span data-ttu-id="45cc9-115">`Customer` 클래스 정의 후에 `Order`가 외래 키로 `Orders.Customer`에 관련된다는 것을 나타내는 다음 코드가 포함된 `Customers.CustomerID` 엔터티 클래스 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-115">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="45cc9-116">Order 엔터티 클래스를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="45cc9-116">To add the Order entity class</span></span>  
  
- <span data-ttu-id="45cc9-117">`Customer` 클래스 뒤에 다음 코드를 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-117">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="45cc9-118">Customer 클래스에 주석 지정</span><span class="sxs-lookup"><span data-stu-id="45cc9-118">Annotating the Customer Class</span></span>  

 <span data-ttu-id="45cc9-119">이 단계에서는 `Customer` 클래스에 대한 관계를 나타내기 위해 `Order` 클래스에 주석을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-119">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="45cc9-120">어느 방향으로든 관계를 정의하여 링크를 충분히 만들 수 있으므로 이 추가 작업이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-120">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="45cc9-121">그러나 이 주석을 추가하면 어느 방향으로나 개체를 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-121">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="45cc9-122">Customer 클래스에 주석을 달려면</span><span class="sxs-lookup"><span data-stu-id="45cc9-122">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="45cc9-123">`Customer` 클래스에 다음 코드를 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-123">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="45cc9-124">Customer 및 Order 관계에서 쿼리 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="45cc9-124">Creating and Running a Query across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="45cc9-125">이제 `Order` 개체에서 `Customer` 개체를 직접 액세스하거나 그 반대 방향으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-125">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="45cc9-126">고객과 주문 간에 명시적 *조인이* 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-126">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="45cc9-127">Customer 개체를 사용하여 Order 개체에 액세스하려면</span><span class="sxs-lookup"><span data-stu-id="45cc9-127">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="45cc9-128">다음 코드를 `Sub Main` 메서드에 입력하거나 붙여넣어 이 메서드를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-128">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="45cc9-129">F5 키를 눌러 애플리케이션을 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-129">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="45cc9-130">두 이름이 메시지 상자에 표시되며 콘솔 창에는 생성된 SQL 코드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-130">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="45cc9-131">메시지 상자를 닫아 디버깅을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-131">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="45cc9-132">강력한 형식의 데이터베이스 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="45cc9-132">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="45cc9-133">강력한 형식의 데이터베이스 뷰로 작업을 시작하는 것이 훨씬 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-133">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="45cc9-134"><xref:System.Data.Linq.DataContext> 개체를 강력한 형식으로 설정하면 <xref:System.Data.Linq.DataContext.GetTable%2A> 호출이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-134">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="45cc9-135">강력한 형식의 <xref:System.Data.Linq.DataContext> 개체를 사용할 경우 모든 쿼리에서 강력한 형식의 테이블을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-135">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="45cc9-136">다음 단계에서는 `Customers`를 데이터베이스의 Customers 테이블에 매핑되는 강력한 형식의 테이블로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-136">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="45cc9-137">DataContext 개체를 강력한 형식으로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="45cc9-137">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="45cc9-138">`Customer` 클래스 선언 위에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-138">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="45cc9-139">다음과 같이 강력한 형식의 `Sub Main`를 사용하도록 <xref:System.Data.Linq.DataContext>을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-139">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="45cc9-140">F5 키를 눌러 애플리케이션을 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-140">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="45cc9-141">콘솔 창 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-141">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="45cc9-142">콘솔 창에서 Enter 키를 눌러 애플리케이션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-142">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="45cc9-143">이 응용 프로그램을 저장 하려면 **파일** 메뉴에서 **모두 저장** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-143">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="45cc9-144">다음 단계</span><span class="sxs-lookup"><span data-stu-id="45cc9-144">Next Steps</span></span>  

 <span data-ttu-id="45cc9-145">다음 연습 ([연습: 데이터 조작 (Visual Basic)](walkthrough-manipulating-data-visual-basic.md))에서는 데이터를 조작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-145">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="45cc9-146">다음 연습에서는 이미 완료한 이 시리즈의 연습 두 개를 저장할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45cc9-146">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cc9-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45cc9-147">See also</span></span>

- [<span data-ttu-id="45cc9-148">연습으로 학습</span><span class="sxs-lookup"><span data-stu-id="45cc9-148">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
