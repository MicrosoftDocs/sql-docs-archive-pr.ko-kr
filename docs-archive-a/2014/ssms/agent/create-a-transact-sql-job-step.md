---
title: Transact-SQL 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b83ee944d2ca5c10ff1b77f3e6e6da6054b5c99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737473"
---
# <a name="create-a-transact-sql-job-step"></a>Create a Transact-SQL Job Step
  이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 스크립트를 실행 하는 에이전트 작업 단계를 만드는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 작업 단계 스크립트는 저장 프로시저와 확장 저장 프로시저를 호출할 수도 있습니다. 단일 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계에는 다수의 일괄 처리 및 GO 명령이 포함됩니다. 작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **Transact-SQL 작업 단계를 만들려면:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
 자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Transact-SQL 작업 단계를 만들려면  
  
1.  **개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.  
  
2.  **SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
3.  **작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.  
  
4.  **새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.  
  
5.  **유형** 목록에서 **T-SQL(Transact-SQL) 스크립트**를 클릭합니다.  
  
6.  **명령** 상자에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령 일괄 처리를 입력하거나 **열기** 를 클릭하여 명령으로 사용할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 파일을 선택합니다.  
  
7.  **구문 분석** 을 클릭하여 구문을 검사합니다.  
  
8.  구문이 정확하면 “구문 분석이 성공했습니다”라는 메시지가 나타납니다. 오류가 발견되면 구문을 수정한 다음 작업을 계속 수행하세요.  
  
9. **고급** 페이지를 클릭하여 작업 단계의 성공 또는 실패 여부에 따라 수행할 동작, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계를 수행할 횟수, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업 단계 출력을 쓸 파일이나 테이블 등의 작업 단계 옵션을 설정합니다. **sysadmin** 고정 서버 역할의 멤버만 운영 체제 파일에 작업 단계 출력을 쓸 수 있습니다. 모든 SQL Server 에이전트 사용자는 테이블에 출력을 기록할 수 있습니다.  
  
10. **sysadmin** 고정 서버 역할의 멤버이면서 이 작업 단계를 다른 SQL 로그인으로 실행하려는 경우 **다음 사용자 이름으로 실행** 목록에서 해당 SQL 로그인을 선택합니다.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL 사용  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Transact-SQL 작업 단계를 만들려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 관리 개체 사용  
 **Transact-SQL 작업 단계를 만들려면**  
  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobStep` 클래스를 사용합니다.  
