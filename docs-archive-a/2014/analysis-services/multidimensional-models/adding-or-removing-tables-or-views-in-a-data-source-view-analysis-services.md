---
title: 데이터 원본 뷰에서 테이블이 나 뷰 추가 또는 제거 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
author: minewiskan
ms.author: owend
ms.openlocfilehash: da1bc2b1ac0af7576cfe3c3593b451f78d6a9fae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660723"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>데이터 원본 뷰에서 테이블이나 뷰 추가 또는 제거(Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 데이터 원본 뷰(DSV)를 만든 후 데이터 원본 뷰 디자이너에서 다른 데이터 원본의 테이블과 열을 비롯하여 테이블 및 열을 추가하거나 제거해서 데이터 원본 뷰(DSV)를 수정할 수 잇습니다.  
  
 데이터 원본 뷰 디자이너에서 DSV를 열려면 솔루션 탐색기에서 DSV를 두 번 클릭합니다. DSV에서 열었으면 단추 모음이나 메뉴에서 **테이블 추가/제거** 명령을 사용하여 DSV를 수정하거나 확장할 수 있습니다. 다이어그램의 개체에 대한 작업을 할 수도 있습니다. 예를 들어 개체를 선택한 다음 키보드에서 Delete 키를 눌러 개체를 삭제할 수 있습니다.  
  
> [!WARNING]  
>  테이블을 제거할 때는 주의해야 합니다. 테이블을 제거하면 연관된 모든 열과 관계가 DSV에서 삭제되고 해당 테이블에 바인딩된 모든 개체가 무효화됩니다.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>추가 또는 제거할 테이블이나 뷰 선택  
 **테이블 추가/제거** 대화 상자를 사용하여 **사용 가능한 개체** 와 **포함된 개체** 목록 사이에서 테이블 또는 뷰를 이동할 수 있습니다. 처음에는 **사용 가능한 개체** 목록에 현재 데이터 원본 뷰에 없는 주 데이터 원본의 모든 테이블 또는 뷰가 포함됩니다. 주 데이터 원본에서 `OPENROWSET` 함수를 사용할 수 있는 경우에는 같은 프로젝트 또는 데이터베이스 내에 있는 다른 데이터 원본의 테이블이나 뷰도 추가할 수 있습니다.  
  
 DSV에 테이블을 추가하거나 DSV에서 테이블을 제거하면 DSV에서 현재 선택된 다이어그램에서도 테이블이 추가되거나 제거됩니다. 다이어그램에 대한 자세한 내용은 [데이터 원본 뷰 디자이너에서의 다이어그램 작업&#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)을 참조하세요.  
  
 **테이블 추가/제거** 대화 상자의 **포함된 개체** 목록에 테이블을 이동한 다음에는 모든 관련 테이블을 추가할 수 있습니다. 이 작업에서는 데이터 원본의 FOREIGN KEY 제약 조건(있는 경우)에 따라 테이블을 추가합니다. FOREIGN KEY 제약 조건이 없는 경우 데이터 원본 뷰의 `NameMatchingCriteria` 속성을 통해 관계 생성을 위한 테이블의 열 이름 일치 조건을 지정하여 관계를 결정할 수 있습니다. `NameMatchingCriteria`데이터 원본 뷰에 대해 속성이 지정 된 경우 **관련 테이블 추가** 를 클릭 하 여 열 이름이 일치 하는 데이터 원본의 테이블을 추가 합니다. 속성을 설정 하는 방법에 대 한 자세한 내용은 `NameMatchingCriteria` [다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md)를 참조 하세요.  
  
> [!NOTE]  
>  데이터 원본 뷰에서 개체를 추가 또는 제거해도 기본 데이터 원본에는 영향을 주지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md)   
 [데이터 원본 뷰 디자이너에서의 다이어그램 작업&#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
