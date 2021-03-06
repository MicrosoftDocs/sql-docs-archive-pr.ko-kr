---
title: 아티클 정의 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661024"
---
# <a name="define-an-article"></a>아티클 정의
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 아티클을 정의하는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **아티클을 정의하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [RMO(복제 관리 개체)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   아티클 이름에는 %, *, [,], |, :, ", ? 등의 문자를 포함할 수 없습니다. , ' , \ , / , \< , >. 이러한 문자를 포함하는 데이터베이스 개체를 복제하려면 개체 이름과 다른 아티클 이름을 지정해야 합니다.  
  
##  <a name="security"></a><a name="Security"></a> 보안  
 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 저장해야 하는 경우 [Windows .NET Framework에서 제공하는](https://go.microsoft.com/fwlink/?LinkId=34733) 암호화 서비스 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 를 사용합니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 새 게시 마법사를 사용하여 게시를 만들고 아티클을 정의할 수 있습니다. 게시를 만든 다음 **게시 속성 - \<Publication>** 대화 상자에서 게시 속성을 보고 수정합니다. Oracle 데이터베이스에서 게시를 만드는 방법에 대한 자세한 내용은 [Oracle 데이터베이스에서 게시 만들기](create-a-publication-from-an-oracle-database.md)를 참조하세요.  
  
#### <a name="to-create-a-publication-and-define-articles"></a>게시를 만들고 아티클을 정의하려면  
  
1.  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음, 해당 서버 노드를 확장합니다.  
  
2.  **복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 마우스 오른쪽 단추로 클릭합니다.  
  
3.  **새 게시**를 클릭합니다.  
  
4.  새 게시 마법사의 페이지에 따라 다음을 수행하세요.  
  
    -   서버에 배포가 구성되어 있지 않은 경우 배포자를 지정합니다. 배포 구성에 대한 자세한 내용은 [게시 및 배포 구성](../configure-publishing-and-distribution.md)을 참조하세요.  
  
         **배포자** 페이지에서 게시자 서버가 자신의 고유 배포자(로컬 배포자) 역할을 하는 것으로 지정했지만 서버가 배포자로 구성되어 있지 않은 경우 새 게시 마법사가 서버를 구성합니다. **스냅샷 폴더** 페이지에서 배포자에 대해 기본 스냅샷 폴더를 지정하게 됩니다. 스냅샷 폴더는 공유하도록 지정된 디렉터리일 뿐이며 이 폴더에 읽기/쓰기 작업을 수행하려면 에이전트에게 충분한 액세스 권한이 있어야 합니다. 폴더의 적절한 보안 유지 방법에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](../security/secure-the-snapshot-folder.md)을 참조하세요.  
  
         다른 서버가 배포자의 역할을 하도록 지정한 경우 게시자에서 배포자로 연결할 때 사용할 암호를 **관리 암호** 페이지에 입력해야 합니다. 이 암호는 원격 배포자에서 게시자를 설정할 때 지정한 암호와 일치해야 합니다.  
  
         자세한 내용은 [Configure Distribution](../configure-distribution.md)를 참조하세요.  
  
    -   게시 데이터베이스를 선택합니다.  
  
    -   보고서 유형을 선택합니다. 자세한 내용은 [복제 유형](../types-of-replication.md)을 참조하세요.  
  
    -   게시할 데이터와 데이터베이스 개체를 지정합니다. 필요에 따라 테이블 아티클에서 열을 필터링하고 아티클 속성을 설정합니다.  
  
    -   필요에 따라 테이블 아티클에서 행을 필터링합니다. 자세한 내용은 [게시된 데이터 필터링](filter-published-data.md)을 참조하세요.  
  
    -   스냅샷 에이전트 일정을 설정합니다.  
  
    -   다음 복제 에이전트를 실행 및 연결하는 자격 증명을 지정합니다.  
  
         모든 게시에 대한 \- 스냅샷 에이전트  
  
         모든 트랜잭션 게시에 대한 \- 로그 판독기 에이전트  
  
         \- 구독 업데이트를 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트  
  
         자세한 내용은 [Replication Agent Security Model](../security/replication-agent-security-model.md) 및 [Replication Security Best Practices](../security/replication-security-best-practices.md)를 참조하세요.  
  
    -   필요에 따라 게시를 스크립팅합니다. 자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하세요.  
  
    -   게시의 이름을 지정합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
 게시를 만든 후에 복제 저장 프로시저를 사용하여 아티클을 프로그래밍 방식으로 만들 수 있습니다. 아티클을 만드는 데 사용되는 저장 프로시저는 정의하려는 아티클의 게시 유형에 따라 달라집니다. 자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>스냅샷 또는 트랜잭션 게시에 대한 아티클을 정의하려면  
  
1.  게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다. ** \@ 게시**에 대해 아티클이 속한 게시의 이름, ** \@ 아티클의**아티클 이름, ** \@ source_object**에 대해 게시 되는 데이터베이스 개체 및 기타 선택적 매개 변수를 지정 합니다. **Dbo**가 아닌 경우 ** \@ source_owner** 를 사용 하 여 개체의 스키마 소유권을 지정 합니다. 아티클이 로그 기반 테이블 아티클이 아닌 경우 ** \@ 유형에**대 한 아티클 유형을 지정 합니다. 자세한 내용은 [복제 Transact-sql&#41;프로그래밍 &#40;아티클 유형 지정 ](specify-article-types-replication-transact-sql-programming.md)을 참조 하세요.  
  
2.  테이블의 행을 행 필터링하거나 아티클을 보려면 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) 를 사용하여 필터 절을 정의합니다. 자세한 내용은 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)을 참조하세요.  
  
