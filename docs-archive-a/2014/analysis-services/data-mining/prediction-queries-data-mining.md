---
title: 예측 쿼리 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e6686c-1360-480e-8c0d-8a56204fbed9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 543055aaed5d8991ed2c913a6ae46575c774e216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734620"
---
# <a name="prediction-queries-data-mining"></a><span data-ttu-id="e4cf4-102">예측 쿼리(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="e4cf4-102">Prediction Queries (Data Mining)</span></span>
  <span data-ttu-id="e4cf4-103">일반적인 데이터 마이닝 프로젝트의 목표는 마이닝 모델을 사용하여 예측을 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-103">The goal of a typical data mining project is to use the mining model to make predictions.</span></span> <span data-ttu-id="e4cf4-104">예를 들어 서버의 특정 클러스터에 대해 예상 작동 중단 시간의 양을 예측하거나, 고객의 세그먼트가 광고 캠페인에 응답할 가능성이 있는지 여부를 표시하는 점수를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-104">For example, you might want to predict the amount of expected downtime for a certain cluster of servers, or generate a score that indicates whether segments of customers are likely to respond to an advertising campaign.</span></span> <span data-ttu-id="e4cf4-105">이러한 작업을 모두 수행하기 위해 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-105">To do all these things, you would create a prediction query.</span></span>  
  
 <span data-ttu-id="e4cf4-106">기능적으로 쿼리에 대한 입력의 유형에 따라 SQL Server에서 다른 유형의 예측 쿼리가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-106">Functionally, there are different types of prediction queries supported in SQL Server, depending on the type of inputs to the query:</span></span>  
  
