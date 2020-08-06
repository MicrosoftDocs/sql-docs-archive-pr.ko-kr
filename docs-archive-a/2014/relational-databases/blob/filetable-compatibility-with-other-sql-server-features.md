---
title: FileTable과 기타 SQL Server 기능 간 호환성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], using with other features
ms.assetid: f12a17e4-bd3d-42b0-b253-efc36876db37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a6ac6668ff362a986646c4e01b1f0e5e722611c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740078"
---
# <a name="filetable-compatibility-with-other-sql-server-features"></a><span data-ttu-id="8aefc-102">FileTable과 기타 SQL Server 기능 간 호환성</span><span class="sxs-lookup"><span data-stu-id="8aefc-102">FileTable Compatibility with Other SQL Server Features</span></span>
  <span data-ttu-id="8aefc-103">FileTable이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 기능과 함께 작동하는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-103">Describes how FileTables work with other features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="alwayson-availability-groups-and-filetables"></a><a name="alwayson"></a> <span data-ttu-id="8aefc-104">AlwaysOn 가용성 그룹과 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-104">AlwaysOn Availability Groups and FileTables</span></span>  
 <span data-ttu-id="8aefc-105">FILESTREAM 또는 FileTable 데이터가 포함된 데이터베이스가 AlwaysOn 가용성 그룹에 속하는 경우</span><span class="sxs-lookup"><span data-stu-id="8aefc-105">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="8aefc-106">FileTable 기능은 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]에서 부분적으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-106">FileTable functionality is partially supported by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="8aefc-107">장애 조치(Failover) 이후 FileTable 데이터는 주 복제본에서 액세스할 수 있지만 FileTable 데이터를 읽기 가능한 보조 복제본에서는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8aefc-108">장애 조치(Failover) 이후 모든 FILESTREAM 기능이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-108">Notice that after a failover all FILESTREAM functionality is supported.</span></span> <span data-ttu-id="8aefc-109">FILESTREAM 데이터는 읽기 가능한 두 보조 복제본 및 새로운 주 복제본에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-109">FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
-   <span data-ttu-id="8aefc-110">FILESTREAM 및 FileTable 함수가 컴퓨터 이름 대신 VNN(가상 네트워크 이름)을 사용하거나 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-110">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="8aefc-111">이러한 함수에 대한 자세한 내용은 [Filestream 및 FileTable 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8aefc-111">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="8aefc-112">파일 시스템 API를 통한 FILESTREAM 또는 FileTable 데이터에 대한 모든 액세스에는 컴퓨터 이름 대신 VNN이 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-112">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="8aefc-113">자세한 내용은 [AlwaysOn 가용성 그룹의 FILESTREAM 및 FileTable&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8aefc-113">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="partitioning-and-filetables"></a><a name="OtherPartitioning"></a> <span data-ttu-id="8aefc-114">분할과 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-114">Partitioning and FileTables</span></span>  
 <span data-ttu-id="8aefc-115">분할은 FileTable에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-115">Partitioning is not supported on FileTables.</span></span> <span data-ttu-id="8aefc-116">여러 FILESTREAM 파일 그룹에 대한 지원을 사용하면 SQL 2008 FILESTREAM과 달리 대부분의 시나리오에서 분할에 의존하지 않고도 순수한 확장 문제를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-116">With the support for multiple FILESTREAM file groups, pure scale-up issues can be handled without having to resort to partitioning  in most scenarios (unlike SQL 2008 FILESTREAMs).</span></span>  
  
##  <a name="replication-and-filetables"></a><a name="OtherRepl"></a> <span data-ttu-id="8aefc-117">복제와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-117">Replication and FileTables</span></span>  
 <span data-ttu-id="8aefc-118">복제 및 관련 기능(트랜잭션 복제, 병합 복제, 변경 데이터 캡처 및 변경 내용 추적 포함)은 FileTable에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-118">Replication and related features (including transactional replication, merge replication, change data capture, and change tracking) are not supported with FileTables.</span></span>  
  
