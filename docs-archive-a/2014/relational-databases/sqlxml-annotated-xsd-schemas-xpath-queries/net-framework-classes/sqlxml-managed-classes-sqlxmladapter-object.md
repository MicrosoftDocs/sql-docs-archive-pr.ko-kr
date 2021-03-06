---
title: SqlXmlAdapter 개체 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1357ab7d070c7c2e451e31bccfda22c58eac42d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646295"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter 개체(SQLXML 관리되는 클래스)
  이 개체는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework에서 데이터 세트과의 상호 작용을 돕는 메서드를 제공합니다. 작업 예제는 [.Net 환경에서 SQLXML 기능에 액세스](accessing-sqlxml-functionality-in-the-net-environment.md)를 참조 하세요.  
  
 SqlXmlAdapter 개체는 다음 메서드를 지원 합니다.  
  
 void 채우기 (데이터 집합 ds)  
 .NET Framework의 데이터 세트을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 검색한 XML 데이터로 채웁니다.  
  
 void 업데이트 (데이터 집합 ds)  
 데이터 세트의 데이터에서 업데이트를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 레코드에 적용합니다.  
  
 SqlXmlAdapter 개체는 다음 생성자를 지원 합니다.  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>참고 항목  
 [SqlXmlCommand 개체 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter 개체 &#40;SQLXML 관리 되는 클래스&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
