---
title: 재생에 대 한 프로파일러 추적 만들기 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- replaying queries
- replaying discovers
- events [Analysis Services]
- replaying commands
- Profiler [SQL Server Profiler], Analysis Services
- performance [Analysis Services], replays
- traces [Analysis Services]
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9822d9d2589decdde731da5f5888572962b0e612
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731080"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a><span data-ttu-id="65ef7-102">재생에 대한 프로파일러 추적 만들기(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="65ef7-102">Create Profiler Traces for Replay (Analysis Services)</span></span>
  <span data-ttu-id="65ef7-103">에서 사용자가 제출한 쿼리, 검색 및 명령을 재생 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 필요한 이벤트를 수집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-103">To replay queries, discovers, and commands that are submitted by users to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must gather the required events.</span></span> <span data-ttu-id="65ef7-104">이러한 이벤트의 컬렉션을 초기화하려면 **추적 속성** 대화 상자의 **이벤트 선택** 탭에서 적합한 이벤트 클래스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-104">In order to initiate collection of these events, appropriate event classes must be selected in the **Event Selection** tab of the **Trace Properties** dialog box.</span></span> <span data-ttu-id="65ef7-105">예를 들어 Query Begin 이벤트 클래스가 선택된 경우 쿼리를 포함한 이벤트가 수집되고 재생에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-105">For example if the Query Begin event class is selected, events that contain queries are collected and used for replay.</span></span> <span data-ttu-id="65ef7-106">또한 추적 파일에는 원래 트랜잭션 시퀀스로 분산 환경에서 서버 트랜잭션 재생을 지원하는 데 충분한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-106">Also, the trace file contains sufficient information to support replaying server transactions in a distributed environment in the original sequence of transactions.</span></span>  
  
## <a name="replay-for-queries"></a><span data-ttu-id="65ef7-107">쿼리 재생</span><span class="sxs-lookup"><span data-stu-id="65ef7-107">Replay for Queries</span></span>  
 <span data-ttu-id="65ef7-108">쿼리를 재생하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 다음 이벤트를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-108">To replay queries, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must capture the following events:</span></span>  
  
-   <span data-ttu-id="65ef7-109">모든 데이터 열을 갖는 Audit Login 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-109">Audit Login event class with all its data columns.</span></span> <span data-ttu-id="65ef7-110">이 이벤트 클래스는 로그인한 사용자 및 세션 설정에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-110">This event class provides information about which user logged in and about the session settings.</span></span> <span data-ttu-id="65ef7-111">SPID(서버 프로세스 ID)는 사용자 세션에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-111">The server process ID (SPID) provides the reference to the user session.</span></span> <span data-ttu-id="65ef7-112">자세한 내용은 [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-112">For more information, see [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).</span></span>  
  
-   <span data-ttu-id="65ef7-113">모든 데이터 열을 갖는 Query Begin 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-113">Query Begin event class with all its data columns.</span></span> <span data-ttu-id="65ef7-114">이 이벤트 클래스는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 전송된 쿼리에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-114">This event class provides information about the query that was submitted to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="65ef7-115">Event Subclass 열은 쿼리 유형에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-115">The Event Subclass column provides information about the type of query.</span></span> <span data-ttu-id="65ef7-116">TextData 열은 쿼리의 실제 텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-116">The TextData column provides the actual text of the query.</span></span> <span data-ttu-id="65ef7-117">RequestParameters 열은 매개 변수가 있는 쿼리의 매개 변수를 제공하고 RequestProperties 열은 XMLA(XML for Analysis) 요청의 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-117">The RequestParameters column provides the parameters for parameterized queries, and the RequestProperties column provides the properties of an XML for Analysis (XMLA) request.</span></span> <span data-ttu-id="65ef7-118">자세한 내용은 [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-118">For more information, see [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).</span></span>  
  
