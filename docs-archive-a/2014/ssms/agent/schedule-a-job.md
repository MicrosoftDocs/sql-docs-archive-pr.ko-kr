---
title: 작업 예약 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731324"
---
# <a name="schedule-a-job"></a>Schedule a Job
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 예약하는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:** ,  
  
     [보안](#Security)  
  
-   **작업 일정을 예약하려면:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
 자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>작업에 대한 일정을 만들고 연결하려면  
  
1.  **개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.  
  
2.  **SQL Server 에이전트**, **작업**을 차례로 확장한 다음 예약할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
3.  **일정** 페이지를 선택한 다음 **새로 만들기**를 클릭합니다.  
  
4.  **이름** 입력란에 새 일정의 이름을 입력합니다.  
  
5.  만든 즉시 일정이 적용되지 않게 하려면 **사용** 확인란의 선택을 해제합니다.  
  
6.  **일정 유형**에 대해 다음 중 하나를 선택합니다.  
  
    -   **SQL Server 에이전트가 시작될 때 자동으로 시작** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 시작할 때 작업을 시작합니다.  
  
    -   **CPU가 유휴 상태로 될 때마다 시작** 을 클릭하여 CPU가 유휴 상태일 때 작업을 시작합니다.  
  
    -   일정을 반복적으로 실행하려면 **되풀이** 를 클릭합니다. 반복 수행 일정을 설정하려면 대화 상자에서 **빈도**, **일별 빈도**및 **기간** 그룹을 입력하세요.  
  
    -   한 번만 실행하도록 예약하려면 **한 번** 을 클릭합니다. **한 번** 예약을 설정하려면 대화 상자에서 **한 번 발생** 그룹을 입력합니다.  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>작업에 일정을 연결하려면  
  
1.  **개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.  
  
2.  **SQL Server 에이전트**, **작업**을 차례로 확장한 다음 예약할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
3.  **일정** 페이지를 선택한 다음 **선택**을 클릭합니다.  
  
4.  연결하려는 일정을 선택한 다음 **확인**을 클릭합니다.  
  
5.  **작업 속성** 대화 상자에서 연결된 일정을 두 번 클릭합니다.  
  
6.  **시작 날짜** 가 올바르게 설정되었는지 확인합니다. 올바르게 설정되지 않았으면 일정을 시작하려는 날짜를 설정한 다음 **확인**을 클릭합니다.  
  
7.  **작업 속성** 대화 상자에서 **확인**을 클릭합니다.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL 사용  
  
#### <a name="to-schedule-a-job"></a>작업을 예약하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 자세한 내용은 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) 및 [sp_attach_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)을 참조 하세요.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 관리 개체 사용  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobSchedule` 클래스를 사용합니다. 자세한 내용은[SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.  
