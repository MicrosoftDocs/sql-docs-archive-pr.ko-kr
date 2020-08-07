---
title: 쿼리 축의 내용 지정 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734491"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a><span data-ttu-id="e6fe7-102">쿼리 축의 내용 지정(MDX)</span><span class="sxs-lookup"><span data-stu-id="e6fe7-102">Specifying the Contents of a Query Axis (MDX)</span></span>
  <span data-ttu-id="e6fe7-103">쿼리 축은 MDX SELECT 문에 의해 반환되는 열 집합의 가장자리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-103">Query axes specify the edges of a cellset returned by a Multidimensional Expressions (MDX) SELECT statement.</span></span> <span data-ttu-id="e6fe7-104">열 집합의 가장자리를 지정하면 클라이언트에 표시되는 반환 데이터를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-104">Specifying the edges of a cellset lets you restrict the returned data that is visible to the client.</span></span>  
  
 <span data-ttu-id="e6fe7-105">쿼리 축을 지정하려면 `<SELECT query axis clause>` 를 사용하여 집합을 특정 쿼리 축에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-105">To specify query axes, you use the `<SELECT query axis clause>` to assign a set to a particular query axis.</span></span> <span data-ttu-id="e6fe7-106">각 `<SELECT query axis clause>` 값은 하나의 쿼리 축을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-106">Each `<SELECT query axis clause>` value defines one query axis.</span></span> <span data-ttu-id="e6fe7-107">데이터 세트의 축 수는 SELECT 문의 `<SELECT query axis clause>` 값의 개수와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-107">The number of axes in the dataset is equal to the number of `<SELECT query axis clause>` values in the SELECT statement.</span></span>  
  
