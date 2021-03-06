---
title: 디자인 창 (마이닝 모델 예측 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32ac73a2d6fde38d15d1f45a8439293695749ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733276"
---
# <a name="design-pane-mining-model-prediction-view"></a>디자인 창(마이닝 모델 예측 뷰)
  **디자인** 창에는 데이터 마이닝 예측을 작성할 때 사용할 수 있는 예측 쿼리 작성기가 있습니다. 데이터 원본 뷰에서 입력 데이터의 테이블을 사용하는 예측 쿼리를 디자인하여 대량 예측을 생성하거나 개별 값을 제공할 수 있는 단일 예측 쿼리를 만들 수 있습니다.  
  
 쿼리를 실행하고 결과를 보려면 쿼리 결과 뷰로 전환합니다.  
  
 **쿼리** 뷰에는 예측 쿼리 작성기에서 만드는 DMX(Data Mining Extensions) 쿼리가 표시됩니다. DMX에 익숙하면 이 쿼리를 사용자 지정할 수 있습니다.  
  
> [!NOTE]  
>  쿼리를 수동으로 변경한 경우 디자인 뷰로 다시 전환하면 변경 내용이 손실됩니다. DMX 쿼리를 저장하려면 쿼리를 Windows 클립보드로 복사한 다음 텍스트 파일에 붙여 넣으면 됩니다.  
  
 **참조 항목:** [데이터 마이닝 쿼리](data-mining/data-mining-queries.md)  
  
## <a name="options"></a>옵션  
 **쿼리 결과 뷰로 전환**  
 **디자인**, **쿼리**및 **결과** 창 사이를 전환하려면 클릭합니다. **결과** 창으로 전환하면 쿼리가 실행됩니다.  
  
 **쿼리 결과 저장**  
 **데이터 마이닝 쿼리 결과 저장** 대화 상자를 엽니다.  
  
 **단일 쿼리**  
 알려진 데이터의 원본으로 테이블을 제공하는 대신 쿼리에 대한 값을 직접 제공할 수 있는 단일 쿼리를 만들 수 있습니다. **입력 테이블 선택** 테이블이 **단일 쿼리 입력** 테이블로 바뀝니다.  
  
 **쿼리 결과 새로 고침**  
 예측 쿼리를 다시 처리합니다. 이 옵션은 **결과** 창에서만 사용할 수 있습니다.  
  
 **마이닝 모델**  
 예측의 기반으로 하려고 선택한 마이닝 모델을 표시합니다.  
  
 **모델 선택**  
 **마이닝 모델 선택** 대화 상자를 엽니다.  
  
 **입력 테이블 선택**  
 예측의 기반이 되는 알려진 데이터를 포함하는 선택한 입력 테이블을 표시합니다.  
  
 **테이블 삭제**  
 선택한 테이블을 삭제합니다. 테이블이 없거나 테이블을 선택하지 않은 경우에는 이 단추를 사용할 수 없습니다.  
  
 **사례 테이블 선택**  
 **테이블 선택** 대화 상자를 엽니다. 이 단추는 사례 테이블을 선택하지 않은 경우에만 나타납니다.  
  
 **중첩 테이블 선택**  
 **테이블 선택** 대화 상자를 엽니다. 이 단추는 사례 테이블을 선택한 경우에만 나타납니다. 관련 마이닝 구조에 중첩 테이블이 없는 경우에는 이 단추를 사용할 수 없습니다.  
  
 **조인 수정**  
 **중첩 조인 지정** 대화 상자를 엽니다. 이 단추는 중첩 테이블을 선택한 경우에만 활성화됩니다.  
  
 **단일 쿼리 입력**  
 **단일 쿼리** 단추를 선택한 경우에 사용할 수 있습니다. 다음 열을 포함합니다.  
  
|값|설명|  
|-----------|-----------------|  
|**마이닝 모델 열**|**마이닝 모델** 테이블에서 선택한 마이닝 모델에 포함된 마이닝 모델 열을 나열합니다.|  
|**값**|선택한 마이닝 모델 열의 가능한 각 상태를 포함하는 목록에서 값을 선택합니다.<br /><br /> 열이 중첩 테이블 열인 경우 값 셀을 클릭하면 **중첩 테이블 입력** 대화 상자가 열립니다.|  
  
 **원본**  
 열에 사용할 필드를 포함하는 원본을 선택합니다. **마이닝 모델** 테이블에서 선택한 마이닝 모델, 입력 테이블 또는 **입력 테이블 선택** 테이블에서 선택한 테이블, 예측 함수 또는 사용자 지정 식을 사용할 수 있습니다.  
  
 마이닝 모델 및 입력 테이블을 포함하는 테이블에서 셀로 열을 끌 수 있습니다.  
  
 **필드**  
 원본 테이블에서 파생된 열 목록에서 열을 선택합니다. **원본** 에서 **예측 함수**를 선택한 경우 여기에는 선택한 마이닝 모델에 사용할 수 있는 예측 함수가 포함되어 있습니다.  
  
 **그룹**  
 **및/또는** 열과 함께 사용하여 식을 그룹화할 수 있습니다. 예들 들어 `(expr1 Or expr2) And expr3`입니다.  
  
 **및/또는**  
 논리적 쿼리를 만드는 데 사용합니다. 예들 들어 `(expr1 Or expr2) And expr3`입니다.  
  
 **조건/인수**  
 열에 적용되는 조건 또는 사용자 식을 지정합니다. 마이닝 모델 및 입력 테이블을 포함하는 테이블에서 셀로 열을 끌 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 마이닝 확장 &#40;DMX&#41; 문 참조](/sql/dmx/data-mining-extensions-dmx-statements)   
 [데이터 마이닝 쿼리 인터페이스](data-mining/data-mining-query-tools.md)   
 [예측 쿼리 작성기&#40;데이터 마이닝&#41;](prediction-query-builder-data-mining.md)  
  
  
