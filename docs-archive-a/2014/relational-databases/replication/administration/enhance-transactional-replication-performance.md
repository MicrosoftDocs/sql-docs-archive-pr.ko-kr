---
title: 트랜잭션 복제 성능 향상 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741872"
---
# <a name="enhance-transactional-replication-performance"></a><span data-ttu-id="700cd-102">트랜잭션 복제 성능 향상</span><span class="sxs-lookup"><span data-stu-id="700cd-102">Enhance Transactional Replication Performance</span></span>
  <span data-ttu-id="700cd-103">[일반적인 복제 성능 향상](enhance-general-replication-performance.md)에 설명된 일반 성능 팁을 살펴본 후에 트랜잭션 복제에 해당하는 이러한 추가 영역을 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="700cd-103">After considering the general performance tips described in [Enhancing General Replication Performance](enhance-general-replication-performance.md), consider these additional areas specific to transactional replication.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="700cd-104">데이터베이스 디자인</span><span class="sxs-lookup"><span data-stu-id="700cd-104">Database Design</span></span>  
  
-   <span data-ttu-id="700cd-105">애플리케이션 디자인에서 트랜잭션 크기를 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-105">Minimize transaction size in your application design.</span></span>  
  
     <span data-ttu-id="700cd-106">기본적으로 트랜잭션 복제는 트랜잭션 경계에 따라 변경 내용을 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-106">By default, transactional replication propagates changes according to transaction boundaries.</span></span> <span data-ttu-id="700cd-107">트랜잭션이 작을수록 배포 에이전트가 네트워크 문제로 인해 트랜잭션을 다시 전송해야 할 확률이 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-107">If transactions are smaller, it is less likely that the Distribution Agent will have to resend a transaction due to network issues.</span></span> <span data-ttu-id="700cd-108">에이전트가 트랜잭션을 다시 전송해야 할 경우 보내는 데이터 양은 적어집니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-108">If the agent is required to resend a transaction, the amount of data sent is smaller.</span></span>  
  
## <a name="distributor-configuration"></a><span data-ttu-id="700cd-109">배포자 구성</span><span class="sxs-lookup"><span data-stu-id="700cd-109">Distributor Configuration</span></span>  
  
-   <span data-ttu-id="700cd-110">전용 서버에서 배포자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-110">Configure the Distributor on a dedicated server.</span></span>  
  
     <span data-ttu-id="700cd-111">원격 배포자를 구성하여 게시자에서 처리 오버헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-111">You can reduce processing overhead on the Publisher by configuring a remote Distributor.</span></span> <span data-ttu-id="700cd-112">자세한 내용은 [Configure Distribution](../configure-distribution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="700cd-112">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
-   <span data-ttu-id="700cd-113">배포 데이터베이스 크기를 적절히 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-113">Size the distribution database appropriately.</span></span>  
  
     <span data-ttu-id="700cd-114">시스템에서 명령 저장에 필요한 공간을 결정할 수 있도록 일반적인 로드 상태에서 복제를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-114">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="700cd-115">데이터베이스는 자주 자동 증가되지 않고도 명령을 저장할 수 있을 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-115">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="700cd-116">데이터베이스의 크기 변경에 대한 자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="700cd-116">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="700cd-117">게시 디자인</span><span class="sxs-lookup"><span data-stu-id="700cd-117">Publication Design</span></span>  
  
