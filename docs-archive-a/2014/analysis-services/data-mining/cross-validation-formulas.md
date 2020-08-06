---
title: 교차 유효성 검사 수식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 878d88f695b2cdbf3c999c54568304accc54e3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649843"
---
# <a name="cross-validation-formulas"></a>교차 유효성 검사 수식
  교차 유효성 검사 보고서를 생성하면 마이닝 모델의 유형(모델을 만드는 데 사용된 알고리즘), 예측 가능한 특성의 데이터 형식 및 예측 가능한 특성 값(있는 경우)에 따라 각 모델에 대한 정확도 측정값이 포함됩니다.  
  
 이 섹션에서는 교차 유효성 검사 보고서에 사용되는 측정값을 보여 주고 해당 계산 방법에 대해 설명합니다.  
  
 모델 유형별 정확도 측정값을 분석하는 방법은 [교차 유효성 검사 보고서의 측정값](measures-in-the-cross-validation-report.md)을 참조하세요.  
  
## <a name="formulas-used-for-cross-validation-measures"></a>교차 유효성 검사 측정값에 사용되는 수식  
  
> [!NOTE]  
>  **중요:** 이러한 정확도 측정값은 각 대상 특성에 대해 계산됩니다. 각 특성에 대해 대상 값을 지정하거나 생략할 수 있습니다. 데이터 집합의 사례에 대상 특성의 값이 없는 경우 이러한 사례는 *누락 값*이라는 특수한 값을 가지고 있는 것으로 간주됩니다. 값이 누락된 행은 특정 대상 특성에 대한 정확도 측정값을 계산할 때 계산되지 않습니다. 점수는 각 특성에 대해 개별적으로 계산되므로 대상 특성의 값은 있지만 다른 특성의 값은 누락된 경우 대상 특성의 점수가 영향을 받지 않습니다.  
  
|측정값|적용 대상|구현|  
|-------------|----------------|--------------------|  
|**참 긍정**|불연속 특성(값이 지정됨)|다음 조건을 충족하는 사례의 수입니다.<br /><br /> 사례에 대상 값이 포함되어 있습니다.<br /><br /> 사례에 대상 값이 포함되어 있을 것으로 모델이 예측했습니다.|  
|**True Negative(TN)**|불연속 특성(값이 지정됨)|다음 조건을 충족하는 사례의 수입니다.<br /><br /> 사례에 대상 값이 포함되어 있지 않습니다.<br /><br /> 사례에 대상 값이 포함되어 있지 않을 것으로 모델이 예측했습니다.|  
|**거짓 긍정**|불연속 특성(값이 지정됨)|다음 조건을 충족하는 사례의 수입니다.<br /><br /> 실제 값이 대상 값과 같습니다.<br /><br /> 사례에 대상 값이 포함되어 있을 것으로 모델이 예측했습니다.|  
|**False Negative(FN)**|불연속 특성(값이 지정됨)|다음 조건을 충족하는 사례의 수입니다.<br /><br /> 실제 값이 대상 값과 같지 않습니다.<br /><br /> 사례에 대상 값이 포함되어 있지 않을 것으로 모델이 예측했습니다.|  
|**통과/실패**|불연속 특성(지정된 대상 없음)|다음 조건을 충족하는 사례의 수입니다.<br /><br /> 확률이 가장 높은 예측 상태가 입력 상태와 같고 확률이 **상태 임계값**의 값보다 크면 통과합니다.<br /><br /> 그렇지 않으면 실패합니다.|  
|**들어**|불연속 특성. 대상 값을 지정할 수 있지만 대상 값이 필수 항목은 아닙니다.|대상 특성 값을 가지며 각 사례의 로그 유사도가 Log(ActualProbability/MarginalProbability)로 계산되는 모든 행의 평균 로그 유사도. 로그 유사도 값의 합계를 입력 데이터 세트의 행 수로 나누어 평균을 계산하며, 이때 대상 특성 값이 누락된 행은 제외됩니다.<br /><br /> 리프트는 양수 또는 음수일 수 있습니다. 양수 값은 임의 추측보다 뛰어난 효과적인 모델을 의미합니다.|  
|**로그 점수**|불연속 특성. 대상 값을 지정할 수 있지만 대상 값이 필수 항목은 아닙니다.|합한 다음, 입력 데이터 세트의 행 수로 나눈 각 사례에 대한 실제 확률의 로그로, 대상 특성 값이 누락된 행은 제외됩니다.<br /><br /> 확률이 소수 부분으로 표현되므로 로그 점수는 항상 음수입니다. 0에 가까운 점수일수록 좋은 점수입니다.|  
|**사례 유사도**|클러스터|파티션의 사례 수로 나눈 모든 파티션 사례에 대한 클러스터 유사도 점수의 합계로, 대상 특성 값이 누락된 행은 제외됩니다.|  
|**절대 평균 오차**|연속 특성|파티션의 사례 수로 나눈 파티션의 모든 사례에 대한 절대 오차의 합계입니다.|  
|**제곱 평균 오차**|연속 특성|파티션에 대한 제곱 평균 오차의 제곱근|  
|**평균 제곱 오차**|불연속 특성. 대상 값을 지정할 수 있지만 대상 값이 필수 항목은 아닙니다.|파티션의 사례 수로 나눈 확률 점수의 보수에 대한 제곱 평균의 제곱근으로, 대상 특성 값이 누락된 행은 제외됩니다.|  
|**평균 제곱 오차**|불연속 특성(지정된 대상 없음)|파티션의 사례 수로 나눈 확률 점수의 보수에 대한 제곱 평균의 제곱근으로, 대상 특성 값이 누락된 사례는 제외됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 마이닝&#41;&#40;테스트 및 유효성 검사](testing-and-validation-data-mining.md)   
 [교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;](cross-validation-analysis-services-data-mining.md)  
  
  