-   <span data-ttu-id="65ef7-119">모든 데이터 열을 갖는 Query End 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-119">Query End event class with all its data columns.</span></span> <span data-ttu-id="65ef7-120">이 이벤트 클래스는 쿼리 실행 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-120">This event class verifies the status of the query execution.</span></span> <span data-ttu-id="65ef7-121">자세한 내용은 [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-121">For more information, see [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).</span></span>  
  
## <a name="replay-for-discovers"></a><span data-ttu-id="65ef7-122">검색 항목 재생</span><span class="sxs-lookup"><span data-stu-id="65ef7-122">Replay for Discovers</span></span>  
 <span data-ttu-id="65ef7-123">검색 항목을 재생하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 다음 이벤트를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-123">To replay discovers, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must capture the following events:</span></span>  
  
-   <span data-ttu-id="65ef7-124">모든 데이터 열을 갖는 Audit Login 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-124">Audit Login event class with all its data columns.</span></span> <span data-ttu-id="65ef7-125">이 이벤트 클래스는 로그인한 사용자 및 세션 설정에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-125">This event class provides information about which user logged in and about the session settings.</span></span> <span data-ttu-id="65ef7-126">SPID는 사용자 세션에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-126">The SPID provides the reference to the user session.</span></span> <span data-ttu-id="65ef7-127">자세한 내용은 [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-127">For more information, see [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).</span></span>  
  
-   <span data-ttu-id="65ef7-128">모든 데이터 열을 갖는 Discover Begin 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-128">Discover Begin event class with all its data columns.</span></span> <span data-ttu-id="65ef7-129">TextData 열은 \<RequestType> 검색 요청의 일부를 제공 하 고 RequestProperties 열은 \<Properties> 검색 요청의 일부를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-129">The TextData column provides the \<RequestType> portion of the discover request, and the RequestProperties column provides the \<Properties> portion of the discover request.</span></span> <span data-ttu-id="65ef7-130">EventSubclass 열은 검색 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-130">The EventSubclass column provides the discover type.</span></span> <span data-ttu-id="65ef7-131">자세한 내용은 [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-131">For more information, see [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).</span></span>  
  
-   <span data-ttu-id="65ef7-132">모든 데이터 열을 갖는 Discover End 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-132">Discover End event class with all its data columns.</span></span> <span data-ttu-id="65ef7-133">이 이벤트 클래스는 검색 요청 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-133">This event class verifies the status of the discover request.</span></span> <span data-ttu-id="65ef7-134">자세한 내용은 [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-134">For more information, see [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).</span></span>  
  
## <a name="replay-for-commands"></a><span data-ttu-id="65ef7-135">명령 재생</span><span class="sxs-lookup"><span data-stu-id="65ef7-135">Replay for Commands</span></span>  
 <span data-ttu-id="65ef7-136">명령을 재생하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 다음 이벤트를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-136">To replay commands, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must capture the following events:</span></span>  
  
-   <span data-ttu-id="65ef7-137">모든 데이터 열을 갖는 Command Begin 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-137">Command Begin event class with all its data columns.</span></span> <span data-ttu-id="65ef7-138">TextData 열은 프로세스 유형, 데이터베이스 ID 및 큐브 ID와 같은 명령 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-138">The TextData column provides the command details, such as the process type, database ID, and cube ID.</span></span> <span data-ttu-id="65ef7-139">RequestParameters 열은 매개 변수가 있는 명령의 매개 변수를 제공하고 RequestProperties 열은 XMLA 요청의 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-139">The RequestParameters column provides the parameters for parameterized command, and the RequestProperties column provides the properties of an XMLA request.</span></span> <span data-ttu-id="65ef7-140">자세한 내용은 [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-140">For more information, see [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).</span></span>  
  
-   <span data-ttu-id="65ef7-141">모든 데이터 열을 갖는 Command End 이벤트 클래스.</span><span class="sxs-lookup"><span data-stu-id="65ef7-141">Command End event class with all its data columns.</span></span> <span data-ttu-id="65ef7-142">이 이벤트 클래스는 명령 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65ef7-142">This event class verifies the status of the command.</span></span> <span data-ttu-id="65ef7-143">자세한 내용은 [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65ef7-143">For more information, see [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ef7-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65ef7-144">See Also</span></span>  
 <span data-ttu-id="65ef7-145">[Analysis Services 추적 이벤트](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) </span><span class="sxs-lookup"><span data-stu-id="65ef7-145">[Analysis Services Trace Events](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) </span></span>  
 [<span data-ttu-id="65ef7-146">SQL Server 프로파일러를 사용한 Analysis Services 모니터링 소개</span><span class="sxs-lookup"><span data-stu-id="65ef7-146">Introduction to Monitoring Analysis Services with SQL Server Profiler</span></span>](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  