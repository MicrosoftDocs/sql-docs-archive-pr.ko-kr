---
title: AlwaysOn 보조 데이터베이스에서 데이터 이동 시작 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ce4f80b456244cd6e024377383abe75e002057a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741291"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a><span data-ttu-id="3531a-102">AlwaysOn 보조 데이터베이스에서 데이터 이동 시작(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3531a-102">Start Data Movement on an AlwaysOn Secondary Database (SQL Server)</span></span>
  <span data-ttu-id="3531a-103">이 항목에서는 AlwaysOn 가용성 그룹에 데이터베이스를 추가한 후 데이터 동기화를 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-103">This topic contains information about how to start data synchronization after you add a database to an AlwaysOn availability group.</span></span> <span data-ttu-id="3531a-104">각 새로운 주 복제본에 대해 보조 복제본을 호스팅하는 서버 인스턴스에서 보조 데이터베이스를 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-104">For each new primary replica, secondary databases must be prepared on the server instances that host the secondary replicas.</span></span> <span data-ttu-id="3531a-105">그런 다음 이러한 각 보조 데이터베이스를 가용성 그룹에 수동으로 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-105">Then each of these secondary databases must be manually joined to the availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3531a-106">가용성 그룹의 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 파일 경로가 동일한 경우 [새 가용성 그룹 마법사](use-the-availability-group-wizard-sql-server-management-studio.md), [가용성 그룹에 복제본 추가 마법사](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)또는 [가용성 그룹에 데이터베이스 추가 마법사](availability-group-add-database-to-group-wizard.md) 를 사용하여 데이터 동기화를 자동으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-106">If the file paths are identical on every server instance that hosts an availability replica for an availability group, the [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md) might be able to automatically start data synchronization for you.</span></span>  
  
 <span data-ttu-id="3531a-107">데이터 동기화를 수동으로 시작하려면 가용성 그룹의 보조 복제본을 호스팅하는 각 서버 인스턴스에 차례로 연결하여 다음 단계를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-107">To start data synchronization manually, you need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
1.  <span data-ttu-id="3531a-108">각 주 데이터베이스와 해당 트랜잭션 로그의 현재 백업을 복원합니다(RESTORE WITH NORECOVERY 사용).</span><span class="sxs-lookup"><span data-stu-id="3531a-108">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="3531a-109">다음과 같은 다른 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-109">You can use either of the following alternative approaches:</span></span>  
  
    -   <span data-ttu-id="3531a-110">RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 데이터베이스 백업을 수동으로 복원한 다음 RESTORE WITH NORECOVERY를 사용하여 각 후속 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-110">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="3531a-111">가용성 그룹의 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 이 복원 시퀀스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-111">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  
  
         <span data-ttu-id="3531a-112">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="3531a-112">**For more information:**</span></span>  
  
         [<span data-ttu-id="3531a-113">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-113">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   <span data-ttu-id="3531a-114">하나 이상의 로그 전달 주 데이터베이스를 가용성 그룹에 추가하는 경우 로그 전달에서 하나 이상의 해당 보조 데이터베이스를 AlwaysOn 가용성 그룹으로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-114">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to AlwaysOn Availability Groups.</span></span> <span data-ttu-id="3531a-115">로그 전달 보조 데이터베이스를 마이그레이션하려면 해당 데이터베이스가 주 데이터베이스와 동일한 이름을 사용하고 가용성 그룹에 대한 보조 복제본을 호스팅하는 서버 인스턴스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-115">Migrating a log shipping secondary database requires that it use the same database name as the primary database and that it reside on a server instance that is hosting a secondary replica for the availability group.</span></span> <span data-ttu-id="3531a-116">또한 주 복제본이 백업에 기본적으로 사용되고 백업 수행 대상이 되도록, 즉 백업 우선 순위가 0보다 크도록 가용성 그룹을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-116">Furthermore, the availability group must be configured so that the primary replica is preferred for backups and is a candidate for performing backups (that is, that has a backup priority that is >0).</span></span> <span data-ttu-id="3531a-117">주 데이터베이스에서 백업 작업이 실행되고 나면 백업 작업을 사용하지 않도록 설정하고, 지정된 보조 데이터베이스에서 복원 작업이 실행되고 나면 복원 작업을 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-117">Once the backup job has run on the primary database, you will need to disable the backup job, and once the restore job has run on a given secondary database, you will need to disable the restore job.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3531a-118">가용성 그룹에 대해 모든 보조 데이터베이스를 만든 후에는 보조 복제본에서 백업을 수행할 경우 가용성 그룹의 자동화된 백업 기본 설정을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-118">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
         <span data-ttu-id="3531a-119">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="3531a-119">**For more information:**</span></span>  
  
         [<span data-ttu-id="3531a-120">로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server로 마이그레이션하기 위한 필수 구성 요소&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-120">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [<span data-ttu-id="3531a-121">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-121">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  <span data-ttu-id="3531a-122">새로 준비된 각 보조 데이터베이스를 최대한 빨리 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="3531a-122">As soon as possible, join each newly prepared secondary database to the availability group.</span></span>  
  
     <span data-ttu-id="3531a-123">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="3531a-123">**For more information:**</span></span>  
  
     [<span data-ttu-id="3531a-124">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-124">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="3531a-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3531a-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3531a-126">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-126">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="3531a-127">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-127">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="3531a-128">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-128">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="3531a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3531a-129">See Also</span></span>  
 [<span data-ttu-id="3531a-130">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="3531a-130">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  