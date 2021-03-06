---
title: 예측 계산기 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model, regression
- Table Analysis tools
- scorecard
- logistic regression
- prediction calculator
ms.assetid: 8bb8c318-e85f-4fd6-b32b-4cdfb13ca1b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: c6e7aece740dc1b9dab0b27affc76954bf372d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741388"
---
# <a name="prediction-calculator-table-analysis-tools-for-excel"></a>예측 계산기(Excel용 테이블 분석 도구)
  ![예측 계산기 도구](media/tat-predcal.gif "예측 계산기 도구")  
  
 **예측 계산기** 도구를 사용 하면 새 데이터를 분석 하 고 옵션 또는 위험을 평가 하는 데 사용할 수 있는 성과 기록표를 만들 수 있습니다. 예를 들어 고객에 대 한 기록 및 인구 통계 데이터가 있는 경우 **예측 계산기** 도구를 통해 다음 두 가지 주요 작업을 수행할 수 있습니다.  
  
-   인구 통계, 구매 동작 및 다른 여러 요인에 대한 기본 분석 생성  
  
-   멤버를 평가하고 신제품 또는 서비스 제공을 추천하는 데 도움이 되는 작업 점수표 작성  
  
 마법사를 실행하면 모든 기본 계산이 저장된 워크시트도 만들어지므로 이를 통해 모델과 상호 작용을 수행하고 여러 입력 값이 최종 점수에 어떤 영향을 미치는지 확인할 수 있습니다.  
  
 오프라인 점수 계산에 사용할 수 있는 워크시트의 인쇄 버전을 만들도록 선택할 수도 있습니다. 온라인 Excel 통합 문서를 사용할 때처럼 모델과 상호 작용을 할 수는 없지만 인쇄 버전에는 값을 입력하고 최종 점수를 계산하는 데 필요한 모든 계산이 포함되어 있습니다.  
  
## <a name="using-the-prediction-calculator-tool"></a>예측 계산기 도구 사용  
  
1.  분석할 데이터가 들어 있는 Excel 테이블을 엽니다.  
  
2.  **분석** 탭에서 **예측 계산기** 를 클릭 합니다.  
  
3.  **예측 계산기** 대화 상자에서 대상에 대해 구매 동작과 같이 예측 하려는 열을 선택 합니다.  
  
4.  목표 값을 지정합니다. 값이 숫자 이면 **범위의**옵션을 사용 하 고 원하는 범위의 최소값과 최 댓 값을 입력 합니다. 불연속 값 이면 **정확히** 옵션을 선택한 다음 드롭다운 목록에서 값을 선택 합니다.  
  
5.  **분석에 사용할 열 선택을**클릭 합니다.  
  
6.  **고급 열 선택** 대화 상자에서 유용한 정보가 있는 열을 선택 합니다. 분석과 관련이 없는 열을 제거하고 **확인**을 클릭합니다.  
  
     결과를 왜곡하지 않으려면 중복된 정보가 들어 있는 열도 제거해야 합니다. 예를 들어 숫자 데이터가 들어 있는 Income 열과 높음, 중간, 낮음과 같은 레이블이 들어 있는 Income Group 열이 있으면 같은 모델에 이 두 열을 모두 포함하는 대신 각 열에 대해 별도의 모델을 만들어야 합니다.  
  
7.  **출력 옵션** 섹션에서 **작업 계산기** 를 선택 하 여 Excel 통합 문서 내에서 분석 및 성과 기록표를 만듭니다. **프린터 준비 계산기** 를 선택 하 여 분석을 만들고 인쇄 하 여 점수를 매기는 데 사용할 수 있는 보고서도 생성 합니다.  
  
8.  **실행**을 클릭합니다.  
  
     보고서와 점수표가 포함된 새 워크시트가 만들어집니다.  
  
### <a name="requirements"></a>요구 사항  
 **예측 계산기** 도구는 불연속 값과 연속 숫자 데이터를 사용할 수 있는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.  
  
## <a name="understanding-the-scoring-reports"></a>점수 계산 보고서 이해  
 두 출력 옵션을 선택하면 예측 계산기는 현재 통합 문서 내부에 다음과 같은 세 개의 새 워크시트를 만듭니다.  
  
