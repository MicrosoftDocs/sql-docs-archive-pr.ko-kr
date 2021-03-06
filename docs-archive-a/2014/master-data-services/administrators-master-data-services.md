---
title: 관리자(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52e16d4e77acc0a6b50b87e00184918cb9ce64b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734240"
---
# <a name="administrators-master-data-services"></a>관리자(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에는 모델 관리자와 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자의 두 가지 관리자 유형이 있습니다.  
  
## <a name="model-administrators"></a>모델 관리자  
 에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 모델 관리자는 **모델 개체** 탭의 최상위 모델 개체에 할당 된 **업데이트** 권한이 있고 다른 할당 된 권한은 없는 사용자입니다.  
  
-   **탐색기** 기능 영역에 대한 액세스 권한을 가진 사용자는 이 영역에서 모든 마스터 데이터를 추가하고, 삭제하고, 업데이트할 수 있습니다.  
  
-   다른 기능 영역에 대한 액세스 권한을 가진 사용자는 해당 영역에서 사용할 수 있는 모든 관리 태스크를 수행할 수 있습니다.  
  
 각 모델은 여러 관리자를 가질 수 있습니다. 각 사용자는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 배포에서 한 개, 여러 개 또는 모든 모델에 대한 모델 관리자일 수 있습니다.  
  
 사용자는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에서 또는 프로그래밍 방식으로 모델 관리자로 구성될 수 있습니다. 자세한 내용은 [모델 관리자 만들기&#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)를 참조하세요.  
  
## <a name="master-data-services-system-administrator"></a>Master Data Services 시스템 관리자  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자는 한 명뿐입니다. 시스템 관리자는 데이터베이스를 만들 때 **관리자 계정** 에 대해 지정 된 사용자입니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자:  
  
-   모든 기능 영역에 대한 액세스 권한을 자동으로 가집니다.  
  
-   **탐색기** 기능 영역에서 모든 모델에 대 한 모든 마스터 데이터를 추가, 삭제 및 업데이트할 수 있습니다.  
  
 시스템 관리자로 할당된 사용자는 변경이 가능합니다. 자세한 내용은 [MDS(Master Data Services)&#41;&#40;시스템 관리자 계정 변경 ](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)을 참조 하세요.  
  
## <a name="comparing-administrator-types"></a>관리자 유형 비교  
  
|관리자 유형|Description|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 할당된 사용 권한은 관리자의 액세스 권한 아무런 영향을 주지 않습니다.<br /><br /> 모든 모델에 대 한 **업데이트** 권한이 자동으로 포함 됩니다.<br /><br /> 모든 기능 영역에 대한 액세스 권한을 자동으로 가집니다.<br /><br /> Mdm. tblUser에서 **ID** 열의 값은 **1**입니다.|  
|모델 관리자|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 할당된 권한에 따라 사용자가 모델 관리자인지 여부가 결정됩니다.<br /><br /> 명시적으로 할당된 사용 권한이나 그룹에서 상속된 사용 권한을 기반으로 하는 모델 관리자일 수 있습니다.<br /><br /> 는 최상위 모델 개체에 할당 된 **업데이트** 권한이 있고 다른 사용 권한은 없는 모델에 대 한 관리자만 해당 합니다.<br /><br /> 액세스 권한이 부여된 기능 영역에 대해서만 액세스 권한을 가집니다.<br /><br /> Mdm. tblUser에서 **ID** 열의 값은 **1**이 아닙니다.|  
  
## <a name="see-also"></a>참고 항목  
 [모델 관리자 &#40;MDS(Master Data Services)를 만듭니다&#41;](create-a-model-administrator-master-data-services.md)   
 [시스템 관리자 계정 변경 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [MDS(Master Data Services) 데이터베이스 만들기](install-windows/create-a-master-data-services-database.md)   
 [알림&#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
