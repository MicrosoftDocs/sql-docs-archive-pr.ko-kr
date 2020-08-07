---
title: SQL Server Profiler 템플릿 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- default SQL Server Profiler templates
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- predefined templates [SQL Server Profiler]
- SQL Server Profiler, templates
ms.assetid: b674e491-dc58-47a1-acdd-7028e9a201fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 989ae2df3b34f846f78942009d99ede39367dc0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647405"
---
# <a name="sql-server-profiler-templates"></a><span data-ttu-id="0fce2-102">SQL Server Profiler 템플릿</span><span class="sxs-lookup"><span data-stu-id="0fce2-102">SQL Server Profiler Templates</span></span>
  <span data-ttu-id="0fce2-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 추적에 포함할 이벤트 클래스와 데이터 열을 정의하는 템플릿을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-103">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create templates that define the event classes and data columns to include in traces.</span></span> <span data-ttu-id="0fce2-104">템플릿을 정의하고 저장한 후 선택한 각 이벤트 클래스에 대한 데이터를 기록하는 추적을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-104">After you define and save the template, you can run a trace that records the data for each event class you selected.</span></span> <span data-ttu-id="0fce2-105">하나의 템플릿을 많은 추적에 사용할 수 있지만 템플릿 자체는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-105">You can use a template on many traces; the template is not itself executed.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0fce2-106">는 특정 추적을 위해 사용될 가능성이 있는 추적 템플릿을 미리 정의하여 이벤트 클래스를 쉽게 구성할 수 있도록 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-106">offers predefined trace templates that allow you to easily configure the event classes that you will most likely need for specific traces.</span></span> <span data-ttu-id="0fce2-107">예를 들어 Standard 템플릿을 사용하여 로그인, 로그아웃, 완료된 일괄 처리 및 연결 정보를 기록하는 일반적인 추적을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-107">The Standard template, for example, helps you to create a generic trace for recording logins, logouts, batches completed, and connection information.</span></span> <span data-ttu-id="0fce2-108">이 템플릿을 수정하지 않고 그대로 사용하여 추적을 실행할 수 있으며 이벤트 구성이 서로 다른 추가 템플릿에 대한 시작점으로 삼을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-108">You can use this template to run traces without modification or as a starting point for additional templates with different event configurations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fce2-109">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하면 미리 정의된 템플릿 외에도 기본적으로 이벤트 클래스가 포함되어 있지 않은 빈 템플릿에서 추적을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-109">In addition to traces from predefined templates, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] also allows you to create them from a blank template, containing no event classes by default.</span></span> <span data-ttu-id="0fce2-110">계획한 추적이 미리 정의된 템플릿의 구성과 비슷하지 않을 때는 빈 추적 템플릿을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-110">Using the blank trace template can be useful when a planned trace does not resemble the configurations of any of the predefined templates.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0fce2-111">는 다양한 서버 유형을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-111">can trace a variety of server types.</span></span> <span data-ttu-id="0fce2-112">예를 들어 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-112">For example you can trace [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  <span data-ttu-id="0fce2-113">하지만 포함할 수 있는 이벤트 클래스는 각 서버 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-113">However, the event classes that can be included are not the same for each type of server.</span></span> <span data-ttu-id="0fce2-114">따라서 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 서버 유형에 따라 다른 템플릿을 유지하여 선택한 서버 유형과 일치하는 특정 템플릿을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-114">Therefore, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] maintains different templates for different servers, and makes available the specific template that matches the selected server type.</span></span>  
  
## <a name="predefined-templates"></a><span data-ttu-id="0fce2-115">미리 정의된 템플릿</span><span class="sxs-lookup"><span data-stu-id="0fce2-115">Predefined Templates</span></span>  
 <span data-ttu-id="0fce2-116">Standard(기본) 템플릿 외에 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에는 특정한 유형의 이벤트를 모니터링하기 위한 여러 개의 미리 정의된 템플릿이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-116">In addition to the Standard (default) template, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] includes several predefined templates for monitoring certain types of events.</span></span> <span data-ttu-id="0fce2-117">다음 표에서는 미리 정의된 템플릿, 그 용도 및 정보를 캡처하는 이벤트 클래스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-117">The following table lists the predefined templates, their purpose, and the event classes for which they capture information.</span></span>  
  
