---
title: 데이터베이스 스키마 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3ac0c00768db6501c7d786c35758c1a9d75a5a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730388"
---
# <a name="create-a-database-schema"></a>데이터베이스 스키마 만들기
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 스키마를 만드는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **다음을 사용하여 스키마를 만듭니다.**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   새 스키마는 데이터베이스 수준 보안 주체인 데이터베이스 사용자, 데이터베이스 역할 또는 애플리케이션 역할 중 하나가 소유합니다. 스키마 내에서 만든 개체는 스키마 소유자가 소유하며 **sys.objects** 의 **principal_id**가 NULL입니다. 스키마 포함 개체의 소유권을 모든 데이터베이스 수준 보안 주체에게 이전할 수 있지만 스키마 소유자는 항상 스키마 내의 개체에 대한 CONTROL 권한을 갖고 있어야 합니다.  
  
-   데이터베이스 개체를 만들 때 개체 소유자로 유효한 도메인 보안 주체(사용자 또는 그룹)를 지정하면 도메인 보안 주체는 데이터베이스에 스키마로 추가됩니다. 새 스키마는 도메인 보안 주체가 소유하게 됩니다.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
  
-   데이터베이스에 대한 CREATE SCHEMA 권한이 필요합니다.  
  
-   다른 사용자를 생성되는 스키마의 소유자로 지정하려면 호출자에게 해당 사용자에 대한 IMPERSONATE 권한이 있어야 합니다. 데이터베이스 역할을 소유자로 지정하는 경우 호출자에게 해당 역할의 멤버 자격이나 해당 역할에 대한 ALTER 권한이 있어야 합니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
##### <a name="to-create-a-schema"></a>스키마를 만들려면  
  
1.  개체 탐색기에서 **데이터베이스** 폴더를 확장합니다.  
  
2.  새 데이터베이스 스키마를 만들 데이터베이스를 확장합니다.  
  
3.  **보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **스키마**를 선택합니다.  
  
4.  **스키마 - 신규** 대화 상자의 **일반** 페이지에서 **스키마 이름** 상자에 새 스키마의 이름을 입력합니다.  
  
5.  **스키마 소유자** 상자에 해당 스키마를 소유할 데이터베이스 사용자 또는 역할의 이름을 입력합니다. 또는 **검색** 을 클릭하여 **역할 및 사용자 검색** 대화 상자를 엽니다.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>추가 옵션  
 **스키마 - 신규** 대화 상자에는 또한 **사용 권한** 및 **확장 속성**의 두 가지 추가 페이지의 옵션이 제공됩니다.  
  
-   **사용 권한** 페이지에는 사용 가능한 모든 보안 개체와 이러한 보안 개체에서 로그인에 부여할 수 있는 권한이 나열됩니다.  
  
-   **확장 속성** 페이지에서는 데이터베이스 사용자에 사용자 지정 속성을 추가할 수 있습니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-create-a-schema"></a>스키마를 만들려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 자세한 내용은 [CREATE SCHEMA&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql)를 참조하세요.  
  
  
