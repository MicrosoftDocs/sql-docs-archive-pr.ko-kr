---
title: 데이터 마이닝 모델 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e27739d3733c0b48dc6cff3e83e01f9cb12bce7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651941"
---
# <a name="creating-a-data-mining-model"></a>데이터 마이닝 모델 만들기
  데이터 모델링은 데이터에 *알고리즘* 을 적용 하 여 패턴 및 추세를 작성 하는 데이터 마이닝 단계입니다. 이러한 패턴을 사용하여 나중에 분석하거나 예측할 수 있습니다.  
  
 Office용 데이터 마이닝 추가 기능은 모델을 간단히 만들 수 있는 마법사를 통해 데이터 마이닝을 지원합니다. 이 마법사는 데이터를 분석하고 상관 관계를 식별하며 모든 변수의 통계적 의미를 계산하고 자동으로 최상의 모델을 선택합니다.  
  
 이 기능은 및에서 제공 하는 데이터 마이닝 도구 만큼 강력 하기는 하지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 마법사와 친숙 한 Excel 인터페이스를 함께 사용 하면 데이터 마이닝을 쉽게 만들고 수정 하 고 사용할 수 있습니다.  
  
## <a name="advanced-data-mining"></a>고급(데이터 마이닝)  
 고급 마법사를 사용 하면의 데이터 마이닝 알고리즘 중 하나를 사용 하 여 Excel에 저장 된 데이터를 기반으로 새 데이터 마이닝 모델을 만들 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
