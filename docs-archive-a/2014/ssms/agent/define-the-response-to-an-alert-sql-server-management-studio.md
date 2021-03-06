---
title: 경고에 대한 응답 정의(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
ms.openlocfilehash: c14e5adf43602b57697483b9ce4c2cdf20ff8e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731352"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>Define the Response to an Alert (SQL Server Management Studio)
  이 항목에서는 또는을 사용 하 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 여에서 에이전트 경고에 응답 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 하는 방법을 정의 하는 방법에 대해 설명 합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **다음을 사용하여 경고에 대한 응답을 정의합니다.**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   **이후 버전에서는** 에이전트에서 호출기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 제거됩니다. 새 개발 작업에서는 이 기능을 사용하지 말고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.  
  
-   SQL Server 에이전트는 데이터베이스 메일을 사용하여 운영자에게 전자 메일 및 호출기 알림을 보내도록 구성해야 합니다. 자세한 내용은 [경고를 운영자에게 할당](assign-alerts-to-an-operator.md)을 참조하세요.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 는 작업 구조를 만들고 관리할 수 있는 바람직한 방법을 제공하는데 이는 그래픽을 사용하여 쉽게 작업을 관리할 수 있는 방법입니다.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 **sysadmin** 고정 서버 역할의 멤버만 경고에 대한 응답을 정의할 수 있습니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-define-the-response-to-an-alert"></a>경고에 대한 응답을 정의하려면  
  
1.  **개체 탐색기**에서 응답을 정의하려는 경고가 포함된 서버를 확장하려면 더하기 기호를 클릭합니다.  
  
2.  더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.  
  
3.  더하기 기호를 클릭하여 **경고** 폴더를 확장합니다.  
  
4.  응답을 정의하려는 경고를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
5.  _Alert_name_**경고 속성** 대화 상자의 **페이지 선택**에서 **응답**을 선택 합니다.  
  
6.  **작업 실행** 확인란을 선택하고 **작업 실행** 확인란 아래의 목록에서 경고가 발생할 때 실행할 작업을 선택합니다. **새 작업**을 클릭하여 새 작업을 만듭니다. **작업 보기**를 클릭하면 해당 작업에 대한 자세한 내용을 확인할 수 있습니다. **새 작업** 및 **작업 속성**_job_name_ 대화 상자에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 만들기](create-a-job.md) 및 [작업 보기](view-a-job.md)를 참조 하세요.  
  
7.  경고가 활성화될 때 운영자에게 알리려면 **운영자에게 알림** 확인란을 선택합니다. **운영자 목록**에서 운영자에게 알림을 보낼 방법으로 **전자 메일**, **호출기**또는 **Net Send**중 하나 이상을 선택합니다. **새 운영자**를 클릭하여 새 운영자를 만들 수 있습니다. **운영자 보기**를 클릭하면 운영자에 대한 자세한 정보를 볼 수 있습니다. **새 운영자** 및 **운영자 속성 보기** 대화 상자에서 사용 가능한 옵션에 대한 자세한 내용은 [Create an Operator](create-an-operator.md) 및 [View Information About an Operator](view-information-about-an-operator.md)를 참조하세요.  
  
8.  완료되었으면 **확인**을 클릭합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-define-the-response-to-an-alert"></a>경고에 대한 응답을 정의하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 자세한 내용은 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)를 참조 하세요.  
  
  
