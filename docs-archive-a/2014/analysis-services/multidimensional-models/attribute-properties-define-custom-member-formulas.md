---
title: 사용자 지정 멤버 수식 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51649bea0c4134971b342b779c778b857343e62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741443"
---
# <a name="define-custom-member-formulas"></a><span data-ttu-id="3d67a-102">사용자 지정 멤버 수식 정의</span><span class="sxs-lookup"><span data-stu-id="3d67a-102">Define Custom Member Formulas</span></span>
  <span data-ttu-id="3d67a-103">사용자 지정 멤버 수식이라고 하는 MDX(Multidimensional Expression) 식을 정의하여 지정된 특성의 멤버에 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-103">You can define a Multidimensional Expressions (MDX) expression, called a custom member formula, to supply the values for the members of a specified attribute.</span></span> <span data-ttu-id="3d67a-104">데이터 원본 뷰의 테이블 열은 특성의 각 멤버에 값을 지정하는 데 사용되는 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-104">A column in a table from a data source view provides, for each member in an attribute, the expression used to supply the value for that member.</span></span>  
  
 <span data-ttu-id="3d67a-105">사용자 지정 멤버 수식은 멤버에 연결되는 셀 값을 결정하고 측정값의 집계 함수를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-105">Custom member formulas determine the cell values that are associated with members and override the aggregate functions of measures.</span></span> <span data-ttu-id="3d67a-106">사용자 지정 멤버 수식은 MDX로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-106">Custom member formulas are written in MDX.</span></span> <span data-ttu-id="3d67a-107">각각의 사용자 지정 멤버 수식은 단일 멤버에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-107">Each custom member formula applies to a single member.</span></span> <span data-ttu-id="3d67a-108">사용자 지정 멤버 수식은 차원 테이블이나 해당 차원 테이블과 외래 키 관계에 있는 다른 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-108">Custom member formulas are stored in the dimension table or in another table that has a foreign key relationship with the dimension table.</span></span>  
  
 <span data-ttu-id="3d67a-109">특성에서 `CustomRollupColumn` 속성은 특성의 멤버에 대한 사용자 지정 멤버 수식을 포함하는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-109">The `CustomRollupColumn` property on an attribute specifies the column that contains custom member formulas for members of the attribute.</span></span> <span data-ttu-id="3d67a-110">열의 행이 비어 있으면 멤버의 셀 값이 정상적으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-110">If a row in the column is empty, the cell value for the member is returned normally.</span></span> <span data-ttu-id="3d67a-111">열의 수식이 유효하지 않으면 멤버를 사용하는 셀 값이 검색될 때마다 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-111">If the formula in the column is not valid, a run-time error occurs whenever a cell value that uses the member is retrieved.</span></span>  
  
 <span data-ttu-id="3d67a-112">특성을 포함하는 차원 테이블이나 직접 관련된 테이블에 사용자 지정 멤버 수식을 저장할 문자열 열이 있어야만 특성에 대한 사용자 지정 멤버 수식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-112">Before you can specify custom member formulas for an attribute, make sure that the dimension table that contains the attribute, or a directly related table, has a string column to store the custom member formulas.</span></span> <span data-ttu-id="3d67a-113">이 경우 `CustomRollupColumn` 특성에 대 한 속성을 수동으로 설정 하거나 비즈니스 인텔리전스 마법사의 사용자 지정 멤버 수식 설정 향상 기능을 사용 하 여 특성에 대 한 사용자 지정 멤버 수식을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-113">If this is the case, you can either set the `CustomRollupColumn` property on an attribute manually or use the Set Custom Member Formula enhancement of the Business Intelligence Wizard to enable a custom member formula on an attribute.</span></span> <span data-ttu-id="3d67a-114">이 향상 기능을 사용하는 방법에 대한 자세한 내용은 [차원에 특성의 사용자 지정 멤버 수식 설정](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d67a-114">For more information about how to use this enhancement, see [Set Custom Member Formulas for Attributes in a Dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).</span></span>  
  
## <a name="evaluating-custom-member-formulas"></a><span data-ttu-id="3d67a-115">사용자 지정 멤버 수식 평가</span><span class="sxs-lookup"><span data-stu-id="3d67a-115">Evaluating Custom Member Formulas</span></span>  
 <span data-ttu-id="3d67a-116">사용자 지정 멤버 수식은 계산 멤버와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-116">Custom member formulas differ from calculated members.</span></span> <span data-ttu-id="3d67a-117">사용자 지정 멤버 수식은 차원 테이블에 있는 멤버에 적용되며 멤버의 값만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-117">Custom member formulas apply to members that exist in dimension tables, and only provide the value of the member.</span></span> <span data-ttu-id="3d67a-118">이와 달리 계산 멤버는 차원 테이블에 저장되지 않으며 계산 멤버 식은 차원이나 계층에 포함된 추가 멤버에 대해 데이터와 메타데이터를 모두 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-118">In contrast, calculated members are not stored in dimension tables, and calculated member expressions define both data and metadata for additional members included in a dimension or hierarchy.</span></span>  
  
 <span data-ttu-id="3d67a-119">사용자 지정 멤버 수식은 측정값에 연결된 집계 함수를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-119">Custom member formulas override the aggregate functions associated with measures.</span></span> <span data-ttu-id="3d67a-120">예를 들어 사용자 지정 멤버 수식을 지정하기 전에 `Sum` 집계 함수를 사용하는 측정값에는 Time 차원의 아래 멤버들에 대한 다음과 같은 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-120">For example, before a custom member formula is specified, a measure using the `Sum` aggregate function has the following values for the following members of the Time dimension:</span></span>  
  
-   <span data-ttu-id="3d67a-121">2003: 2100</span><span class="sxs-lookup"><span data-stu-id="3d67a-121">2003: 2100</span></span>  
  
    -   <span data-ttu-id="3d67a-122">Quarter 1: 700</span><span class="sxs-lookup"><span data-stu-id="3d67a-122">Quarter 1: 700</span></span>  
  
    -   <span data-ttu-id="3d67a-123">Quarter 2: 500</span><span class="sxs-lookup"><span data-stu-id="3d67a-123">Quarter 2: 500</span></span>  
  
    -   <span data-ttu-id="3d67a-124">Quarter 3: 100</span><span class="sxs-lookup"><span data-stu-id="3d67a-124">Quarter 3: 100</span></span>  
  
    -   <span data-ttu-id="3d67a-125">Quarter 4: 800</span><span class="sxs-lookup"><span data-stu-id="3d67a-125">Quarter 4: 800</span></span>  
  
-   <span data-ttu-id="3d67a-126">2004: 1500</span><span class="sxs-lookup"><span data-stu-id="3d67a-126">2004: 1500</span></span>  
  
    -   <span data-ttu-id="3d67a-127">Quarter 1: 600</span><span class="sxs-lookup"><span data-stu-id="3d67a-127">Quarter 1: 600</span></span>  
  
    -   <span data-ttu-id="3d67a-128">Quarter 2: 200</span><span class="sxs-lookup"><span data-stu-id="3d67a-128">Quarter 2: 200</span></span>  
  
    -   <span data-ttu-id="3d67a-129">Quarter 3: 300</span><span class="sxs-lookup"><span data-stu-id="3d67a-129">Quarter 3: 300</span></span>  
  
    -   <span data-ttu-id="3d67a-130">Quarter 4: 400</span><span class="sxs-lookup"><span data-stu-id="3d67a-130">Quarter 4: 400</span></span>  
  
 <span data-ttu-id="3d67a-131">사용자 지정 멤버 수식을 사용할 경우 사용자 지정 롤업 수식에서 멤버의 값을 대신 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-131">With a custom member formula, the value of the member is instead supplied by the custom rollup formula.</span></span> <span data-ttu-id="3d67a-132">예를 들어 다음과 같은 사용자 지정 멤버 수식을 사용하여 Time 차원에 있는 2004 멤버의 Quarter 4 자식 멤버에 대한 값을 450으로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-132">For example, the following custom member formula can be used to supply the value for the Quarter 4 child member of the 2004 member in the Time dimension as 450.</span></span>  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 <span data-ttu-id="3d67a-133">사용자 지정 멤버 수식은 차원 테이블의 열에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-133">Custom member formulas are stored in a column of the dimension table.</span></span> <span data-ttu-id="3d67a-134">특성에 `CustomRollupColumn` 속성을 설정하여 사용자 지정 롤업 수식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-134">You enable custom rollup formulas by setting the `CustomRollupColumn` property on an attribute.</span></span>  
  
 <span data-ttu-id="3d67a-135">특성의 모든 멤버에 단일 MDX 식을 적용하려면 MDX 식을 리터럴 문자열로 반환하는 차원 테이블에 명명된 계산을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-135">To apply a single MDX expression to all members of an attribute, create a named calculation on the dimension table that returns an MDX expression as a literal string.</span></span> <span data-ttu-id="3d67a-136">그런 다음 구성할 특성에 `CustomRollupColumn` 속성 설정을 사용하여 명명된 계산을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-136">Then, specify the named calculation with the `CustomRollupColumn` property setting on the attribute that you want to configure.</span></span> <span data-ttu-id="3d67a-137">명명된 계산은 SQL 식으로 정의된 행 값을 반환하는 데이터 원본 뷰 테이블의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-137">A named calculation is a column in a data source view table that returns row values defined by a SQL expression.</span></span> <span data-ttu-id="3d67a-138">명명된 계산을 만드는 방법에 대한 자세한 내용은 [데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d67a-138">For more information about constructing named calculations, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d67a-139">특정 특성을 기반으로 모든 수준의 멤버 대신 특정 수준의 멤버에 MDX 식을 적용하려면 수준에 식을 MDX 스크립트로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-139">To apply an MDX expression to members of a particular level instead of to members of all levels based on a particular attribute, you can define the expression as an MDX script on the level.</span></span> <span data-ttu-id="3d67a-140">자세한 내용은 [MDX 스크립팅 기본 사항&#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d67a-140">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
 <span data-ttu-id="3d67a-141">특성의 멤버에 대해 계산 멤버와 사용자 지정 롤업 수식을 모두 사용하려면 평가 순서를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-141">If you use both calculated members and custom rollup formulas for members of an attribute, you should be aware of the order of evaluation.</span></span> <span data-ttu-id="3d67a-142">계산 멤버가 사용자 지정 롤업 수식보다 먼저 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d67a-142">Calculated members are resolved before custom rollup formulas are resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d67a-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d67a-143">See Also</span></span>  
 <span data-ttu-id="3d67a-144">[특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="3d67a-144">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="3d67a-145">차원에 특성의 사용자 지정 멤버 수식 설정</span><span class="sxs-lookup"><span data-stu-id="3d67a-145">Set Custom Member Formulas for Attributes in a Dimension</span></span>](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  