|<span data-ttu-id="0fce2-118">템플릿 이름</span><span class="sxs-lookup"><span data-stu-id="0fce2-118">Template name</span></span>|<span data-ttu-id="0fce2-119">템플릿 용도</span><span class="sxs-lookup"><span data-stu-id="0fce2-119">Template purpose</span></span>|<span data-ttu-id="0fce2-120">이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="0fce2-120">Event classes</span></span>|  
|-------------------|----------------------|-------------------|  
|<span data-ttu-id="0fce2-121">SP_Counts</span><span class="sxs-lookup"><span data-stu-id="0fce2-121">SP_Counts</span></span>|<span data-ttu-id="0fce2-122">시간별로 저장 프로시저 실행 동작을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-122">Captures stored procedure execution behavior over time.</span></span>|<span data-ttu-id="0fce2-123">**SP:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-123">**SP:Starting**</span></span>|  
|<span data-ttu-id="0fce2-124">Standard</span><span class="sxs-lookup"><span data-stu-id="0fce2-124">Standard</span></span>|<span data-ttu-id="0fce2-125">추적을 만들기 위한 일반적인 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-125">Generic starting point for creating a trace.</span></span> <span data-ttu-id="0fce2-126">실행되는 모든 저장 프로시저와 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-126">Captures all stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] batches that are run.</span></span> <span data-ttu-id="0fce2-127">일반적인 데이터베이스 서버 활동을 모니터링하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-127">Use to monitor general database server activity.</span></span>|<span data-ttu-id="0fce2-128">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="0fce2-128">**Audit Login**</span></span><br /><br /> <span data-ttu-id="0fce2-129">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="0fce2-129">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="0fce2-130">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="0fce2-130">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="0fce2-131">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="0fce2-131">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="0fce2-132">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-132">**SQL:BatchCompleted**</span></span><br /><br /> <span data-ttu-id="0fce2-133">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-133">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="0fce2-134">TSQL</span><span class="sxs-lookup"><span data-stu-id="0fce2-134">TSQL</span></span>|<span data-ttu-id="0fce2-135">클라이언트가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 로 전송하는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문과 전송된 시간을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-135">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients and the time issued.</span></span> <span data-ttu-id="0fce2-136">클라이언트 애플리케이션을 디버깅하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-136">Use to debug client applications.</span></span>|<span data-ttu-id="0fce2-137">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="0fce2-137">**Audit Login**</span></span><br /><br /> <span data-ttu-id="0fce2-138">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="0fce2-138">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="0fce2-139">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="0fce2-139">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="0fce2-140">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-140">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="0fce2-141">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-141">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="0fce2-142">TSQL_Duration</span><span class="sxs-lookup"><span data-stu-id="0fce2-142">TSQL_Duration</span></span>|<span data-ttu-id="0fce2-143">클라이언트가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 로 전송하는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문과 실행 시간(밀리초)을 캡처하고 이 문들을 기간별로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-143">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients, their execution time (in milliseconds), and groups them by duration.</span></span> <span data-ttu-id="0fce2-144">느린 쿼리를 식별하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-144">Use to identify slow queries.</span></span>|<span data-ttu-id="0fce2-145">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="0fce2-145">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="0fce2-146">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-146">**SQL:BatchCompleted**</span></span>|  
|<span data-ttu-id="0fce2-147">TSQL_Grouped</span><span class="sxs-lookup"><span data-stu-id="0fce2-147">TSQL_Grouped</span></span>|<span data-ttu-id="0fce2-148">[!INCLUDE[tsql](../../includes/tsql-md.md)] 로 전송된 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문과 전송 시간을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-148">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the time they were issued.</span></span> <span data-ttu-id="0fce2-149">문을 전송한 사용자 또는 클라이언트를 기준으로 정보를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-149">Groups information by user or client that submitted the statement.</span></span> <span data-ttu-id="0fce2-150">특정 클라이언트 또는 사용자가 전송한 쿼리를 조사하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-150">Use to investigate queries from a particular client or user.</span></span>|<span data-ttu-id="0fce2-151">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="0fce2-151">**Audit Login**</span></span><br /><br /> <span data-ttu-id="0fce2-152">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="0fce2-152">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="0fce2-153">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="0fce2-153">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="0fce2-154">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-154">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="0fce2-155">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-155">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="0fce2-156">TSQL_Locks</span><span class="sxs-lookup"><span data-stu-id="0fce2-156">TSQL_Locks</span></span>|<span data-ttu-id="0fce2-157">클라이언트가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 로 전송하는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문을 예외 잠금 이벤트와 함께 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-157">Captures all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients along with exceptional lock events.</span></span> <span data-ttu-id="0fce2-158">교착 상태, 잠금 제한 시간 및 잠금 에스컬레이션 이벤트를 해결하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-158">Use to troubleshoot deadlocks, lock time-out, and lock escalation events.</span></span>|<span data-ttu-id="0fce2-159">**Blocked Process Report**</span><span class="sxs-lookup"><span data-stu-id="0fce2-159">**Blocked Process Report**</span></span><br /><br /> <span data-ttu-id="0fce2-160">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-160">**SP:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="0fce2-161">**SP:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-161">**SP:StmtStarting**</span></span><br /><br /> <span data-ttu-id="0fce2-162">**SQL:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-162">**SQL:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="0fce2-163">**SQL:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-163">**SQL:StmtStarting**</span></span><br /><br /> <span data-ttu-id="0fce2-164">**Deadlock Graph**</span><span class="sxs-lookup"><span data-stu-id="0fce2-164">**Deadlock Graph**</span></span><br /><br /> <span data-ttu-id="0fce2-165">**Lock:Cancel**</span><span class="sxs-lookup"><span data-stu-id="0fce2-165">**Lock:Cancel**</span></span><br /><br /> <span data-ttu-id="0fce2-166">**Lock:Deadlock**</span><span class="sxs-lookup"><span data-stu-id="0fce2-166">**Lock:Deadlock**</span></span><br /><br /> <span data-ttu-id="0fce2-167">**Lock:Deadlock Chain**</span><span class="sxs-lookup"><span data-stu-id="0fce2-167">**Lock:Deadlock Chain**</span></span><br /><br /> <span data-ttu-id="0fce2-168">**Lock:Escalation**</span><span class="sxs-lookup"><span data-stu-id="0fce2-168">**Lock:Escalation**</span></span><br /><br /> <span data-ttu-id="0fce2-169">**Lock:Timeout (timeout>0)**</span><span class="sxs-lookup"><span data-stu-id="0fce2-169">**Lock:Timeout (timeout>0)**</span></span>|  
|<span data-ttu-id="0fce2-170">TSQL_Replay</span><span class="sxs-lookup"><span data-stu-id="0fce2-170">TSQL_Replay</span></span>|<span data-ttu-id="0fce2-171">추적이 재생될 경우 필요한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 대한 세부 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-171">Captures detailed information about [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that is required if the trace will be replayed.</span></span> <span data-ttu-id="0fce2-172">벤치마크 테스트와 같이 반복되는 튜닝을 수행하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-172">Use to perform iterative tuning, such as benchmark testing.</span></span>|<span data-ttu-id="0fce2-173">**CursorClose**</span><span class="sxs-lookup"><span data-stu-id="0fce2-173">**CursorClose**</span></span><br /><br /> <span data-ttu-id="0fce2-174">**CursorExecute**</span><span class="sxs-lookup"><span data-stu-id="0fce2-174">**CursorExecute**</span></span><br /><br /> <span data-ttu-id="0fce2-175">**CursorOpen**</span><span class="sxs-lookup"><span data-stu-id="0fce2-175">**CursorOpen**</span></span><br /><br /> <span data-ttu-id="0fce2-176">**CursorPrepare**</span><span class="sxs-lookup"><span data-stu-id="0fce2-176">**CursorPrepare**</span></span><br /><br /> <span data-ttu-id="0fce2-177">**CursorUnprepare**</span><span class="sxs-lookup"><span data-stu-id="0fce2-177">**CursorUnprepare**</span></span><br /><br /> <span data-ttu-id="0fce2-178">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="0fce2-178">**Audit Login**</span></span><br /><br /> <span data-ttu-id="0fce2-179">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="0fce2-179">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="0fce2-180">**Existing Connection**</span><span class="sxs-lookup"><span data-stu-id="0fce2-180">**Existing Connection**</span></span><br /><br /> <span data-ttu-id="0fce2-181">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="0fce2-181">**RPC Output Parameter**</span></span><br /><br /> <span data-ttu-id="0fce2-182">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="0fce2-182">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="0fce2-183">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-183">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="0fce2-184">**Exec Prepared SQL**</span><span class="sxs-lookup"><span data-stu-id="0fce2-184">**Exec Prepared SQL**</span></span><br /><br /> <span data-ttu-id="0fce2-185">**Prepare SQL**</span><span class="sxs-lookup"><span data-stu-id="0fce2-185">**Prepare SQL**</span></span><br /><br /> <span data-ttu-id="0fce2-186">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-186">**SQL:BatchCompleted**</span></span><br /><br /> <span data-ttu-id="0fce2-187">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-187">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="0fce2-188">TSQL_SPs</span><span class="sxs-lookup"><span data-stu-id="0fce2-188">TSQL_SPs</span></span>|<span data-ttu-id="0fce2-189">실행 중인 모든 저장 프로시저에 대한 세부 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-189">Captures detailed information about all executing stored procedures.</span></span> <span data-ttu-id="0fce2-190">저장 프로시저의 구성 요소 단계를 분석하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-190">Use to analyze the component steps of stored procedures.</span></span> <span data-ttu-id="0fce2-191">프로시저가 다시 컴파일 중이라고 생각되면 **SP:Recompile** 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-191">Add the **SP:Recompile** event if you suspect that procedures are being recompiled.</span></span>|<span data-ttu-id="0fce2-192">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="0fce2-192">**Audit Login**</span></span><br /><br /> <span data-ttu-id="0fce2-193">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="0fce2-193">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="0fce2-194">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="0fce2-194">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="0fce2-195">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-195">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="0fce2-196">**SP:Completed**</span><span class="sxs-lookup"><span data-stu-id="0fce2-196">**SP:Completed**</span></span><br /><br /> <span data-ttu-id="0fce2-197">**SP:Starting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-197">**SP:Starting**</span></span><br /><br /> <span data-ttu-id="0fce2-198">**SP:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-198">**SP:StmtStarting**</span></span><br /><br /> <span data-ttu-id="0fce2-199">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="0fce2-199">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="0fce2-200">튜닝</span><span class="sxs-lookup"><span data-stu-id="0fce2-200">Tuning</span></span>|<span data-ttu-id="0fce2-201">저장 프로시저와 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리 실행에 대한 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-201">Captures information about stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] batch execution.</span></span> <span data-ttu-id="0fce2-202">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자가 데이터베이스를 튜닝할 때 작업으로 사용할 수 있는 추적 출력을 생성하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-202">Use to produce trace output that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use as a workload to tune databases.</span></span>|<span data-ttu-id="0fce2-203">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="0fce2-203">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="0fce2-204">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-204">**SP:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="0fce2-205">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="0fce2-205">**SQL:BatchCompleted**</span></span>|  
  
 <span data-ttu-id="0fce2-206">이벤트 클래스에 대한 자세한 내용은 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fce2-206">For information about the event classes, see [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
