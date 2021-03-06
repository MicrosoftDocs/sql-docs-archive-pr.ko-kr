---
title: 테이블의 데이터 필터링 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f4003457df4068713e75e6bb5c0ab78c15ac03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728839"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>테이블의 데이터 필터링(SSAS 테이블 형식)
  데이터를 가져올 때 필터를 적용하여 테이블에 로드되는 행을 제어할 수 있습니다. 데이터를 가져온 후에는 개별 행을 삭제할 수 없습니다. 그러나 사용자 지정 필터를 적용하여 행이 표시되는 방식을 제어할 수 있습니다. 필터링 조건을 충족하지 않는 행은 숨겨집니다. 하나 이상의 열을 기준으로 필터링할 수 있습니다. 필터는 가산적이므로 현재 필터를 기준으로 필터를 추가할 때마다 데이터의 하위 집합이 줄어듭니다.  
  
> [!NOTE]  
>  필터 미리 보기 창에서는 표시되는 서로 다른 값의 수가 제한됩니다. 제한을 초과하는 경우 메시지가 표시됩니다.  
  
### <a name="to-filter-data-based-on-column-values"></a>열 값을 기준으로 데이터를 필터링하려면  
  
1.  모델 디자이너에서 테이블을 선택한 다음 필터링 기준으로 사용할 열의 머리글에 있는 화살표를 클릭합니다.  
  
2.  자동 필터 메뉴에서 다음 중 하나를 수행합니다.  
  
    -   열 값 목록에서 필터링 기준으로 하나 이상의 값을 선택 하거나 선택을 취소 한 다음 **확인**을 클릭 합니다.  
  
         값의 수가 너무 많은 경우 개별 항목이 목록에 표시되지 않을 수 있습니다. 대신 "표시할 항목이 너무 많음"이라는 메시지가 나타납니다.  
  
    -   열 형식에 따라 **숫자 필터** 또는 **텍스트 필터** 를 클릭 한 다음 비교 연산자 명령 (예: **Equals**) 중 하나을 클릭 하거나 **사용자 지정 필터**를 클릭 합니다. **사용자 지정 필터** 대화 상자에서 필터를 만든 다음 **확인**을 클릭합니다.  
  
### <a name="to-clear-a-filter-for-a-column"></a>열에 대한 필터를 지우려면  
  
1.  필터를 지우려는 열의 머리글에 있는 화살표를 클릭합니다.  
  
2.  **필터 지우기를 \<Column Name> **클릭 합니다.  
  
### <a name="to-clear-all-filters-for-a-table"></a>테이블에 대한 필터를 모두 지우려면  
  
1.  모델 디자이너에서 필터를 지우려는 테이블을 선택합니다.  
  
2.  **열** 메뉴에서 **필터 모두 지우기**를 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SSAS 테이블 형식&#41;&#40;데이터 필터링 및 정렬](../filter-and-sort-data-ssas-tabular.md)   
 [SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md)   
 [역할&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)  
  
  