-   분석 결과를 포함 하는 **예측 보고서**이며 대화형 테이블과 그래프를 사용 하 여 상호 작용 및 수익을 시험해 볼 수 있습니다.  
  
-   점수를 만드는 데 도움이 되는 대화형 **예측 계산기** 입니다.  
  
-   점수 매기기에 사용할 지침과 계수를 포함 하는 **인쇄 가능한 계산기** 입니다.  
  
-   이 섹션에서는 각 보고서에 있는 정보 및 여러 보고서 옵션 사용법에 대해 설명합니다.  
  
### <a name="prediction-report-with-graphs"></a>그래프가 포함된 예측 보고서  
 첫 번째 예측 보고서는 ** \<target state> 의 \<target attribute> 에 대 한 예측 계산기 보고서 **라는 제목의 제목을 갖습니다. 이 보고서에는 분석에서 파생된 요인의 테이블과 특정 분석의 재무 효과를 평가하는 데 사용할 수 있는 도구가 들어 있습니다.  
  
#### <a name="table-for-specifying-costs-and-profits"></a>비용 및 수익을 지정할 수 있는 테이블  
 보고서의 왼쪽 위에 있는 이 보고서의 첫 번째 도구는 값을 올바르게 또는 잘못 예측하는 것과 관련된 비용과 수익을 지정할 수 있는 테이블입니다.  이러한 비용/수익은 계산기의 최적 점수 임계값을 계산하는 데 필요합니다.  
  
|항목|설명 및 예|  
|----------|-----------------------------|  
|거짓 긍정 비용|실제로는 예측이 잘못되었는데 모델에서 긍정적인 결과를 올바르게 예측했다고 간주하는 비용<br /><br /> 예를 들어 모델에서 고객이 상품을 구매할 것이라고 예측하여 해당 고객을 대상으로 하는 캠페인을 고안한 경우 여기에 고객에게 다가가는 비용을 입력할 수 있습니다.|  
|거짓 부정 비용|실제로는 예측이 잘못되었는데 모델에서 부정적인 결과를 올바르게 예측했다고 간주하는 비용<br /><br /> 예를 들어 모델에서 나이가 많은 고객이 자전거를 구매할 가능성이 낮다고 예측했는데 모델에 오류가 있어서 나이가 많은 고객을 대상으로 삼을 기회를 놓쳤다는 사실을 발견한 경우 놓친 기회 비용을 여기에 할당할 수 있습니다.|  
|참 긍정 수익|긍정적 결과를 올바르게 예측하여 발생한 수익. 예를 들어 올바른 고객을 대상으로 하여 판매에 성공했다면 고객당 수익을 여기에 입력할 수 있습니다.|  
|참 부정 수익|부정적 결과를 올바르게 예측하여 발생한 수익<br /><br /> 예를 들어 대상이 되지 않아야 할 고객을 올바르게 식별할 수 있으면 고객당 광고비를 여기에 입력할 수 있습니다.|  
  
#### <a name="chart-for-viewing-maximum-profit"></a>최대 수익을 볼 수 있는 차트  
 테이블에 값을 입력하면 관련 그래프가 자동으로 업데이트되어 현재 모델에서 수익을 최대화하는 최적의 지점이 표시됩니다. 이 테이블 오른쪽의 꺾은선형 그래프는 여러 점수 임계값에 대한 수익을 표시합니다. 수익은 모델의 예측 및 확률을 기준으로 테이블에 입력한 수익 및 비용 수치를 사용하여 계산됩니다.  
  
 예를 들어 왼쪽 위의 표에서 **수익을 최대화 하기 위해 제안 된 임계값** 에 대 한 셀이 값 500을 표시 하는 경우 오른쪽의 차트는 선 그래프의 가장 높은 점으로 500을 표시 합니다. 이 값 500은 수익을 최대화하려면 마이닝 모델의 최상위 500개 권장 사항을 확률 순서대로 사용해야 한다는 것을 의미합니다.  
  
