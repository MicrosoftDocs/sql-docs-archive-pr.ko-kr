---
title: SQL Server 감사 로그 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647570"
---
# <a name="view-a-sql-server-audit-log"></a>SQL Server 감사 로그 보기
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 SQL Server 감사 로그를 보는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **다음을 사용하여 SQL Server 감사 로그를 봅니다.**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 `CONTROL SERVER` 권한이 필요합니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-a-sql-server-audit-log"></a>SQL Server 감사 로그를 보려면  
  
1.  개체 탐색기에서 **보안** 폴더를 확장합니다.  
  
2.  **감사** 폴더를 확장합니다.  
  
3.  보려는 감사 로그를 마우스 오른쪽 단추로 클릭하고 **감사 로그 보기**를 선택합니다. 그러면 **로그 파일 뷰어-**_server_name_ 대화 상자가 열립니다. 자세한 내용은 [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md)을 참조하세요.  
  
4.  완료되면 **닫기**를 클릭합니다.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 은 로그 파일 뷰어를 사용하여 감사 로그를 보는 것을 권장합니다. 그러나 자동화된 모니터링 시스템을 만들면 [sys.fn_get_audit_file&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) 함수를 사용하여 감사 파일에서 정보를 직접 읽을 수 있습니다. 파일을 직접 읽으면 약간 다른 (처리되지 않은) 형식으로 데이터를 반환합니다. 자세한 내용은 fn_get_audit_file를 참조 하세요 **.**  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Audit&#40;데이터베이스 엔진&#41;](sql-server-audit-database-engine.md)   
 [보안 로그에 SQL Server 감사 이벤트 쓰기](write-sql-server-audit-events-to-the-security-log.md)  
  
  
