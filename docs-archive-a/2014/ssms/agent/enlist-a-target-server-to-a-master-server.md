---
title: 마스터 서버에 대상 서버 등록 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 256f1a78d298d89a36412ee5689695f3ab3fde8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639227"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>마스터 서버에 대상 서버 등록
  이 항목에서는 대상 서버를 다중 서버 관리 구성에 추가하는 방법에 대해 설명합니다. 이 절차는 마스터 서버에서 실행하십시오. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]또는 SMO(SQL Server 관리 개체)를 사용합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 사용되는 Windows 계정이 다중 서버 환경에 미치는 영향에 대한 자세한 내용은 [다중 서버 환경 만들기](create-a-multiserver-environment.md)를 참조하세요.  
  
 전체 SSL(Secure Sockets Layer) 암호화 및 인증서 확인은 기본적으로 마스터 서버와 대상 서버 간 연결에서 사용할 수 있습니다. 자세한 내용은 [대상 서버의 암호화 옵션 설정](set-encryption-options-on-target-servers.md)을 참조하세요.  
  
 **항목 내용**  
  
-   **대상 서버를 등록하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-enlist-a-target-server"></a>대상 서버를 등록하려면  
  
1.  **개체 탐색기**에서 마스터 서버로 구성된 서버를 확장합니다.  
  
2.  **SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 추가**를 클릭합니다.  
  
3.  전체 프로세스를 안내하는 대상 서버 마법사를 완료합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-enlist-a-target-server"></a>대상 서버를 등록하려면  
  
1.  `sp_msx_enlist` 저장 프로시저를 사용합니다.  자세한 내용은 [sp_msx_enlist &#40;transact-sql](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql) 을 참조 하세요&#41;  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a>SQL Server 관리 개체 사용 (SMO)  
  
## <a name="see-also"></a>참고 항목  
 [기업 내 관리 자동화](automated-administration-across-an-enterprise.md)  
  
  