## <a name="query-axis-syntax"></a><span data-ttu-id="e6fe7-108">쿼리 축 구문</span><span class="sxs-lookup"><span data-stu-id="e6fe7-108">Query Axis Syntax</span></span>  
 <span data-ttu-id="e6fe7-109">다음 구문은 `<SELECT query axis clause>`의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-109">The following syntax shows the syntax for the `<SELECT query axis clause>`:</span></span>  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 <span data-ttu-id="e6fe7-110">각 쿼리 축에는 번호가 있습니다. 즉, x-축에는 0, y-축에는 1, z-축에는 2 등과 같은 번호가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-110">Each query axis has a number: zero (0) for the x-axis, 1 for the y-axis, 2 for the z-axis, and so on.</span></span> <span data-ttu-id="e6fe7-111">`<SELECT query axis clause>`구문에서 `Integer_Expression` 값은 축 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-111">In the syntax for the `<SELECT query axis clause>`, the `Integer_Expression` value specifies the axis number.</span></span> <span data-ttu-id="e6fe7-112">MDX 쿼리는 지정된 축을 128개까지 지원할 수 있지만, 6개 이상의 축을 사용하는 MDX 쿼리는 극소수입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-112">An MDX query can support up to 128 specified axes, but very few MDX queries will use more than 5 axes.</span></span> <span data-ttu-id="e6fe7-113">처음 5개의 축에 대해서는 COLUMNS, ROWS, PAGES, SECTIONS 및 CHAPTERS와 같은 별칭을 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-113">For the first 5 axes, the aliases COLUMNS, ROWS, PAGES, SECTIONS, and CHAPTERS can instead be used.</span></span>  
  
 <span data-ttu-id="e6fe7-114">MDX 쿼리는 쿼리 축을 건너뛸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-114">An MDX query cannot skip query axes.</span></span> <span data-ttu-id="e6fe7-115">즉, 한 개 이상의 쿼리 축이 포함된 쿼리는 하위 번호 또는 중간 축을 제외해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-115">That is, a query that includes one or more query axes must not exclude lower-numbered or intermediate axes.</span></span> <span data-ttu-id="e6fe7-116">예를 들어 COLUMNS 축 없이는 쿼리에 ROWS 축을 사용할 수 없습니다. 또는 ROWS 축 없이는 COLUMNS와 PAGES 축을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-116">For example, a query cannot have a ROWS axis without a COLUMNS axis, or have COLUMNS and PAGES axes without a ROWS axis.</span></span>  
  
 <span data-ttu-id="e6fe7-117">그러나 축 없이 SELECT 절(즉, 빈 SELECT 절)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-117">However, you can specify a SELECT clause without any axes (that is, an empty SELECT clause).</span></span> <span data-ttu-id="e6fe7-118">이 경우 모든 차원이 slicer 차원이며, MDX 쿼리에서 한 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-118">In this case, all dimensions are slicer dimensions, and the MDX query selects one cell.</span></span>  
  
 <span data-ttu-id="e6fe7-119">앞에서 표시한 쿼리 축 구문에서 각 `Set_Expression` 값은 쿼리 축의 내용을 정의하는 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-119">In the query axis syntax previously shown, each `Set_Expression` value specifies the set that defines the contents of the query axis.</span></span> <span data-ttu-id="e6fe7-120">집합에 대한 자세한 내용은 [멤버, 튜플 및 집합 작업&#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-120">For more information about sets, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e6fe7-121">예제</span><span class="sxs-lookup"><span data-stu-id="e6fe7-121">Examples</span></span>  
 <span data-ttu-id="e6fe7-122">아래의 간단한 SELECT 문은 Columns 축에 대한 측정값 Internet Sales Amount를 반환하고 MDX MEMBERS 함수를 사용하여 Rows 축의 Date 차원에 있는 Calendar 계층 구조의 모든 멤버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-122">The following simple SELECT statement returns the measure Internet Sales Amount on the Columns axis, and uses the MDX MEMBERS function to return all the members from the Calendar hierarchy on the Date dimension on the Rows axis:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e6fe7-123">다음 두 쿼리는 정확히 동일한 결과를 반환하지만 별칭 대신 축 번호의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-123">The two following queries return exactly the same results but demonstrate the use of axis numbers rather than aliases:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e6fe7-124">집합 정의 전에 사용되는 NON EMPTY 키워드는 축에서 모든 빈 튜플을 제거하는 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-124">The NON EMPTY keyword, used before the set definition, is an easy way to remove all empty tuples from an axis.</span></span> <span data-ttu-id="e6fe7-125">예를 들어 지금까지 살펴본 예제에서는 8 월 2004 일 이후의 큐브에 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-125">For example, in the examples we've seen so far there is no data in the cube from August 2004 onwards.</span></span> <span data-ttu-id="e6fe7-126">열에 데이터가 없는 셀 집합에서 모든 행을 제거하려면 다음과 같이 Rows 축 정의의 집합 앞에 NON EMPTY를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-126">To remove all rows from the cellset that have no data in any column, simply add NON EMPTY before the set on the Rows axis definition as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="e6fe7-127">NON EMPTY는 쿼리의 모든 축에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-127">NON EMPTY can be used on all axes in a query.</span></span> <span data-ttu-id="e6fe7-128">다음 두 쿼리의 결과를 비교해 보십시오. 첫 번째 쿼리는 NON EMPTY를 사용하지 않고 두 번째 쿼리는 두 축에서 모두 NON EMPTY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-128">Compare the results of the following two queries, the first of which does not use NON EMPTY and the second of which does on both axes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 <span data-ttu-id="e6fe7-129">HAVING 절을 사용하여 특정 조건에 따라 축의 내용을 필터링할 수 있습니다. 이 방법은 동일한 결과를 얻을 수 있는 FILTER 함수 등의 다른 방법보다 융통성이 적지만 더 간단하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-129">The HAVING clause can be used to filter the contents of an axis based on a specific criteria; it is less flexible than other methods that can achieve the same results, such as the FILTER function, but it is simpler to use.</span></span> <span data-ttu-id="e6fe7-130">다음 예제에서는 Internet Sales Amount가 $15,000보다 큰 날짜만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe7-130">Here is an example that returns only those dates where Internet Sales Amount is greater than $15,000:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6fe7-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6fe7-131">See Also</span></span>  
 [<span data-ttu-id="e6fe7-132">Slicer 축의 내용 지정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="e6fe7-132">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  