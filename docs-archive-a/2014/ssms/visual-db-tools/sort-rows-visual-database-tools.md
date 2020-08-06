---
title: 행 정렬(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4939c08a4be8c6a7aa3a52d55928abe077f25d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737366"
---
# <a name="sort-rows-visual-database-tools"></a><span data-ttu-id="dc3f9-102">행 정렬(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dc3f9-102">Sort Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="dc3f9-103">쿼리 결과에서 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-103">You can order the rows in a query result.</span></span> <span data-ttu-id="dc3f9-104">즉, 해당 값이 결과 집합의 행 순서를 결정하는 특정 열 또는 열 집합의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-104">That is, you can name a particular column or set of columns whose values determine the order of rows in the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc3f9-105">정렬 순서는 부분적으로 열의 배치 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-105">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="dc3f9-106">[데이터 정렬 대화 상자](visual-database-tools.md)에서 데이터 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-106">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="dc3f9-107">쿼리 결과를 정렬하는 데는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-107">There are several ways in which you can sort query results:</span></span>  
  
-   <span data-ttu-id="dc3f9-108">**행을 오름차순 또는 내림차순으로 정렬할 수 있습니다.** 기본적으로 SQL에서는 열 정렬을 사용하여 오름차순으로 행을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-108">**You can arrange rows in ascending or descending order** By default, SQL uses order-by columns to arrange rows in ascending order.</span></span> <span data-ttu-id="dc3f9-109">예를 들어, 오름차순 가격으로 책 제목을 정렬하려면 price 열을 기준으로 행을 정렬하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-109">For example, to arrange the book titles by ascending price, simply sort the rows by the price column.</span></span> <span data-ttu-id="dc3f9-110">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-110">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     <span data-ttu-id="dc3f9-111">반면에 가격이 비싼 책의 제목부터 먼저 표시되도록 정렬하려면 내림차순으로 정렬하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-111">On the other hand, if you want to arrange the titles with the more expensive books first, you can explicitly specify a highest-first ordering.</span></span> <span data-ttu-id="dc3f9-112">즉, 결과 행을 price 열 값의 내림차순으로 정렬하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-112">That is, you indicate that the result rows should be arranged by descending values of the price column.</span></span> <span data-ttu-id="dc3f9-113">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-113">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="dc3f9-114">**여러 열을 기준으로 정렬할 수 있습니다.** 예를 들어, 각 저자별로 행이 하나씩 있는 결과 집합을 만들어 주별로 정렬한 다음 다시 도시별로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-114">**You can sort by multiple columns** For example, you can create a result set with one row for each author, ordering first by state and then by city.</span></span> <span data-ttu-id="dc3f9-115">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-115">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   <span data-ttu-id="dc3f9-116">**결과 집합에 표시되지 않는 열을 기준으로 정렬할 수 있습니다.** 예를 들어, 가격이 결과 집합에 표시되지 않더라도 가장 비싼 책 제목을 먼저 표시하는 결과 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-116">**You can sort by columns not appearing in the result set** For example, you can create a result set with the most expensive titles first, even though the prices do not appear.</span></span> <span data-ttu-id="dc3f9-117">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-117">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="dc3f9-118">**파생 열을 기준으로 정렬할 수 있습니다.** 예를 들어 각 행에 책 제목이 있는 결과 집합을 만들어 한 권당 가장 높은 인세를 지불하는 책이 먼저 표시되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-118">**You can sort by derived columns** For example, you can create a result set in which each row contains a book title - with the books that pay the highest royalty per copy appearing first.</span></span> <span data-ttu-id="dc3f9-119">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-119">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     <span data-ttu-id="dc3f9-120">한 권 판매될 때마다 받는 인세를 계산하는 공식이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-120">(The formula for calculating the royalty that each book earns per copy is emphasized.)</span></span>  
  
     <span data-ttu-id="dc3f9-121">파생 열을 계산하려면 위 예제에서와 같이 SQL 구문을 사용하거나 스칼라 값을 반환하는 사용자 정의 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-121">To calculate a derived column, you can use SQL syntax, as in the preceding example, or you can use a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="dc3f9-122">사용자 정의 함수에 대한 자세한 내용은 SQL Server 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-122">For more information about user-defined functions, see the SQL Server documentation.</span></span>  
  
-   <span data-ttu-id="dc3f9-123">**그룹화된 행을 정렬할 수 있습니다.** 예를 들어 각 행에 도시와 해당 도시에 있는 저자 수를 나타내는 결과 집합을 만들어 저자를 많이 포함하는 도시가 먼저 표시되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-123">**You can sort grouped rows** For example; you can create a result set in which each row describes a city, plus the number of authors in that city - with the cities containing many authors appearing first.</span></span> <span data-ttu-id="dc3f9-124">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-124">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     <span data-ttu-id="dc3f9-125">이 쿼리에서는 `state` 를 두 번째 정렬 열로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-125">Notice that the query uses `state` as a secondary sort column.</span></span> <span data-ttu-id="dc3f9-126">따라서 두 개의 주에 같은 수의 저자가 있을 경우 해당 주들은 사전순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-126">Thus, if two states have the same number of authors, those states will appear in alphabetical order.</span></span>  
  
-   <span data-ttu-id="dc3f9-127">**국가별 데이터를 사용하여 정렬할 수 있습니다.** 해당 열에 대한 기본 규칙과 다른 데이터 정렬 규칙을 사용하여 열을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-127">**You can sort using international data** That is; you can sort a column using collating conventions that differ from the default conventions for that column.</span></span> <span data-ttu-id="dc3f9-128">예를 들어 Jaime Pati?의 모든 책 제목을 검색 하는 쿼리를 작성할 수 있습니다. i/o.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-128">For example, you can write a query that retrieves all the book titles by Jaime Pati??o.</span></span> <span data-ttu-id="dc3f9-129">제목을 사전순으로 표시하려면 title 열에 스페인어 데이터 정렬 순서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-129">To display the titles in alphabetical order, you use a Spanish collating sequence for the title column.</span></span> <span data-ttu-id="dc3f9-130">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc3f9-130">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Pati??o'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc3f9-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc3f9-131">See Also</span></span>  
 <span data-ttu-id="dc3f9-132">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="dc3f9-132">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="dc3f9-133">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dc3f9-133">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