## <a name="default-template"></a><span data-ttu-id="0fce2-207">기본 템플릿</span><span class="sxs-lookup"><span data-stu-id="0fce2-207">Default Template</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0fce2-208">는 **Standard** 템플릿을 새 추적에 적용되는 기본 템플릿으로 자동 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-208">automatically designates the **Standard** template as the default template applied to any new trace.</span></span> <span data-ttu-id="0fce2-209">하지만 미리 정의된 템플릿 또는 사용자 정의 템플릿으로 기본 템플릿을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-209">However you can change the default template to any other predefined or user-defined template.</span></span> <span data-ttu-id="0fce2-210">기본 템플릿을 변경하려면 템플릿을 만들거나 편집할 때 **추적 템플릿 속성** 대화 상자의 **일반** 탭에서 **선택한 서버 유형에 대한 기본 템플릿으로 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-210">To change the default template, select the **Use as a default template for selected server type** check box when you create or edit a template by using the **General** tab of the **Trace Template Properties** dialog box.</span></span>  
  
 <span data-ttu-id="0fce2-211">**추적 템플릿 속성** 대화 상자는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **파일** 메뉴에서 **템플릿**을 선택한 다음, **새 템플릿** 또는 **템플릿 편집**을 클릭하면 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-211">To navigate to the **Trace Template Properties** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu, choose **Templates**, and then click **New Template** or **Edit Template**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fce2-212">기본 템플릿은 지정된 서버 유형에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-212">The default template is specific for a given server type.</span></span> <span data-ttu-id="0fce2-213">한 가지 서버 유형의 기본값을 변경해도 다른 서버 유형의 기본 템플릿에는 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fce2-213">Changing the default for one server type does not affect the default template for any other server type.</span></span> <span data-ttu-id="0fce2-214">특정 서버용 기본 템플릿을 설정하는 방법은 [추적 정의 기본값 설정&#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fce2-214">For more information about setting a default template for a specific server, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fce2-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fce2-215">See Also</span></span>  
 <span data-ttu-id="0fce2-216">[추적 템플릿 만들기&#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0fce2-216">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="0fce2-217">[추적 템플릿 수정&#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0fce2-217">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="0fce2-218">[추적 템플릿 내보내기&#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0fce2-218">[Export a Trace Template &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="0fce2-219">추적 템플릿 가져오기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="0fce2-219">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](import-a-trace-template-sql-server-profiler.md)  
  
  