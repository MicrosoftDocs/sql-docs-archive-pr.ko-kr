---
title: 데이터베이스 백업(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c315c827e1c8b206b2098009510bf6468bd7d74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661196"
---
# <a name="back-up-database-general-page"></a><span data-ttu-id="4a055-102">데이터베이스 백업(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="4a055-102">Back Up Database (General Page)</span></span>
  <span data-ttu-id="4a055-103">**데이터베이스 백업** 대화 상자의 **일반** 페이지를 사용하여 데이터베이스 백업 작업에 대한 설정을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-103">Use the **General** page of the **Back Up Database** dialog box to view or modify settings for a database back up operation.</span></span>  
  
 <span data-ttu-id="4a055-104">기본 백업 개념에 대한 자세한 내용은 [백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-104">For more information about basic backup concepts, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a055-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 백업 태스크를 지정할 때 [!INCLUDE[tsql](../../includes/tsql-md.md)][스크립트](/sql/t-sql/statements/backup-transact-sql) 단추를 클릭한 다음 스크립트에 대한 대상을 선택하여 해당되는 **BACKUP** 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-105">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
 <span data-ttu-id="4a055-106">**SQL Server Management Studio를 사용하여 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="4a055-106">**To use SQL Server Management Studio to create a backup**</span></span>  
  
-   [<span data-ttu-id="4a055-107">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a055-107">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="4a055-108">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a055-108">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a055-109">데이터베이스 유지 관리 계획을 정의하여 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-109">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="4a055-110">자세한 내용은 [온라인 설명서의](../maintenance-plans/maintenance-plans.md) 데이터베이스 유지 관리 계획 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-110">For more information, see [Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="4a055-111">**부분 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="4a055-111">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="4a055-112">부분 백업의 경우 PARTIAL 옵션과 함께 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-112">For a partial backup, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a055-113">옵션</span><span class="sxs-lookup"><span data-stu-id="4a055-113">Options</span></span>  
  
### <a name="source"></a><span data-ttu-id="4a055-114">원본</span><span class="sxs-lookup"><span data-stu-id="4a055-114">Source</span></span>  
 <span data-ttu-id="4a055-115">**원본** 패널의 옵션은 데이터베이스를 식별하고 백업 작업에 대한 구성 요소 및 백업 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-115">The options of the **Source** panel identify the database and specify the backup type and component for the back up operation.</span></span>  
  
 <span data-ttu-id="4a055-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="4a055-116">**Database**</span></span>  
 <span data-ttu-id="4a055-117">백업할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-117">Select the database to back up.</span></span>  
  
 <span data-ttu-id="4a055-118">**복구 모델**</span><span class="sxs-lookup"><span data-stu-id="4a055-118">**Recovery model**</span></span>  
 <span data-ttu-id="4a055-119">선택한 데이터베이스에 대해 표시되는 복구 모델(SIMPLE, FULL 또는 BULK_LOGGED)을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-119">View the recovery model (SIMPLE, FULL, or BULK_LOGGED) displayed for the selected database.</span></span>  
  
 <span data-ttu-id="4a055-120">**백업 유형**</span><span class="sxs-lookup"><span data-stu-id="4a055-120">**Backup type**</span></span>  
 <span data-ttu-id="4a055-121">지정한 데이터베이스에서 수행할 백업 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-121">Select the type of backup you want to perform on the specified database.</span></span>  
  
|<span data-ttu-id="4a055-122">백업 유형</span><span class="sxs-lookup"><span data-stu-id="4a055-122">Backup type</span></span>|<span data-ttu-id="4a055-123">사용 가능한 대상</span><span class="sxs-lookup"><span data-stu-id="4a055-123">Available for</span></span>|<span data-ttu-id="4a055-124">제한</span><span class="sxs-lookup"><span data-stu-id="4a055-124">Restrictions</span></span>|  
|-----------------|-------------------|------------------|  
|<span data-ttu-id="4a055-125">전체</span><span class="sxs-lookup"><span data-stu-id="4a055-125">Full</span></span>|<span data-ttu-id="4a055-126">데이터베이스, 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4a055-126">Databases, files, and filegroups</span></span>|<span data-ttu-id="4a055-127">**master** 데이터베이스에서는 전체 백업만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-127">On the **master** database, only full backups are possible.</span></span><br /><br /> <span data-ttu-id="4a055-128">단순 복구 모델에서는 읽기 전용 파일 그룹에 대해서만 파일 및 파일 그룹 백업을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-128">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="4a055-129">차등</span><span class="sxs-lookup"><span data-stu-id="4a055-129">Differential</span></span>|<span data-ttu-id="4a055-130">데이터베이스, 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="4a055-130">Databases, files, and filegroups</span></span>|<span data-ttu-id="4a055-131">단순 복구 모델에서는 읽기 전용 파일 그룹에 대해서만 파일 및 파일 그룹 백업을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-131">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="4a055-132">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4a055-132">Transaction Log</span></span>|<span data-ttu-id="4a055-133">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4a055-133">Transaction logs</span></span>|<span data-ttu-id="4a055-134">단순 복구 모델에는 트랜잭션 로그 백업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-134">Transaction log backups are not available for the Simple Recovery Model.</span></span>|  
  
 <span data-ttu-id="4a055-135">**복사 전용 백업**</span><span class="sxs-lookup"><span data-stu-id="4a055-135">**Copy Only Backup**</span></span>  
 <span data-ttu-id="4a055-136">복사 전용 백업을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-136">Select to create a copy-only backup.</span></span> <span data-ttu-id="4a055-137">*복사 전용 백업*은 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 시퀀스와 독립적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-137">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="4a055-138">자세한 내용은 [복사 전용 백업&#40;SQL Server&#41;](copy-only-backups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-138">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a055-139">**차등** 옵션을 선택하는 경우 복사 전용 백업을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-139">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
 <span data-ttu-id="4a055-140">**백업 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="4a055-140">**Backup component**</span></span>  
 <span data-ttu-id="4a055-141">백업할 데이터베이스 구성 요소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-141">Select the database component to be backed up.</span></span> <span data-ttu-id="4a055-142">**백업 유형** 목록에서 **트랜잭션 로그** 를 선택한 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-142">If **Transaction Log** is selected in the **Backup type** list, this option is not activated.</span></span>  
  
 <span data-ttu-id="4a055-143">다음 옵션 단추 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-143">Select one of the following option buttons:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a055-144">**Database**</span><span class="sxs-lookup"><span data-stu-id="4a055-144">**Database**</span></span>|<span data-ttu-id="4a055-145">전체 데이터베이스를 백업할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-145">Specifies that the entire database be backed up.</span></span>|  
|<span data-ttu-id="4a055-146">**파일 및 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="4a055-146">**Files and filegroups**</span></span>|<span data-ttu-id="4a055-147">선택한 파일 및/또는 파일 그룹을 백업할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-147">Specifies that the specified files and/or filegroups be backed up.</span></span><br /><br /> <span data-ttu-id="4a055-148">이 옵션을 선택하면 **파일 및 파일 그룹 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-148">Selecting this option, opens the **Select Files and Filegroups** dialog box.</span></span> <span data-ttu-id="4a055-149">백업하려는 파일 그룹이나 파일을 선택하고 **확인**을 클릭하면 **파일 그룹 및 파일** 상자에 선택한 내용이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-149">After you select the filegroups or files you want to back up and click **Ok**, your selections appear in the **Filegroups and files** box.</span></span>|  
  
### <a name="destination"></a><span data-ttu-id="4a055-150">대상</span><span class="sxs-lookup"><span data-stu-id="4a055-150">Destination</span></span>  
 <span data-ttu-id="4a055-151">**대상** 패널의 옵션을 사용하면 백업 작업에 대한 백업 디바이스 유형을 지정하고 기존 논리적 또는 물리적 백업 디바이스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-151">The options of the **Destination** panel allow for you to specify the type of backup device for the back up operation and find an existing logical or physical backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a055-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 디바이스에 대한 자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-152">For information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="4a055-153">**백업할 위치**</span><span class="sxs-lookup"><span data-stu-id="4a055-153">**Back up to**</span></span>  
 <span data-ttu-id="4a055-154">다음 중 백업할 미디어 유형 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-154">Select one of the following types of media to which to back up.</span></span> <span data-ttu-id="4a055-155">**백업할 위치** 목록에 선택한 대상이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-155">The destinations you select appear in the **Back up to** list.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a055-156">**디스크**</span><span class="sxs-lookup"><span data-stu-id="4a055-156">**Disk**</span></span>|<span data-ttu-id="4a055-157">디스크에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-157">Backs up to disk.</span></span> <span data-ttu-id="4a055-158">데이터베이스에 대해 만든 시스템 파일이나 디스크 기반의 논리적 백업 디바이스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-158">This may be a system file or a disk-based logical backup device created for the database.</span></span> <span data-ttu-id="4a055-159">**백업할 위치** 목록에 현재 선택한 디스크가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-159">The currently selected disks appear in the **Back up to** list.</span></span> <span data-ttu-id="4a055-160">백업 작업에 대해 최대 64개의 디스크 디바이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-160">You can select up to 64 disk devices for your backup operation.</span></span>|  
|<span data-ttu-id="4a055-161">**테이프**</span><span class="sxs-lookup"><span data-stu-id="4a055-161">**Tape**</span></span>|<span data-ttu-id="4a055-162">테이프에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-162">Backs up to tape.</span></span> <span data-ttu-id="4a055-163">데이터베이스에 대해 만든 로컬 테이프 드라이브나 테이프 기반의 논리적 백업 디바이스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-163">This may be a local tape drive or a tape-based logical backup device created for the database.</span></span> <span data-ttu-id="4a055-164">**백업할 위치** 목록에 현재 선택한 테이프가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-164">The currently selected tapes appear in the **Back up to** list.</span></span> <span data-ttu-id="4a055-165">최대 개수는 64개입니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-165">The maximum number is 64.</span></span> <span data-ttu-id="4a055-166">서버에 연결된 테이프 디바이스가 없으면 이 옵션이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-166">If there are no tape devices attached to the server, this option is deactivated.</span></span> <span data-ttu-id="4a055-167">**백업할 위치** 목록에 선택한 테이프가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-167">The tapes you select are listed in the **Back up to** list.</span></span><br /><br /> <span data-ttu-id="4a055-168">참고: 테이프 백업 디바이스에 대한 지원은 이후 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-168">Note: Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a055-169">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-169">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>|  
|<span data-ttu-id="4a055-170">**URL**</span><span class="sxs-lookup"><span data-stu-id="4a055-170">**URL**</span></span>|<span data-ttu-id="4a055-171">Azure Blob 저장소에 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-171">Backs up to Azure Blob storage.</span></span>|  
  
 <span data-ttu-id="4a055-172">아래 표시된 다음 옵션 집합은 선택한 대상 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-172">The next set of options displayed depends on the type of destination selected.</span></span> <span data-ttu-id="4a055-173">디스크 또는 테이프를 선택하면 다음 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-173">If you select Disk or Tape, the following options are displayed.</span></span>  
  
 <span data-ttu-id="4a055-174">**추가**</span><span class="sxs-lookup"><span data-stu-id="4a055-174">**Add**</span></span>  
 <span data-ttu-id="4a055-175">**백업할 위치** 목록에 파일이나 디바이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-175">Adds a file or device to the **Back up to** list.</span></span> <span data-ttu-id="4a055-176">로컬 디스크 또는 원격 디스크의 최대 64개의 디바이스로 동시에 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-176">You can back up to 64 devices simultaneously on a local disk or remote disk.</span></span> <span data-ttu-id="4a055-177">원격 디스크에서 파일을 지정하려면 정규화된 UNC(Universal Naming Convention) 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-177">To specify a file on a remote disk, use the fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="4a055-178">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-178">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="4a055-179">**제거**</span><span class="sxs-lookup"><span data-stu-id="4a055-179">**Remove**</span></span>  
 <span data-ttu-id="4a055-180">**백업할 위치** 목록에서 현재 선택한 디바이스를 하나 이상 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-180">Removes one or more currently selected devices from the **Back up to** list.</span></span>  
  
 <span data-ttu-id="4a055-181">**콘텐츠**</span><span class="sxs-lookup"><span data-stu-id="4a055-181">**Contents**</span></span>  
 <span data-ttu-id="4a055-182">선택한 디바이스의 미디어 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-182">Displays the media contents for the selected device.</span></span>  
  
 <span data-ttu-id="4a055-183">URL을 백업 대상으로 선택하면 다음 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-183">If you select URL as the backup destination, the following options are displayed:</span></span>  
  
 <span data-ttu-id="4a055-184">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="4a055-184">**File Name**</span></span>  
 <span data-ttu-id="4a055-185">백업 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-185">Specify the name of the backup file.</span></span>  
  
 <span data-ttu-id="4a055-186">**SQL 자격 증명**</span><span class="sxs-lookup"><span data-stu-id="4a055-186">**SQL credential**</span></span>  
 <span data-ttu-id="4a055-187">Azure Storage에 인증 하는 데 사용 되는 SQL 자격 증명을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-187">Select a SQL Credential used to authenticate to  Azure Storage.</span></span> <span data-ttu-id="4a055-188">사용할 수 있는 기존 SQL 자격 증명이 없는 경우 **만들기** 단추를 클릭하여 새 SQL 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-188">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4a055-189">**만들기** 를 클릭하면 열리는 대화 상자에서는 관리 인증서나 구독용 게시 프로필이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-189">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="4a055-190">관리 인증서나 게시 프로필에 액세스할 수 없는 경우 Transact-SQL이나 SQL Server Management Studio를 사용하여 스토리지 계정 이름을 지정하고 키 정보에 액세스하여 SQL 자격 증명을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-190">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="4a055-191">Transact-sql을 사용 하 여 자격 증명을 만들려면 [이 항목의 샘플 코드를 참조](../security/authentication-access/create-a-credential.md#Credential) 하세요.</span><span class="sxs-lookup"><span data-stu-id="4a055-191">See the sample code in the in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="4a055-192">또는 SQL Server Management Studio를 사용하여 데이터베이스 엔진 인스턴스에서 **보안**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **자격 증명**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-192">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="4a055-193">**ID** 에 대한 스토리지 계정 이름을 지정하고 **암호** 필드에 액세스 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-193">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
 <span data-ttu-id="4a055-194">**Azure Storage 컨테이너**</span><span class="sxs-lookup"><span data-stu-id="4a055-194">**Azure storage container**</span></span>  
 <span data-ttu-id="4a055-195">Azure Storage 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-195">Specify the name of the Azure storage container</span></span>  
  
 <span data-ttu-id="4a055-196">**URL 접두사:**</span><span class="sxs-lookup"><span data-stu-id="4a055-196">**URL prefix:**</span></span>  
 <span data-ttu-id="4a055-197">이는 지정된 Azure 스토리지 컨테이너 이름 및 SQL 자격 증명에 저장된 스토리지 계정 정보를 기반으로 자동 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-197">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="4a055-198">**\<storage account>.blob.core.windows.net** 이외의 형식을 사용하는 도메인을 사용하지 않는 경우 이 필드의 정보를 편집하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4a055-198">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a055-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a055-199">See Also</span></span>  
 <span data-ttu-id="4a055-200">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4a055-200">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="4a055-201">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4a055-201">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="4a055-202">[디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4a055-202">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="4a055-203">[테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4a055-203">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="4a055-204">복구 모델&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4a055-204">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
