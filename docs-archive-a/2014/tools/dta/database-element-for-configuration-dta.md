---
title: Configuration의 Database 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 69ce1a0ac9912907f6d22916dd6243621e0778db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727655"
---
# <a name="database-element-for-configuration-dta"></a>Configuration의 Database 요소(DTA)
  데이터베이스 엔진 튜닝 관리자가 가상 구성(`Configuration` 요소에 의해 지정됨)을 평가하게 하려는 데이터베이스를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특성|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|`Server` 요소마다 한 번 이상 지정해야 합니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[Configuration의 Server 요소&#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**자식 요소**|[Database의 Name 요소&#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database의 Schema 요소&#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation 요소&#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>설명  
 데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **DatabaseTypecomplexType** 입니다. 이 `Database` 요소와 XML 입력 파일의 맨 위에서 발생하는 `Server` 요소가 루트 부모인 요소를 혼동하지 마십시오. 자세한 내용은 [Server의 Database 요소&#40;DTA&#41;](database-element-for-server-dta.md)를 참조하세요.  
  
## <a name="example"></a>예제  
 이 요소의 사용 예를 `Database` 보려면 [DTA&#41;&#40;사용자 지정 구성이 포함 된 XML 입력 파일 샘플 ](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