##  <a name="transaction-semantics-and-filetables"></a><a name="OtherIsolation"></a> <span data-ttu-id="8aefc-119">트랜잭션 의미 체계와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-119">Transaction Semantics and FileTables</span></span>  
 <span data-ttu-id="8aefc-120">**Windows 애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="8aefc-120">**Windows applications**</span></span>  
 <span data-ttu-id="8aefc-121">Windows 애플리케이션은 데이터베이스 트랜잭션을 인식하지 못하므로 Windows 쓰기 작업에서는 데이터베이스 트랜잭션의 ACID 속성을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-121">Windows applications do not understand database transactions, so Windows write operations do not provide the ACID properties of a database transaction.</span></span> <span data-ttu-id="8aefc-122">따라서 Windows 업데이트 작업에는 트랜잭션 롤백 및 복구를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-122">Therefore transactional rollbacks and recovery are not possible with Windows update operations.</span></span>  
  
 <span data-ttu-id="8aefc-123">**Transact-SQL 애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="8aefc-123">**Transact-SQL applications**</span></span>  
 <span data-ttu-id="8aefc-124">FileTable의 FILESTREAM(file_stream) 열에서 작동하는 TSQL 애플리케이션의 경우 격리 의미 체계는 일반적인 사용자 테이블의 FILESTREAM 데이터 형식을 사용할 때와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-124">For TSQL applications working on the FILESTREAM (file_stream) column in a FileTable, the isolation semantics are the same as with FILESTREAM datatype in a regular user table.</span></span>  
  
##  <a name="query-notifications-and-filetables"></a><a name="OtherQueryNot"></a> <span data-ttu-id="8aefc-125">쿼리 알림과 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-125">Query Notifications and FileTables</span></span>  
 <span data-ttu-id="8aefc-126">쿼리의 WHERE 절이나 다른 부분에 FileTable의 FILESTREAM 열에 대한 참조를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-126">The query cannot contain reference to the FILESTREAM column in the FileTable, in the WHERE clause or any other part of the query.</span></span>  
  
##  <a name="select-into-and-filetables"></a><a name="OtherSelectInto"></a> <span data-ttu-id="8aefc-127">SELECT INTO와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-127">SELECT INTO and FileTables</span></span>  
 <span data-ttu-id="8aefc-128">FileTable에서 실행된 SELECT INTO 문은 일반적인 테이블의 FILESTREAM 열과 마찬가지로 만들어진 대상 테이블의 FileTable 의미 체계를 전파하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-128">SELECT INTO statements from a FileTable will not propagate the FileTable semantics on the created destination table (just like FILESTREAM columns in a regular table).</span></span> <span data-ttu-id="8aefc-129">모든 대상 테이블 열은 일반적인 열과 같이 동작하며</span><span class="sxs-lookup"><span data-stu-id="8aefc-129">All the destination table columns will behave just like normal columns.</span></span> <span data-ttu-id="8aefc-130">FileTable 의미 체계가 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-130">They will not have any FileTable semantics associated with them.</span></span>  
  
