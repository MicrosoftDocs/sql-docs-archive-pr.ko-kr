---
title: 데이터 원본 뷰에서 데이터 탐색 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661374"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>데이터 원본 뷰에서 데이터 탐색(Analysis Services)
  **의 데이터 원본 뷰 디자이너에 있는** 데이터 탐색 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 DSV(데이터 원본 뷰)에서 테이블, 뷰 또는 명명된 쿼리의 데이터를 찾아볼 수 있습니다. 데이터 원본 뷰 디자이너에서 데이터를 탐색하면 선택한 테이블, 뷰 또는 명명된 쿼리에 있는 각 데이터 열의 내용을 볼 수 있습니다. 실제 내용을 보면 모든 열이 필요한지 여부, 사용자에게 친숙함과 유용성을 높이기 위해 명명된 계산이 필요한지 여부 및 기존의 명명된 계산이나 명명된 쿼리에서 예상된 값을 반환하는지 여부를 확인할 수 있습니다.  
  
 데이터를 보려면 DSV에서 선택한 개체의 데이터 원본에 대한 활성 연결이 있어야 합니다. 테이블에 있는 모든 명명된 계산도 쿼리에서 전송됩니다.  
  
 데이터는 정렬하고 복사할 수 있는 테이블 형식으로 반환됩니다. 해당 열을 기준으로 행을 재정렬하려면 열 머리글을 클릭합니다. 또한 표에서 데이터를 강조 표시하고 Ctrl+C를 눌러 선택 내용을 클립 보드로 복사할 수 있습니다.  
  
 샘플 방법과 샘플 개수를 제어할 수도 있습니다. 기본적으로 상위 5000갱의 행이 반환됩니다.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>데이터를 검색하거나 샘플링 옵션을 변경하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 프로젝트를 열거나 데이터를 찾아볼 데이터 원본 뷰를 포함하는 데이터베이스에 연결합니다.  
  
2.  솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.  
  
3.  확인할 데이터가 포함된 테이블, 뷰 또는 명명된 쿼리를 마우스 오른쪽 단추로 클릭한 다음 **데이터 탐색**을 클릭합니다.  
  
     데이터 원본 뷰의 테이블, 뷰 또는 명명 된 쿼리를 기반으로 하는 데이터 원본은 쿼리이 고 결과는 ** \<object name> 테이블 탐색** 탭에 나타납니다.  
  
4.  ** \<object name> 테이블 탐색** 도구 모음에서 **샘플링 옵션** 아이콘을 클릭 합니다.  
  
     **데이터 탐색 옵션** 대화 상자가 열립니다. 이 대화 상자에서 샘플링 방법(기본 샘플링 크기인 5000행보다 많거나 적은 레코드) 또는 샘플 개수를 지정할 수 있습니다.  
  
5.  필요에 따라 **확인** 또는 **취소** 를 클릭합니다.  
  
6.  데이터를 다시 샘플링 하려면 ** \<object name> 테이블 탐색** 도구 모음에서 **데이터 다시 샘플링** 을 클릭 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md)  
  
  