#### <a name="table-listing-scores-for-each-attribute-and-value"></a>각 특성 및 값에 대한 점수를 표시하는 테이블  
 보고서의 왼쪽 아래에 있는 테이블은 검색된 값의 상세한 분석 및 각 값이 결과에 미치는 영향을 보여 줍니다. 이 테이블의 값은 예측을 이해하는 데 도움을 주기 위해 표시된 것으로 변경할 수 없습니다.  
  
 예를 들어 다음 테이블은 목표하는 결과가 고객의 자전거 구매일 때 이 결과에 대한 예를 보여 줍니다. 이 테이블에는 입력이 모델에 영향을 주었는지 여부에 관계없이 모델에 사용된 각 입력 열이 표시됩니다. 이 테이블에는 불연속 값과, 입력 열에 연속 숫자 데이터가 포함된 경우 불연속화된 값도 표시됩니다.  
  
 **상대적 영향** 열의 값은 백분율로 표시 되는 확률입니다. 이 값이 결과에 미치는 영향을 시각적으로 나타내기 위해 셀에 음영이 표시됩니다.  
  
|특성|값|상대적 영향|  
|---------------|-----------|---------------------|  
|Marital Status|Married|0|  
|Marital Status|Single|71|  
|성별|Female|13|  
|성별|Male|0|  
  
 이 요인은 다음과 같이 해석될 수 있습니다.  
  
-   결혼 여부는 고객이 자전거를 구입할 가능성에 영향을 미치지 않습니다.  
  
-   하지만 미혼이라는 사실은 고객이 자전거를 구입할 가능성에 대한 강한 지표(70%)가 됩니다.  
  
-   고객이 여성인 경우 고객의 성별은 예측된 자전거 구입 동작에 미미한 영향(13%)밖에 미치지 않으며 고객이 남성인 경우에는 영향이 전혀 없습니다.  
  
#### <a name="chart-of-cumulative-misclassification-cost"></a>누적 오분류 비용 차트  
 보고서 오른쪽 아래의 영역형 차트는 다양한 점수 임계값에 대한 누적 오분류 비용을 보여 줍니다. 이 차트에는 거짓 긍정, 참 긍정, 거짓 부정 및 참 부정에 대해 입력된 비용/수익 수치도 사용됩니다.  
  
 수익을 최대화하는 데 중점을 둔 보고서 오른쪽 위의 차트와는 달리 이 차트는 잘못된 예측 비용을 고려합니다. 이 차트는 잘못된 의사 결정을 수행하는 비용이 올바른 추측을 수행하는 비용을 훨씬 초과하므로 이를 방지해야 하는 시나리오에 특히 유용합니다.  
  
 예를 들어 첫 번째 차트를 보면 모델에서 예측한 최상위 500명의 고객을 대상으로 하는 것이 수익을 최대화할 수 있는 방법이지만 두 번째 차트를 보고 대상 고객을 잘못 선정하는 비용이 너무 크다고 생각되면 마케팅 캠페인 대상을 처음 400명의 고객으로 한정하는 결정을 내릴 수 있습니다.  
  
### <a name="interactive-prediction-calculator"></a>대화형 예측 계산기  
 예측 계산기 도구에서 만든 두 번째 워크시트는 ** \<target state> 의 \<target attribute> 에 대 한 예측 계산기 **제목입니다. 이 워크시트는 개별 점수를 계산하는 데 사용할 수 있는 대화형 워크시트입니다. 이 워크시트는 모델에 저장된 패턴 및 통계를 사용하므로 여러 가지 값을 테스트하여 이 값이 예측 점수에 미치는 영향을 확인해 볼 수 있습니다. 이 보고서에는 두 개의 섹션도 있습니다. 하나는 대화형 이며 하나는 참조로 제공 됩니다.  
  
#### <a name="first-table"></a>첫 번째 테이블  
 테이블의 **값** 열에서 새 값을 선택 하거나 입력 하 여 값 변경이 점수에 미치는 영향을 확인할 수 있습니다.  
  
 예를 들어 보고서에 다음 값이 있는 경우 Cars의 값을 1로 변경했다가 다시 0으로 변경하여 이에 따라 고객의 구매 동작이 어떻게 변경되는지 확인할 수 있습니다. **자동차** 값을 0으로 변경 하면 아래쪽의 예측이 TRUE로 변경 됩니다.  
  