##  <a name="triggers-and-filetables"></a><a name="OtherTriggers"></a> <span data-ttu-id="8aefc-131">트리거와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-131">Triggers and FileTables</span></span>  
 <span data-ttu-id="8aefc-132">**DDL(데이터 정의 언어) 트리거**</span><span class="sxs-lookup"><span data-stu-id="8aefc-132">**DDL (Data Definition Language) Triggers**</span></span>  
 <span data-ttu-id="8aefc-133">DDL 트리거의 경우 FileTable과 관련하여 특별히 고려해야 할 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-133">There are no special considerations for DDL triggers with FileTables.</span></span> <span data-ttu-id="8aefc-134">일반적인 DDL 트리거는 CREATE/ALTER DATABASE 작업과 FileTable에 대한 CREATE/ALTER TABLE 작업이 수행될 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-134">Normal DDL triggers will fire for Create/Alter database operations as well as CREATE/ALTER TABLE operations for FileTables.</span></span> <span data-ttu-id="8aefc-135">트리거는 EVENTDATA() 함수를 호출하여 DDL 명령 텍스트 및 기타 정보를 비롯한 실제 이벤트 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-135">Triggers can retrieve the actual event data that includes the DDL command text and other information by calling the EVENTDATA() function.</span></span> <span data-ttu-id="8aefc-136">기존 Eventdata 스키마에 대한 새 이벤트나 변경 내용은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-136">There are no new events or changes to the existing Eventdata schema.</span></span>  
  
 <span data-ttu-id="8aefc-137">**DML(데이터 조작 언어) 트리거**</span><span class="sxs-lookup"><span data-stu-id="8aefc-137">**DML (Data Manipulation Language) Triggers**</span></span>  
 <span data-ttu-id="8aefc-138">트리거를 만드는 DDL 작업 중에는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-138">These restrictions will be enforced during the DDL operation to create triggers.</span></span>  
  
-   <span data-ttu-id="8aefc-139">FileTable은 DML 작업에 대한 INSTEAD OF 트리거를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-139">FileTables will NOT support INSTEAD OF triggers for DML operations.</span></span> <span data-ttu-id="8aefc-140">이는 FILESTREAM 열이 포함된 모든 테이블에 적용되던 기존 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-140">This is an existing restriction on all tables that contain FILESTREAM columns.</span></span>  
  
-   <span data-ttu-id="8aefc-141">FileTable은 DML 작업에 대한 AFTER 트리거를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-141">FileTables will support AFTER triggers for DML operations.</span></span>  
  
-   <span data-ttu-id="8aefc-142">FileTable에 정의된 트리거는 부모 FileTable을 포함하여 모든 FileTable을 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-142">Triggers defined on a FileTable cannot update any FileTables (including the parent FileTable).</span></span> <span data-ttu-id="8aefc-143">이 제한 사항은 주로 동일한 트랜잭션의 파일 시스템 액세스가 보유하는 잠금으로 인해 트리거와의 잠금 충돌이 발생하지 않도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-143">This restriction exists mainly to prevent a trigger from getting into locking conflicts with the locks held by the file system access in the same transaction.</span></span>  
  
 <span data-ttu-id="8aefc-144">**비트랜잭션 액세스 및 이러한 액세스가 트리거에 미치는 영향**</span><span class="sxs-lookup"><span data-stu-id="8aefc-144">**Non-transactional access and its effects on triggers**</span></span>  
 -   <span data-ttu-id="8aefc-145">데이터베이스에서 비트랜잭션 업데이트 액세스가 허용되는 경우 해당 데이터베이스의 FileTable을 비롯하여 모든 테이블에 있는 FILESTREAM 데이터를 현재 위치에서 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-145">When non-transactional update access is allowed in a database, it is possible to do in-place update of the FILESTREAM data in any table, including FileTable in that database.</span></span> <span data-ttu-id="8aefc-146">이러한 가능성 때문에 FILESTREAM 내용의 이전 이미지를 트리거에서 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-146">Due to this possibility, the before image of the FILESTREAM contents may not be available for use by the trigger.</span></span>  
  
-   <span data-ttu-id="8aefc-147">파일 시스템을 통한 비트랜잭션 업데이트 작업의 경우 SQL Server에서는 내부 트랜잭션을 만들어 CloseHandle 작업을 캡처하며, 이 트랜잭션의 일부로 정의된 DML 트리거가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-147">For non-transactional update operations through File system, SQL Server will create an internal transaction to capture the CloseHandle operation and the any defined DML triggers may be fired as part of that transaction.</span></span> <span data-ttu-id="8aefc-148">트리거 본문 내부의 트랜잭션에 대한 롤백은 금지되지는 않지만 FILESTREAM의 변경 내용은 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-148">A rollback such a transaction inside the trigger body, while not prevented, does not roll back the changes done to the FILESTREAM.</span></span>  <span data-ttu-id="8aefc-149">이러한 롤백은 FILESTREAM 내용이 변경된 경우에도 Update 트리거가 실행되지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-149">Such a rollback may also prevent the Update triggers from being fired, even though the FILESTREAM contents may have been changed.</span></span>  
  
