---
title: 통합 사용 권한 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4c93e74acc84d6e742139263bedc011c4028efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661705"
---
# <a name="consolidated-permissions-master-data-services"></a>통합 사용 권한(Master Data Services)
  통합 사용 권한은 엔터티의 모든 통합 멤버에 대한 특성 값에 적용됩니다.  
  
 통합 사용 권한은 명시적 계층 및 컬렉션을 사용할 수 있는 엔터티에만 적용됩니다.  
  
 **참고:**  
  
-   리프 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.  
  
-   **이름** 및 **코드** 특성에 할당된 사용 권한은 적용되지 않습니다.  
  
|사용 권한|Description|  
|----------------|-----------------|  
|**읽기 전용**|통합 멤버가 표시되지만 사용자가 이를 추가, 제거 또는 변경할 수 없습니다.|  
|**Update**|통합 멤버가 표시되고 사용자가 이를 추가, 제거 및 변경할 수 있습니다.|  
|**Deny**|엔터티의 통합 멤버가 표시되지 않습니다.|  
  
## <a name="attribute-permissions"></a>특성 사용 권한  
 특성 사용 권한은 특정 엔터티의 특성 값에 적용됩니다. 특성 사용 권한만 있는 사용자는 멤버를 추가하거나 제거할 수 없습니다.  
  
|사용 권한|Description|  
|----------------|-----------------|  
|**읽기 전용**|특성이 표시되지만 사용자가 특성 값을 변경할 수 없습니다.|  
|**Update**|특성이 표시되고 사용자가 특성 값을 변경할 수 있습니다.|  
|**Deny**|특성이 표시되지 않습니다.<br /><br /> 참고: 이름 및 코드 특성에 대한 액세스를 명시적으로 거부할 수 없습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](assign-model-object-permissions-master-data-services.md)   
 [리프 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [특성&#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
