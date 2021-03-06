---
title: 스키마 변경 내용 복제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651648"
---
# <a name="replicate-schema-changes"></a>스키마 변경 내용 복제
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 스키마 변경 내용을 복제하는 방법에 대해 설명합니다.  
  
 게시된 아티클에서 다음 스키마를 변경하면 기본적으로 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구독자에 변경 내용이 전파됩니다.  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
-   **다음을 사용하여 스키마 변경을 복제하려면**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   ALTER TABLE ... DROP COLUMN 문은 스키마 변경 내용 복제를 해제한 경우에도 항상 삭제된 열이 있는 구독이 포함된 모든 구독자에 복제됩니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 게시에 대한 스키마 변경 내용을 복제하지 않으려면 **게시 속성 - \<Publication>** 대화 상자에서 스키마 변경 내용 복제를 사용하지 않도록 설정합니다. 이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.  
  
#### <a name="to-disable-replication-of-schema-changes"></a>스키마 변경 내용 복제를 해제하려면  
  
1.  **게시 속성 - \<Publication>** 대화 상자의 **구독 옵션** 페이지에서 **스키마 변경 내용 복제** 속성의 값을 **False**로 설정합니다.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     특정 스키마 변경 내용만 전파하려면 스키마를 변경하기 전에 해당 속성을 **True** 로 설정한 다음 스키마 변경 후 **False** 로 설정합니다. 반대로 지정된 변경 내용을 제외한 대부분의 스키마 변경 내용을 전파하려면 스키마를 변경하기 전에 해당 속성을 **False** 로 설정한 다음 스키마 변경 후 **True** 로 설정합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
 복제 저장 프로시저를 사용하여 이러한 스키마 변경 내용을 복제할지 여부를 지정할 수 있습니다. 사용하는 저장 프로시저는 게시 유형에 따라 달라집니다.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>스키마 변경 내용을 복제하지 않는 스냅샷 또는 트랜잭션 게시를 만들려면  
  
1.  게시 데이터베이스의 게시자에서 ** \@ replicate_ddl**에 값 **0** 을 지정 하 여 [transact-sql&#41;&#40;sp_addpublication ](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)를 실행 합니다. 자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>스키마 변경 내용을 복제하지 않는 병합 게시를 만들려면  
  
1.  게시 데이터베이스의 게시자에서 ** \@ replicate_ddl**에 값 **0** 을 지정 하 여 [transact-sql&#41;&#40;sp_addmergepublication ](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)를 실행 합니다. 자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>스냅샷 또는 트랜잭션 게시에 대해 스키마 변경 내용 복제를 일시적으로 해제하려면  
  
1.  스키마 변경 내용 복제를 사용 하는 게시의 경우 ** \@ 속성** 에 **replicate_ddl** 값을 지정 하 고 ** \@ 값**에 **0** 값을 지정 하 여 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)를 실행 합니다.  
  
2.  게시된 개체에서 DDL 명령을 실행합니다.  
  
3.  필드 ** \@ 속성** 에 **replicate_ddl** 값을 지정 하 고 ** \@ 값**에 **1** 값을 지정 하 여 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)를 실행 하 여 스키마 변경 내용 복제를 다시 사용 하도록 설정 합니다.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>병합 게시에 대한 스키마 변경 내용 복제를 일시적으로 해제하려면  
  
1.  스키마 변경 내용 복제를 사용 하는 게시의 경우 ** \@ 속성** 에 **replicate_ddl** 값을 지정 하 고 ** \@ 값**에 **0** 값을 지정 하 여 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)를 실행 합니다.  
  
2.  게시된 개체에서 DDL 명령을 실행합니다.  
  
3.  필드 ** \@ 속성** 에 **replicate_ddl** 값을 지정 하 고 ** \@ 값**에 **1** 값을 지정 하 여 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)를 실행 하 여 스키마 변경 내용 복제를 다시 사용 하도록 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md)   
 [게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md)  
  
  