-   <span data-ttu-id="8aefc-150">이러한 영향 이외에도 FileTable의 트리거는 두 가지 동작을 더 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-150">In addition to these impacts, triggers on FileTables need to deal with couple of additional behaviors</span></span>  
  
    -   <span data-ttu-id="8aefc-151">파일 시스템을 통해 FileTable에 대한 비트랜잭션 업데이트 작업을 수행하는 경우 FILESTREAM 내용이 다른 Win32 작업에 의해 배타적으로 잠겨 트리거 본문을 통한 읽기/쓰기 액세스가 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-151">In case of non-transactional update operations on FileTable through the File system, it is possible that the FILESTREAM contents may be exclusively locked by other Win32 operations and may not be accessible for read/write through the trigger body.</span></span> <span data-ttu-id="8aefc-152">이 경우 트리거 본문 내의 FILESTREAM 내용에 액세스하려고 하면 "공유 위반 오류"가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-152">In such cases, any attempt to access the FILESTREAM contents within the trigger body may give a "Sharing Violation" error.</span></span> <span data-ttu-id="8aefc-153">이러한 오류를 적절히 처리하도록 트리거를 디자인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-153">Triggers should be designed to handle such errors appropriately.</span></span>  
  
    -   <span data-ttu-id="8aefc-154">일부 경우에는 파일 시스템 액세스에 공유 모드가 허용되어 있어서 다른 비트랜잭션 업데이트 작업에서 동시에 쓰기 작업을 수행할 수 있으므로 FILESTREAM의 AFTER 이미지는 안정적이지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-154">AFTER image of the FILESTREAM may not be stable since in some cases it may be actively being written by other non-transactional updates at the same time (due to the sharing modes permitted in the File system access).</span></span>  
  
-   <span data-ttu-id="8aefc-155">관리 작업이나 데이터베이스 충돌로 인해 Win32 핸들이 명시적으로 중지된 경우와 같이 Win32 핸들이 비정상적으로 종료된 경우에는 이 비정상적으로 종료된 Win32 애플리케이션에서 FILESTREAM 내용을 변경했더라도 복구 작업 중 사용자 트리거가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-155">Abnormal termination of Win32 handles, like explicit killing of Win32 handles by an admin OR a database crash, will not execute user triggers during the recovery operations, even though the FILESTREAM content may have been changed by the abnormally terminated Win32 application.</span></span>  
  
##  <a name="views-and-filetables"></a><a name="OtherViews"></a> <span data-ttu-id="8aefc-156">뷰와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-156">Views and FileTables</span></span>  
 <span data-ttu-id="8aefc-157">**뷰**</span><span class="sxs-lookup"><span data-stu-id="8aefc-157">**Views**</span></span>  
 <span data-ttu-id="8aefc-158">다른 테이블과 마찬가지로 FileTable에서도 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-158">A view can be created on a FileTable as on any other table.</span></span> <span data-ttu-id="8aefc-159">그러나 FileTable에서 만든 뷰에는 다음 고려 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-159">However the following considerations apply to a view created on a FileTable:</span></span>  
  
-   <span data-ttu-id="8aefc-160">뷰에는 FileTable 의미 체계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-160">View will not have any FileTable semantics.</span></span> <span data-ttu-id="8aefc-161">즉, 파일 특성 열을 비롯한 뷰의 열은 특별한 의미 체계가 없는 일반적인 뷰 열처럼 동작하며, 이는 파일/디렉터리를 나타내는 행에도 동일하게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-161">i.e. the columns in the view (including File Attribute columns) behave just like normal view columns without any special semantics and same is true for rows representing Files/directories.</span></span>  
  
