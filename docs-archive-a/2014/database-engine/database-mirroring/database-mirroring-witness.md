---
title: 데이터베이스 미러링 모니터 서버 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], about witness
- witness [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: 05606de8-90c3-451a-938d-1ed34211dad7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6ac02e2a5dbe86af72c15c07e14de70b12892b48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647206"
---
# <a name="database-mirroring-witness"></a><span data-ttu-id="41a77-102">Database Mirroring Witness</span><span class="sxs-lookup"><span data-stu-id="41a77-102">Database Mirroring Witness</span></span>
  <span data-ttu-id="41a77-103">자동 장애 조치(Failover)를 지원하려면 데이터베이스 미러링 세션을 보호 우선 모드로 구성해야 하며 *미러링 모니터 서버*라는 세 번째 서버 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-103">To support automatic failover, a database mirroring session must be configured in high-safety mode and also possess a third server instance, known as the *witness*.</span></span> <span data-ttu-id="41a77-104">미러링 모니터 서버는 보호 우선 모드에 있는 미러 서버가 자동 장애 조치의 시작 여부를 인식할 수 있도록 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 선택적 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-104">The witness is an optional instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that enables the mirror server in a high-safety mode session to recognize whether to initiate an automatic failover.</span></span> <span data-ttu-id="41a77-105">미러링 모니터 서버는 두 파트너와는 달리 데이터베이스를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-105">Unlike the two partners, the witness does not serve the database.</span></span> <span data-ttu-id="41a77-106">미러링 모니터 서버는 자동 장애 조치(Failover)를 지원하는 역할만 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-106">Supporting automatic failover is the only role of the witness.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41a77-107">성능 우선 모드에서는 미러링 모니터 서버로 인해 가용성이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-107">In high-performance mode, the witness can adversely affect availability.</span></span> <span data-ttu-id="41a77-108">미러링 모니터 서버가 데이터베이스 미러링 세션에 대해 구성된 경우 주 서버는 다른 서버 인스턴스인 미러 서버나 미러링 모니터 서버 중 하나에 연결되거나 둘 다에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-108">If a witness is configured for a database mirroring session, the principal server must be connected at least to one of the other server instances, the mirror server or the witness, or both of them.</span></span> <span data-ttu-id="41a77-109">그렇지 않으면 데이터베이스를 사용할 수 없게 되며 서비스를 강제(데이터 손실 가능)할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-109">Otherwise, the database becomes unavailable and forcing service (with possible data loss) is impossible.</span></span> <span data-ttu-id="41a77-110">따라서 성능 우선 모드에서는 항상 미러링 모니터 서버를 OFF로 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-110">Therefore, for high-performance mode, we strongly recommend that you always keep the witness set to OFF.</span></span> <span data-ttu-id="41a77-111">성능 우선 모드에서 미러링 모니터 서버의 영향에 대한 자세한 내용은 [데이터베이스 미러링 운영 모드](database-mirroring-operating-modes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41a77-111">For information about the impact of a witness on high-performance mode, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="41a77-112">다음 그림에서는 미러링 모니터 서버가 포함된 보호 우선 모드 세션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-112">The following illustration shows a high-safety mode session with a witness.</span></span>  
  
 <span data-ttu-id="41a77-113">![미러링 모니터 서버가 있는 미러링 세션](../media/dbm-3-way-session-intro.gif "미러링 모니터 서버가 있는 미러링 세션")</span><span class="sxs-lookup"><span data-stu-id="41a77-113">![Mirroring session with a witness](../media/dbm-3-way-session-intro.gif "Mirroring session with a witness")</span></span>  
  
 <span data-ttu-id="41a77-114">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="41a77-114">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="41a77-115">여러 세션에서 미러링 모니터 서버 사용</span><span class="sxs-lookup"><span data-stu-id="41a77-115">Using a Witness in Multiple Sessions</span></span>](#InMultipleSessions)  
  
-   [<span data-ttu-id="41a77-116">소프트웨어 및 하드웨어 권장 사항</span><span class="sxs-lookup"><span data-stu-id="41a77-116">Software and Hardware Recommendations</span></span>](#SwHwRecommendations)  
  
-   [<span data-ttu-id="41a77-117">자동 장애 조치에서의 미러링 모니터 서버 역할</span><span class="sxs-lookup"><span data-stu-id="41a77-117">Role of the Witness in Automatic Failover</span></span>](#InAutoFo)  
  
-   [<span data-ttu-id="41a77-118">미러링 모니터 서버를 추가하거나 제거하려면</span><span class="sxs-lookup"><span data-stu-id="41a77-118">To Add or Remove a Witness</span></span>](#AddRemoveWitness)  
  
##  <a name="using-a-witness-in-multiple-sessions"></a><a name="InMultipleSessions"></a> <span data-ttu-id="41a77-119">여러 세션에서 미러링 모니터 서버 사용</span><span class="sxs-lookup"><span data-stu-id="41a77-119">Using a Witness in Multiple Sessions</span></span>  
 <span data-ttu-id="41a77-120">특정 서버 인스턴스는 동시 데이터베이스 미러링 세션에서 서로 다른 데이터베이스에 대해 미러링 모니터 서버로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-120">A specific server instance can act as a witness in concurrent database mirroring sessions, each for a different database.</span></span> <span data-ttu-id="41a77-121">세션마다 서로 다른 파트너를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-121">Different sessions can be with different partners.</span></span> <span data-ttu-id="41a77-122">다음 그림에서는 서로 다른 파트너를 사용하는 두 개의 데이터베이스 미러링 세션에 속하는 미러링 모니터 서버인 서버 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-122">The following illustration shows a server instance that is a witness in two database mirroring sessions with different partners.</span></span>  
  
 <span data-ttu-id="41a77-123">![두 데이터베이스에 대한 미러링 모니터 서버에 해당하는 서버 인스턴스](../media/dbm-witness-in-2-sessions.gif "두 데이터베이스에 대한 미러링 모니터 서버에 해당하는 서버 인스턴스")</span><span class="sxs-lookup"><span data-stu-id="41a77-123">![Server instance that is a witness for 2 databases](../media/dbm-witness-in-2-sessions.gif "Server instance that is a witness for 2 databases")</span></span>  
  
 <span data-ttu-id="41a77-124">단일 서버 인스턴스는 일부 세션의 미러링 모니터 서버와 다른 세션의 파트너로 동시에 작동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-124">A single-server instance can also function at the same time as a witness in some sessions and a partner in other sessions.</span></span> <span data-ttu-id="41a77-125">그러나 실제로 서버 인스턴스는 대개 미러링 모니터 서버나 파트너 중 하나로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-125">However, in practice, a server instance typically functions as either a witness or a partner.</span></span> <span data-ttu-id="41a77-126">이는 파트너의 경우 프로덕션 데이터베이스를 지원하기 위해 하드웨어 용량이 충분한 고성능 컴퓨터가 필요하지만 미러링 모니터 서버는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 지원하는 모든 사용 가능한 Windows 시스템에서 실행될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-126">This is because the partners require sophisticated computers that have enough hardware to support a production database, whereas the witness can run on any available Windows system that supports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="software-and-hardware-recommendations"></a><a name="SwHwRecommendations"></a> <span data-ttu-id="41a77-127">소프트웨어 및 하드웨어 권장 사항</span><span class="sxs-lookup"><span data-stu-id="41a77-127">Software and Hardware Recommendations</span></span>  
 <span data-ttu-id="41a77-128">미러링 모니터 서버는 파트너와 별도의 컴퓨터에 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-128">We strongly recommend that the witness reside on a separate computer from the partners.</span></span> <span data-ttu-id="41a77-129">데이터베이스 미러링 파트너는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-129">Database mirroring partners are supported only by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard edition and by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition.</span></span> <span data-ttu-id="41a77-130">반대로 미러링 모니터 서버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Workgroup 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-130">Witnesses, in contrast, are also supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Workgroup and by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="41a77-131">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 업그레이드하는 동안을 제외하고 미러링 세션의 서버 인스턴스는 모두 같은 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-131">Except during an upgrade from an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the server instances in a mirroring session must all be running the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="41a77-132">예를 들어 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 미러링 구성에서 업그레이드하는 경우 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 미러링 모니터 서버가 지원되지만 이 미러링 모니터 서버를 기존 또는 새로운 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 이상 버전의 미러링 구성에 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-132">For example, a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] witness is supported when you are upgrading from a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] mirroring configuration but cannot be added to an existing or new [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or later mirroring configuration.</span></span>  
  
 <span data-ttu-id="41a77-133">미러링 모니터 서버는 이러한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전을 지원하는 모든 신뢰할 수 있는 컴퓨터 시스템에서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-133">A witness can run on any reliable computer system that supports any of these editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="41a77-134">그러나 미러링 모니터 서버로 사용되는 모든 서버 인스턴스에는 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard 버전에 필요한 최소 구성을 적용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-134">However, we recommend that every server instance that is used as a witness correspond to the minimum configuration that is required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard version that you are running.</span></span> <span data-ttu-id="41a77-135">이러한 요구 사항에 대 한 자세한 내용은 [SQL Server 2014을 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41a77-135">For more information about these requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
##  <a name="role-of-the-witness-in-automatic-failover"></a><a name="InAutoFo"></a> <span data-ttu-id="41a77-136">자동 장애 조치에서의 미러링 모니터 서버 역할</span><span class="sxs-lookup"><span data-stu-id="41a77-136">Role of the Witness in Automatic Failover</span></span>  
 <span data-ttu-id="41a77-137">데이터베이스 미러링 세션 동안 모든 서버 인스턴스가 해당 연결 상태를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-137">Throughout a database mirroring session, all the server instances monitor their connection status.</span></span> <span data-ttu-id="41a77-138">파트너가 서로 분리되면 미러링 모니터 서버를 통해 둘 중 하나만 데이터베이스를 제공하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-138">If the partners become disconnected from each other, they rely on the witness to make sure that only one of them is currently serving the database.</span></span> <span data-ttu-id="41a77-139">동기화된 미러 서버와 주 서버와의 연결이 끊겼지만 미러링 모니터 서버와의 연결은 지속되는 경우 미러 서버는 미러링 모니터 서버에 연결하여 미러링 모니터 서버와 주 서버와의 연결이 끊겼는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-139">If a synchronized mirror server loses its connection to the principal server but remains connected to the witness, the mirror server contacts the witness to determine whether the witness has lost its connection to the principal server:</span></span>  
  
-   <span data-ttu-id="41a77-140">주 서버가 미러링 모니터 서버에 연결되어 있으면 자동 장애 조치가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-140">If the principal server is still connected to the witness, automatic failover does not occur.</span></span> <span data-ttu-id="41a77-141">대신 주 서버는 파트너가 다시 연결되었을 때 미러 서버로 보낼 로그 레코드를 누적하는 동안 데이터베이스를 계속 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-141">Instead, the principal server continues to server the database while accumulating log records to send the mirror server when the partners reconnect.</span></span>  
  
-   <span data-ttu-id="41a77-142">미러링 모니터 서버와 주 서버와의 연결도 끊어진 경우 미러 서버는 주 데이터베이스를 사용할 수 없는 상태임을 인식하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-142">If the witness is also disconnected from the principal server, the mirror server knows that principal database has become unavailable.</span></span> <span data-ttu-id="41a77-143">이 경우 미러 서버는 자동 장애 조치를 즉시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-143">In this case, the mirror server immediately initiates an automatic failover.</span></span>  
  
-   <span data-ttu-id="41a77-144">미러 서버와 미러링 모니터 서버 및 주 서버와의 연결이 끊어진 경우에는 주 서버의 상태에 관계없이 자동 장애 조치를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-144">If the mirror server is disconnected from the witness and also from the principal server, automatic failover is not possible, regardless of the state of the principal server.</span></span>  
  
 <span data-ttu-id="41a77-145">둘 이상의 서버 인스턴스가 연결되어 있어야 하는 요구 사항을 *쿼럼*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-145">The requirement that at least two of the server instances be connected is known as *quorum*.</span></span> <span data-ttu-id="41a77-146">쿼럼을 사용하면 한 번에 하나의 파트너만 데이터베이스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a77-146">Quorum makes sure that the database can only be served by one partner at a time.</span></span> <span data-ttu-id="41a77-147">쿼럼 작동 방법과 쿼럼이 세션에 미치는 영향에 대한 자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41a77-147">For information about how quorum works and its impact on a session, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
##  <a name="to-add-or-remove-a-witness"></a><a name="AddRemoveWitness"></a> <span data-ttu-id="41a77-148">미러링 모니터 서버를 추가하거나 제거하려면</span><span class="sxs-lookup"><span data-stu-id="41a77-148">To Add or Remove a Witness</span></span>  
 <span data-ttu-id="41a77-149">**미러링 모니터 서버를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="41a77-149">**To add a witness**</span></span>  
  
-   [<span data-ttu-id="41a77-150">데이터베이스 미러링 모니터 서버 추가 또는 바꾸기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="41a77-150">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="41a77-151">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="41a77-151">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
 <span data-ttu-id="41a77-152">**미러링 모니터를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="41a77-152">**To remove the witness**</span></span>  
  
-   [<span data-ttu-id="41a77-153">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41a77-153">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="41a77-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41a77-154">See Also</span></span>  
 <span data-ttu-id="41a77-155">[데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41a77-155">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="41a77-156">[데이터베이스 미러링 운영 모드](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="41a77-156">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="41a77-157">[쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="41a77-157">[Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md) </span></span>  
 <span data-ttu-id="41a77-158">[데이터베이스 미러링 중에 발생 가능한 오류](possible-failures-during-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="41a77-158">[Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md) </span></span>  
 [<span data-ttu-id="41a77-159">미러링 상태&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41a77-159">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  