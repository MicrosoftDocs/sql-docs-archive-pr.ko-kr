---
title: 데이터 원본 정보 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: rothja
ms.author: jroth
ms.openlocfilehash: c10a4e762bbe3421e720753941f5e0a5702832ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740879"
---
# <a name="data-source-information-properties"></a>데이터 원본 정보 속성
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 공급자별 속성 집합 DBPROPSET_SQLSERVERDATASOURCEINFO에 다음과 같은 데이터 원본 정보 속성을 정의합니다.  
  
|속성 ID|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|유형: VT_BOOL<br /><br /> R/W: Read<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: 열 데이터 정렬이 지원되는지 확인하는 데 사용됩니다.<br /><br /> VARIANT_TRUE: 열 수준 데이터 정렬이 지원 됩니다.<br /><br /> VARIANT_FALSE: 열 수준 데이터 정렬은 지원 되지 않습니다.|  
|SSPROP_UNICODELCID|형식: VT_I4 R/W: Read<br /><br /> 설명: 유니코드 로캘 ID입니다.<br /><br /> 유니코드 데이터 정렬에 사용되는 로캘입니다.|  
|SSPROP_UNICODECOMPARISONSTYLE|형식: VT_I4 R/W: Read<br /><br /> 설명: 유니코드 비교 스타일입니다.<br /><br /> 유니코드 데이터 정렬에 사용되는 정렬 옵션입니다.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 공급자별 속성 집합 DBPROPSET_SQLSERVERSTREAM에 다음과 같은 추가 속성을 정의합니다.  
  
|속성 ID|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|형식: VT_BSTR R/W: 읽기/쓰기<br /><br /> 설명: FOR XML 쿼리 결과가 올바른 형식의 문서가 아닐 수 있습니다. 이 속성이 지정되면 ‘select ... for XML’ 쿼리의 결과가 이 속성에서 제공한 루트 태그에 래핑되어 올바른 형식의 XML 문서가 반환됩니다. 쿼리가 브라우저에서 실행되는 경우에는 결과를 로드할 때 브라우저에서 파서 오류가 표시될 수 있습니다. 오류를 방지하기 위해 SQL ISAPI는 ROOT 키워드를 지원합니다. 이 키워드는 SSPROP_STREAM_XMLROOT 속성에 매핑됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 원본 개체 &#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  