-   <span data-ttu-id="8aefc-162">"업데이트 가능한 뷰" 의미 체계에 따라 뷰를 업데이트할 수 있지만 테이블에서와 마찬가지로 기본 테이블 제약 조건에 따라 업데이트가 거부될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-162">View may be updateable based on the "updateable view" semantics, but the underlying table constraints can reject the updates just like in the table.</span></span>  
  
-   <span data-ttu-id="8aefc-163">파일의 경로를 뷰의 명시적 열로 추가하여 뷰에 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-163">File path for a file can be visualized in the view by adding it as an explicit column in the view.</span></span> <span data-ttu-id="8aefc-164">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-164">For example:</span></span>  
  
     `CREATE VIEW MP3FILES AS SELECT column1, column2, ..., GetFileNamespacePath() AS PATH, column3,...  FROM Documents`  
  
 <span data-ttu-id="8aefc-165">**인덱싱된 뷰**</span><span class="sxs-lookup"><span data-stu-id="8aefc-165">**Indexed Views**</span></span>  
 <span data-ttu-id="8aefc-166">현재 인덱싱된 뷰에는 FILESTREAM 열이나 FILESTREAM 열에 종속된 계산/지속형 계산 열이 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-166">Currently Indexed views cannot include FILESTREAM columns or computed/persisted computed columns that depend on the FILESTREAM columns.</span></span> <span data-ttu-id="8aefc-167">이 동작은 FileTable에 정의된 뷰에도 그대로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-167">This behavior remains unchanged with views defined on the FileTable also.</span></span>  
  
##  <a name="snapshot-isolation-and-filetables"></a><a name="OtherSnapshots"></a> <span data-ttu-id="8aefc-168">스냅샷 격리와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-168">Snapshot Isolation and FileTables</span></span>  
 <span data-ttu-id="8aefc-169">RCSI(커밋된 읽기 스냅샷 격리)와 SI(스냅샷 격리)는 데이터에 대한 업데이트 작업이 수행 중인 경우에도 판독기에서 데이터의 스냅샷을 사용할 수 있도록 하는 기능에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-169">Read Committed Snapshot Isolation (RCSI) and Snapshot Isolation (SI) rely on the ability to have a snapshot of the data available for readers even when update operations are happening on the data.</span></span> <span data-ttu-id="8aefc-170">그러나 FileTable을 사용하면 Filestream 데이터에 대한 비트랜잭션 쓰기 액세스가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-170">However FileTables allow non-transactional write access to Filestream data.</span></span> <span data-ttu-id="8aefc-171">따라서 FileTable이 포함된 데이터베이스에서 이러한 기능을 사용하는 경우에는 다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-171">As a result, the following restrictions apply to the use of these features in databases that contain FileTables:</span></span>  
  
-   <span data-ttu-id="8aefc-172">FileTable이 포함된 데이터베이스를 변경하여 RCSI/SI를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-172">A database that contains FileTables can be altered to enable RCSI/SI.</span></span>  
  
