---
title: timestamp 데이터 형식에 대한 FOR XML 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
author: rothja
ms.author: jroth
ms.openlocfilehash: cbc37cc396922631a958fff270032e669387d72d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743088"
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a><span data-ttu-id="8163b-102">timestamp 데이터 형식에 대한 FOR XML 지원</span><span class="sxs-lookup"><span data-stu-id="8163b-102">FOR XML Support for the timestamp Data Type</span></span>
  <span data-ttu-id="8163b-103">FOR XML 변환에서 **timestamp** 유형 값은 **varbinary(8)** 데이터로 취급되며 항상 base 64로 인코드됩니다.</span><span class="sxs-lookup"><span data-stu-id="8163b-103">In the FOR XML transformation, **timestamp** type values are treated as **varbinary(8)** data and will always be base 64 encoded.</span></span> <span data-ttu-id="8163b-104">요청된 경우 XSD 또는 XDR 스키마는 이 유형을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="8163b-104">The XSD or XDR schema, if requested, reflects this type.</span></span>  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 <span data-ttu-id="8163b-105">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="8163b-105">This is the result:</span></span>  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="8163b-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8163b-106">See Also</span></span>  
 [<span data-ttu-id="8163b-107">다양한 SQL Server 데이터 형식에 대한 FOR XML 지원</span><span class="sxs-lookup"><span data-stu-id="8163b-107">FOR XML Support for Various SQL Server Data Types</span></span>](for-xml-support-for-various-sql-server-data-types.md)  
  
  