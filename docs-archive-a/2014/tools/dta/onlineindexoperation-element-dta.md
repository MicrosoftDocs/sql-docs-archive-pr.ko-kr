---
title: OnlineIndexOperation 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48943c1b31d7a0a24ae939050d44494476e50034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653094"
---
# <a name="onlineindexoperation-element-dta"></a>OnlineIndexOperation 요소(DTA)
  데이터베이스 엔진 튜닝 관리자가 권장하는 인덱스, 인덱싱된 뷰 또는 파티션을 온라인으로 만들 수 있는지 여부를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특성|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|`string`, 최대 길이 없음|  
|**허용된 값**|**OFF**<br /> 권장되는 물리적 디자인 구조를 온라인으로 만들 수 없습니다.<br /><br /> **ON**<br /> 권장되는 모든 물리적 디자인 구조를 온라인으로 만들 수 있습니다.<br /><br /> **MIXED**<br /> 데이터베이스 엔진 튜닝 관리자는 가능한 경우 온라인으로 만들 수 있는 물리적 디자인 구조를 제안합니다.<br /><br /> 이 요소에 이러한 값 중 하나를 사용합니다. 인덱스를 온라인으로 만들 경우 **ONLINE = ON** 키워드가 개체 정의에 추가됩니다.|  
|**기본값**|없음|  
|**발생 빈도**|(선택 사항) 사용할 경우 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[TuningOptions 요소&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**자식 요소**|없음|  
  
## <a name="example"></a>예제  
 이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
