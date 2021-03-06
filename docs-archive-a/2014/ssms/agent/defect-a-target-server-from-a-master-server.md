---
title: 마스터 서버에서 대상 서버 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731367"
---
# <a name="defect-a-target-server-from-a-master-server"></a>마스터 서버에서 대상 서버 제거
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] 또는 SMO(SQL Server 관리 개체)를 사용하여 마스터 서버에서 대상 서버를 제거하는 방법에 대해 설명합니다. 이 프로시저를 대상 서버에서 실행합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **대상 서버를 제거하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 이 저장 프로시저를 실행하려면 사용자가 `sysadmin` 고정 서버 역할의 멤버여야 합니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>마스터 서버에서 대상 서버를 제거하려면  
  
1.  **개체 탐색기**에서 대상 서버로 구성된 서버를 확장합니다.  
  
2.  **SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **제거**를 클릭합니다.  
  
3.  **예** 를 클릭하여 마스터 서버에서 이 대상 서버를 제거할 것을 확인합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>마스터 서버에서 대상 서버를 제거하려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
```sql
sp_msx_defect ;  
```  
  
 자세한 내용은 [sp_msx_defect &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)를 참조 하세요.  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a>SQL Server 관리 개체 사용 (SMO)  
 `MsxDefect Method`를 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [다중 서버 환경 만들기](create-a-multiserver-environment.md)   
 [기업 내 관리 자동화](automated-administration-across-an-enterprise.md)   
 [마스터 서버에서 여러 대상 서버 제거](defect-multiple-target-servers-from-a-master-server.md)  
