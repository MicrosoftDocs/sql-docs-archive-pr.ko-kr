---
title: 리프 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738463"
---
# <a name="leaf-permissions-master-data-services"></a>리프 권한(Master Data Services)
  리프 권한은 엔터티의 모든 리프 멤버에 대한 특성 값에 적용됩니다.  
  
 명시적 계층이 설정되지 않은 엔터티의 경우 **리프** 에 사용 권한을 할당하는 것은 엔터티에 사용 권한을 할당하는 것과 같습니다.  
  
 **참고:**  
  
-   리프 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.  
  
-   **이름** 및 **코드** 특성에 할당된 사용 권한은 적용되지 않습니다.  
  
|사용 권한|설명|  
|----------------|-----------------|  
|**읽기 전용**|리프 멤버가 표시되지만 사용자가 이를 추가, 제거 또는 변경할 수 없습니다.<br /><br /> 통합 멤버가 있는 경우 Name 및 Code가 표시되지만 사용자는 이를 추가, 제거 또는 변경할 수 없습니다.|  
|**Update**|리프 멤버가 표시되고 사용자가 이를 추가, 제거 및 변경할 수 있습니다.<br /><br /> 통합 멤버가 있는 경우 Name 및 Code가 표시되지만 사용자는 이를 추가, 제거 또는 변경할 수 없습니다.|  
|**Deny**|엔터티의 리프 멤버가 표시되지 않습니다.|  
  
## <a name="attribute-permissions"></a>특성 사용 권한  
 특성 사용 권한은 특정 엔터티의 특성 값에 적용됩니다. 특성 사용 권한만 있는 사용자는 멤버를 추가하거나 제거할 수 없습니다.  
  
|사용 권한|설명|  
|----------------|-----------------|  
|**읽기 전용**|특성이 표시되지만 사용자가 특성 값을 변경할 수 없습니다.|  
|**Update**|특성이 표시되고 사용자가 특성 값을 변경할 수 있습니다.|  
|**Deny**|특성이 표시되지 않습니다.<br /><br /> 참고: 이름 및 코드 특성에 대한 액세스를 명시적으로 거부할 수 없습니다.|  
  
### <a name="example"></a>예제  
 Product 엔터티에 대해 Subcategory 특성에 **업데이트** 권한을 할당합니다. 모든 다른 특성에 대한 사용 권한은 거부합니다.  
  
|이름|코드|Subcategory(업데이트)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5}산악 자전거|  
|Mountain-100|BK-M201|{5}산악 자전거|  
  
 **탐색기**에서 Subcategory 열의 특성 값을 업데이트할 수 있습니다. 특성에 대한 사용 권한이 없는 경우에는 해당 특성이 표시되지 않습니다.  
  
> [!NOTE]  
>  이 예에서 Subcategory는 SubcategoryList 엔터티를 기반으로 하는 도메인 기반 특성입니다. Mountain-100에 대해 다른 Subcategory를 선택할 수 있지만 SubcategoryList 엔터티에서 멤버를 추가하거나 삭제할 수는 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](assign-model-object-permissions-master-data-services.md)   
 [MDS(Master Data Services)&#41;&#40;통합 된 사용 권한](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [특성&#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
