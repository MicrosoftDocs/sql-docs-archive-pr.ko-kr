---
title: 일정 만들기 | Microsoft 문서
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
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659788"
---
# <a name="create-a-schedule"></a>Create a Schedule
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 SQL Server 관리 개체를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에이전트 작업에 대한 일정을 만들 수 있습니다.  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **일정을 만들려면:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
 자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-create-a-schedule"></a>일정을 만들려면  
  
1.  **개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.  
  
2.  **SQL Server 에이전트**를 확장하고 **작업**을 마우스 오른쪽 단추로 클릭한 후 **일정 관리**를 클릭합니다.  
  
3.  **일정 관리** 대화 상자에서 **새로 만들기**를 클릭합니다.  
  
4.  **이름** 입력란에 새 일정의 이름을 입력합니다.  
  
5.  만든 즉시 일정이 적용되지 않게 하려면 **사용** 확인란의 선택을 해제합니다.  
  
6.  **일정 유형**에 대해 다음 중 하나를 선택합니다.  
  
    -   CPU가 유휴 상태일 때 작업을 시작하려면 **CPU가 유휴 상태로 될 때마다 시작**을 클릭합니다.  
  
    -   일정을 반복적으로 실행하려면 **되풀이**를 클릭합니다. 반복 수행 일정을 설정하려면 대화 상자에서 **빈도**, **일별 빈도**및 **기간** 그룹을 입력하세요.  
  
    -   한 번만 실행하도록 예약하려면 **한 번**을 클릭합니다. **한 번** 예약을 설정하려면 대화 상자에서 **한 번 발생** 그룹을 입력합니다.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL 사용  
  
#### <a name="to-create-a-schedule"></a>일정을 만들려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 자세한 내용은 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)를 참조 하세요.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 관리 개체 사용  
 **일정을 만들려면**  
  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobSchedule` 클래스를 사용합니다. 자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.  
