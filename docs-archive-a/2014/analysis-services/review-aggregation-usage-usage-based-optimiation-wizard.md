---
title: 집계 사용법 검토 (사용 빈도 기반 최적화 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ef9f900e64858515db226d1f9b864874a4ba827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647926"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>집계 사용법 검토(사용 빈도 기반 최적화 마법사)
  **집계 사용 검토** 페이지를 사용하여 집계 사용 설정을 구성할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **기본값**  
 특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다. 이 설정을 사용하면 디자이너에서 특성 및 차원의 유형을 기반으로 기본 규칙을 적용합니다.  
  
 **전체**  
 특성의 집계 사용 설정을 전체로 설정하려면 선택합니다. 이 설정을 사용하면 큐브의 모든 집계에 이 특성이나 특성 체인에서 이 특성 아래에 있는 관련 특성이 포함되어야 합니다. 특성에 많은 멤버가 포함되어 있는 경우에는 전체 집계 사용 설정을 사용하면 안 됩니다. 이 특성을 여러 특성이나 많은 멤버가 포함된 특성에 지정하면 크기가 너무 커지기 때문에 집계를 디자인할 수 없습니다.  
  
 **없음**  
 특성의 집계 사용 설정을 없음으로 설정하려면 선택합니다. 이 설정을 사용하면 큐브의 집계에 이 특성을 포함할 수 없습니다.  
  
 **무제한**  
 특성의 집계 사용 설정을 제한 없음으로 설정하려면 선택합니다. 이 설정을 사용하면 집계 디자이너에 제한 사항이 지정되지 않지만 해당 특성이 집계에 적절한 특성인지 여부는 계속 평가되어야 합니다.  
  
 **모두 기본값으로 설정**  
 모든 특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md)   
 [다차원 데이터를 &#40;마법사 Analysis Services&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