-   <span data-ttu-id="8aefc-173">데이터베이스에 대해 비트랜잭션 액세스가 FULL로 설정된 경우 트랜잭션이 RCSI에서 실행되거나 SI가 다음과 같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-173">When non_transactional access is set to FULL for the database, then a transaction running under RCSI or SI has the following behavior:</span></span>  
  
    -   <span data-ttu-id="8aefc-174">FileTable의 file_stream 열에 대한 모든 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 읽기가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-174">Any [!INCLUDE[tsql](../../../includes/tsql-md.md)] reads of the FileTable file_stream column fail.</span></span> <span data-ttu-id="8aefc-175">file_stream 열에 대한 INSERT 및 UPDATE는 해당 열에서 읽는 경우만 아니면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-175">INSERT and UPDATE to the column still succeed, as long as they do not read from the file_stream column.</span></span>  
  
    -   <span data-ttu-id="8aefc-176">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문에서 READCOMMITTEDLOCK 테이블 힌트를 지정한 경우 읽기가 성공하며, 행 버전 관리를 사용하는 대신 행에 대한 잠금이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-176">If the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement specifies READCOMMITTEDLOCK table hints, the reads succeed, and take locks on the rows, rather than use row versioning.</span></span>  
  
    -   <span data-ttu-id="8aefc-177">트랜잭션된 Win32 FileStream 열기 요청도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-177">Transacted Win32 FileStream open requests also fail.</span></span>  
  
    -   <span data-ttu-id="8aefc-178">트랜잭션되지 않은 FileTable Win32 액세스는 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-178">Non-transacted FileTable Win32 access succeeds.</span></span> <span data-ttu-id="8aefc-179">FileTable이 수행한 모든 내부 쿼리는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-179">All internal queries done by FileTable are not affected.</span></span>  
  
    -   <span data-ttu-id="8aefc-180">전체 텍스트 인덱싱은 데이터베이스 옵션이 READ_COMMITTED_SNAPSHOT이든 ALLOW_SNAPSHOT_ISOLATION이든 관계없이 항상 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-180">Fulltext indexing always succeeds, no matter what the database options are (READ_COMMITTED_SNAPSHOT or ALLOW_SNAPSHOT_ISOLATION).</span></span>  
  
##  <a name="readable-secondary-databases"></a><a name="readsec"></a> <span data-ttu-id="8aefc-181">읽기 가능한 보조 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="8aefc-181">Readable Secondary Databases</span></span>  
 <span data-ttu-id="8aefc-182">읽기 가능한 보조 데이터베이스에는 이전 섹션인 [스냅샷 격리와 FileTable](#OtherSnapshots)에 설명된 것처럼 스냅샷과 동일한 고려 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-182">The same considerations apply to readable secondary databases as to snapshots, as described in the preceding section, [Snapshot Isolation and FileTables](#OtherSnapshots).</span></span>  
  
##  <a name="contained-databases-and-filetables"></a><a name="CDB"></a> <span data-ttu-id="8aefc-183">포함된 데이터베이스와 FileTable</span><span class="sxs-lookup"><span data-stu-id="8aefc-183">Contained Databases and FileTables</span></span>  
 <span data-ttu-id="8aefc-184">FileTable 기능이 종속되는 FILESTREAM 기능을 사용하려면 데이터베이스 외부에서의 몇 가지 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-184">The FILESTREAM feature on which the FileTable feature depends requires some configuration outside of the database.</span></span> <span data-ttu-id="8aefc-185">따라서 FILESTREAM 또는 FileTable을 사용하는 데이터베이스는 완전히 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-185">Therefore a database that uses FILESTREAM or FileTable is not fully contained.</span></span>  
  
 <span data-ttu-id="8aefc-186">포함된 사용자와 같은 포함된 데이터베이스의 특정 기능을 사용하려면 데이터베이스 포함 옵션을 PARTIAL로 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-186">You can set database containment to PARTIAL if you want to use certain features of contained databases, such as contained users.</span></span> <span data-ttu-id="8aefc-187">그러나 이 경우 일부 데이터베이스 설정은 데이터베이스에 포함되지 않으며 데이터베이스를 이동할 때 자동으로 이동되지 않는다는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aefc-187">In this case, however, you must be aware that some of the database settings are not contained in the database and are not automatically moved when the database moves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aefc-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8aefc-188">See Also</span></span>  
 [<span data-ttu-id="8aefc-189">FileTable 관리</span><span class="sxs-lookup"><span data-stu-id="8aefc-189">Manage FileTables</span></span>](manage-filetables.md)  
  
  