### <a name="create-mining-structure"></a>마이닝 구조 만들기  
 마이닝 구조 만들기 마법사를 사용하면 여러 마이닝 모델의 기반으로 사용할 수 있는 새로운 데이터 마이닝 구조를 작성할 수 있습니다. 마법사에는 테스트 집합으로 사용할 데이터 부분을 따로 지정할 수 있는 옵션이 있으므로 일관된 테스트 표준에 따라 같은 데이터를 사용하는 모든 모델을 평가할 수 있습니다.  
  
 [데이터 마이닝 추가 기능을 SQL Server &#40;마이닝 구조를 만듭니다&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>구조에 모델 추가  
 구조에 모델 추가 마법사를 사용하면 기존 데이터 마이닝 구조를 선택하여 이 구조에 대한 새 데이터 마이닝 모델을 만들 수 있습니다. 매개 변수를 변경하고 서로 다른 데이터 마이닝 알고리즘을 선택하여 다양한 마이닝 모델을 구조에 추가하고 출력을 사용자 지정할 수 있습니다.  
  
 [Excel 용 데이터 마이닝 추가 기능 &#40;구조에 모델 추가&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>주요 영향 요인 분석(분석)  
 관심 있는 열 또는 출력 값을 선택한 다음 알고리즘으로 모든 입력 데이터를 분석하여 대상에 가장 많은 영향을 미친 요소를 식별합니다. 필요한 경우 두 값을 비교하는 보고서를 만들어 영향 요인이 어떻게 변경되는지 확인할 수 있습니다.  
  
 **주요 영향 요인 분석** 도구는 Microsoft naive Bayes 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구 &#40;주요 영향 요인 분석&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>연결(데이터 마이닝)  
 **연결** 마법사는 여러 트랜잭션에 표시 되는 항목 간의 연결을 검색 하는 연결 모델을 작성 합니다 (예: 시장 바구니 분석).  
  
 [Excel 용 데이터 마이닝 클라이언트 &#40;마법사 연결&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>분류(데이터 마이닝)  
 **분류** 마법사는 대상 결과에 적용 된 요인을 분석 하는 분류 모델을 작성 합니다. 이 마법사에서는 의사 결정 트리, Naïve Bayes, 신경망을 포함하여 여러 알고리즘을 사용할 수 있습니다.  
  
 [분류 마법사 &#40;Excel 용 데이터 마이닝 추가 기능&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>클러스터(데이터 마이닝)  
 **클러스터** 마법사는 비슷한 특성을 공유 하는 행 그룹을 검색 하는 클러스터링 모델을 작성 합니다. 클러스터링 (종종 *조각화*라고도 함)은 패턴 및 새 데이터의 그룹화를 이해 하려고 할 때 매우 유용한 자율 학습 기술입니다.  
  
 Microsoft 클러스터링 알고리즘은 K-means와 EM(Expectation maximization) 클러스터링의 다양한 변형을 지원합니다.  
  
 [클러스터 마법사는 Excel 용 데이터 마이닝 추가 기능&#41;를 &#40;](cluster-wizard-data-mining-add-ins-for-excel.md)합니다.  
  
## <a name="detect-categories-analyze"></a>범주 검색(분석)  
 **범주 검색** 도구를 사용 하면 데이터 집합을 추가 하 고 클러스터링을 적용 하 여 데이터 그룹화를 찾을 수 있습니다. 유사성을 찾고 추가 분석을 위해 그룹을 만드는 데 유용 합니다.  
  
 **범주 검색** 도구는 Microsoft 클러스터링 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구 &#40;범주 검색&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>예상(데이터 마이닝)  
 추정 마법사는 데이터 패턴을 추출하고 이 패턴을 사용하여 연속 숫자, 날짜 또는 시간 값을 예측하는 추정 모델을 작성합니다. 이 마법사는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 사용합니다.  
  
 [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>예제로 채우기(분석)  
 **예제로 채우기** 도구를 사용 하 여 누락 된 값을 돌립니다 수 있습니다. 사용자는 어떤 값이 누락되었는지에 대한 예를 제공하고 해당 도구에서 표의 모든 데이터를 기반으로 패턴을 작성한 다음 데이터의 패턴을 기반으로 한 새 값을 제안합니다.  
  
 **예제로 채우기** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구 &#40;예제로 채우기&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>예측(분석)  
 **예측** 도구는 시간이 지남에 따라 변경 되는 데이터를 사용 하 여 미래 값을 예측 합니다.  
  
 **예측** 도구는 Microsoft 시계열 알고리즘을 사용 합니다.  
  
 [Excel 용 예측 &#40;테이블 분석 도구&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>예측(데이터 마이닝)  
 **예측** 마법사는 일련의 셀에서 패턴을 검색 한 다음 추가 값을 예측 하는 예측 모델을 작성 합니다.  
  
 [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>예외 강조 표시(분석)  
 **예외 강조 표시** 도구는 데이터 테이블의 패턴을 분석 하 고 패턴에 맞지 않는 행과 값을 찾습니다. 그런 다음 모델을 검토하여 수정한 후 다시 실행하거나 향후 작업을 위해 값에 플래그를 지정합니다.  
  
 **예외 강조 표시** 도구는 Microsoft 클러스터링 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구 &#40;예외 강조 표시&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>예측 계산기(분석)  
 이 도구는 대상 결과를 이끄는 요인을 분석하는 모델을 만든 다음 해당 패턴에서 유추한 기준을 기반으로 새로운 입력 결과를 예측합니다. 또한 새로운 입력 사항을 손쉽게 평가할 수 있는 대화형 의사 결정 워크시트도 생성합니다. 오프라인에서 사용할 수 있는 평가 워크시트 인쇄 버전도 만들 수 있습니다.  
  
 **예측 계산기** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구&#41;예측 계산기 &#40;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>시나리오: 목표 검색 (분석)  
 **목표 검색** 도구에서 대상 값을 지정 하면이 도구는 해당 대상을 충족 하기 위해 변경 해야 하는 기본 요소를 식별 합니다. 예를 들어, 전화 만족도를 20% 증가시켜야 하는 경우 해당 모델을 통해 목표를 달성하기 위해 변경해야 하는 요소를 예측할 수 있습니다.  
  
 **목표 검색** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.  
  
 자세히  
  
 [Excel 용 테이블 분석 도구 &#40;목표 검색 시나리오&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>시나리오: 가상 시나리오 (분석)  
 **가상 분석** 도구는 **목표 검색** 도구를 보완 합니다. 이 도구를 사용하여 변경하려는 값을 입력하면 모델에서 해당 변경을 통해 원하는 결과를 얻기에 충분한지 예측합니다. 예를 들어, 모델을 통해 전화 상담원을 한 명 더 추가하면 해당 시점에서 고객 만족도를 높일 수 있는지 유추할 수 있습니다.  
  
 **가상** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.  
  
 [Excel 용 테이블 분석 도구 &#40;가상 시나리오&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>시장 바구니 분석(분석)  
 시장 **바구니 분석** 도구는 자주 함께 구매 하는 제품 그룹을 만들어 교차 판매 또는 업 판매에 사용할 수 있는 패턴을 식별 합니다. 또한 관련 제품 번들의 가격 및 비용을 기반으로 보고서를 생성하여 의사 결정을 지원합니다.  
  
 자주 함께 발생하는 이벤트, 진단 요소 또는 기타 일련의 잠재적 원인 및 결과에 대해서도 이 도구를 사용할 수 있습니다.  
  
 시장 **바구니 분석** 도구는 Microsoft 연결 알고리즘을 사용 합니다.  
  
 [시장 바구니 분석 &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>참고 항목  
 [데이터 탐색 및 정리](exploring-and-cleaning-data.md)   
 [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