|<span data-ttu-id="e4cf4-107">쿼리 유형</span><span class="sxs-lookup"><span data-stu-id="e4cf4-107">Query Type</span></span>|<span data-ttu-id="e4cf4-108">쿼리 옵션</span><span class="sxs-lookup"><span data-stu-id="e4cf4-108">Query Options</span></span>|  
|----------------|-------------------|  
|<span data-ttu-id="e4cf4-109">단일 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="e4cf4-109">Singleton prediction queries</span></span>|<span data-ttu-id="e4cf4-110">새로운 단일 사례 또는 복수 사례에 대한 결과를 예측하려는 경우 단일 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-110">Use a singleton query when you want to predict outcomes for a single new case, or multiple new cases.</span></span> <span data-ttu-id="e4cf4-111">쿼리에서 입력 값을 직접 제공하며 쿼리는 단일 세션으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-111">You provide the input values directly in the query, and the query is executed as a single session.</span></span>|  
|<span data-ttu-id="e4cf4-112">일괄 처리 예측</span><span class="sxs-lookup"><span data-stu-id="e4cf4-112">Batch predictions</span></span>|<span data-ttu-id="e4cf4-113">예측의 기반으로 사용하기 위해 모델로 피드하려는 외부 데이터가 있는 경우 일괄 처리 예측을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-113">Use batch predictions when you have external data that you want to feed into the model, to use as the basis for predictions.</span></span> <span data-ttu-id="e4cf4-114">전체 데이터 집합에 대한 예측을 만들려면 외부 원본의 데이터를 모델의 열에 매핑한 다음 출력할 예측 데이터의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-114">To make predictions for an entire set of data, you map the data in the external source to the columns in the model, and then specify the type of predictive data you want to output.</span></span><br /><br /> <span data-ttu-id="e4cf4-115">전체 데이터 세트에 대한 쿼리가 단일 세션에서 실행되므로 이 옵션은 반복되는 쿼리를 여러 개 보내는 것보다 훨씬 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-115">The query for the entire dataset is executed in a single session, making this option much more efficient than sending multiple repeated queries.</span></span>|  
|<span data-ttu-id="e4cf4-116">시계열 예측</span><span class="sxs-lookup"><span data-stu-id="e4cf4-116">Time Series predictions</span></span>|<span data-ttu-id="e4cf4-117">몇 가지 이후 단계에 대한 값을 예측하려는 경우 시계열 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-117">Use a time series query when you want to predict a value over some number of future steps.</span></span> <span data-ttu-id="e4cf4-118">SQL Server 데이터 마이닝은 시계열 쿼리에서 다음 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-118">SQL Server Data Mining also provides the following functionality in time series queries:</span></span><br /><br /> <span data-ttu-id="e4cf4-119">쿼리의 일부로 새 데이터를 추가하여 기존 모델을 확장하고 복합 계열을 기반으로 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-119">You can extend an existing model by adding new data as part of the query, and make predictions based on the composite series.</span></span><br /><br /> <span data-ttu-id="e4cf4-120">REPLACE_MODEL_CASES 옵션을 사용하여 새 데이터 계열에 기존 모델을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-120">You can apply an existing model to a new data series by using the REPLACE_MODEL_CASES option.</span></span><br /><br /> <span data-ttu-id="e4cf4-121">교차 예측을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-121">You can perform cross-prediction.</span></span>|  
  
 <span data-ttu-id="e4cf4-122">다음 섹션에서는 예측 쿼리의 일반 구문, 예측 쿼리의 다양한 유형 및 예측 쿼리의 결과로 작업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-122">The following sections describe the general syntax of prediction queries, the different types of prediction queries, and how to work with the results of prediction queries.</span></span>  
  
 [<span data-ttu-id="e4cf4-123">기본 예측 쿼리 디자인</span><span class="sxs-lookup"><span data-stu-id="e4cf4-123">Basic Prediction Query Design</span></span>](#bkmk_PredQuery)  
  
-   [<span data-ttu-id="e4cf4-124">예측 함수 추가</span><span class="sxs-lookup"><span data-stu-id="e4cf4-124">Adding Prediction Functions</span></span>](#bkmk_PredFunc)  
  
-   [<span data-ttu-id="e4cf4-125">단일 쿼리</span><span class="sxs-lookup"><span data-stu-id="e4cf4-125">Singleton Queries</span></span>](#bkmk_SingletonQuery)  
  
-   [<span data-ttu-id="e4cf4-126">일괄 처리 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="e4cf4-126">Batch Prediction Queries</span></span>](#bkmk_BatchQuery)  
  
 [<span data-ttu-id="e4cf4-127">쿼리 결과 작업</span><span class="sxs-lookup"><span data-stu-id="e4cf4-127">Working with the Results of Queries</span></span>](#bkmk_WorkResults)  
  
##  <a name="basic-prediction-query-design"></a><a name="bkmk_PredQuery"></a> <span data-ttu-id="e4cf4-128">기본 예측 쿼리 디자인</span><span class="sxs-lookup"><span data-stu-id="e4cf4-128">Basic Prediction Query Design</span></span>  
 <span data-ttu-id="e4cf4-129">예측을 만들 때 사용자는 일반적으로 몇 가지 새로운 데이터를 제공한 다음 이 새로운 데이터를 기반으로 모델이 예측을 생성하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-129">When you create a prediction, you typically provide some piece of new data and ask the model to generate a prediction based on the new data.</span></span>  
  
-   <span data-ttu-id="e4cf4-130">일괄 처리 예측 쿼리에서는 *예측 조인*을 사용하여 모델을 외부 데이터 원본에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-130">In a batch prediction query, you map the model to an external source of data by using a *prediction join*.</span></span>  
  
-   <span data-ttu-id="e4cf4-131">단일 예측 쿼리에서는 입력으로 사용할 값을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-131">In a singleton prediction query, you type one or more values to use as inputs.</span></span> <span data-ttu-id="e4cf4-132">단일 예측 쿼리를 사용하여 여러 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-132">You can create multiple predictions using a singleton prediction query.</span></span> <span data-ttu-id="e4cf4-133">그러나 많은 예측을 만들어야 하는 경우 일괄 처리 쿼리를 사용하면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-133">However, if you need to create many predictions, performance is better when you use a batch query.</span></span>  
  
 <span data-ttu-id="e4cf4-134">단일 및 일괄 처리 예측 쿼리는 모두 PREDICTION JOIN 구문을 사용하여 새 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-134">Both singleton and batch prediction queries use the PREDICTION JOIN syntax to define the new data.</span></span> <span data-ttu-id="e4cf4-135">차이점은 예측 조인의 입력 쪽을 지정하는 방법에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-135">The difference is in how the input side of the prediction join is specified.</span></span>  
  
-   <span data-ttu-id="e4cf4-136">일괄 처리 예측 쿼리에서 데이터는 OPENQUERY 구문을 사용하여 지정한 외부 데이터 원본에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-136">In a batch prediction query, the data comes from an external data source that is specified by using the OPENQUERY syntax.</span></span>  
  
-   <span data-ttu-id="e4cf4-137">단일 예측 쿼리에서 데이터는 쿼리에 포함되어 인라인으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-137">In a singleton prediction query, the data is supplied inline as part of the query.</span></span>  
  
 <span data-ttu-id="e4cf4-138">시계열 모델의 경우 입력 데이터가 필요하지 않은 경우도 있습니다. 모델에 이미 있는 데이터만 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-138">For time series models, input data is not always required; it is possible to make predictions using just the data already in the model.</span></span> <span data-ttu-id="e4cf4-139">하지만 새 입력 데이터를 지정하는 경우에는 새 데이터를 사용하여 모델을 업데이트하고 확장할지 아니면 모델에서 사용된 데이터의 원래 계열을 바꿀지를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-139">However, if you do specify new input data, you must decide whether you will use the new data to update and extend the model, or to replace the original series of data that was used in the model.</span></span>  <span data-ttu-id="e4cf4-140">이러한 옵션에 대한 자세한 내용은 [Time Series Model Query Examples](time-series-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-140">For more information about these options, see [Time Series Model Query Examples](time-series-model-query-examples.md).</span></span>  
  
###  <a name="adding-prediction-functions"></a><a name="bkmk_PredFunc"></a><span data-ttu-id="e4cf4-141">예측 함수 추가</span><span class="sxs-lookup"><span data-stu-id="e4cf4-141">Adding Prediction Functions</span></span>  
 <span data-ttu-id="e4cf4-142">값을 예측하는 것 외에도 예측 쿼리를 사용자 지정하여 예측과 관련된 여러 종류의 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-142">In addition to predicting a value, you can customize a prediction query to return various kinds of information that are related to the prediction.</span></span> <span data-ttu-id="e4cf4-143">예를 들어 예측에 따라 고객에게 권장할 제품 목록을 만드는 경우 예측을 평가하여 최상위 권장 사항만 사용자에게 제공할 수 있도록 각 예측에 대한 확률을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-143">For example, if the prediction creates a list of products to recommend to a customer, you might also want to return the probability for each prediction, so that you can rank them and present only the top recommendations to the user.</span></span>  
  
 <span data-ttu-id="e4cf4-144">이렇게 하려면 쿼리에 *예측 함수* 를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-144">To do this, you add *prediction functions* to the query.</span></span> <span data-ttu-id="e4cf4-145">지원되는 함수는 모델 또는 쿼리 유형마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-145">Each model or query type supports specific functions.</span></span> <span data-ttu-id="e4cf4-146">예를 들어 클러스터링 모델은 모델에서 만들어진 클러스터에 대한 추가 세부 정보를 제공하는 특수한 예측 함수를 지원하지만 시계열 모델에는 시간 경과에 따른 차이를 계산하는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-146">For example, clustering models support special prediction functions that provide extra detail about the clusters created by the model, whereas time series models have functions that calculate differences over time.</span></span> <span data-ttu-id="e4cf4-147">또한 모든 모델 유형에서 작동하는 일반 예측 함수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-147">There are also general prediction functions that work with almost all model types.</span></span> <span data-ttu-id="e4cf4-148">다양한 유형의 쿼리에서 지원되는 예측 함수 목록은 DMX 참조 항목 [일반 예측 함수&#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-148">For a list of the prediction functions supported in different types of queries, see this topic the DMX reference:  [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span>  
  
###  <a name="creating-singleton-prediction-queries"></a><a name="bkmk_SingletonQuery"></a><span data-ttu-id="e4cf4-149">단일 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="e4cf4-149">Creating Singleton Prediction Queries</span></span>  
 <span data-ttu-id="e4cf4-150">단일 예측 쿼리는 빠른 예측을 실시간으로 만들려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-150">A singleton prediction query is useful when you want to create quick predictions in real time.</span></span> <span data-ttu-id="e4cf4-151">일반적인 시나리오는 웹 사이트에서 폼을 사용하는 등의 방법으로 고객으로부터 정보를 얻은 다음 해당 데이터를 단일 예측 쿼리에 입력으로 전송하려는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-151">A common scenario might be that you have obtained information from a customer, perhaps by using a form on a Web site, and you want to submit that data as the input to a singleton prediction query.</span></span> <span data-ttu-id="e4cf4-152">예를 들어 고객이 목록에서 제품을 선택하는 경우 추천할 최고의 제품을 예측하는 쿼리에 대한 입력으로 해당 선택을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-152">For example, when a customer chooses a product from a list, you could use that selection as the input to a query that predicts the best products to recommend.</span></span>  
  
 <span data-ttu-id="e4cf4-153">단일 예측 쿼리에는 입력을 포함하는 별도의 테이블이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-153">Singleton prediction queries do not require a separate table that contains input.</span></span> <span data-ttu-id="e4cf4-154">대신 하나 또는 여러 행의 값을 모델에 입력으로 제공하면 예측이 실시간으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-154">Instead, you provide one or multiple rows of values as input to the model, and the prediction or predictions are returned in real time.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="e4cf4-155">이름에도 불구 하 고 단일 예측 쿼리는 단일 예측만 수행 하는 것이 아니라 각 입력 집합에 대해 여러 예측을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-155">Despite the name, singleton prediction queries do not just make single predictions-you can generate multiple predictions for each set of inputs.</span></span> <span data-ttu-id="e4cf4-156">각 입력 사례에 대해 SELECT 문을 만들고 UNION 연산자로 입력 사례를 결합하여 여러 입력 사례를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-156">You provide multiple input cases by creating a SELECT statement for each input case and combining them with the UNION operator.</span></span>  
  
 <span data-ttu-id="e4cf4-157">단일 예측 쿼리를 만들 때 PREDICTION JOIN의 형태로 모델에 새 데이터를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-157">When you create a singleton prediction query, you must provide the new data to the model in the form of a PREDICTION JOIN.</span></span> <span data-ttu-id="e4cf4-158">즉, 실제 테이블에 매핑하는 것은 아니지만 새 데이터가 마이닝 모델의 기존 열과 일치하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-158">This means that even though you are not mapping to an actual table, you must make sure that the new data matches the existing columns in the mining model.</span></span> <span data-ttu-id="e4cf4-159">새 데이터 열과 새 데이터가 정확하게 일치할 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 자동으로 열을 매핑하는데</span><span class="sxs-lookup"><span data-stu-id="e4cf4-159">If the new data columns and the new data match exactly, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will map the columns for you.</span></span> <span data-ttu-id="e4cf4-160">이를 *NATURAL PREDICTION JOIN*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-160">This is called a *NATURAL PREDICTION JOIN*.</span></span> <span data-ttu-id="e4cf4-161">하지만 열이 일치하지 않거나 모델에 있는 것과 동일한 종류 및 양의 데이터가 새 데이터에 들어 있지 않은 경우 모델의 어떤 열이 새 데이터에 매핑되는지 지정하거나 누락된 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-161">However, if the columns do not match, or if the new data does not contain the same kind and amount of data that is in the model, you must specify which columns in the model map to the new data, or specify the missing values.</span></span>  
  
###  <a name="batch-prediction-queries"></a><a name="bkmk_BatchQuery"></a> <span data-ttu-id="e4cf4-162">일괄 처리 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="e4cf4-162">Batch Prediction Queries</span></span>  
 <span data-ttu-id="e4cf4-163">예측을 만드는 데 사용하려는 외부 데이터가 있는 경우 일괄 처리 예측 쿼리가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-163">A batch prediction query is useful when you have external data that you want to use in making predictions.</span></span> <span data-ttu-id="e4cf4-164">예를 들어 온라인 활동과 구매 기록을 기준으로 고객을 범주화하는 모델을 작성했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-164">For example, you might have built a model that categorizes customers by their online activity and purchasing history.</span></span> <span data-ttu-id="e4cf4-165">이 모델을 새로 얻은 잠재 고객의 목록에 적용하여 매출 예상치를 구하거나 제안된 캠페인의 대상을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-165">You could apply that model to a list of newly acquired leads, to create projections for sales, or to identify targets for proposed campaigns.</span></span>  
  
 <span data-ttu-id="e4cf4-166">예측 조인을 수행하는 경우 모델의 열을 새 데이터 원본의 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-166">When you perform a prediction join, you must map the columns the model to the columns in the new data source.</span></span> <span data-ttu-id="e4cf4-167">따라서 입력을 위해 선택하는 데이터 원본은 모델의 데이터와 어느 정도 비슷한 데이터여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-167">Therefore, the data source that you choose for an input must data that is somewhat similar to the data in the model.</span></span> <span data-ttu-id="e4cf4-168">새 정보는 정확히 일치할 필요가 없으며 불완전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-168">The new information does not have to match exactly, and can be incomplete.</span></span> <span data-ttu-id="e4cf4-169">예를 들어 수입 및 연령에 대한 정보를 사용하여 모델을 학습했지만 예측에 사용할 고객 목록에 수입에 대한 정보는 전혀 없고 연령 정보만 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-169">For example, suppose the model was trained using information about income and age, but the customer list you are using for predictions has age but nothing about income.</span></span> <span data-ttu-id="e4cf4-170">이 경우 새 데이터를 모델에 매핑하고 각 고객에 대한 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-170">In this scenario, you could still map the new data to the model and create a prediction for each customer.</span></span> <span data-ttu-id="e4cf4-171">그러나 수입은 모델을 예측하는 데 중요한 요소이므로 완전한 정보가 없음으로 인해 예측 품질이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-171">However, if income was an important predictor for the model, the lack of complete information would affect the quality of predictions.</span></span>  
  
 <span data-ttu-id="e4cf4-172">최상의 결과를 얻기 위해서는 새 데이터와 모델 간에 일치하는 열을 가능한 많이 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-172">To get the best results, you should join as many of the matching columns as possible between the new data and the model.</span></span> <span data-ttu-id="e4cf4-173">그러나 일치하는 열이 없더라도 쿼리는 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-173">However, the query will succeed even if there are no matches.</span></span> <span data-ttu-id="e4cf4-174">즉, 조인된 열이 없는 경우 쿼리가 한계 예측을 반환하는데 이는 PREDICTION JOIN 절이 없는 `SELECT <predictable-column> FROM <model>` 문과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-174">If no columns are joined, the query will return the marginal prediction, which is equivalent to the statement `SELECT <predictable-column> FROM <model>` without a PREDICTION JOIN clause.</span></span>  
  
 <span data-ttu-id="e4cf4-175">모든 관련 열을 성공적으로 매핑한 후 쿼리를 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 모델의 패턴을 기반으로 새 데이터의 각 행에 대해 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-175">After you have successfully mapped all relevant columns, you run the query, and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] makes predictions for each row in the new data based on patterns in the model.</span></span> <span data-ttu-id="e4cf4-176">외부 데이터가 포함된 데이터 원본 뷰의 새 테이블에 결과를 저장하거나, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하는 경우 데이터를 복사하여 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-176">You can save the results back to a new table in the data source view that contains the external data, or you can copy and paste the data is you are using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="e4cf4-177">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 디자이너를 사용하는 경우 먼저 외부 데이터 원본을 데이터 원본 뷰로 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-177">If you use the designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the external data source must first be defined as a data source view.</span></span>  
  
 <span data-ttu-id="e4cf4-178">DMX를 사용하여 예측 조인을 만드는 경우 OPENQUERY, OPENROWSET 또는 SHAPE 명령을 사용하여 외부 데이터 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-178">If you use DMX to create a prediction join, you can specify the external data source by using the OPENQUERY, OPENROWSET, or SHAPE commands.</span></span> <span data-ttu-id="e4cf4-179">DMX 템플릿의 기본 데이터 액세스 메서드는 OPENQUERY입니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-179">The default data access method in the DMX templates is OPENQUERY.</span></span> <span data-ttu-id="e4cf4-180">이러한 메서드에 대한 자세한 내용은 [&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-180">For information about these methods, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
###  <a name="predictions-in-time-series-mining-models"></a><a name="bkmk_TSQuery"></a> <span data-ttu-id="e4cf4-181">시계열 마이닝 모델의 예측</span><span class="sxs-lookup"><span data-stu-id="e4cf4-181">Predictions in Time Series Mining Models</span></span>  
 <span data-ttu-id="e4cf4-182">시계열 모델은 다른 모델 유형과 다릅니다. 모델을 있는 그대로 사용하여 예측을 만들 수도 있고, 모델에 새 데이터를 제공하여 최신 추세를 기반으로 모델을 업데이트하고 예측을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-182">Time series models are different from other models types; you can either use the model as it is to create predictions, or you can provide new data to the model to update the model and create predictions based on recent trends.</span></span> <span data-ttu-id="e4cf4-183">새 데이터를 추가하는 경우 새 데이터를 사용할 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-183">If you add new data, you can specify the way the new data should be used.</span></span>  
  
-   <span data-ttu-id="e4cf4-184">*모델 사례 확장* 은 시계열 모델의 기존 데이터 계열에 새 데이터를 추가하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-184">*Extending the model cases* means that you add the new data onto the existing series of data in the time series model.</span></span> <span data-ttu-id="e4cf4-185">이후에는 예측이 결합된 새 계열을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-185">Henceforth, predictions are based on the new, combined series.</span></span> <span data-ttu-id="e4cf4-186">이 옵션은 몇 가지 데이터 요소를 기존 모델에 추가하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-186">This option is good when you want to simply add a few data points to an existing model.</span></span>  
  
     <span data-ttu-id="e4cf4-187">예를 들어 전년도 판매 데이터에 대해 학습된 기존 시계열 모델이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-187">For example, suppose that you have an existing time series model that has been trained on the sales data from the previous year.</span></span> <span data-ttu-id="e4cf4-188">수개월 동안 새로운 판매 데이터를 수집한 후 현재 연도에 대한 예측 판매량을 업데이트하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-188">After you have collected several months of new sales data, you decide to update your sales forecasts for the current year.</span></span> <span data-ttu-id="e4cf4-189">이 경우 새 데이터를 추가하여 모델을 업데이트하고 새로운 예측을 만들도록 모델을 확장하는 예측 조인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-189">You can create a prediction join that updates the model by adding new data and extends the model to make new predictions.</span></span>  
  
-   <span data-ttu-id="e4cf4-190">*모델 사례 대체* 는 학습된 모델은 그대로 유지하지만 기본 사례를 새로운 사례 데이터 집합으로 대체하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-190">*Replacing the model cases* means that you keep the trained model, but replace the underlying cases with a new set of case data.</span></span> <span data-ttu-id="e4cf4-191">이 옵션은 추세를 모델에 유지하지만 다른 데이터 집합에 적용하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-191">This option is useful when you want to keep the trend in the model, but apply it to a different set of data.</span></span>  
  
     <span data-ttu-id="e4cf4-192">예를 들어 원래 모델이 판매량이 매우 많은 데이터 집합에 대해 학습되었을 수도 있습니다. 기본 데이터를 새 계열(판매량이 적은 상점 등에서 제공됨)로 대체할 때 추세를 유지하지만 예측은 대체 계열의 값에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-192">For example, your original model might have been trained on a set of data with very high sales volumes; when you replace the underlying data with a new series (perhaps from a store with lower sales volume), you preserve the trend, but the predictions begin from the values in the replacement series.</span></span>  
  
 <span data-ttu-id="e4cf4-193">사용하는 방법에 관계없이 예측은 항상 원래 계열의 끝에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-193">Regardless of which approach you use, the starting point for predictions is always the end of the original series.</span></span>  
  
 <span data-ttu-id="e4cf4-194">시계열 모델에 대한 예측 조인을 만드는 방법은 [시계열 모델 쿼리 예제](time-series-model-query-examples.md) 또는 [PredictTimeSeries&#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-194">For more information about how to create prediction joins on time series models, see [Time Series Model Query Examples](time-series-model-query-examples.md) or [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
##  <a name="working-with-the-results-of-a-prediction-query"></a><a name="bkmk_WorkResults"></a> <span data-ttu-id="e4cf4-195">예측 쿼리 결과 처리</span><span class="sxs-lookup"><span data-stu-id="e4cf4-195">Working with the Results of a Prediction Query</span></span>  
 <span data-ttu-id="e4cf4-196">데이터 마이닝 예측 쿼리의 결과를 저장하기 위한 옵션은 쿼리를 만드는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-196">Your options for saving the results of a data mining prediction query are different depending on how you create the query.</span></span>  
  
-   <span data-ttu-id="e4cf4-197">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 예측 쿼리 작성기를 사용하여 쿼리를 작성할 경우 예측 쿼리의 결과를 기존 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 원본에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-197">When you build a query using Prediction Query Builder in either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can save the results of a prediction query to an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="e4cf4-198">자세한 내용은 [예측 쿼리 결과 보기 및 저장](view-and-save-the-results-of-a-prediction-query.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-198">For more information, see [View and Save the Results of a Prediction Query](view-and-save-the-results-of-a-prediction-query.md).</span></span>  
  
-   <span data-ttu-id="e4cf4-199">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 창에서 DMX를 사용하여 예측 쿼리를 만드는 경우 쿼리 출력 옵션을 사용하여 결과를 파일로 저장하거나 쿼리 결과 창에 텍스트 또는 표로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-199">When you create prediction queries using DMX in the Query pane of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can use the query output options to save the results to a file, or to the Query Results pane as text or in a grid.</span></span> <span data-ttu-id="e4cf4-200">자세한 내용은 [쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-200">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="e4cf4-201">Integration Services 구성 요소를 사용하여 예측 쿼리를 실행하는 경우 해당 태스크에서 사용 가능한 ADO.NET 연결 관리자나 OLEDB 연결 관리자를 사용하여 데이터베이스에 결과를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-201">When you run a prediction query using the Integration Services components, the tasks provides the ability to write the results to a database by using an available ADO.NET connection manager or OLEDB connection manager.</span></span> <span data-ttu-id="e4cf4-202">자세한 내용은 [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-202">For more information, see [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md).</span></span>  
  
 <span data-ttu-id="e4cf4-203">예측 쿼리의 결과는 항상 관련 값의 단일 행을 반환하는 관계형 데이터베이스에 대한 쿼리 결과와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-203">It is important to understand that the results of a prediction query are not like the results of a query on a relational database, which always returns a single row of related values.</span></span> <span data-ttu-id="e4cf4-204">쿼리에 추가된 각 DMX 예측 함수는 고유한 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-204">Each DMX prediction function that you add to a query returns its own rowset.</span></span> <span data-ttu-id="e4cf4-205">그러므로 단일 사례에 대한 예측을 만들면 그 결과는 추가 세부 정보를 포함하는 중첩 테이블의 여러 열이 함께 표시되는 예측 값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-205">Therefore, when you make a prediction on a single case, the result might be a predicted value together with several columns of nested tables containing additional detail.</span></span>  
  
 <span data-ttu-id="e4cf4-206">여러 개의 함수를 한 개의 쿼리에 결합하면 반환 결과는 계층적 행 집합으로 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-206">If you combine multiple functions in one query, the return results are combined as a hierarchical rowset.</span></span> <span data-ttu-id="e4cf4-207">예를 들어 시계열 모델을 사용하여 다음 DMX 문과 같은 쿼리를 통해 판매액 및 판매 수량에 대한 미래 값을 예측한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-207">For example, say you use a time series model to predict future values for sales amount and sales quantity, using a query such as this DMX statement:</span></span>  
  
```  
SELECT  
  PredictTimeSeries([Forecasting].[Amount]) as [PredictedAmount]  
, PredictTimeSeries([Forecasting].[Quantity]) as [PredictedQty]  
FROM  
  [Forecasting]  
  
```  
  
 <span data-ttu-id="e4cf4-208">이 쿼리의 결과는 각 예측 시계열에 대한 두 개의 열이며 열의 각 행에는 예측 값이 있는 중첩 테이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-208">The results of this query are two columns, one for each predicted series, where each row contains a nested table with the predicted values:</span></span>  
  
 <span data-ttu-id="e4cf4-209">**PredictedAmount**</span><span class="sxs-lookup"><span data-stu-id="e4cf4-209">**PredictedAmount**</span></span>  
  
|<span data-ttu-id="e4cf4-210">$TIME</span><span class="sxs-lookup"><span data-stu-id="e4cf4-210">$TIME</span></span>|<span data-ttu-id="e4cf4-211">금액</span><span class="sxs-lookup"><span data-stu-id="e4cf4-211">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="e4cf4-212">201101</span><span class="sxs-lookup"><span data-stu-id="e4cf4-212">201101</span></span>|<span data-ttu-id="e4cf4-213">172067.11</span><span class="sxs-lookup"><span data-stu-id="e4cf4-213">172067.11</span></span>|  
  
|<span data-ttu-id="e4cf4-214">$TIME</span><span class="sxs-lookup"><span data-stu-id="e4cf4-214">$TIME</span></span>|<span data-ttu-id="e4cf4-215">금액</span><span class="sxs-lookup"><span data-stu-id="e4cf4-215">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="e4cf4-216">201102</span><span class="sxs-lookup"><span data-stu-id="e4cf4-216">201102</span></span>|<span data-ttu-id="e4cf4-217">363390.68</span><span class="sxs-lookup"><span data-stu-id="e4cf4-217">363390.68</span></span>|  
  
 <span data-ttu-id="e4cf4-218">**PredictedQty**</span><span class="sxs-lookup"><span data-stu-id="e4cf4-218">**PredictedQty**</span></span>  
  
|<span data-ttu-id="e4cf4-219">$TIME</span><span class="sxs-lookup"><span data-stu-id="e4cf4-219">$TIME</span></span>|<span data-ttu-id="e4cf4-220">수량</span><span class="sxs-lookup"><span data-stu-id="e4cf4-220">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="e4cf4-221">201101</span><span class="sxs-lookup"><span data-stu-id="e4cf4-221">201101</span></span>|<span data-ttu-id="e4cf4-222">77</span><span class="sxs-lookup"><span data-stu-id="e4cf4-222">77</span></span>|  
  
|<span data-ttu-id="e4cf4-223">$TIME</span><span class="sxs-lookup"><span data-stu-id="e4cf4-223">$TIME</span></span>|<span data-ttu-id="e4cf4-224">수량</span><span class="sxs-lookup"><span data-stu-id="e4cf4-224">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="e4cf4-225">201102</span><span class="sxs-lookup"><span data-stu-id="e4cf4-225">201102</span></span>|<span data-ttu-id="e4cf4-226">260</span><span class="sxs-lookup"><span data-stu-id="e4cf4-226">260</span></span>|  
  
 <span data-ttu-id="e4cf4-227">공급자가 계층적 행 집합을 처리할 수 없는 경우 예측 쿼리에 FLATTEN 키워드를 사용하여 결과를 평면화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-227">If your provider cannot handle hierarchical rowsets, you can flatten the results by using the FLATTEN keyword in the prediction query.</span></span> <span data-ttu-id="e4cf4-228">일반 행 집합의 예를 비롯한 자세한 내용은 [SELECT&#40;DMX&#41;](/sql/dmx/select-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4cf4-228">For more information, including examples of flattened rowsets, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cf4-229">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4cf4-229">See Also</span></span>  
 <span data-ttu-id="e4cf4-230">[데이터 마이닝을 &#40;내용 쿼리&#41;](content-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e4cf4-230">[Content Queries &#40;Data Mining&#41;](content-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="e4cf4-231">데이터 정의 쿼리&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="e4cf4-231">Data Definition Queries &#40;Data Mining&#41;</span></span>](data-definition-queries-data-mining.md)  
  
  