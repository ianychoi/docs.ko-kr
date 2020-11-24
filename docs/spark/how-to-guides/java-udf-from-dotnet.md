---
title: .NET for Apache Spark 애플리케이션에서 Java UDF 호출
description: .NET for Apache Spark 애플리케이션에서 Java UDF를 호출하는 방법을 알아봅니다.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 17f0ff611e68a5dab2032f78ef75912f314d88a5
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688269"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="30111-103">.NET for Apache Spark 애플리케이션에서 Java UDF 호출</span><span class="sxs-lookup"><span data-stu-id="30111-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="30111-104">이 문서에서는 [.NET for Apache Spark](https://github.com/dotnet/spark) 애플리케이션에서 Java UDF(사용자 정의 함수)를 호출하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="30111-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="30111-105">Java UDF를 정의하고 jar로 컴파일하는 방법 - jar 파일에 UDF가 이미 정의되어 있으면 이 단계는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30111-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="30111-106">이 경우 패키지를 포함하는, UDF 함수의 전체 이름만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30111-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="30111-107">.NET for Apache Spark 애플리케이션에서 Java UDF를 등록하고 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="30111-108">Java UDF 정의 및 컴파일</span><span class="sxs-lookup"><span data-stu-id="30111-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="30111-109">Maven 또는 SBT 프로젝트를 만들고 프로젝트 구성 파일에 다음 종속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="30111-110">아래의 간단한 예제와 같이 UDF 시그니처에 따라 [관련 인터페이스](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java)를 구현하고 관련 패키지를 가져와 Java UDF를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. <span data-ttu-id="30111-111">프로젝트를 컴파일하고 패키지하여 `UdfApp-0.0.1.jar`이라는 실행 파일 jar를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30111-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="30111-112">.NET for Apache Spark에서 Java UDF 등록 및 호출</span><span class="sxs-lookup"><span data-stu-id="30111-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="30111-113">[`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API를 사용하여 Spark SQL에 Java UDF를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="30111-114">[`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) 함수를 사용하여 UDF를 호출할 `DataFrame`을 SQL 테이블로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="30111-115">`SparkSession.Sql`을 사용하여 Spark SQL을 통해 테이블 뷰에서 UDF를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="30111-116">위 단계를 설명하기 위한 기본 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30111-116">A basic example to illustrate the above steps:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. <span data-ttu-id="30111-117">`spark-submit`를 사용하고 이전에 컴파일된 Java UDF jar를 `--jars` 옵션으로 전달하여 애플리케이션을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="30111-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="30111-118">결과로 생성된 `dfUdf` DataFrame에서 `JavaUdf`를 통해 정의된 입력 열의 각 행에는 숫자 5가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="30111-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="30111-119">Apache Spark의 Scala 또는 Python에서 .NET UDF 호출</span><span class="sxs-lookup"><span data-stu-id="30111-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="30111-120">[sparkdotnetudf 오픈 소스 도구](https://github.com/imback82/sparkdotnetudf)를 사용하여 Scala 또는 Python으로 작성된 Apache Spark 애플리케이션에서 C# UDF를 등록하고 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30111-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
