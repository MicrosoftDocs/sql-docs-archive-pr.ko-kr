---
title: '예제: 제품 모델 정보를 XML로 검색 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: rothja
ms.author: jroth
ms.openlocfilehash: d580f53c4b5185a8b1b1467c75a08fc6929bdcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651571"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>예제: 제품 모델 정보를 XML로 검색
  다음 쿼리는 제품 모델 정보를 반환합니다. `RAW` 모드는 `FOR XML` 절에서 지정됩니다.  
  
## <a name="example"></a>예제  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 다음은 결과의 일부입니다.  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 `ELEMENTS` 지시어를 지정하여 요소 중심 XML을 검색할 수 있습니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 다음은 결과입니다.  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 선택적으로 `TYPE` 지시어를 지정하여 결과를 `xml` 유형으로 검색할 수 있습니다. `TYPE` 지시어는 결과의 내용을 변경하지 않습니다. 결과의 데이터 형식에만 영향을 줍니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)  
  
  
