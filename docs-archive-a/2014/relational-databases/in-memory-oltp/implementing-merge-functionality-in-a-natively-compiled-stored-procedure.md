---
title: 병합 기능 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649556"
---
# <a name="implementing-merge-functionality"></a>MERGE 기능 구현
  데이터베이스에 특정 행 이 이미 있는지 여부에 따라 데이터베이스에서 삽입 또는 업데이트를 수행해야 할 수 있습니다.  
  
 `MERGE` 문을 사용하지 않는 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용할 수 있는 방법 중 하나는 다음과 같습니다.  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 병합을 구현하는 다른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 방법:  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 고유하게 컴파일된 저장 프로시저의 경우  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>참고 항목  
 [고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md)   
 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
