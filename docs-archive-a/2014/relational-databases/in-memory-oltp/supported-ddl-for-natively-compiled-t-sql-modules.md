---
title: 고유 하 게 컴파일된 저장 프로시저에서 지원 되는 구문 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bc7e28fa2a868ac39c6adbb2dea3cc5c3ace73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649549"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>고유하게 컴파일된 저장 프로시저의 지원되는 구문
  이 항목에서는 고유하게 컴파일된 저장 프로시저에서 지원되는 구문에 대해 설명합니다.  
  
 지원되지 않는 구문에 대한 정보는 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)을 참조하세요.  
  
## <a name="procedure-ddl"></a>프로시저 DDL  
 다음 항목이 지원됩니다.  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING(고유하게 컴파일된 저장 프로시저에 필요함)  
  
-   NATIVE_COMPILATION  
  
-   매개 변수는 NOT NULL로 선언할 수 없습니다.  
  
-   테이블 반환 매개 변수  
  
## <a name="security"></a>보안  
 다음 항목이 지원됩니다.  
  
-   프로시저: EXECUTE AS OWNER, SELF 및 사용자  
  
-   테이블 및 프로시저에 대한 GRANT 및 DENY 권한  
  
## <a name="see-also"></a>참고 항목  
 [고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md)  
  
  
