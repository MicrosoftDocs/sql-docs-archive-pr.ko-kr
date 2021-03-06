---
title: 정확도 차트 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 45ca5b4d3944948b257b5fa063ebce5583701157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647348"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a>정확도 차트(SQL Server 데이터 마이닝 추가 기능)
  ![데이터 마이닝 리본 메뉴의 정확도 차트 단추](media/dmc-accchart.gif "데이터 마이닝 리본 메뉴의 정확도 차트 단추")  
  
 정확도 차트를 사용하면 모델을 새로운 데이터 집합에 적용하고 모델이 얼마나 잘 작동하는지 평가할 수 있습니다. 이 마법사로 만든 정확도 차트는 데이터 마이닝 모델의 정확도를 측정 하는 데 자주 사용 되는 차트의 유형인 *리프트 차트*입니다. 이 유형의 정확도 차트는 지정된 데이터 마이닝 모델을 사용함으로써 얻을 수 있는 기능 향상을 무작위 예측 및 예측이 100% 정확한 이상적인 사례와 비교하여 그래픽 표현으로 보여 줍니다. 하나의 차트 내에서 여러 모델을 비교할 수 있습니다.  
  
## <a name="example"></a>예제  
 Adventure Works Cycles의 마케팅 부서에서 타겟 메일링 캠페인을 만들려고 한다고 가정해 봅니다. 과거 캠페인을 통해 응답률이 일반적으로 10%임을 알아냈습니다. 이 부서의 데이터베이스에는 10,000명의 잠재적인 고객 목록이 테이블에 저장되어 있는데 일반 응답률을 기준으로 이 중 1,000명의 고객이 응답하리라는 것을 예측할 수 있습니다.  
  
 그러나 5,000명의 고객에게만 광고 메일을 전송할 수 있는 경우 마케팅 부서에서는 마이닝 모델을 사용하여 응답 가능성이 가장 높은 5,000명의 고객을 대상으로 선택할 수 있습니다.  
  
 회사에서 5,000명의 고객을 임의로 선택하는 경우 일반적으로 대상 고객의 10%만 응답하므로 500개의 응답만 받을 수 있습니다. 이 시나리오는 리프트 차트에서 임의 선으로 나타납니다.  
  
 그러나 마케팅 부서에서 마이닝 모델을 사용하여 메일 전송 대상을 결정하며 이러한 모델이 완벽한 경우에는 모델에서 권장하는 잠재 고객 1,000명에게 광고 메일을 전송하여 1,000개의 응답을 모두 받을 것으로 기대할 수 있습니다. 이 시나리오는 리프트 차트에서 이상적인 선으로 나타납니다.  
  
## <a name="using-the-accuracy-chart-wizard"></a>정확도 차트 마법사 사용  
 정확도 차트를 만들려면 기존 데이터 마이닝 구조를 참조해야 합니다. 해당 구조를 기반으로 같은 내용을 예측하는 여러 모델의 정확도를 측정할 수 있습니다.  
  
 구조를 사용할 수 있는지 잘 모르는 경우 서버를 찾아볼 수 있습니다. 자세한 내용은 [데이터 마이닝 추가 기능&#41;SQL Server Excel에서 모델 찾아보기 &#40;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)를 참조 하세요.  
  
#### <a name="to-create-an-accuracy-chart"></a>정확도 차트를 만들려면  
  
1.  **데이터 마이닝 클라이언트** 리본을 클릭 합니다.  
  
2.  **정확도 및 유효성 검사** 그룹에서 **정확도 차트**를 클릭 합니다.  
  
3.  **구조 또는 모델 선택** 대화 상자에서 평가 하려는 모델을 선택 합니다. **다음**을 클릭합니다.  
  
    > [!NOTE]  
    >  테스트하려는 데이터와 가장 일치하는 모델을 선택해야 합니다.  
  
4.  **예측할 열과 예측할 값 지정** 대화 상자에서 예측할 열과 대상 값 (해당 하는 경우)을 선택 합니다. **다음**을 클릭합니다.  
  
     예를 들어 위 예에서는 고객 응답을 모델링하는 열을 선택하고 대상 값을 "구입 가능성 있음"으로 지정할 수 있습니다.  
  
    > [!NOTE]  
    >  연속 값은 예측할 수 없지만 값을 불연속 범위로 분리하여 해당 열을 불연속화할 수 있습니다. 열 불연속화는 데이터 마이닝 모델을 만들기 전에 수행해야 합니다.  
  
5.  **원본 데이터 선택** 대화 상자에서 예측을 만들기 위해 모델을 통해 전달 되는 데이터의 원본을 지정 합니다.  
  
6.  모델에 저장 된 테스트 데이터가 아닌 외부 데이터 원본을 사용 하는 경우 **관계 지정** 대화 상자에서 새 원본 데이터의 열을 데이터 마이닝 모델에 사용 된 열에 매핑합니다.  
  
     열 이름이 비슷한 경우 마법사가 자동으로 매핑합니다. 입력 데이터에 분석과 관계없는 무시할 수 있는 열이 일부 포함되어 있는 경우에도 데이터 마이닝 모델이 입력을 처리하려면 해당 열이 필요합니다. 이러한 열에는 트랜잭션 ID, 대상 값 또는 예측에 사용된 열이 있습니다. 필요한 열을 매핑하지 못하면 마법사가 경고 메시지를 표시합니다.  
  
7.  **Finish**를 클릭합니다.  
  
     마법사에서 리프트 차트 및 기본 데이터를 포함하는 보고서를 만듭니다.  
  
### <a name="requirements"></a>요구 사항  
 불연속 값을 예측하는 경우 예측할 대상 값을 선택해야 합니다. 예를 들어 데이터가 "예: 구입"을 1로 분류 하 고 응답을 "아니요: 구매 하지 않음"으로 2로 분류 하는 경우에는 1 또는 2를 예측 값으로 지정 해야 합니다. 그러나 값 범위를 예측하는 경우 값을 한 번에 두 개만 비교할 수 있습니다. 예를 들어 5 보다 큰 점수를 예측 하려는 경우 원본 데이터를 레이블 재지정 하 고 결과를 두 개의 집합으로 구분 하는 새 모델을 만들어야 합니다. 5 보다 크고 5 보다 작은 값을 반환 합니다. 그런 다음 이러한 두 그룹의 정확도 비교할 수 있습니다.  
  
## <a name="understanding-accuracy"></a>정확도 이해  
 예측 가능한 열의 상태를 지정하는 차트 종류와 상태를 지정하지 않는 차트 종류를 만들 수 있습니다.  
  
 예측 가능한 열의 상태를 지정하는 경우 차트의 X축은 예측을 비교하는 데 사용되는 테스트 데이터 세트의 비율을 나타냅니다. 차트의 Y축은 지정한 상태로 예측되는 값의 비율을 나타냅니다.  
  
 예측 가능한 열의 상태를 지정하지 않는 경우에는 가능한 모든 예측에 대해 모델의 정확도가 차트에 표시됩니다.  
  
 리프트 차트 작업 방법과 무작위 및 이상적인 예측 선을 기반으로 정확도를 계산하는 방법은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 "리프트 차트" 항목을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
