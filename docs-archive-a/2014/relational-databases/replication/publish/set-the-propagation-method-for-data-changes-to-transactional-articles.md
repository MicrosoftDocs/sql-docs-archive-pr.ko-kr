---
title: 트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
- propagating data changes [SQL Server replication]
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3f8be8b6df1034b06d0aaff6ee61c0c494833c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733875"
---
# <a name="set-the-propagation-method-for-data-changes-to-transactional-articles"></a><span data-ttu-id="dbc85-102">트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법 설정</span><span class="sxs-lookup"><span data-stu-id="dbc85-102">Set the Propagation Method for Data Changes to Transactional Articles</span></span>
  <span data-ttu-id="dbc85-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-103">This topic describes how to set the propagation method for data changes to transactional articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dbc85-104">기본적으로 트랜잭션 복제는 각 아티클에 대한 저장 프로시저 집합을 사용하여 변경 내용을 구독자에 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-104">By default, transactional replication propagates changes to Subscribers using a set of stored procedures for each article.</span></span> <span data-ttu-id="dbc85-105">이 프로시저는 사용자 지정 프로시저로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-105">You can replace these procedures with custom procedures.</span></span> <span data-ttu-id="dbc85-106">자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="dbc85-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="dbc85-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dbc85-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="dbc85-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dbc85-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="dbc85-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="dbc85-110">**트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법을 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="dbc85-110">**To set the propagation method for data changes to transactional articles, using:**</span></span>  
  
     [<span data-ttu-id="dbc85-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dbc85-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dbc85-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dbc85-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
## <a name="before-you-begin"></a><span data-ttu-id="dbc85-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="dbc85-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dbc85-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="dbc85-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="dbc85-115">복제에서 생성된 스냅샷 파일을 편집할 때는 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-115">Care must be taken when editing any of the snapshot files generated by replication.</span></span> <span data-ttu-id="dbc85-116">사용자 지정 저장 프로시저의 사용자 지정 논리를 테스트하고 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-116">You must test and support custom logic in the custom stored procedures.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="dbc85-117">에서는 사용자 지정 논리에 대한 지원을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-117">does not provide support for custom logic.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dbc85-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="dbc85-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="dbc85-119">새 게시 마법사와 **게시 속성 - \<Publication>** 대화 상자에서 사용 가능한 **아티클 속성 - \<Article>** 대화 상자의 **속성** 탭에서 전파 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-119">Specify the propagation method on the **Properties** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="dbc85-120">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-120">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-the-propagation-method"></a><span data-ttu-id="dbc85-121">전파 방법을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-121">To specify the propagation method</span></span>  
  
1.  <span data-ttu-id="dbc85-122">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 테이블을 선택한 다음 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-122">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="dbc85-123">**선택한 테이블 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-123">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="dbc85-124">**아티클 속성 - \<Article>** 대화 상자의 **속성** 탭에 있는 **문 배달** 섹션에서 **INSERT 배달 형식**, **UPDATE 배달 형식** 및 **DELETE 배달 형식** 메뉴를 사용하여 각 작업의 전파 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-124">On the **Properties** tab of the **Article Properties - \<Article>** dialog box, in the **Statement Delivery** section, specify the propagation method for each operation using the **INSERT delivery format**, **UPDATE delivery format**, and **DELETE delivery format** menus.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="dbc85-125">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-125">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-generate-and-use-custom-stored-procedures"></a><span data-ttu-id="dbc85-126">사용자 지정 저장 프로시저를 생성하여 사용하려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-126">To generate and use custom stored procedures</span></span>  
  
1.  <span data-ttu-id="dbc85-127">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 테이블을 선택한 다음 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-127">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="dbc85-128">**선택한 테이블 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-128">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
     <span data-ttu-id="dbc85-129">**아티클 속성 - \<Article>** 대화 상자의 **속성** 탭에 있는 **문 배달** 섹션에서 해당 배달 형식 메뉴(**INSERT 배달 형식**, **UPDATE 배달 형식** 또는 **DELETE 배달 형식**)에서 CALL 구문을 선택한 다음, **INSERT 저장 프로시저**, **DELETE 저장 프로시저** 또는 **UPDATE 저장 프로시저**에 사용할 프로시저 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-129">On the **Properties** tab of the **Article Properties - \<Article>** dialog box, in the **Statement Delivery** section, select the CALL syntax from the appropriate delivery format menu (**INSERT delivery format**, **UPDATE delivery format**, or **DELETE delivery format**), and then type the name of the procedure to use in **INSERT stored procedure**, **DELETE stored procedure**, or **UPDATE stored procedure**.</span></span> <span data-ttu-id="dbc85-130">CALL 구문에 대한 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)에서 "저장 프로시저 호출 구문" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-130">For more information about CALL syntax, see the section "Call syntax for stored procedures" in [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="dbc85-131">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
5.  <span data-ttu-id="dbc85-132">게시에 대한 스냅샷이 생성되면 이전 단계에서 지정한 프로시저가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-132">When the snapshot for the publication is generated, it will include the procedure you specified in the previous step.</span></span> <span data-ttu-id="dbc85-133">이 프로시저는 지정한 CALL 구문을 사용하지만 복제에 사용되는 기본 논리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-133">The procedures will use the CALL syntax you specified, but will include the default logic that replication uses.</span></span>  
  
     <span data-ttu-id="dbc85-134">스냅샷이 생성된 후 이 아티클이 속해 있는 게시의 스냅샷 폴더로 이동하여 아티클과 동일한 이름을 가진 **.sch** 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-134">After the snapshot has been generated, navigate to the snapshot folder for the publication to which this article belongs and locate the **.sch** file with the same name as the article.</span></span> <span data-ttu-id="dbc85-135">메모장이나 다른 텍스트 편집기를 사용하여 이 파일을 열고 삽입, 업데이트 또는 삭제 저장 프로시저에 대한 CREATE PROCEDURE 명령을 찾은 후 프로시저 정의를 편집하여 데이터 변경 내용 전파에 대한 사용자 지정 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-135">Open this file using Notepad or another text editor, locate the CREATE PROCEDURE command for the insert, update, or delete stored procedures, and edit the procedure definition to supply any custom logic for propagating data changes.</span></span> <span data-ttu-id="dbc85-136">스냅샷이 다시 생성되면 사용자 지정 프로시저를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-136">If the snapshot is regenerated, you must re-create the custom procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dbc85-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="dbc85-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="dbc85-138">트랜잭션 복제를 사용하면 게시자에서 구독자로 변경 내용을 전파하는 방법을 제어할 수 있습니다. 이 전파 방법은 아티클을 만들 때 프로그래밍 방식으로 설정될 수 있으며 나중에 복제 저장 프로시저에서 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-138">Transactional replication enables you to control how changes are propagated from the Publisher to Subscribers, and this propagation method can be set programmatically when an article is created and changed later using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbc85-139">게시된 데이터 행에서 수행되는 각 DML(데이터 조작 언어) 작업 유형(삽입, 업데이트 또는 삭제)에 따라 다른 전파 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-139">You can specify a different propagation method for each type of DML (data manipulation language) operation (insert, update, or delete) that occurs on a row of a published data.</span></span>  
  
 <span data-ttu-id="dbc85-140">자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-140">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-create-an-article-that-uses-transact-sql-commands-to-propagate-data-changes"></a><span data-ttu-id="dbc85-141">Transact-SQL 명령을 사용하여 데이터 변경 내용을 전파하는 아티클을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-141">To create an article that uses Transact-SQL commands to propagate data changes</span></span>  
  
1.  <span data-ttu-id="dbc85-142">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-142">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="dbc85-143">**\@publication**에 아티클이 속한 게시 이름, **\@article**에 아티클 이름, **\@source_object**에 게시할 데이터베이스 개체를 지정하고 다음 매개 변수 중 하나 이상에 **SQL** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-143">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and a value of **SQL** for at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="dbc85-144">**\@ins_cmd** - [INSERT](/sql/t-sql/statements/insert-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-144">**\@ins_cmd** - controls the replication of [INSERT](/sql/t-sql/statements/insert-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="dbc85-145">**\@upd_cmd** - [UPDATE](/sql/t-sql/queries/update-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-145">**\@upd_cmd** - controls the replication of [UPDATE](/sql/t-sql/queries/update-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="dbc85-146">**\@del_cmd** - [DELETE](/sql/t-sql/statements/delete-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-146">**\@del_cmd** - controls the replication of [DELETE](/sql/t-sql/statements/delete-transact-sql) commands.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-147">위 매개 변수 중 하나에 **SQL** 값을 지정하면 해당 유형의 명령이 적절한 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 명령으로 구독자에 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-147">When specifying a value of **SQL** for any of the above parameters, commands of that type will be replicated to the Subscriber as the appropriate [!INCLUDE[tsql](../../../includes/tsql-md.md)] command.</span></span>  
  
     <span data-ttu-id="dbc85-148">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-148">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-create-an-article-that-does-not-propagate-data-changes"></a><span data-ttu-id="dbc85-149">데이터 변경 내용을 전파하지 않는 아티클을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-149">To create an article that does not propagate data changes</span></span>  
  
1.  <span data-ttu-id="dbc85-150">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-150">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="dbc85-151">**\@publication**에 아티클이 속한 게시 이름, **\@article**에 아티클 이름, **\@source_object**에 게시할 데이터베이스 개체를 지정하고 다음 매개 변수 중 하나 이상에 **NONE** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-151">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and a value of **NONE** for at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="dbc85-152">**\@ins_cmd** - [INSERT](/sql/t-sql/statements/insert-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-152">**\@ins_cmd** - controls the replication of [INSERT](/sql/t-sql/statements/insert-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="dbc85-153">**\@upd_cmd** - [UPDATE](/sql/t-sql/queries/update-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-153">**\@upd_cmd** - controls the replication of [UPDATE](/sql/t-sql/queries/update-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="dbc85-154">**\@del_cmd** - [DELETE](/sql/t-sql/statements/delete-transact-sql) 명령의 복제를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-154">**\@del_cmd** - controls the replication of [DELETE](/sql/t-sql/statements/delete-transact-sql) commands.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-155">위 매개 변수 중 하나에 **NONE** 값을 지정하면 해당 유형의 명령이 구독자에 복제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-155">When specifying a value of **NONE** for any of the above parameters, commands of that type will not be replicated to the Subscriber.</span></span>  
  
     <span data-ttu-id="dbc85-156">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-156">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-create-an-article-with-user-modified-custom-stored-procedures"></a><span data-ttu-id="dbc85-157">사용자가 수정한 사용자 지정 저장 프로시저를 포함하는 아티클을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-157">To create an article with user-modified custom stored procedures</span></span>  
  
1.  <span data-ttu-id="dbc85-158">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-158">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="dbc85-159">**\@publication**에 아티클이 속한 게시 이름, **\@article**에 아티클 이름, **\@source_object**에 게시할 데이터베이스 개체, **0x02** 값(사용자 지정 저장 프로시저의 자동 생성 설정)을 포함하는 **\@schema_option** 비트 마스크에 값을 지정하고 다음 매개 변수 중 하나 이상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-159">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, a value for the **\@schema_option** bitmask that contains the value **0x02** (enables automatic generation of custom stored procedures), and at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="dbc85-160">\*\* \@ Ins_cmd\*\* - <strong>호출 sp_MSins_*article_name*</strong>값을 지정 합니다. 여기서 **_article_name_** 은 \*\* \@ 아티클에\*\*지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-160">**\@ins_cmd** - specify a value of <strong>CALL sp_MSins_*article_name*</strong>, where **_article_name_** is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="dbc85-161">\*\* \@ Del_cmd\*\* - <strong>CALL sp_MSdel_*article_name* </strong> 또는 <strong>XCALL sp_MSdel_*article_name*</strong>값을 지정 합니다. 여기서 **_article_name_** 은 _ \* \@ article \* \*에 지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-161">**\@del_cmd** - specify a value of <strong>CALL sp_MSdel_*article_name*</strong> or <strong>XCALL sp_MSdel_*article_name*</strong>, where **_article_name_** is the value specified for _\*\@article\*\*.</span></span>  
  
    -   <span data-ttu-id="dbc85-162">\*\* \@ upd_cmd\*\* - <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd__article_name *</strong> 또는 <strong>MCALL sp_MSupd_* article_name \*</strong>값을 지정 합니다. 여기서 _**article_name**_ 은 \*\* \@ 아티클에\*\*지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-162">**\@upd_cmd** - specify a value of <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd__article_name*</strong>, or <strong>MCALL sp_MSupd_* article_name\*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-163">위 명령 매개 변수마다 복제 시 생성되는 저장 프로시저의 이름을 고유하게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-163">For each of the above command parameters, you can specify your own name for the stored procedures that replication generates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-164">CALL, SCALL, XCALL 및 MCALL 구문에 대한 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-164">For more information on CALL, SCALL, XCALL, and MCALL syntax, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
     <span data-ttu-id="dbc85-165">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="dbc85-166">스냅샷이 생성된 후 이 아티클이 속해 있는 게시의 스냅샷 폴더로 이동하여 아티클과 동일한 이름을 가진 **.sch** 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-166">After the snapshot has been generated, navigate to the snapshot folder for the publication to which this article belongs and locate the **.sch** file with the same name as the article.</span></span> <span data-ttu-id="dbc85-167">Notepad.exe를 사용하여 이 파일을 열고 삽입, 업데이트 또는 삭제 저장 프로시저에 대한 CREATE PROCEDURE 명령을 찾은 후 프로시저 정의를 편집하여 데이터 변경 내용 전파에 대한 사용자 지정 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-167">Open this file using Notepad.exe, locate the CREATE PROCEDURE command for the insert, update, or delete stored procedures, and edit the procedure definition to supply any custom logic for propagating data changes.</span></span> <span data-ttu-id="dbc85-168">자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-168">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-create-an-article-with-custom-scripting-in-the-custom-stored-procedures-to-propagate-data-changes"></a><span data-ttu-id="dbc85-169">데이터 변경 내용을 전파하기 위해 사용자 지정 저장 프로시저의 사용자 지정 스크립팅을 포함하는 아티클을 만들려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-169">To create an article with custom scripting in the custom stored procedures to propagate data changes</span></span>  
  
1.  <span data-ttu-id="dbc85-170">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-170">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="dbc85-171">**\@publication**에 아티클이 속한 게시 이름, **\@article**에 아티클 이름, **\@source_object**에 게시할 데이터베이스 개체, **0x02** 값(사용자 지정 저장 프로시저의 자동 생성 설정)을 포함하는 **\@schema_option** 비트 마스크에 값을 지정하고 다음 매개 변수 중 하나 이상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-171">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, a value for the **\@schema_option** bitmask that contains the value **0x02** (enables automatic generation of custom stored procedures), and at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="dbc85-172">\*\* \@ Ins_cmd\*\* - <strong>호출 sp_MSins_*article_name*</strong>값을 지정 합니다. 여기서 _**article_name**_ 은 \*\* \@ 아티클에\*\*지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-172">**\@ins_cmd** - specify a value of <strong>CALL sp_MSins_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="dbc85-173">\*\* \@ Del_cmd\*\* - <strong>CALL sp_MSdel_*article_name* </strong> 또는 <strong>XCALL sp_MSdel_*article_name*</strong>값을 지정 합니다. 여기서 _**article_name**_ 은 \*\* \@ 아티클에\*\*지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-173">**\@del_cmd** - specify a value of <strong>CALL sp_MSdel_*article_name*</strong> or <strong>XCALL sp_MSdel_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="dbc85-174">\*\* \@ upd_cmd\*\* - <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd_*article_name*</strong>, <strong>MCALL sp_MSupd_*article_name*</strong>값을 지정 합니다. 여기서 _**article_name**_ 은 \*\* \@ 아티클에\*\*지정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-174">**\@upd_cmd** - specify a value of <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd_*article_name*</strong>, <strong>MCALL sp_MSupd_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-175">위 명령 매개 변수마다 복제 시 생성되는 저장 프로시저의 이름을 고유하게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-175">For each of the above command parameters, you can specify your own name for the stored procedures that replication generates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dbc85-176">CALL, SCALL, XCALL 및 MCALL 구문에 대한 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-176">For more information on CALL, SCALL, XCALL, and MCALL syntax, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
     <span data-ttu-id="dbc85-177">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-177">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="dbc85-178">게시 데이터베이스의 게시자에서 [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) 문을 사용하여 삽입, 업데이트 및 삭제 사용자 지정 저장 프로시저에 대한 [CREATE PROCEDURE](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) 스크립트를 반환하도록 [sp_scriptpublicationcustomprocs](/sql/t-sql/statements/create-procedure-transact-sql) 를 편집하면 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-178">At the Publisher on the publication database, use the [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) statement to edit [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) so that it returns a [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) script for the insert, update, and delete custom stored procedures.</span></span> <span data-ttu-id="dbc85-179">자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbc85-179">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-change-the-method-of-propagating-changes-for-an-existing-article"></a><span data-ttu-id="dbc85-180">기존 아티클에 대한 변경 내용 전파 방법을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="dbc85-180">To change the method of propagating changes for an existing article</span></span>  
  
1.  <span data-ttu-id="dbc85-181">게시 데이터베이스의 게시자에서 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-181">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="dbc85-182">**\@publication** 및 **\@article**을 지정하고 **\@property**에 **ins_cmd**, **upd_cmd** 또는 **del_cmd** 값을 지정하고, **\@value**에 적합한 전파 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-182">Specify **\@publication**, **\@article**, a value of **ins_cmd**, **upd_cmd**, or **del_cmd** for **\@property**, and the appropriate propagation method for **\@value**.</span></span>  
  
2.  <span data-ttu-id="dbc85-183">변경하려는 각 전파 방법에 대해 1단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="dbc85-183">Repeat step 1 for each propagation method to be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc85-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbc85-184">See Also</span></span>  
 <span data-ttu-id="dbc85-185">[트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../transactional/transactional-articles-specify-how-changes-are-propagated.md) </span><span class="sxs-lookup"><span data-stu-id="dbc85-185">[Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md) </span></span>  
 [<span data-ttu-id="dbc85-186">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="dbc85-186">Create a publication</span></span>](create-a-publication.md)  
  
  