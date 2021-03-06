---
title: '4 단원: DMX를 사용 하 여 시계열 예측 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727496"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>4단원: DMX를 사용하여 시계열 예측 만들기
  이 단원과 다음 단원에서는 [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) 및 [Lesson 2: Adding Mining Models to the Time Series Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)에서 만든 시계열 모델을 기반으로 DMX(Data Mining Extensions)를 사용하여 여러 가지 유형의 예측을 만듭니다.  
  
 시계열 모델을 사용하면 여러 가지 방법으로 예측을 만들 수 있습니다.  
  
-   마이닝 모델의 기존 패턴 및 데이터 사용  
  
-   마이닝 모델의 기존 패턴을 사용하지만 새 데이터 제공  
  
-   모델에 새 데이터 추가 또는 모델 업데이트  
  
 이러한 예측 유형을 만드는 구문은 아래에 요약되어 있습니다.  
  
 기본 시계열 예측  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) 를 사용 하 여 학습 된 마이닝 모델에서 지정 된 수의 예측을 반환 합니다.  
  
 예를 들어 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) 또는 [시계열 모델 쿼리 예제](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)를 참조 하세요.  
  
 EXTEND_MODEL_CASES  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) 을 EXTEND_MODEL_CASES 인수와 함께 사용 하 여 새 데이터를 추가 하 고, 계열을 확장 하 고, 업데이트 된 마이닝 모델을 기반으로 예측을 만들 수 있습니다.  
  
 이 자습서에는 EXTEND_MODEL_CASES를 사용하는 방법에 대한 예가 포함되어 있습니다.  
  
 REPLACE_MODEL_CASES  
 REPLACE_MODEL_CASES 인수와 함께 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) 를 사용 하 여 원래 데이터를 새 데이터 계열로 바꾼 다음 마이닝 모델의 패턴을 새 데이터 계열에 적용 하는 방법에 따라 예측을 만듭니다.  
  
 REPLACE_MODEL_CASES를 사용 하는 방법에 대 한 예제는 [2 단원: &#40;중급 데이터 마이닝 자습서&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)를 참조 하세요.  
  
## <a name="lesson-tasks"></a>단원 태스크  
 이 단원에서는 다음 태스크를 수행합니다.  
  
-   쿼리를 만들어 기존 데이터를 기반으로 기본 예측을 얻습니다.  
  
 후속 단원에서는 다음 관련 태스크를 수행합니다.  
  
-   쿼리를 만들어 새 데이터를 제공하고 업데이트된 예측을 얻습니다.  
  
 DMX를 사용하여 수동으로 쿼리를 만들 수 있지만 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 예측 쿼리 작성기를 사용하여 예측을 만들 수도 있습니다.  
  
## <a name="simple-time-series-prediction-query"></a>간단한 시계열 예측 쿼리  
 첫 번째 단계는 `SELECT FROM` 문을 `PredictTimeSeries` 함수와 함께 사용하여 시계열 예측을 만드는 것입니다. 시계열 모델은 예측을 만드는 간단한 구문을 지원합니다. 입력을 제공할 필요 없이 만들 예측 수만 지정하면 됩니다. 다음은 사용하게 될 문의 일반적인 예입니다.  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 Select 목록에는 예측을 만드는 데 사용할 제품 라인의 이름과 같이 모델의 열이 포함 될 수 있으며, 시계열 마이닝 모델에 대 한 [PredictTimeSeries &#40;dmx&#41;또는 dmx&#41;](/sql/dmx/predicttimeseries-dmx) [&#40;](/sql/dmx/lag-dmx) 와 같은 예측 함수도 포함 될 수 있습니다.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>간단한 시계열 예측 쿼리를 만들려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.  
  
     비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.  
  
2.  문의 일반적인 예를 빈 쿼리에 복사합니다.  
  
3.  다음 내용을  
  
    ```  
    <select list>   
    ```  
  
     다음으로 바꿉니다.  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     첫 번째 줄에서는 마이닝 모델에서 계열을 식별하는 값을 검색합니다.  
  
     두 번째 및 세 번째 줄에서는 `PredictTimeSeries` 함수를 사용합니다. 각 줄에서는 `[Quantity]` 또는 `[Amount]`등 서로 다른 특성을 예측합니다. 예측 가능한 특성 이름 뒤의 숫자는 예측할 시간 단계 수를 지정합니다.  
  
     `AS` 절은 각 예측 함수에 의해 반환되는 열에 이름을 제공하는 데 사용됩니다. 별칭을 제공하지 않으면 기본적으로 두 열 모두 레이블 `Expression`이 지정되어 반환됩니다.  
  
4.  다음 내용을  
  
    ```  
    [<mining model>]   
    ```  
  
     다음으로 바꿉니다.  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  다음 내용을  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     다음으로 바꿉니다.  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     이제 전체 문이 다음과 같아야 합니다.  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  **파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.  
  
7.  다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `SimpleTimeSeriesPrediction.dmx` 합니다.  
  
8.  도구 모음에서 **실행** 단추를 클릭합니다.  
  
     쿼리가 `WHERE` 절에 지정된 제품 및 지역의 두 조합 각각에 대해 6개의 예측을 반환합니다.  
  
 다음 단원에서는 모델에 새 데이터를 제공하는 쿼리를 만들고 예측 결과를 방금 만든 쿼리와 비교합니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [5단원: 시계열 모델 확장](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>참고 항목  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)   
 [DMX &#40;DMX&#41;](/sql/dmx/lag-dmx)   
 [시계열 모델 쿼리 예제](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