-   <span data-ttu-id="700cd-118">게시된 테이블을 일괄로 업데이트할 때 저장 프로시저 실행을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-118">Replicate stored procedure execution when making batch updates to published tables.</span></span>  
  
     <span data-ttu-id="700cd-119">구독자의 다수 행에 가끔씩 영향을 미치는 일괄 처리 업데이트가 있는 경우 저장 프로시저를 사용하여 게시된 테이블을 업데이트하고 저장 프로시저의 실행을 게시해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="700cd-119">If you have batch updates that occasionally affect a large number of rows at the Subscriber, you should consider updating the published table using a stored procedure and publish the execution of the stored procedure.</span></span> <span data-ttu-id="700cd-120">배포 에이전트는 영향을 받은 모든 행의 업데이트나 삭제를 보내는 대신 구독자에서 같은 매개 변수 값으로 동일한 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-120">Instead of sending an update or delete for every row affected, the Distribution Agent executes the same procedure at the Subscriber with the same parameter values.</span></span> <span data-ttu-id="700cd-121">자세한 내용은 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="700cd-121">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="700cd-122">여러 게시 간에 아티클을 분산시킵니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-122">Spread articles across multiple publications.</span></span>  
  
     <span data-ttu-id="700cd-123">**-SubscriptionStreams** 매개 변수(이 항목의 뒷부분에 설명됨)를 사용할 수 없는 경우 여러 게시를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="700cd-123">If you cannot use the **-SubscriptionStreams** parameter (described later in this topic), consider creating multiple publications.</span></span> <span data-ttu-id="700cd-124">이러한 게시에 아티클을 분산시키면 복제가 구독자에게 변경 내용을 병렬로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-124">Spreading articles across these publications allows replication to apply changes in parallel to Subscribers.</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="700cd-125">구독 고려 사항</span><span class="sxs-lookup"><span data-stu-id="700cd-125">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="700cd-126">같은 게시자에 여러 게시가 있을 경우 공유 에이전트가 아닌 독립 에이전트를 사용합니다. 새 게시 마법사에서는 이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-126">Use independent agents rather than shared agents if you have multiple publications on the same Publisher (this is the default for the New Publication Wizard).</span></span>  
  
-   <span data-ttu-id="700cd-127">에이전트를 잦은 간격으로 실행하는 대신 계속 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-127">Run agents continuously instead of on very frequent schedules.</span></span>  
  
     <span data-ttu-id="700cd-128">일정을 분 단위처럼 자주 실행하도록 설정하는 대신 계속 실행되도록 설정하면 에이전트를 시작하고 중지할 필요가 없으므로 복제 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-128">Setting the agents to run continuously rather than creating frequent schedules (such as every minute) improves replication performance, because the agent does not have to start and stop.</span></span> <span data-ttu-id="700cd-129">배포 에이전트가 계속 실행되도록 설정하면 변경 내용이 토폴로지에 연결된 다른 서버로 짧은 대기 시간 내에 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-129">When you set the Distribution Agent to run continuously, changes are propagated with low latency to the other servers that are connected in the topology.</span></span> <span data-ttu-id="700cd-130">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="700cd-130">For more information, see:</span></span>  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="700cd-131">: [동기화 일정 지정](../specify-synchronization-schedules.md)</span><span class="sxs-lookup"><span data-stu-id="700cd-131">: [Specify Synchronization Schedules](../specify-synchronization-schedules.md)</span></span>  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a><span data-ttu-id="700cd-132">배포 에이전트 및 로그 판독기 에이전트 매개 변수</span><span class="sxs-lookup"><span data-stu-id="700cd-132">Distribution Agent and Log Reader Agent Parameters</span></span>  
  