|특성|값|상대적 영향|  
|---------------|-----------|---------------------|  
|Marital Status|Married|0|  
|성별|Male|0|  
|Income|39050-71062|117|  
|Children|0|157|  
|Education|Bachelors|22|  
|Occupation|Skilled Manual|33|  
|Home Owner|예|8|  
|Cars|2|50|  
|Commute Distance|0-1 Miles|99|  
|지역|북아메리카|0|  
|연령|37-46|5|  
|합계||491|  
|Prediction for 'Yes'||FALSE|  
  
 새 값을 입력 하면 셀에 표시 되는 점수와 예에 대 한 예측이 TRUE로 바뀌고 다양 한 특성에 대 한 **상대적 영향** 점수가 업데이트 됩니다.  
  
> [!NOTE]  
>  자동차 대수 등 값을 하나만 수정하는 경우에도 다른 특성의 값과 영향이 변경될 수 있습니다. 이는 데이터 마이닝 모델이 데이터 간 복잡한 관계를 찾아내므로 하나의 변수를 변경하는 것이 예상치 못한 효과를 가져올 수 있기 때문입니다. 따라서 대화형 예측 계산기를 사용하여 여러 가지 값을 테스트해 보거나 마이닝 모델을 살펴보아 상호 작용에 대한 이해를 높이는 것이 좋습니다. 자세한 내용은 [모델 찾아보기](prediction-calculator-table-analysis-tools-for-excel.md)를 참조 하세요.  
  
#### <a name="score-breakdown"></a>점수 분석  
 이 테이블은 입력 열의 가능한 각 상태에 대한 개별 점수 및 이 점수가 결과에 미치는 상대적인 영향을 보여 줍니다. 이 테이블은 정적이며 참조용으로만 사용됩니다.  
  
### <a name="printable-prediction-calculator"></a>인쇄 가능한 예측 계산기  
 예측 계산기 도구에서 만든 세 번째 워크시트의 제목은 ** \<target state> 의 \<target attribute> 에 대 한 Printableprediction 계산기 **입니다. 이 점수표를 인쇄하여 컴퓨터를 사용하지 않고 직접 점수를 계산할 수 있습니다.  
  
##### <a name="to-print-and-use-the-scoring-report-generated-by-the-prediction-calculator"></a>예측 계산기에서 생성된 점수 계산 보고서를 인쇄하고 사용하려면  
  
1.  **에 대해 \<attribute> 인쇄 가능한 예측 계산기 **탭을 클릭 합니다.  
  
2.  Excel 파일 메뉴에서 **인쇄 미리 보기**를 선택 합니다.  
  
3.  점수표가 원하는 형태로 페이지에 맞추어질 때까지 페이지 방향, 여백 및 기타 인쇄 옵션을 변경합니다.  
  
     이 점수표는 동적 점수표가 아니며 모델과 전혀 연결되어 있지 않으므로 기본 데이터에 영향을 주지 않고 열이나 행을 이동하여 서식을 개선할 수 있습니다.  
  
4.  점수표를 인쇄합니다.  
  
5.  각 특성에 대해 값을 하나만 선택합니다. 선택한 값에 대해 상자에 확인 표시를 입력 하 고 **점수** 열에 해당 숫자를 씁니다.  
  
6.  정확도를 높이기 위해 가능한 한 많은 특성을 사용합니다.  
  
7.  각 특성에 대 한 점수 합계를 계산 하 고 **합계** 행에 해당 숫자를 입력 합니다.  
  
8.  시트의 **합계** 행 바로 다음에 인쇄 된 조건을 사용 하 여 점수를 예측 된 결과로 변환 합니다.  
  
## <a name="related-tools"></a>관련 도구  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에는 이러한 종류의 분석에 사용할 수 있는 Microsoft 로지스틱 회귀 알고리즘이 제공됩니다. 로지스틱 회귀를 이미 잘 알고 있는 경우 Excel 용 데이터 마이닝 클라이언트의 **고급** 옵션을 사용 하 여 로지스틱 회귀 모델을 쉽게 만들 수 있습니다. 자세한 내용은 [고급 모델링 &#40;Excel 용 데이터 마이닝 추가 기능&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)을 참조 하세요. 로지스틱 회귀 모델에 대 한 옵션 및 매개 변수에 대 한 자세한 내용은 온라인 설명서의 "Microsoft 로지스틱 회귀 알고리즘" 항목을 참조 하십시오 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [Excel용 테이블 분석 도구](table-analysis-tools-for-excel.md)  
  
  
