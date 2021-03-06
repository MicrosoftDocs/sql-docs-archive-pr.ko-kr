---
title: 모델 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651075"
---
# <a name="model-permissions-master-data-services"></a>모델 권한(Master Data Services)
  모델 권한은 모델 내의 모든 엔터티, 파생 계층, 명시적 계층 및 컬렉션에 적용됩니다. 모델에 할당된 사용 권한은 개별 개체에 대해 재정의할 수 있습니다.  
  
> [!NOTE]  
>  사용자가 모델 관리자인 경우 사용자 인터페이스의 모든 기능 영역에 모델이 표시됩니다. 그렇지 않은 경우에는 **탐색기** 기능 영역에만 모델이 표시됩니다. 자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.  
  
|사용 권한|Description|  
|----------------|-----------------|  
|**읽기 전용**|**탐색기**에서 모델이 표시 되지만 사용자가 멤버를 추가 하거나 제거할 수 없으며 특성 값, 계층 멤버 자격 또는 컬렉션 멤버 자격을 업데이트할 수 없습니다.|  
|**Update**|**탐색기**에 모델이 표시 되 고 사용자가 멤버를 추가 및 제거 하 고, 특성 값, 계층 멤버 자격 및 컬렉션 멤버 자격을 업데이트할 수 있습니다.|  
|**Deny**|모델이 표시되지 않습니다.|  
  
 모델에 사용 권한을 할당하면 사용자가 모델의 모든 버전에 액세스할 수 있습니다. 개별 버전에는 사용 권한을 할당할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [엔터티 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [컬렉션 권한&#40;Master Data Services&#41;](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
