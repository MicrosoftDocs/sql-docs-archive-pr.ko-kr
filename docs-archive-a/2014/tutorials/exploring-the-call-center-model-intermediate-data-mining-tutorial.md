---
title: 콜 센터 모델 탐색 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734724"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>콜 센터 모델 탐색(중급 데이터 마이닝 자습서)
  지금까지 탐구 모델을 작성했으므로 이제 이 모델을 사용하여 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 제공되는 다음과 같은 도구로 데이터에 대해 보다 자세한 정보를 알 수 있습니다.  
  
-   [Microsoft 신경망 뷰어](#bkmk_NNviewer) **:** 이 뷰어는 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에서 사용할 수 있으며 데이터의 상호 작용을 시험해 볼 수 있도록 설계 되었습니다.  
  
-   [Microsoft 일반 콘텐츠 트리 뷰어](#bkmk_genviewer) **:** 이 표준 뷰어에서는 모델을 생성할 때 알고리즘에서 발견 한 패턴 및 통계에 대 한 자세한 정보를 제공 합니다.  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a>Microsoft 신경망 뷰어  
 뷰어에는 **입력**, **출력**및 **변수**라는 세 개의 창이 있습니다.  
  
 **출력** 창을 사용 하 여 예측 가능한 특성 또는 종속 변수에 대해 서로 다른 값을 선택할 수 있습니다. 모델에 예측 가능한 특성이 여러 개 있는 경우 **출력 특성** 목록에서 특성을 선택할 수 있습니다.  
  
 **변수** 창에서는 영향을 주는 특성 또는 변수 측면에서 선택한 두 결과를 비교 합니다. 색이 지정된 막대는 변수가 대상 결과에 얼마나 많은 영향을 주는지를 시각적으로 나타냅니다. 변수에 대한 리프트 점수를 볼 수도 있습니다. 리프트 점수는 사용하고 있는 마이닝 모델 유형에 따라 다르게 계산되지만 일반적으로 예측을 위해 이 특성을 사용할 때 모델의 향상률을 보여 줍니다.  
  
 **입력** 창에서는 모델에 영향 요인을 추가 하 여 다양 한 시나리오를 시험해 볼 수 있습니다.  
  
### <a name="using-the-output-pane"></a>출력 창 사용  
 이 초기 모델에서는 얼마나 다양한 요인이 서비스 등급에 영향을 주는지 살펴보려고 합니다. 이렇게 하려면 출력 특성 목록에서 서비스 등급을 선택한 다음 **값 1** 및 **값 2**에 대 한 드롭다운 목록에서 범위를 선택 하 여 서로 다른 서비스 수준을 비교할 수 있습니다.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>가장 낮은 서비스 등급과 가장 높은 서비스 등급을 비교하려면  
  
1.  **값 1**에서 값이 가장 낮은 범위를 선택 합니다. 예를 들어 0-0-0.7 범위는 가장 낮은 중단율을 나타내므로 결국 가장 높은 서비스 수준을 보여 줍니다.  
  
    > [!NOTE]  
    >  이 범위의 정확한 값은 모델 구성 방법에 따라 매우 다를 수 있습니다.  
  
2.  **값 2**에서 가장 높은 값의 범위를 선택 합니다. 예를 들어 값이 >= 0.12 인 범위는 최고 중단 율을 나타내므로 최악의 서비스 등급을 나타냅니다. 즉 이 교대조 근무 시간 동안 전화를 건 고객 중 12%가 상담원과 연결하기 전에 전화를 끊었습니다.  
  
     **변수** 창의 내용이 결과 값에 영향을 주는 특성을 비교 하 여 업데이트 됩니다. 따라서 왼쪽 열에서는 가장 높은 서비스 등급과 연결된 특성을 보여 주고 오른쪽 열에서는 가장 낮은 서비스 등급과 연결된 특성을 보여 줍니다.  
  
### <a name="using-the-variables-pane"></a>변수 창 사용  
 이 모델에는 `Average Time Per Issue` 중요 한 요소 라고 표시 됩니다. 이 변수는 호출 유형에 상관없이 평균 호출 응답 시간을 나타냅니다.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>특성에 대한 확률 및 리프트 점수를 보고 복사하려면  
  
1.  **변수** 창에서 첫 번째 행의 색이 지정 된 막대 위에 마우스를 놓습니다.  
  
     이 색이 지정 된 막대는 `Average Time Per Issue` 서비스 등급에 얼마나 강력한 기여를 보여 줍니다. 도구 설명은 변수와 대상 결과의 각 조합에 대한 총 점수, 확률 및 리프트 점수를 보여 줍니다.  
  
2.  **변수** 창에서 색이 지정 된 막대를 마우스 오른쪽 단추로 클릭 하 고 **복사**를 선택 합니다.  
  
3.  Excel 워크시트에서 아무 셀 이나 마우스 오른쪽 단추로 클릭 하 고 **붙여넣기**를 선택 합니다.  
  
     보고서가 HTML 테이블로 붙여 넣어지고 각 막대에 대한 점수만 표시합니다.  
  
4.  다른 Excel 워크시트에서 셀을 마우스 오른쪽 단추로 클릭 하 고 선택 하 **여 붙여넣기**를 선택 합니다.  
  
     보고서가 텍스트 형식으로 붙여 넣어지고 다음 섹션에서 설명하는 관련 통계를 포함합니다.  
  
### <a name="using-the-input-pane"></a>입력 창 사용  
 교대조 또는 전화 상담원 수와 같은 특정 요인의 영향을 살펴보려고 합니다. **입력** 창을 사용 하 여 특정 변수를 선택할 수 있으며, **변수** 창이 자동으로 업데이트 되어 지정 된 변수와 함께 이전에 선택한 두 그룹을 비교 합니다.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>입력 특성을 변경하여 서비스 등급에 대한 효과를 검토하려면  
  
1.  **입력** 창에서 **특성**에 대해 Shift를 선택 합니다.  
  
2.  **값**에 **AM**을 선택 합니다.  
  
     **변수** 창은 교대조가 **AM**일 때 모델에 미치는 영향을 표시 하도록 업데이트 됩니다. 다른 모든 선택 항목은 동일 하 게 유지 됩니다. 즉, 가장 낮은 서비스와 최고 등급을 비교 하 고 있습니다.  
  
3.  **값**에 대해 **오후 1**를 선택 합니다.  
  
     **변수** 창은 이동이 변경 될 때 모델에 미치는 영향을 표시 하도록 업데이트 됩니다.  
  
4.  **입력** 창에서 **특성**아래에 있는 다음 빈 행을 클릭 하 고 호출을 선택 합니다. **값**에 대해 가장 많은 수의 호출을 나타내는 범위를 선택 합니다.  
  
     새 입력 조건이 목록에 추가됩니다. **변수** 창은 호출 볼륨이 가장 높을 때 특정 교대조에 대 한 모델의 영향을 표시 하도록 업데이트 됩니다.  
  
5.  계속 Shift 및 Calls에 대한 값을 변경하여 교대조, 호출량 및 서비스 등급 간의 흥미로운 상관 관계를 발견합니다.  
  
    > [!NOTE]  
    >  다른 특성을 사용할 수 있도록 **입력** 창을 지우려면 **뷰어 콘텐츠 새로 고침**을 클릭 합니다.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>뷰어에서 제공하는 통계 해석  
 오래 걸리는 대기 시간은 높은 중단율을 예측하는 강력한 요인으로, 낮은 서비스 등급을 의미합니다. 확실하게 이러한 결론을 내릴 수 있지만 마이닝 모델에서는 이러한 추세를 해석하는 데 유용한 몇 가지 추가 통계 데이터를 제공합니다.  
  
-   **점수**: 결과 간 판별에 대 한이 변수의 전반적인 중요도를 나타내는 값입니다. 점수가 높을수록 변수가 결과에 끼치는 영향도 큽니다.  
  
-   **값 1의 확률**:이 결과에 대 한이 값의 확률을 나타내는 백분율입니다.  
  
-   **값 2의 확률**:이 결과에 대 한이 값의 확률을 나타내는 백분율입니다.  
  
-   값 **1** 및 값 **2에**대 한 리프트: 값 1 및 값 2 결과를 예측 하기 위해이 특정 변수를 사용 하는 경우의 영향을 나타내는 점수입니다. 점수가 높을수록 변수가 결과를 보다 잘 예측할 수 있습니다.  
  
 다음 표에는 가장 많은 영향을 주는 요인에 대한 일부 값 예가 포함되어 있습니다. 예를 들어 **값 1의 확률** 은 60.6%이 고 **값 2의 확률** 은 8.30%입니다. 즉, 문제의 평균 시간이 44-70 분의 범위 내에 있고, 사례의 60.6%가 가장 높은 서비스 등급 (값 1 8.30)으로 전환 된 경우에는 서비스 등급이 더 심한 (값 2)이를 의미 합니다.  
  
 이 정보를 사용하여 몇 가지 결론을 내릴 수 있습니다. 보다 짧은 호출 응답 시간(44-70 범위)이 보다 높은 서비스 등급(0.00-0.07 범위)에 더 많은 영향을 끼칩니다. 점수(92.35)는 이 변수가 매우 중요함을 나타냅니다.  
  
 그러나 영향을 주는 요인 목록을 살펴보면 보다 미묘하고 해석하기 더 어려운 영향을 가진 몇 가지 다른 요인을 확인할 수 있습니다. 예를 들어 교대조가 서비스에 영향을 주는 것 같지만 리프트 점수 및 상대 확률은 교대조가 주요 요인이 아님을 나타냅니다.  
  
|attribute|값|\<0.07 우위|>= 0.12 우위|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89.087-120.000||점수: 100<br /><br /> Value1의 확률: 4.45%<br /><br /> Value2의 확률: 51.94%<br /><br /> Value1의 리프트: 0.19<br /><br /> Value2의 리프트: 1.94|  
|Average Time Per Issue|44.000-70.597|점수: 92.35<br /><br /> 값 1의 확률: 60.06%<br /><br /> 값 2의 확률: 8.30%<br /><br /> 값 1의 리프트: 2.61<br /><br /> 값 2의 리프트: 0.31||  
  
 [맨 위로 이동](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a>Microsoft 일반 콘텐츠 트리 뷰어  
 이 뷰어를 사용하면 모델을 처리할 때 알고리즘에서 만든 보다 자세한 정보를 볼 수 있습니다. **MicrosoftGeneric 콘텐츠 트리 뷰어** 는 마이닝 모델을 일련의 노드로 나타내며 각 노드는 학습 데이터에 대 한 배운 정보를 나타냅니다. 이 뷰어는 모든 모델에서 사용할 수 있지만 노드 내용은 모델 유형에 따라 다릅니다.  
  
 신경망 모델 또는 로지스틱 회귀 모델의 경우 특히 `marginal statistics node`가 유용합니다. 이 노드에는 데이터의 값 분포에 대한 파생 통계가 들어 있습니다. 많은 T-SQL 쿼리를 작성하지 않고 데이터 요약을 얻으려는 경우 이 정보가 유용할 수 있습니다. 이전 항목의 값 범주화에 대한 차트가 marginal statistics node에서 파생되었습니다.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>마이닝 모델에서 데이터 값 요약을 얻으려면  
  
1.  데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에서을 선택 \<mining model name> 합니다.  
  
2.  **뷰어** 목록에서 **Microsoft 일반 콘텐츠 트리 뷰어**를 선택 합니다.  
  
     마이닝 모델 뷰가 새로 고쳐져 왼쪽 창에 노드 계층이 표시되고 오른쪽 창에 HTML 테이블이 표시됩니다.  
  
3.  **노드 캡션** 창에서 이름이 10000000000000000 인 노드를 클릭 합니다.  
  
     모델의 최상위 노드는 항상 모델 루트 노드입니다. 신경망 또는 로지스틱 회귀 모델에서 이 노드 바로 아래에 있는 노드가 marginal statistics node입니다.  
  
4.  **노드 세부 정보** 창에서 행을 찾을 때까지 아래로 스크롤합니다 NODE_DISTRIBUTION 합니다.  
  
5.  NODE_DISTRIBUTION 테이블 아래로 스크롤하여 신경망 알고리즘에서 계산한 값 분포를 봅니다.  
  
 보고서에 이 값을 사용하려면 특정 행에 대한 정보를 선택한 다음 복사하거나 다음 DMX(Data Mining Extensions) 쿼리를 사용하여 노드의 전체 내용을 추출합니다.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 또한 NODE_DISTRIBUTION 테이블의 노드 계층 및 정보를 사용하여 신경망의 개별 경로를 이동하고 숨겨진 계층의 통계를 볼 수 있습니다. 자세한 내용은 [신경망 모델 쿼리 예제](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)를 참조 하세요.  
  
 [맨 위로 이동](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [로지스틱 회귀 모델을 콜 센터 구조에 추가 &#40;중급 데이터 마이닝 자습서&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>참고 항목  
 [신경망 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [신경망 모델 쿼리 예제](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Microsoft 신경망 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [마이닝 모델에서 열의 분할 변경](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
