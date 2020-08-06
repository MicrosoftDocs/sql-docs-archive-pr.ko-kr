---
title: 데이터베이스의 속성 보기 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6aee7503ca02d47575be4e8103641f61d9696d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741063"
---
# <a name="view-or-change-the-properties-of-a-database"></a><span data-ttu-id="5a5a9-102">데이터베이스의 속성 보기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="5a5a9-102">View or Change the Properties of a Database</span></span>
  <span data-ttu-id="5a5a9-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]데이터베이스의 속성을 보거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-103">This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5a5a9-104">데이터베이스 속성을 변경하면 수정 사항이 즉시 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-104">After you change a database property, the modification takes effect immediately.</span></span>  
  
 <span data-ttu-id="5a5a9-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5a5a9-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5a5a9-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5a5a9-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5a5a9-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a5a9-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="5a5a9-108">보안</span><span class="sxs-lookup"><span data-stu-id="5a5a9-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5a5a9-109">**데이터베이스의 속성을 보거나 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="5a5a9-109">**To view or change the properties of a database, using:**</span></span>  
  
     [<span data-ttu-id="5a5a9-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5a5a9-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5a5a9-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5a5a9-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5a5a9-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5a5a9-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5a5a9-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a5a9-113">Recommendations</span></span>  
  
-   <span data-ttu-id="5a5a9-114">AUTO_CLOSE가 ON으로 설정되어 있으면 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 카탈로그 뷰의 일부 열과 DATABASEPROPERTYEX 함수는 데이터베이스에서 데이터를 검색할 수 없는 경우 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-114">When AUTO_CLOSE is ON, some columns in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data.</span></span> <span data-ttu-id="5a5a9-115">이 문제를 해결하려면 USE 문을 실행하여 데이터베이스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-115">To resolve this, execute a USE statement to open the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5a5a9-116">보안</span><span class="sxs-lookup"><span data-stu-id="5a5a9-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5a5a9-117">권한</span><span class="sxs-lookup"><span data-stu-id="5a5a9-117">Permissions</span></span>  
 <span data-ttu-id="5a5a9-118">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5a5a9-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5a5a9-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a><span data-ttu-id="5a5a9-120">데이터베이스의 속성을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5a5a9-120">To view or change the properties of a database</span></span>  
  
1.  <span data-ttu-id="5a5a9-121">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5a5a9-122">**데이터베이스**를 확장하고 확인할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-122">Expand **Databases**, right-click the database to view, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5a5a9-123">**데이터베이스 속성** 대화 상자에서 해당 정보를 확인할 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-123">In the **Database Properties** dialog box, select a page to view the corresponding information.</span></span> <span data-ttu-id="5a5a9-124">예를 들어 데이터 파일 및 로그 파일 정보를 보려면 **파일** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-124">For example, select the **Files** page to view data and log file information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5a5a9-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5a5a9-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a><span data-ttu-id="5a5a9-126">DATABASEPROPERTYEX를 사용하여 데이터베이스의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="5a5a9-126">To view a property of a database by using DATABASEPROPERTYEX</span></span>  
  
1.  <span data-ttu-id="5a5a9-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a5a9-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a5a9-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5a5a9-130">이 예에서는 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 시스템 함수를 사용하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 AUTO_SHRINK 데이터베이스 옵션 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-130">This example uses the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) system function to return the status of the AUTO_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="5a5a9-131">반환 값이 1이면 해당 옵션이 ON으로 설정되어 있고 반환 값이 0이면 해당 옵션이 OFF로 설정되어 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-131">A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a><span data-ttu-id="5a5a9-132">sys.databases를 쿼리하여 데이터베이스의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="5a5a9-132">To view the properties of a database by querying sys.databases</span></span>  
  
1.  <span data-ttu-id="5a5a9-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a5a9-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a5a9-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5a5a9-136">이 예에서는 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 카탈로그 뷰를 쿼리하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 여러 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-136">This example queries the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="5a5a9-137">이 예에서는 데이터베이스 ID 번호(`database_id`), 데이터베이스가 읽기 전용인지 읽기/쓰기인지 여부(`is_read_only`), 데이터베이스의 데이터 정렬(`collation_name`) 및 데이터베이스 호환성 수준(`compatibility_level`)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-137">This example returns the database ID number (`database_id`), whether the database is read-only or read-write (`is_read_only`), the collation for the database (`collation_name`), and the database compatibility level (`compatibility_level`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a><span data-ttu-id="5a5a9-138">데이터베이스의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5a5a9-138">To change the properties of a database</span></span>  
  
1.  <span data-ttu-id="5a5a9-139">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a5a9-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a5a9-141">다음 예를 복사하여 쿼리 창에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-141">Copy and paste the following example into the query window.</span></span> <span data-ttu-id="5a5a9-142">이 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 대한 스냅샷 격리 상태를 확인하고 속성 상태를 변경한 다음 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-142">The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, changes the state of the property, and then verifies the change.</span></span>  
  
     <span data-ttu-id="5a5a9-143">스냅샷 격리 상태를 확인하려면 첫 번째 `SELECT` 문을 선택하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-143">To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="5a5a9-144">스냅샷 격리 상태를 변경하려면 `ALTER DATABASE` 문을 선택하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-144">To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="5a5a9-145">변경 내용을 확인하려면 두 번째 `SELECT` 문을 선택하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5a9-145">To verify the change, select the second `SELECT` statement, and click **Execute**.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a><span data-ttu-id="5a5a9-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a5a9-146">See Also</span></span>  
 <span data-ttu-id="5a5a9-147">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a5a9-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="5a5a9-148">[ALTER DATABASE SET HADR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="5a5a9-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="5a5a9-149">[ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="5a5a9-149">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="5a5a9-150">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="5a5a9-150">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="5a5a9-151">[ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="5a5a9-151">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 [<span data-ttu-id="5a5a9-152">ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5a5a9-152">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