-   <span data-ttu-id="700cd-133">실수로 인 한 문제를 해결 하기 위해 로그 판독기 에이전트에 **-MaxCmdsInTran** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-133">To resolve accidental, one-time bottlenecks use the **-MaxCmdsInTran** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="700cd-134">**-MaxCmdsInTran** 매개 변수는 로그 판독기가 배포 데이터베이스에 명령을 쓸 때 트랜잭션으로 그룹화 된 최대 문 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-134">The **-MaxCmdsInTran** parameter specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="700cd-135">이 매개 변수를 사용하면 구독자에서 명령을 적용할 때 로그 판독기 에이전트와 배포 에이전트가 게시자에서 큰 트랜잭션(여러 명령으로 구성됨)을 여러 개의 작은 트랜잭션으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-135">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applying commands at the Subscriber.</span></span> <span data-ttu-id="700cd-136">이 매개 변수를 지정하면 배포자에서 경합을 줄일 수 있고 게시자와 구독자 간 대기 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-136">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="700cd-137">원래 트랜잭션이 작은 단위로 적용되므로 구독자는 엄격한 트랜잭션 원자성을 깨고 원래 트랜잭션이 끝나기 전에 큰 논리적 게시자 트랜잭션의 행에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-137">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="700cd-138">기본값은 **0**으로 게시자의 트랜잭션 경계를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-138">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span> <span data-ttu-id="700cd-139">이 매개 변수는 Oracle 게시자에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-139">This parameter does not apply to Oracle Publishers.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="700cd-140">`MaxCmdsInTran`은 항상 설정되도록 설계되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-140">`MaxCmdsInTran` was not designed to be always turned on.</span></span> <span data-ttu-id="700cd-141">단일 트랜잭션에 많은 DML 작업을 실수로 수행한 경우의 문제(전체 트랜잭션이 배포 데이터베이스에 있고 잠금이 보유될 때까지 명령 배포에 지연 발생)를 해결하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-141">It exists to work around cases where someone accidentally performed a large number of DML operations in a single transaction (causing delay in distribution of commands until the entire transaction is in distribution database, locks being held, etc.).</span></span> <span data-ttu-id="700cd-142">정기적으로 이 상황이 발생하는 경우 애플리케이션을 검토하고 트랜잭션 크기를 줄일 수 있는 방법을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-142">If you routinely fall into this situation, you should review your applications and find ways to reduce the transaction size.</span></span>  
  
