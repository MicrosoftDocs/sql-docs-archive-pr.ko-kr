---
title: 모델링 플래그 확인 또는 변경 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf0edd827321685a2d6a9041759328a7ac6e7cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733324"
---
# <a name="view-or-change-modeling-flags-data-mining"></a>모델링 플래그 확인 또는 변경(데이터 마이닝)
  모델링 플래그는 알고리즘이 분석 중에 데이터를 처리하는 방법을 제어하기 위해 마이닝 구조 열이나 마이닝 모델 열에 대해 설정하는 속성입니다.  
  
 데이터 마이닝 디자이너에서 구조 또는 모델의 속성을 확인하여 마이닝 구조 또는 마이닝 열과 관련된 모델링 플래그를 확인하고 수정할 수 있습니다. DMX, AMO 또는 XMLA를 사용하여 모델링 플래그를 설정할 수도 있습니다.  
  
 이 절차에서는 디자이너에서 모델링 플래그를 변경하는 방법에 대해 설명합니다.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>구조 열 또는 모델 열에 대한 모델링 플래그 확인 또는 변경  
  
1.  SQL Server Design Studio에서 솔루션 탐색기를 열고 마이닝 구조를 두 번 클릭합니다.  
  
2.  NOT NULL 모델링 플래그를 설정 하려면 **마이닝 구조** 탭을 클릭 합니다. 회귀 변수 또는 MODEL_EXISTENCE_ONLY 플래그를 설정 하려면 **마이닝 모델** 탭을 클릭 합니다.  
  
3.  확인하거나 변경할 열을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
4.  새 모델링 플래그를 추가하려면 **ModelingFlags** 속성 옆에 있는 입력란을 클릭한 다음 사용하려는 모델링 플래그에 대한 확인란을 선택합니다.  
  
     모델링 플래그는 열 데이터 형식에 적합할 경우에만 표시됩니다.  
  
    > [!NOTE]  
    >  모델링 플래그를 변경한 후에는 모델을 다시 처리해야 합니다.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>모델에 사용되는 모델링 플래그 가져오기  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 DMX 쿼리 창을 열고 다음과 같은 쿼리를 입력합니다.  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md)   
 [모델링 플래그&#40;데이터 마이닝&#41;](modeling-flags-data-mining.md)  
  
  
