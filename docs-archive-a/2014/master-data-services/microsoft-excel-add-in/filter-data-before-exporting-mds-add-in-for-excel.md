---
title: 로드 하기 전에 데이터 필터링 (Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d0ccf667f37763326e27dcd8d0cfc005627ebc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731800"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a>로드하기 전 데이터 필터링(Excel용 MDS 추가 기능)
  에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] Excel로 로드 하는 데이터의 크기나 범위를 제한 하려는 경우 데이터를 필터링 합니다.  
  
## <a name="prerequisites"></a>필수 조건  
 이 절차를 수행하려면  
  
-   **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
### <a name="to-filter-data-before-loading"></a>로드하기 전에 데이터를 필터링하려면  
  
1.  Excel을 열고 **마스터 데이터** 탭에서 MDS 저장소에 연결합니다. 자세한 내용은 [MDS 리포지토리에 연결&#40;Excel용 MDS 추가 기능&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)을 참조하세요.  
  
2.  **마스터 데이터 탐색기** 창에서 모델 및 버전을 선택합니다. 엔터티 목록이 채워집니다.  
  
    -   **마스터 데이터 탐색기** 창이 표시되지 않으면 **연결 및 로드** 그룹에서 **탐색기 표시**를 클릭합니다.  
  
    -   **마스터 데이터 탐색기** 창이 해제되어 있으면 기존 시트에 이미 MDS 관리 데이터가 포함되어 있기 때문입니다. 창을 활성화하려면 새 워크시트를 엽니다.  
  
3.  **마스터 데이터 탐색기** 창의 엔터티 목록에서 필터링하려는 엔터티를 클릭합니다.  
  
4.  리본 메뉴의 **연결 및 로드** 그룹에서 **필터**를 클릭합니다.  
  
5.  표시할 특성(열)을 선택하여 **필터** 대화 상자를 완료하여 열 순서를 설정하고 필요한 경우 더 적은 행이 반환되도록 데이터를 필터링합니다. **요약** 창에서 반환된 데이터의 양을 확인합니다. 자세한 내용은 [필터 대화 상자&#40;Excel용 MDS 추가 기능&#41;](filter-dialog-box-mds-add-in-for-excel.md)를 참조하세요.  
  
6.  **데이터 로드**를 클릭합니다. 시트에 MDS 관리 데이터가 채워집니다.  
  
    > [!NOTE]  
    >  -   처음 100만 개의 멤버만 Excel에 로드됩니다.  
    > -   제한 된 목록 (도메인 기반 특성)에는 처음 1000 값만 로드 됩니다.  
  
## <a name="next-steps"></a>다음 단계  
 [Excel의 데이터를 MDS &#40;Excel용 MDS 추가 기능에 게시&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>참고 항목  
 [데이터 &#40;Excel용 MDS 추가 기능&#41;로드](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [필터 대화 상자 &#40;Excel용 MDS 추가 기능&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [열 순서 바꾸기&#40;Excel용 MDS 추가 기능&#41;](reorder-columns-mds-add-in-for-excel.md)  
  
  
