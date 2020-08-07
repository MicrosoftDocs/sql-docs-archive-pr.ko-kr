---
title: MSRS 2014 웹 서비스 SharePoint 모드 및 MSRS 2014 Windows 서비스 SharePoint 모드 성능 개체에 대 한 성능 카운터 (SharePoint 모드) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- counters [Reporting Services]
- Report Server Windows service, performance counters
- RS Windows Service performance object
- Scheduling and Delivery Processor performance object [Reporting Services]
- performance [Reporting Services]
ms.assetid: 70bf6980-7845-4ab5-8b2a-ebf526d811a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91b77a62ea9d81af836e062cfafe9b700c47109e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732419"
---
# <a name="performance-counters-for-the-msrs-2014-web-service-sharepoint-mode-and-msrs-2014-windows-service-sharepoint-mode-performance-objects-sharepoint-mode"></a><span data-ttu-id="2a35a-102">MSRS 2014 웹 서비스 SharePoint 모드 및 MSRS 2014 Windows 서비스 SharePoint 모드 성능 개체에 대한 성능 카운터(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="2a35a-102">Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects (SharePoint Mode)</span></span>
  <span data-ttu-id="2a35a-103">이 항목에서는 `MSRS 2014 Web Service SharePoint Mode` SharePoint 모드 배포 중에 포함되는 `MSRS 2014 Windows Service SharePoint Mode` 및 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 성능 개체의 성능 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-103">This topic describes performance counters for the `MSRS 2014 Web Service SharePoint Mode` and `MSRS 2014 Windows Service SharePoint Mode` performance objects that are part of a [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] SharePoint mode deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="2a35a-104">이 성능 개체는 로컬 보고서 서버의 이벤트를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-104">This performance objects monitor events on the local report server.</span></span> <span data-ttu-id="2a35a-105">스케일 아웃 배포에서 보고서 서버를 실행 중이면 카운터는 현재 서버에만 적용되고 스케일 아웃 배포 전체에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-105">If you are running a report server in a scale-out deployment, the counts apply to the current server and not the scale-out deployment as a whole.</span></span>

 <span data-ttu-id="2a35a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="2a35a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 <span data-ttu-id="2a35a-107">성능 개체는 Windows 성능 모니터(**Perfmon.exe**)에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-107">The performance objects are available in the Windows Performance Monitor (**Perfmon.exe**).</span></span> <span data-ttu-id="2a35a-108">자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a35a-108">For more information, see the Windows documentation.</span></span> <span data-ttu-id="2a35a-109">[런타임 프로 파일링](https://msdn.microsoft.com/library/w4bz2147.aspx).</span><span class="sxs-lookup"><span data-stu-id="2a35a-109">[Runtime Profiling](https://msdn.microsoft.com/library/w4bz2147.aspx).</span></span>

 <span data-ttu-id="2a35a-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2a35a-110">**In this topic:**</span></span>

-   [<span data-ttu-id="2a35a-111">MSRS 2014 웹 서비스 SharePoint 모드 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-111">MSRS 2014 Web Service SharePoint Mode Performance Counters</span></span>](#bkmk_webservice)

-   [<span data-ttu-id="2a35a-112">MSRS 2014 Windows 서비스 SharePoint 모드 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-112">MSRS 2014 Windows Service SharePoint Mode Performance Counters</span></span>](#bkmk_windowsservice)

-   [<span data-ttu-id="2a35a-113">PowerShell Cmdlet을 사용하여 목록 반환</span><span class="sxs-lookup"><span data-stu-id="2a35a-113">Use PowerShell Cmdlets to return lists</span></span>](#bkmk_powershell)

##  <a name="msrs-2014-web-service-sharepoint-mode-performance-counters"></a><a name="bkmk_webservice"></a><span data-ttu-id="2a35a-114">MSRS 2014 웹 서비스 SharePoint 모드 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-114">MSRS 2014 Web Service SharePoint Mode Performance Counters</span></span>
 <span data-ttu-id="2a35a-115">`MSRS 2014 Web Service SharePoint Mode` 성능 개체는 보고서 서버 성능을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-115">The `MSRS 2014 Web Service SharePoint Mode` performance object monitors report server performance.</span></span> <span data-ttu-id="2a35a-116">이 성능 개체에는 일반적으로 대화형 보고서 보기 작업을 통해 시작된 보고서 서버 처리를 추적하는 데 사용되는 카운터 모음이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-116">This performance object includes a collection of counters used to track report server processing typically initiated through interactive report viewing operations.</span></span> <span data-ttu-id="2a35a-117">이 카운터를 설정하면 모든 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 인스턴스에 카운터를 적용하거나 특정 인스턴스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-117">When you set up this counter, you can apply the counter to all instances of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] or you can select specific instances.</span></span> <span data-ttu-id="2a35a-118">이러한 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-118">These counters are reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>

 <span data-ttu-id="2a35a-119">다음 표에서는 `MSRS 2014 Web Service SharePoint Mode` 성능 개체와 함께 제공되는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-119">The following table lists the counters that are included with the `MSRS 2014 Web Service SharePoint Mode` performance object.</span></span>

|<span data-ttu-id="2a35a-120">카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-120">Counter</span></span>|<span data-ttu-id="2a35a-121">Description</span><span class="sxs-lookup"><span data-stu-id="2a35a-121">Description</span></span>|
|-------------|-----------------|
|`Active Sessions`|<span data-ttu-id="2a35a-122">활성 세션 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-122">Number of active sessions.</span></span> <span data-ttu-id="2a35a-123">이 카운터는 활성 상태인지 여부에 관계없이 보고서 실행에서 생성된 모든 브라우저 세션의 누적 개수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-123">This counter provides a cumulative count of all browser sessions generated from report executions, whether they are still active or not.</span></span><br /><br /> <span data-ttu-id="2a35a-124">이 카운터는 세션 레코드를 제거하면 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-124">The counter is decremented as session records are removed.</span></span> <span data-ttu-id="2a35a-125">기본적으로 10분 동안 활동이 없으면 세션이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-125">By default, sessions are removed after ten minutes of no activity.</span></span>|
|`Cache Hits/Sec`|<span data-ttu-id="2a35a-126">캐시된 보고서에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-126">Number of requests per second for cached reports.</span></span> <span data-ttu-id="2a35a-127">이러한 요청은 다시 렌더링된 보고서에 대한 것이며 캐시에서 직접 처리된 보고서에 대한 요청은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-127">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span> <span data-ttu-id="2a35a-128">이 항목 뒷부분에서 `Total Cache Hits`를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a35a-128">(See `Total Cache Hits` later in this topic.)</span></span>|
|`Cache Hits/Sec (Semantic Models)`|<span data-ttu-id="2a35a-129">캐시된 모델에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-129">Number of requests per second for cached model.</span></span> <span data-ttu-id="2a35a-130">이러한 요청은 다시 렌더링된 보고서에 대한 것이며 캐시에서 직접 처리된 보고서에 대한 요청은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-130">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span>|
|`Cache Misses/Sec`|<span data-ttu-id="2a35a-131">캐시에서 보고서를 반환하지 못한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-131">Number of requests per second that failed to return a report from cache.</span></span> <span data-ttu-id="2a35a-132">캐싱(디스크 또는 메모리)에 사용된 리소스가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-132">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Cache Misses/Sec (Semantic Models)`|<span data-ttu-id="2a35a-133">캐시에서 모델을 반환하지 못한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-133">Number of requests per second that failed to return a model from cache.</span></span> <span data-ttu-id="2a35a-134">캐싱(디스크 또는 메모리)에 사용된 리소스가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-134">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`First Session Requests/Sec`|<span data-ttu-id="2a35a-135">매 초마다 보고서 서버 캐시에서 시작된 새 사용자 세션 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-135">Number of new user sessions that are started from the report server cache each second.</span></span>|
|`Memory Cache Hits/Sec`|<span data-ttu-id="2a35a-136">메모리 내 캐시에서 보고서가 검색된 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-136">Number of times per second that reports are retrieved from the in-memory cache.</span></span> <span data-ttu-id="2a35a-137">*메모리 내 캐시* 는 캐시 중 CPU 메모리에 보고서를 저장하는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-137">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="2a35a-138">메모리 내 캐시가 사용되면 보고서 서버는 캐시된 내용에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 쿼리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-138">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Memory Cache Misses/Sec`|<span data-ttu-id="2a35a-139">메모리 내 캐시에서 보고서를 검색하지 못한 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-139">Number of times per second that reports could not be retrieved from the in-memory cache.</span></span>|
|`Next Session Requests/Sec`|<span data-ttu-id="2a35a-140">기존 세션에서 열려 있는 보고서(예: 세션 스냅샷에서 렌더링된 보고서)에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-140">Number of requests per second for reports that are open in an existing session (such as reports that are rendered from a session snapshot).</span></span>|
|`Report Requests`|<span data-ttu-id="2a35a-141">현재 활성 상태이며 보고서 서버에서 처리 중인 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-141">Number of reports that are currently active and being handled by the report server.</span></span>|
|`Reports Executed/Sec`|<span data-ttu-id="2a35a-142">초당 성공적으로 실행된 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-142">Number of successful report executions per second.</span></span> <span data-ttu-id="2a35a-143">이 카운터는 보고서 볼륨에 대한 통계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-143">This counter provides statistics about report volume.</span></span> <span data-ttu-id="2a35a-144">캐시에서 반환할 수 있는 보고서 요청과 보고서 실행을 비교하기 위해 `Request/Sec` 카운터와 이 카운터를 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-144">Use this counter with `Request/Sec` to compare report execution to report requests that can be returned from cache.</span></span>|
|`Requests/Sec`|<span data-ttu-id="2a35a-145">보고서 서버에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-145">Number of requests per second made to the report server.</span></span> <span data-ttu-id="2a35a-146">이 카운터는 보고서 서버에서 처리하는 모든 요청 종류를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-146">This counter tracks all types of requests that are handled by the report server.</span></span>|
|`Total Cache Hits`|<span data-ttu-id="2a35a-147">서비스 시작 이후 캐시에서 보고서를 요청한 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-147">Total number of requests for reports from the cache after the service started.</span></span> <span data-ttu-id="2a35a-148">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-148">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Cache Hits (Semantic Models)`|<span data-ttu-id="2a35a-149">서비스 시작 이후 캐시에서 모델을 요청한 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-149">Total number of requests for model from the cache after the service started.</span></span> <span data-ttu-id="2a35a-150">이 카운터는 ASP.NET에서 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-150">This counter is reset whenever ASP.NET stops the Report Server Web service.</span></span>|
|`Total Cache Misses`|<span data-ttu-id="2a35a-151">서비스 시작 이후 캐시에서 보고서를 반환하지 못한 총 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-151">Total number of times that a report could not be returned from the cache after the service started.</span></span> <span data-ttu-id="2a35a-152">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-152">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span> <span data-ttu-id="2a35a-153">디스크 공간 및 메모리가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-153">Use this counter to determine whether disk space and memory are sufficient.</span></span>|
|`Total Cache Misses (Semantic Models)`|<span data-ttu-id="2a35a-154">서비스 시작 이후 캐시에서 모델을 반환하지 못한 총 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-154">Total number of times that a model could not be returned from the cache after the service started.</span></span> <span data-ttu-id="2a35a-155">이 카운터는 ASP.NET에서 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-155">This counter is reset whenever ASP.NET stops the Report Server Web service.</span></span> <span data-ttu-id="2a35a-156">디스크 공간 및 메모리가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-156">Use this counter to determine whether disk space and memory are sufficient.</span></span>|
|`Total Memory Cache Hits`|<span data-ttu-id="2a35a-157">서비스 시작 이후 메모리 내 캐시에서 반환한 캐시된 보고서의 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-157">Total number of cached reports returned from the in-memory cache after the service started.</span></span> <span data-ttu-id="2a35a-158">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-158">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span> <span data-ttu-id="2a35a-159">*메모리 내 캐시* 는 캐시 중 CPU 메모리에 보고서를 저장하는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-159">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="2a35a-160">메모리 내 캐시가 사용되면 보고서 서버는 캐시된 내용에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 쿼리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-160">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Total Memory Cache Misses`|<span data-ttu-id="2a35a-161">서비스 시작 이후 메모리 내 캐시에 대한 총 캐시 누락 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-161">Total number of cache misses against the in-memory cache after the service started.</span></span> <span data-ttu-id="2a35a-162">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-162">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Processing Failures`|<span data-ttu-id="2a35a-163">보고서 서버 웹 서비스 요청 처리 오류 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-163">Number of errors in report server web service request processing.</span></span>|
|`Total Rejected Threads`|<span data-ttu-id="2a35a-164">비동기 처리에 대해 거부되고 이후에 동일한 스레드에서 동기 프로세스로 처리된 총 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-164">Total number of threads rejected for asynchronous processing, and subsequently handled as synchronous processes in the same thread.</span></span> <span data-ttu-id="2a35a-165">각 데이터 원본은 하나의 스레드에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-165">Each data source is processed on one thread.</span></span> <span data-ttu-id="2a35a-166">스레드 볼륨이 용량을 초과하면 스레드는 비동기 처리에는 거부되고 순차 방식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-166">If the volume of threads exceeds capacity, threads are rejected for asynchronous processing, and are then processed in a serial manner.</span></span>|
|`Total Reports Executed`|<span data-ttu-id="2a35a-167">서비스 시작 이후 성공적으로 실행된 총 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-167">Total number of reports that ran successfully after the service started.</span></span> <span data-ttu-id="2a35a-168">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-168">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|
|`Total Requests`|<span data-ttu-id="2a35a-169">서비스 시작 이후 보고서 서버에 대한 총 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-169">Total number of all requests made to the report server after the service started.</span></span> <span data-ttu-id="2a35a-170">이 카운터는 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-170">This counter is reset whenever [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>|

##  <a name="msrs-2014-windows-service-sharepoint-mode-performance-counters"></a><a name="bkmk_windowsservice"></a><span data-ttu-id="2a35a-171">MSRS 2014 Windows 서비스 SharePoint 모드 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-171">MSRS 2014 Windows Service SharePoint Mode Performance Counters</span></span>
 <span data-ttu-id="2a35a-172">`MSRS 2014 Windows Service SharePoint Mode` 성능 개체는 보고서 서버 Windows 서비스를 모니터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-172">The `MSRS 2014 Windows Service SharePoint Mode` performance object is used to monitor the Report Server Windows service.</span></span> <span data-ttu-id="2a35a-173">이 성능 개체에는 예약된 작업을 통해 시작된 보고서 처리를 추적하는 데 사용되는 카운터 모음이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-173">This performance object includes a collection of counters used to track report processing that is initiated through scheduled operations.</span></span> <span data-ttu-id="2a35a-174">예약된 작업에는 구독 및 배달, 보고서 실행 스냅샷 및 보고서 기록이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-174">Scheduled operations can include subscription and delivery, report execution snapshots, and report history.</span></span> <span data-ttu-id="2a35a-175">이 카운터를 설정하면 모든 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 인스턴스에 카운터를 적용하거나 특정 인스턴스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-175">When you set up this counter, you can apply the counter to all instances of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] or you can select specific instances.</span></span>

 <span data-ttu-id="2a35a-176">다음 표에서는 `MSRS 2014 Windows Service SharePoint mode` 성능 개체에 포함된 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-176">The following table lists the counters that are included in the `MSRS 2014 Windows Service SharePoint mode` performance object.</span></span>

|<span data-ttu-id="2a35a-177">카운터</span><span class="sxs-lookup"><span data-stu-id="2a35a-177">Counter</span></span>|<span data-ttu-id="2a35a-178">설명</span><span class="sxs-lookup"><span data-stu-id="2a35a-178">Description</span></span>|
|-------------|-----------------|
|`Active Sessions`|<span data-ttu-id="2a35a-179">보고서 서버 데이터베이스에 저장된 활성 세션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-179">Number of active sessions stored in the report server database.</span></span> <span data-ttu-id="2a35a-180">이 카운터는 활성 상태인지 여부에 관계없이 보고서 구독에서 생성된 사용 가능한 모든 브라우저 세션의 누적 개수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-180">This counter provides a cumulative count of all usable browser sessions generated from report subscriptions, whether they are still active or not.</span></span>|
|`Alerting: event queue length`||
|`Alerting: events processed - CreateSchedule`||
|`Alerting: events processed - Delete schedule`||
|`Alerting: events processed - DeliverAlert`||
|`Alerting: events processed - FireAlert`||
|`Alerting: events processed - FireSchedule`||
|`Alerting: events processed - GenerateAlert`||
|`Alerting: events processed - UpdateSchedule`||
|`Cache Flushes/Sec`|<span data-ttu-id="2a35a-181">초당 캐시 플러시 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-181">Number of cache flushes per second.</span></span>|
|`Cache Hits/Sec`|<span data-ttu-id="2a35a-182">캐시된 보고서에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-182">Number of requests per second for cached reports.</span></span> <span data-ttu-id="2a35a-183">이러한 요청은 다시 렌더링된 보고서에 대한 것이며 캐시에서 직접 처리된 보고서에 대한 요청은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-183">These are requests for re-rendered reports, not requests for reports processed directly from the cache.</span></span> <span data-ttu-id="2a35a-184">이 항목 뒷부분에서 `Total Cache Hits`를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a35a-184">(See `Total Cache Hits` later in this topic.)</span></span>|
|`Cache Hits/Sec (Semantic Models)`|<span data-ttu-id="2a35a-185">캐시된 모델에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-185">Number of requests per second for cached models.</span></span>|
|`Cache Misses/Sec`|<span data-ttu-id="2a35a-186">캐시에서 보고서를 반환하지 못한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-186">Number of requests per second that failed to return a report from cache.</span></span> <span data-ttu-id="2a35a-187">캐싱(디스크 또는 메모리)에 사용된 리소스가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-187">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Cache Misses/Sec (Semantic Models)`|<span data-ttu-id="2a35a-188">캐시에서 모델을 반환하지 못한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-188">Number of requests per second that failed to return a model from cache.</span></span> <span data-ttu-id="2a35a-189">캐싱(디스크 또는 메모리)에 사용된 리소스가 충분한지 여부를 확인할 때 이 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-189">Use this counter to find out whether the resources used for caching (disk or memory) are sufficient.</span></span>|
|`Delivers/Sec`|<span data-ttu-id="2a35a-190">배달 확장 프로그램에서 초당 보고서를 배달한 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-190">Number of report deliveries per second, from any delivery extension.</span></span>|
|`Events/Sec`|<span data-ttu-id="2a35a-191">초당 처리된 이벤트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-191">Number of events processed per second.</span></span> <span data-ttu-id="2a35a-192">모니터링된 이벤트에는 `SnapshotUpdated` 및 `TimedSubscription`이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-192">Events that are monitored include `SnapshotUpdated` and `TimedSubscription`.</span></span>|
|`First Session Requests/Sec`|<span data-ttu-id="2a35a-193">초당 만들어진 새 보고서 실행 세션 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-193">Number of new report execution sessions created per second.</span></span>|
|`Memory Cache Hits/Sec`|<span data-ttu-id="2a35a-194">메모리 내 캐시에서 보고서가 검색된 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-194">Number of times per second that reports are retrieved from the in-memory cache.</span></span> <span data-ttu-id="2a35a-195">*메모리 내 캐시* 는 캐시 중 CPU 메모리에 보고서를 저장하는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-195">*In-memory cache* is a part of the cache that stores reports in CPU memory.</span></span> <span data-ttu-id="2a35a-196">메모리 내 캐시가 사용되면 보고서 서버는 캐시된 내용에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 쿼리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-196">When in-memory cache is used, the report server does not query [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for cached content.</span></span>|
|`Memory Cache Misses/Sec`|<span data-ttu-id="2a35a-197">메모리 내 캐시에서 보고서를 검색하지 못한 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-197">Number of times per second that reports cannot be retrieved from the in-memory cache.</span></span>|
|`Next Session Requests/Sec`|<span data-ttu-id="2a35a-198">기존 세션에서 열려 있는 보고서(예: 세션 스냅샷에서 렌더링된 보고서)에 대한 초당 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-198">Number of requests per second for reports that are open in an existing session (such as reports that are rendered from a session snapshot).</span></span>|
|`Report Requests`|<span data-ttu-id="2a35a-199">현재 활성 상태이며 보고서 서버에서 처리 중인 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-199">Number of reports that are currently active and being handled by the report server.</span></span> <span data-ttu-id="2a35a-200">이 카운터는 캐싱 전략을 평가하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-200">Use this counter to evaluate caching strategy.</span></span> <span data-ttu-id="2a35a-201">생성된 보고서보다 훨씬 더 많은 요청이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-201">There might be significantly more requests than reports generated.</span></span>|
|`Reports Executed/Sec`|<span data-ttu-id="2a35a-202">초당 성공적으로 생성된 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-202">Number of reports successfully generated per second.</span></span>|
|`Requests/Sec`|<span data-ttu-id="2a35a-203">보고서 서버 서비스가 초당 성공적으로 처리한 총 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-203">Total number of successful requests the report server service processed per second.</span></span>|
|`Snapshot Updates/Sec`|<span data-ttu-id="2a35a-204">초당 총 보고서 실행 스냅샷 업데이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-204">Total number of report execution snapshot updates per second.</span></span>|
|`Total App Domain Recycles`|<span data-ttu-id="2a35a-205">보고서 서버 Windows 서비스 시작 이후 애플리케이션 도메인의 총 재활용 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-205">Total number of application domain cycles after the Report Server Windows service started.</span></span>|
|<span data-ttu-id="2a35a-206">**Total Cache Flushes**</span><span class="sxs-lookup"><span data-stu-id="2a35a-206">**Total Cache Flushes**</span></span>|<span data-ttu-id="2a35a-207">서비스 시작 이후 보고서 서버 캐시의 총 업데이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-207">Total number of report server cache updates after the service started.</span></span> <span data-ttu-id="2a35a-208">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-208">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="2a35a-209">`Cache Flushes/Sec`을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a35a-209">See `Cache Flushes/Sec`.</span></span>|
|`Total Cache Hits`|<span data-ttu-id="2a35a-210">보고서 서버 Windows 서비스 시작 이후 캐시에서 직접 처리된 보고서에 대한 총 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-210">Total number of requests for reports processed directly from the cache after the Report Server Windows service started.</span></span> <span data-ttu-id="2a35a-211">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-211">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="2a35a-212">`Cache Hits/Sec`을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a35a-212">See `Cache Hits/Sec`.</span></span>|
|`Total Cache Hits (Semantic Models)`|<span data-ttu-id="2a35a-213">보고서 서버 Windows 서비스 시작 이후 캐시에서 직접 처리된 총 모델 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-213">Total number of model requests processed directly from the cache after the report server Windows service started.</span></span> <span data-ttu-id="2a35a-214">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-214">This counter resets when the application domain recycles.</span></span>|
|`Total Cache Misses`|<span data-ttu-id="2a35a-215">보고서 서버 Windows 서비스 시작 이후 캐시에서 보고서를 반환하지 못한 총 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-215">Total number of times that a report could not be returned from cache after the Report Server Windows service started.</span></span> <span data-ttu-id="2a35a-216">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-216">This counter resets when the application domain recycles.</span></span> <span data-ttu-id="2a35a-217">`Cache Misses/Sec`을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a35a-217">See `Cache Misses/Sec`.</span></span>|
|`Total Cache Misses (Semantic Models)`|<span data-ttu-id="2a35a-218">보고서 서버 Windows 서비스 시작 이후 캐시에서 모델을 반환하지 못한 총 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-218">Total number of times that a model could not be returned from cache after the Report Server Windows service started.</span></span> <span data-ttu-id="2a35a-219">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-219">This counter resets when the application domain recycles.</span></span>|
|`Total Deliveries`|<span data-ttu-id="2a35a-220">모든 배달 확장 프로그램의 일정 예약 및 배달 프로세서에서 배달한 총 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-220">Total number of reports delivered by the Scheduling and Delivery Processor, for all delivery extensions.</span></span> <span data-ttu-id="2a35a-221">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-221">This counter resets when the application domain recycles.</span></span>|
|`Total Events`|<span data-ttu-id="2a35a-222">보고서 서버 Windows 서비스 시작 이후 이벤트의 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-222">Total number of events after the Report Server Windows service started.</span></span> <span data-ttu-id="2a35a-223">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-223">This counter resets when the application domain recycles.</span></span>|
|`Total Memory Cache Hits`|<span data-ttu-id="2a35a-224">보고서 서버 Windows 서비스 시작 이후 메모리 내 캐시에서 반환된 캐시된 보고서의 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-224">Total number of cached reports returned from the in-memory cache after the Report Server Windows service started.</span></span> <span data-ttu-id="2a35a-225">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-225">This counter resets when the application domain recycles.</span></span>|
|`Total Memory Cache Misses`|<span data-ttu-id="2a35a-226">서비스 시작 이후 메모리 내 캐시에 대한 총 캐시 누락 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-226">Total number of cache misses against the in-memory cache after the service started.</span></span> <span data-ttu-id="2a35a-227">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-227">This counter resets when the application domain recycles.</span></span>|
|`Total Processing Failures`|<span data-ttu-id="2a35a-228">보고서 서버 Windows 서비스에 대한 요청 처리 오류 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-228">Number of request processing errors for the report server Windows service.</span></span>|
|`Total Rejected Threads`|<span data-ttu-id="2a35a-229">비동기 처리에 대해 거부되고 이후에 동일한 스레드에서 동기 프로세스로 처리된 총 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-229">Total number of threads rejected for asynchronous processing, and subsequently handled as a synchronous process in the same thread.</span></span> <span data-ttu-id="2a35a-230">보통 또는 과도한 로드 상태에서 이 카운터는 계속 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-230">Under moderate or heavy load, this counter steadily increases.</span></span>|
|`Total Reports Executed`|<span data-ttu-id="2a35a-231">실행된 총 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-231">Total number of reports run.</span></span>|
|`Total Requests`|<span data-ttu-id="2a35a-232">서비스 시작 이후 성공적으로 실행된 총 보고서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-232">Total number of reports that ran successfully after the service started.</span></span> <span data-ttu-id="2a35a-233">애플리케이션 도메인을 재활용하면 이 카운터가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-233">This counter resets when the application domain recycles.</span></span>|
|`Total Snapshot Updates`|<span data-ttu-id="2a35a-234">총 보고서 실행 스냅샷 업데이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-234">Total number of report execution snapshot updates.</span></span>|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a><span data-ttu-id="2a35a-235">PowerShell Cmdlet을 사용 하 여 목록 반환</span><span class="sxs-lookup"><span data-stu-id="2a35a-235">Use PowerShell Cmdlets to return lists</span></span>
 <span data-ttu-id="2a35a-236">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")다음 Windows PowerShell 스크립트는 CounterSetName이 “msr”로 시작되는 카운터 집합 반환</span><span class="sxs-lookup"><span data-stu-id="2a35a-236">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")The following Windows PowerShell script will return the counter sets where the CounterSetName starts with "msr"</span></span>

```powershell
Get-Counter -ListSet msr*
```

<span data-ttu-id="2a35a-237">다음 정보를 포함 하는 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-237">Returns a list with the following information:</span></span>

```
CounterSetName     : MSRS 2014 Windows Service SharePoint Mode
CounterSetName     : MSRS 2014 Web Service SharePoint Mode
```

 <span data-ttu-id="2a35a-238">다음 Windows PowerShell 스크립트는 CounterSetName "MSRS 2014 Windows 서비스 SharePoint 모드"에 대 한 성능 카운터 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a35a-238">The following Windows PowerShell script will return the list of performance counters for the CounterSetName "MSRS 2014 Windows Service SharePoint Mode".</span></span>

```powershell
(Get-Counter -ListSet "MSRS 2014 Windows Service SharePoint Mode").Paths
```

## <a name="see-also"></a><span data-ttu-id="2a35a-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a35a-239">See Also</span></span>
 <span data-ttu-id="2a35a-240">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [Msrs 2014 웹 서비스 및 Msrs 2014 Windows 서비스 성능 개체에 대 한 보고서 서버 성능 성능 카운터를 모니터링 하는 기본 모드 &#40;&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)</span><span class="sxs-lookup"><span data-stu-id="2a35a-240">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)</span></span>