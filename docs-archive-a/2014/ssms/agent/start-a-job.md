---
title: 작업 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737414"
---
# <a name="start-a-job"></a>작업 시작
  이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , 또는 SQL Server 관리 개체를 사용 하 여에서 에이전트 작업 실행을 시작 하는 방법에 대해 설명 합니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행하도록 지정된 일련의 동작입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업은 한 대의 로컬 서버나 다중 원격 서버에서 실행될 수 있습니다.  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **작업을 시작하려면:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
 자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio 사용  
  
### <a name="to-start-a-job"></a>작업을 시작하려면  
  
1.  **개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.  
  
2.  **SQL Server 에이전트** 를 확장한 다음 **작업**을 확장합니다. 원하는 작업 시작 방법에 따라 다음 중 하나를 수행합니다.  
  
    -   단일 서버 또는 대상 서버에서 작업 중이거나 마스터 서버에서 로컬 서버 작업을 실행하고 있는 경우 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**을 클릭합니다.  
  
    -   여러 작업을 시작하려면 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다. 작업 활동 모니터에서 여러 작업을 선택한 다음 마우스 오른쪽 단추로 클릭하고 **작업 시작**을 클릭합니다.  
  
    -   마스터 서버에서 작업 중이고 모든 대상 서버에서 동시에 작업을 실행하려는 경우에는 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**, **모든 대상 서버에서 시작**을 차례로 클릭합니다.  
  
    -   마스터 서버에서 작업 중이고 작업 대상 서버를 지정하려는 경우에는 시작하려는 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작**, **특정 대상 서버에서 시작**을 차례로 클릭합니다. **다운로드 명령 게시** 대화 상자에서 **대상 서버 지정** 확인란을 선택한 다음 작업을 실행할 각각의 대상 서버를 선택합니다.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL 사용  
  
### <a name="to-start-a-job"></a>작업을 시작하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 자세한 내용은 [sp_start_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)을 참조하세요.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 관리 개체 사용  

### <a name="to-start-a-job"></a>작업을 시작하려면
  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Start` 클래스의 `Job` 메서드를 호출합니다. 자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.  
