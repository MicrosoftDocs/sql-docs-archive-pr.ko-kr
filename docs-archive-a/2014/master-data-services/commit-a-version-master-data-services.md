---
title: 버전 커밋(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731859"
---
# <a name="commit-a-version-master-data-services"></a>버전 커밋(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델의 멤버 및 특성이 변경되지 않게 하려면 모델의 버전을 커밋합니다. 커밋된 버전의 잠금은 해제할 수 없습니다.  
  
## <a name="prerequisites"></a>필수 조건  
 이 절차를 수행하려면  
  
-   **버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.  
  
-   버전의 상태가 **잠금**이어야 합니다. 자세한 내용은 [버전 잠금&#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)를 참조하세요.  
  
-   모든 멤버가 유효성 검사를 통과해야 합니다.  
  
### <a name="to-commit-a-version"></a>버전을 커밋하려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.  
  
2.  **버전 관리** 페이지의 메뉴 모음에서 **버전 유효성 검사**를 클릭합니다.  
  
3.  **버전 유효성 검사** 페이지에서 커밋하려는 모델과 버전을 선택합니다.  
  
4.  **커밋**을 클릭합니다.  
  
5.  확인 대화 상자에서 **확인**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
  
-   [버전 플래그 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [버전에 플래그 할당&#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [버전 복사&#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>참고 항목  
 [버전&#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
  
