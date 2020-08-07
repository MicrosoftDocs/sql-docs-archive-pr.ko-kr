---
title: Background Job Error 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11aeaa058209eebd93b83fc812db2173167bf65a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731595"
---
# <a name="background-job-error-event-class"></a><span data-ttu-id="38362-102">Background Job Error 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="38362-102">Background Job Error Event Class</span></span>
  <span data-ttu-id="38362-103">**Background Job Error** 이벤트 클래스는 백그라운드 작업이 비정상적으로 종료되었을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="38362-103">The **Background Job Error** event class occurs when a background job has terminated abnormally.</span></span> <span data-ttu-id="38362-104">이 경우 시스템 관리자의 조치가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38362-104">This condition might require the attention of a system administrator.</span></span>  
  
## <a name="background-job-error-event-class-data-columns"></a><span data-ttu-id="38362-105">Background Job Error 이벤트 클래스 데이터 열</span><span class="sxs-lookup"><span data-stu-id="38362-105">Background Job Error Event Class Data Columns</span></span>  
  
|<span data-ttu-id="38362-106">데이터 열 이름</span><span class="sxs-lookup"><span data-stu-id="38362-106">Data column name</span></span>|<span data-ttu-id="38362-107">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="38362-107">Data type</span></span>|<span data-ttu-id="38362-108">Description</span><span class="sxs-lookup"><span data-stu-id="38362-108">Description</span></span>|<span data-ttu-id="38362-109">열 ID</span><span class="sxs-lookup"><span data-stu-id="38362-109">Column ID</span></span>|<span data-ttu-id="38362-110">필터 가능</span><span class="sxs-lookup"><span data-stu-id="38362-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="38362-111">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="38362-111">**DatabaseID**</span></span>|<span data-ttu-id="38362-112">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-112">**int**</span></span>|<span data-ttu-id="38362-113">작업에서 지정한 데이터베이스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-113">ID of the database specified by job.</span></span> <span data-ttu-id="38362-114">DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38362-114">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="38362-115">3</span><span class="sxs-lookup"><span data-stu-id="38362-115">3</span></span>|<span data-ttu-id="38362-116">yes</span><span class="sxs-lookup"><span data-stu-id="38362-116">Yes</span></span>|  
|<span data-ttu-id="38362-117">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="38362-117">**DatabaseName**</span></span>|<span data-ttu-id="38362-118">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="38362-118">**nvarchar**</span></span>|<span data-ttu-id="38362-119">사용자 문이 실행되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-119">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="38362-120">35</span><span class="sxs-lookup"><span data-stu-id="38362-120">35</span></span>|<span data-ttu-id="38362-121">yes</span><span class="sxs-lookup"><span data-stu-id="38362-121">Yes</span></span>|  
|<span data-ttu-id="38362-122">**오류**</span><span class="sxs-lookup"><span data-stu-id="38362-122">**Error**</span></span>|<span data-ttu-id="38362-123">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-123">**int**</span></span>|<span data-ttu-id="38362-124">마지막 시도의 오류 번호입니다(**EventSubClass** 1에만 해당).</span><span class="sxs-lookup"><span data-stu-id="38362-124">Error number of the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="38362-125">31</span><span class="sxs-lookup"><span data-stu-id="38362-125">31</span></span>|<span data-ttu-id="38362-126">yes</span><span class="sxs-lookup"><span data-stu-id="38362-126">Yes</span></span>|  
|<span data-ttu-id="38362-127">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="38362-127">**EventClass**</span></span>|<span data-ttu-id="38362-128">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-128">**int**</span></span>|<span data-ttu-id="38362-129">이벤트 유형 = 193</span><span class="sxs-lookup"><span data-stu-id="38362-129">Type of event = 193.</span></span>|<span data-ttu-id="38362-130">27</span><span class="sxs-lookup"><span data-stu-id="38362-130">27</span></span>|<span data-ttu-id="38362-131">예</span><span class="sxs-lookup"><span data-stu-id="38362-131">No</span></span>|  
|<span data-ttu-id="38362-132">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="38362-132">**EventSequence**</span></span>|<span data-ttu-id="38362-133">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-133">**int**</span></span>|<span data-ttu-id="38362-134">요청 내의 지정된 이벤트 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-134">The sequence of a given event within the request.</span></span>|<span data-ttu-id="38362-135">51</span><span class="sxs-lookup"><span data-stu-id="38362-135">51</span></span>|<span data-ttu-id="38362-136">예</span><span class="sxs-lookup"><span data-stu-id="38362-136">No</span></span>|  
|<span data-ttu-id="38362-137">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="38362-137">**EventSubClass**</span></span>|<span data-ttu-id="38362-138">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-138">**int**</span></span>|<span data-ttu-id="38362-139">이벤트 하위 클래스의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-139">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="38362-140">1 = 실패 후 백그라운드 작업 포기 중</span><span class="sxs-lookup"><span data-stu-id="38362-140">1 = Background job giving up after failure.</span></span><br /><br /> <span data-ttu-id="38362-141">2 = 백그라운드 작업 삭제됨 - 큐가 꽉 참</span><span class="sxs-lookup"><span data-stu-id="38362-141">2 = Background job dropped - queue is full.</span></span><br /><br /> <span data-ttu-id="38362-142">3 = 백그라운드 작업이 오류를 반환했음</span><span class="sxs-lookup"><span data-stu-id="38362-142">3 = Background job returned an error.</span></span>|<span data-ttu-id="38362-143">21</span><span class="sxs-lookup"><span data-stu-id="38362-143">21</span></span>|<span data-ttu-id="38362-144">yes</span><span class="sxs-lookup"><span data-stu-id="38362-144">Yes</span></span>|  
|<span data-ttu-id="38362-145">**IndexID**</span><span class="sxs-lookup"><span data-stu-id="38362-145">**IndexID**</span></span>|<span data-ttu-id="38362-146">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-146">**int**</span></span>|<span data-ttu-id="38362-147">이벤트에 의해 영향 받는 개체의 인덱스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-147">ID for the index on the object affected by the event.</span></span> <span data-ttu-id="38362-148">개체의 인덱스 ID를 확인하려면 **sysindexes** 시스템 테이블의 **indid** 열을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="38362-148">To determine the index ID for an object, use the **indid** column of the **sysindexes** system table.</span></span>|<span data-ttu-id="38362-149">24</span><span class="sxs-lookup"><span data-stu-id="38362-149">24</span></span>|<span data-ttu-id="38362-150">yes</span><span class="sxs-lookup"><span data-stu-id="38362-150">Yes</span></span>|  
|<span data-ttu-id="38362-151">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="38362-151">**IntegerData**</span></span>|<span data-ttu-id="38362-152">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-152">**int**</span></span>|<span data-ttu-id="38362-153">작업이 시도한 횟수입니다(**EventSubClass** 1에만 해당).</span><span class="sxs-lookup"><span data-stu-id="38362-153">Number of tries attempted by the job (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="38362-154">25</span><span class="sxs-lookup"><span data-stu-id="38362-154">25</span></span>|<span data-ttu-id="38362-155">yes</span><span class="sxs-lookup"><span data-stu-id="38362-155">Yes</span></span>|  
|<span data-ttu-id="38362-156">**IntegerData2**</span><span class="sxs-lookup"><span data-stu-id="38362-156">**IntegerData2**</span></span>|<span data-ttu-id="38362-157">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-157">**int**</span></span>|<span data-ttu-id="38362-158">작업 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-158">Job sequence number.</span></span>|<span data-ttu-id="38362-159">55</span><span class="sxs-lookup"><span data-stu-id="38362-159">55</span></span>|<span data-ttu-id="38362-160">yes</span><span class="sxs-lookup"><span data-stu-id="38362-160">Yes</span></span>|  
|<span data-ttu-id="38362-161">**Exchange Spill**</span><span class="sxs-lookup"><span data-stu-id="38362-161">**ObjectID**</span></span>|<span data-ttu-id="38362-162">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-162">**int**</span></span>|<span data-ttu-id="38362-163">시스템이 할당한 개체의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-163">System-assigned ID of the object.</span></span>|<span data-ttu-id="38362-164">22</span><span class="sxs-lookup"><span data-stu-id="38362-164">22</span></span>|<span data-ttu-id="38362-165">yes</span><span class="sxs-lookup"><span data-stu-id="38362-165">Yes</span></span>|  
|<span data-ttu-id="38362-166">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="38362-166">**SessionLoginName**</span></span>|<span data-ttu-id="38362-167">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="38362-167">**nvarchar**</span></span>|<span data-ttu-id="38362-168">세션을 시작한 사용자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-168">Login name of the user that originated the session.</span></span> <span data-ttu-id="38362-169">예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38362-169">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="38362-170">이 열에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 로그인이 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38362-170">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows logins.</span></span>|<span data-ttu-id="38362-171">64</span><span class="sxs-lookup"><span data-stu-id="38362-171">64</span></span>|<span data-ttu-id="38362-172">yes</span><span class="sxs-lookup"><span data-stu-id="38362-172">Yes</span></span>|  
|<span data-ttu-id="38362-173">**Severity**</span><span class="sxs-lookup"><span data-stu-id="38362-173">**Severity**</span></span>|<span data-ttu-id="38362-174">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-174">**int**</span></span>|<span data-ttu-id="38362-175">마지막 시도에서 발생한 오류의 심각도입니다(**EventSubClass** 1에만 해당).</span><span class="sxs-lookup"><span data-stu-id="38362-175">Severity level of the error on the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="38362-176">20</span><span class="sxs-lookup"><span data-stu-id="38362-176">20</span></span>|<span data-ttu-id="38362-177">yes</span><span class="sxs-lookup"><span data-stu-id="38362-177">Yes</span></span>|  
|<span data-ttu-id="38362-178">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="38362-178">**StartTime**</span></span>|<span data-ttu-id="38362-179">**datetime**</span><span class="sxs-lookup"><span data-stu-id="38362-179">**datetime**</span></span>|<span data-ttu-id="38362-180">이 작업이 만들어진 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-180">Time at which the job was created.</span></span>|<span data-ttu-id="38362-181">14</span><span class="sxs-lookup"><span data-stu-id="38362-181">14</span></span>|<span data-ttu-id="38362-182">yes</span><span class="sxs-lookup"><span data-stu-id="38362-182">Yes</span></span>|  
|<span data-ttu-id="38362-183">**State**</span><span class="sxs-lookup"><span data-stu-id="38362-183">**State**</span></span>|<span data-ttu-id="38362-184">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-184">**int**</span></span>|<span data-ttu-id="38362-185">마지막 시도에서 발생한 오류의 상태입니다(**EventSubClass** 1에만 해당).</span><span class="sxs-lookup"><span data-stu-id="38362-185">State of the error on the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="38362-186">30</span><span class="sxs-lookup"><span data-stu-id="38362-186">30</span></span>|<span data-ttu-id="38362-187">yes</span><span class="sxs-lookup"><span data-stu-id="38362-187">Yes</span></span>|  
|<span data-ttu-id="38362-188">**TextData**</span><span class="sxs-lookup"><span data-stu-id="38362-188">**TextData**</span></span>|<span data-ttu-id="38362-189">**ntext**</span><span class="sxs-lookup"><span data-stu-id="38362-189">**ntext**</span></span>|<span data-ttu-id="38362-190">이벤트 하위 클래스 값의 텍스트 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-190">Text description of the event subclass value.</span></span>|<span data-ttu-id="38362-191">1</span><span class="sxs-lookup"><span data-stu-id="38362-191">1</span></span>|<span data-ttu-id="38362-192">yes</span><span class="sxs-lookup"><span data-stu-id="38362-192">Yes</span></span>|  
|<span data-ttu-id="38362-193">**형식**</span><span class="sxs-lookup"><span data-stu-id="38362-193">**Type**</span></span>|<span data-ttu-id="38362-194">**int**</span><span class="sxs-lookup"><span data-stu-id="38362-194">**int**</span></span>|<span data-ttu-id="38362-195">작업 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="38362-195">Type of job.</span></span>|<span data-ttu-id="38362-196">57</span><span class="sxs-lookup"><span data-stu-id="38362-196">57</span></span>|<span data-ttu-id="38362-197">yes</span><span class="sxs-lookup"><span data-stu-id="38362-197">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38362-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38362-198">See Also</span></span>  
 <span data-ttu-id="38362-199">[확장 이벤트](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="38362-199">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="38362-200">[sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="38362-200">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="38362-201">Auto Stats 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="38362-201">Auto Stats Event Class</span></span>](auto-stats-event-class.md)  
  
  