-   <span data-ttu-id="700cd-143">배포 에이전트에 **-subscriptionstreams** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-143">Use the **-SubscriptionStreams** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="700cd-144">**-Subscriptionstreams** 매개 변수는 집계 복제 처리량을 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-144">The **-SubscriptionStreams** parameter can greatly improve aggregate replication throughput.</span></span> <span data-ttu-id="700cd-145">이 매개 변수는 변경 내용의 일괄 처리를 병렬로 적용하기 위해 구독자에 여러 연결을 설정하도록 허용하지만 단일 스레드를 사용할 때 나타나는 여러 가지 트랜잭션 특징을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-145">It allows multiple connections to a Subscriber to apply batches of changes in parallel, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="700cd-146">여러 연결 중 하나가 실행 또는 커밋되지 않으면 모든 연결에서 현재 일괄 처리를 중지하고 에이전트가 단일 스트림을 사용하여 실패한 일괄 처리를 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-146">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="700cd-147">이러한 재시도 단계가 완료되기 전에는 구독자에 임시 트랜잭션 불일치가 발생할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="700cd-147">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="700cd-148">실패한 일괄 처리가 성공적으로 커밋되면 구독자의 트랜잭션 일관성이 다시 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-148">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
     <span data-ttu-id="700cd-149">[Transact-sql&#41;sp_addsubscription &#40;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) \*\* \@ subscriptionstreams\*\* 을 사용 하 여이 에이전트 매개 변수의 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-149">A value for this agent parameter can be specified using the **\@subscriptionstreams** of [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span>  
  
-   <span data-ttu-id="700cd-150">로그 판독기 에이전트에 대해 **-ReadBatchSize** 매개 변수의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-150">Increase the value of the **-ReadBatchSize** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="700cd-151">로그 판독기 에이전트와 배포 에이전트는 트랜잭션 읽기 및 커밋 작업을 위한 일괄 처리 크기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-151">The Log Reader Agent and Distribution Agent support batch sizes for transaction read and commit operations.</span></span> <span data-ttu-id="700cd-152">일괄 처리 크기는 기본적으로 500개 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-152">Batch sizes default to 500 transactions.</span></span> <span data-ttu-id="700cd-153">로그 판독기 에이전트는 트랜잭션의 복제 표시 여부에 상관없이 로그에서 특정 트랜잭션 수를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-153">The Log Reader Agent reads the specific number of transactions from the log, whether or not they are marked for replication.</span></span> <span data-ttu-id="700cd-154">많은 트랜잭션이 게시 데이터베이스에 기록되는데 그 중 일부 하위 집합만이 복제용으로 표시되는 경우 **-ReadBatchSize** 매개 변수를 사용하여 로그 판독기 에이전트의 읽기 일괄 처리 크기를 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-154">When a large number of transactions is written to a publication database, but only a small subset of those are marked for replication, you should use the **-ReadBatchSize** parameter to increase the read batch size of the Log Reader Agent.</span></span> <span data-ttu-id="700cd-155">이 매개 변수는 Oracle 게시자에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-155">This parameter does not apply to Oracle Publishers.</span></span>  
  
-   <span data-ttu-id="700cd-156">배포 에이전트에 대해 **-CommitBatchSize** 매개 변수의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-156">Increase the value of the **-CommitBatchSize** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="700cd-157">트랜잭션 세트를 커밋할 때 오버헤드는 고정되어 있습니다. 그러므로 다수의 트랜잭션을 커밋하는 횟수를 줄이면 오버헤드가 대량의 데이터에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-157">Committing a set of transactions has a fixed overhead; by committing a larger number of transactions less frequently, the overhead is spread across a larger volume of data.</span></span> <span data-ttu-id="700cd-158">그러나 변경 내용 적용 비용은 로그가 포함된 디스크의 최대 I/O와 같은 다른 요인에 의해 제어되므로 이 매개 변수를 늘려서 얻을 수 있는 장점이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-158">However, the benefit of increasing this parameter drops off as the cost of applying changes is gated by other factors, such as the maximum I/O of the disk that contains the log.</span></span> <span data-ttu-id="700cd-159">또한 배포 에이전트를 다시 시작해야 하는 오류가 발생할 경우 많은 수의 트랜잭션을 롤백하고 다시 적용해야 한다는 것을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-159">Additionally, there is a trade off to be considered: any failure that causes the Distribution Agent to start over must rollback and reapply a larger number of transactions.</span></span> <span data-ttu-id="700cd-160">네트워크가 불안정한 경우 값을 낮게 설정하면 오류 발생 빈도가 줄어들고 오류가 발생해도 적은 수의 트랜잭션을 롤백하고 다시 적용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-160">For unreliable networks, a lower value can result in less failures and a smaller number of transactions to rollback and reapply if a failure occurs.</span></span>  
  
-   <span data-ttu-id="700cd-161">로그 판독기 에이전트에 대해 **-PollingInterval** 매개 변수의 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-161">Decrease the value of the **-PollingInterval** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="700cd-162">**-PollingInterval** 매개 변수는 게시된 데이터베이스의 트랜잭션 로그에서 복제할 트랜잭션을 쿼리할 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-162">The **-PollingInterval** parameter specifies how often the transaction log of a published database is queried for transactions to replicate.</span></span> <span data-ttu-id="700cd-163">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-163">The default is 5 seconds.</span></span> <span data-ttu-id="700cd-164">이 값을 줄이면 로그가 더 자주 폴링되므로 게시 데이터베이스에서 배포 데이터베이스로 트랜잭션을 배달할 때 대기 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-164">If you decrease this value, the log is polled more frequently, which can result in lower latency for the delivery of transactions from the publication database to the distribution database.</span></span> <span data-ttu-id="700cd-165">그러나 자주 폴링하면 서버의 로드가 증가하므로 적절한 대기 시간과 서버 로드 간의 균형을 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-165">However, you should balance the need for lower latency against the increased load on the server from polling more frequently.</span></span>  
  
 <span data-ttu-id="700cd-166">에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="700cd-166">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="700cd-167">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="700cd-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="700cd-168">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="700cd-168">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
-   [<span data-ttu-id="700cd-169">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="700cd-169">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [<span data-ttu-id="700cd-170">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="700cd-170">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
  