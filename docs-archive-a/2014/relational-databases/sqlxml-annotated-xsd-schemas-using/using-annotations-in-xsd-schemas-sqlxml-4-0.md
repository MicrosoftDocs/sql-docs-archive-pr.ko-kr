---
title: XSD 스키마에 주석 사용 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: e2be94aa5815593d7a5a2e0c00bcd8849e81484e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650893"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>XSD 스키마에 주석 사용(SQLXML 4.0)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0의 XSD 스키마 언어는 XDR(XML-Data Reduced) 스키마 언어에 도입된 주석과 비슷한 방식으로 주석을 지원합니다. XSD에는 XDR에서는 지원되지 않은 추가 주석도 도입되었습니다.  
  
 이러한 주석은 XSD 스키마 내에서 XML-관계형 매핑을 지정하는 데 사용됩니다. 여기에는 XSD 스키마의 요소 및 특성을 데이터베이스의 테이블(뷰) 및 열에 매핑하는 작업이 포함됩니다.  
  
 주석을 지정하지 않으면 기본 매핑이 수행됩니다. 기본적으로 복합 유형의 XSD 요소는 지정된 데이터베이스의 테이블(뷰) 이름에 매핑되며 단순 유형의 요소 또는 특성은 같은 이름의 열에 매핑됩니다.  
  
 이러한 주석은 XML에서 계층 관계를 지정 하는 데에도 사용할 수 있습니다. 따라서 XSD 스키마는 단순히 관계형 데이터의 XML 뷰입니다.  
  
 이 섹션에서는 XSD 스키마에서 사용할 수 있는 주석에 대해 설명하고 사용 예를 제공합니다.  
  
> [!NOTE]  
>  이 섹션에 있는 모든 예는 각 예에서 설명된 주석이 추가된 XSD 스키마에 대해 간단한 XPath 쿼리를 지정합니다. 이 섹션에서는 사용자가 XPath 언어에 대해 잘 알고 있다고 가정합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [&#40;SQLXML 4.0&#41;XSD 주석](xsd-annotations-sqlxml-4-0.md)  
 XSD 스키마에서 사용할 수 있는 주석, 이러한 주석에 대한 설명, 그리고 이러한 주석에 해당하는 XDR 주석을 나열합니다.  
  
 [SQLXML 4.0 &#40;테이블 및 열에 대 한 XSD 요소 및 특성의 기본 매핑&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 기본 매핑 및 이와 관련된 태스크의 예를 설명합니다.  
  
 [SQLXML 4.0 &#40;테이블 및 열에 대 한 XSD 요소 및 특성의 명시적 매핑&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 `sql:relation` 및 `sql:field` 주석을 사용한 명시적 매핑에 대해 설명하고 예를 제공합니다.  
  
 [Sql: relationship &#40;SQLXML 4.0&#41;를 사용 하 여 관계 지정](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 `sql:relationship` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: relationship에 sql: 역 특성 지정 &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 `sql:inverse` 주석에 대해 설명합니다.  
  
 [Sql: is 상수 &#40;SQLXML 4.0&#41;를 사용 하 여 상수 요소를 만듭니다.](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 `sql:is-constant` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: mapped &#40;SQLXML 4.0&#41;를 사용 하 여 결과 XML 문서에서 스키마 요소 제외](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 `sql:mapped` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: limit 필드 및 sql: limit 값을 사용 하 여 값 필터링 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 `sql:limit-field` 및 `sql:limit-value` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: 키-필드 &#40;SQLXML 4.0&#41;를 사용 하 여 키 열 식별](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 `sql:key-fields` 주석에 대해 설명하고 예를 제공합니다.  
  
 [TargetNamespace 특성 &#40;사용 하 여 대상 네임 스페이스 지정&#41;SQLXML 4.0](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 **TargetNamespace** 특성에 대해 설명 하 고 예제를 제공 합니다.  
  
 [Sql: prefix &#40;SQLXML 4.0&#41;를 사용 하 여 유효한 ID, IDREF 및 IDREFS 유형 특성 만들기](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 `sql:prefix` 주석에 대해 설명하고 예를 제공합니다.  
  
 [데이터 형식 강제 변환 및 sql: datatype 주석 &#40;SQLXML 4.0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 `sql:datatype` 주석에 대해 설명하고 예를 제공합니다.  
  
 [&#40;SQLXML 4.0&#41;XSD 데이터 형식을 XPath 데이터 형식에 매핑](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 XSD, XDR 및 XPath 데이터 형식을 비교하고 연관된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변환을 나열하는 표를 제공합니다.  
  
 [Sql: use-cdata &#40;SQLXML 4.0&#41;를 사용 하 여 CDATA 섹션 만들기](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 `sql:use-data` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: encoding &#40;SQLXML 4.0&#41;를 사용 하 여 BLOB 데이터에 대 한 URL 참조 요청](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 `sql:encode` 주석에 대해 설명하고 예를 제공합니다.  
  
 [Sql: 오버플로 필드 &#40;SQLXML 4.0&#41;를 사용 하 여 사용 되지 않은 데이터를 검색 합니다.](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 `sql:overflow-field` 주석에 대해 설명하고 예를 제공합니다.  
  
 [sql:hide를 사용하여 요소 및 특성 숨기기](hiding-elements-and-attributes-by-using-sql-hide.md)  
 `sql:hide` 주석에 대해 설명하고 예를 제공합니다.  
  
 [sql:identity 및 sql:guid 주석 사용](using-the-sql-identity-and-sql-guid-annotations.md)  
 `sql:identity` 및 `sql:guid` 주석에 대해 설명하고 예를 제공합니다.  
  
 [sql:max-depth를 사용하여 재귀 관계의 깊이 지정](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 `sql:max-depth` 주석에 대해 설명하고 예를 제공합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLXML 4.0 &#40;주석이 추가 된 스키마 보안 고려 사항&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