3.  테이블의 열을 열 필터링하거나 아티클을 보려면 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)을 사용합니다. 자세한 내용은 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)을 참조하세요.  
  
4.  아티클이 필터링되었으면 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) 를 실행합니다.  
  
5.  게시에 기존 구독이 있고 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 이 **immediate_sync** 열에 값 **0** 을 반환하면 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 을 호출하여 각각의 기존 구독에 아티클을 추가해야 합니다.  
  
6.  게시에 기존 끌어오기 구독이 있으면 게시자에서 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) 를 실행하여 새 아티클을 포함하는, 기존 끌어오기 구독에 대한 새 스냅샷을 만듭니다.  
  
    > [!NOTE]  
    >  스냅샷을 사용하여 초기화되지 않은 구독에 대해서는 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) 를 실행하지 않아도 됩니다. 이 절차는 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)에 의해 실행됩니다.  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>병합 게시에 대한 아티클을 정의하려면  
  
1.  게시 데이터베이스의 게시자에서 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다. 게시에 대 한 게시 이름, ** \@ ** ** \@ 아티클의**아티클 이름 이름 및 ** \@ source_object**에 대해 게시 되는 개체를 지정 합니다. 테이블 행을 행 필터링 하려면 ** \@ subset_filterclause**의 값을 지정 합니다. 자세한 내용은 [병합 아티클에 대한 매개 변수가 있는 행 필터 정의 및 수정](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 및 [정적 행 필터 정의 및 수정](define-and-modify-a-static-row-filter.md)를 참조하세요. 아티클이 테이블 아티클이 아닌 경우 ** \@ 유형**의 아티클 유형을 지정 합니다. 자세한 내용은 [아티클 유형 정의&#40;복제 Transact-SQL 프로그래밍&#41;](specify-article-types-replication-transact-sql-programming.md)를 참조하세요.  
  
2.  필요에 따라 게시 데이터베이스의 게시자에서 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) 를 실행하여 두 아티클 간의 조인 필터를 정의합니다. 자세한 내용은 [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)을 참조하세요.  
  
3.  필요에 따라 게시 데이터베이스의 게시자에서 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 을 실행하여 테이블 열을 필터링합니다. 자세한 내용은 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)을 참조하세요.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> 예(Transact-SQL)  
 이 예에서는 `Product` 테이블을 기반으로 트랜잭션 게시에 대한 아티클을 정의합니다. 여기에서 아티클은 행 및 열 방향으로 필터링됩니다.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 이 예에서는 병합 게시에 대한 아티클을 정의합니다. 여기에서 `SalesOrderHeader` 아티클은 **SalesPersonID**에 따라 정적으로 필터링되고 `SalesOrderDetail` 아티클은 `SalesOrderHeader`에 따라 조인 필터링됩니다.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> RMO(복제 관리 개체) 사용  
 RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 아티클을 정의할 수 있습니다. 아티클을 정의하는 데 사용하는 RMO 클래스는 정의되는 아티클의 게시 유형에 따라 달라집니다.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> 예(RMO)  
 다음 예에서는 행 및 열 필터가 포함된 아티클을 트랜잭션 게시에 추가합니다.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 다음 예에서는 병합 게시에 세 개의 아티클을 추가합니다. 이 아티클에는 열 필터가 포함되며, 두 개의 조인 필터를 사용하여 매개 변수가 있는 행 필터를 다른 아티클에 전파합니다.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>참고 항목  
 [Create a Publication](create-a-publication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [기존 게시에 대한 아티클 추가 및 삭제](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [게시된 데이터 필터링](filter-published-data.md)   
 [데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
