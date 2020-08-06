---
title: SQL:StmtRecompile 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL:StmtRecompile event class
ms.assetid: 3a134751-3e93-4fe8-bf22-1e0561189293
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec5f055f8ca86efc350436458ba0145efb0419a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743295"
---
# <a name="sqlstmtrecompile-event-class"></a><span data-ttu-id="d49c0-102">SQL:StmtRecompile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="d49c0-102">SQL:StmtRecompile Event Class</span></span>
  <span data-ttu-id="d49c0-103">SQL:StmtRecompile 이벤트 클래스는 모든 유형의 일괄 처리로 인해 발생한 문 수준의 다시 컴파일을 나타냅니다. 여기에는 저장 프로시저, 트리거, 임시 일괄 처리 및 쿼리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-103">The SQL:StmtRecompile event class indicates statement-level recompilations caused by all types of batches: stored procedures, triggers, ad hoc batches, and queries.</span></span> <span data-ttu-id="d49c0-104">sp_executesql, 동적 SQL, Prepare 메서드, Execute 메서드 또는 비슷한 인터페이스를 사용하여 쿼리를 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-104">Queries can be submitted by using sp_executesql, dynamic SQL, Prepare methods, Execute methods, or similar interfaces.</span></span> <span data-ttu-id="d49c0-105">SP:Recompile 이벤트 클래스 대신 SQL:StmtRecompile 이벤트 클래스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-105">The SQL:StmtRecompile event class should be used instead of the SP:Recompile event class.</span></span>  
  
## <a name="sqlstmtrecompile-event-class-data-columns"></a><span data-ttu-id="d49c0-106">SQL:StmtRecompile 이벤트 클래스 데이터 열</span><span class="sxs-lookup"><span data-stu-id="d49c0-106">SQL:StmtRecompile Event Class Data Columns</span></span>  
  
|<span data-ttu-id="d49c0-107">데이터 열 이름</span><span class="sxs-lookup"><span data-stu-id="d49c0-107">Data column name</span></span>|<span data-ttu-id="d49c0-108">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d49c0-108">Data type</span></span>|<span data-ttu-id="d49c0-109">Description</span><span class="sxs-lookup"><span data-stu-id="d49c0-109">Description</span></span>|<span data-ttu-id="d49c0-110">열 ID</span><span class="sxs-lookup"><span data-stu-id="d49c0-110">Column ID</span></span>|<span data-ttu-id="d49c0-111">필터 가능</span><span class="sxs-lookup"><span data-stu-id="d49c0-111">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="d49c0-112">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="d49c0-112">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결한 클라이언트 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-113">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d49c0-114">이 열은 프로그램의 표시 이름이 아니라 애플리케이션에서 전달한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-114">This column is populated with the values passed by the application rather than the displayed name of the program</span></span>|<span data-ttu-id="d49c0-115">10</span><span class="sxs-lookup"><span data-stu-id="d49c0-115">10</span></span>|<span data-ttu-id="d49c0-116">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-116">Yes</span></span>|  
|<span data-ttu-id="d49c0-117">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="d49c0-117">ClientProcessID</span></span>|`int`|<span data-ttu-id="d49c0-118">클라이언트 애플리케이션이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="d49c0-119">클라이언트가 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-119">This data column is populated if the client provides the process ID.</span></span>|<span data-ttu-id="d49c0-120">9</span><span class="sxs-lookup"><span data-stu-id="d49c0-120">9</span></span>|<span data-ttu-id="d49c0-121">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-121">Yes</span></span>|  
|<span data-ttu-id="d49c0-122">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="d49c0-122">DatabaseID</span></span>|`int`|<span data-ttu-id="d49c0-123">저장 프로시저가 실행되는 데이터베이스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-123">ID of the database in which the stored procedure is running.</span></span> <span data-ttu-id="d49c0-124">DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-124">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="d49c0-125">3</span><span class="sxs-lookup"><span data-stu-id="d49c0-125">3</span></span>|<span data-ttu-id="d49c0-126">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-126">Yes</span></span>|  
|<span data-ttu-id="d49c0-127">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="d49c0-127">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-128">저장 프로시저가 실행되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-128">Name of the database in which the stored procedure is running.</span></span>|<span data-ttu-id="d49c0-129">35</span><span class="sxs-lookup"><span data-stu-id="d49c0-129">35</span></span>|<span data-ttu-id="d49c0-130">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-130">Yes</span></span>|  
|<span data-ttu-id="d49c0-131">EventSequence</span><span class="sxs-lookup"><span data-stu-id="d49c0-131">EventSequence</span></span>|`int`|<span data-ttu-id="d49c0-132">요청 내의 이벤트 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-132">The sequence of an event within the request.</span></span>|<span data-ttu-id="d49c0-133">51</span><span class="sxs-lookup"><span data-stu-id="d49c0-133">51</span></span>|<span data-ttu-id="d49c0-134">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-134">No</span></span>|  
|<span data-ttu-id="d49c0-135">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="d49c0-135">EventSubClass</span></span>|`int`|<span data-ttu-id="d49c0-136">다시 컴파일하는 원인을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-136">Describes the cause of the recompilation:</span></span><br /><br /> <span data-ttu-id="d49c0-137">1 = 스키마 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-137">1 = Schema changed</span></span><br /><br /> <span data-ttu-id="d49c0-138">2 = 통계 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-138">2 = Statistics changed</span></span><br /><br /> <span data-ttu-id="d49c0-139">3 = 지연된 컴파일</span><span class="sxs-lookup"><span data-stu-id="d49c0-139">3 = Deferred compile</span></span><br /><br /> <span data-ttu-id="d49c0-140">4 = SET 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-140">4 = Set option changed</span></span><br /><br /> <span data-ttu-id="d49c0-141">5 = 임시 테이블 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-141">5 = Temp table changed</span></span><br /><br /> <span data-ttu-id="d49c0-142">6 = 원격 행 집합 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-142">6 = Remote rowset changed</span></span><br /><br /> <span data-ttu-id="d49c0-143">7 = 찾아보기 권한 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-143">7 = For Browse permissions changed</span></span><br /><br /> <span data-ttu-id="d49c0-144">8 = 쿼리 알림 환경 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-144">8 = Query notification environment changed</span></span><br /><br /> <span data-ttu-id="d49c0-145">9 = 분할 뷰 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-145">9 = Partition view changed</span></span><br /><br /> <span data-ttu-id="d49c0-146">10 = 커서 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="d49c0-146">10 = Cursor options changed</span></span><br /><br /> <span data-ttu-id="d49c0-147">11 = 옵션(recompile) 요청</span><span class="sxs-lookup"><span data-stu-id="d49c0-147">11 = Option (recompile) requested</span></span>|<span data-ttu-id="d49c0-148">21</span><span class="sxs-lookup"><span data-stu-id="d49c0-148">21</span></span>|<span data-ttu-id="d49c0-149">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-149">Yes</span></span>|  
|<span data-ttu-id="d49c0-150">GroupID</span><span class="sxs-lookup"><span data-stu-id="d49c0-150">GroupID</span></span>|`int`|<span data-ttu-id="d49c0-151">SQL 추적 이벤트가 발생한 작업 그룹의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-151">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="d49c0-152">66</span><span class="sxs-lookup"><span data-stu-id="d49c0-152">66</span></span>|<span data-ttu-id="d49c0-153">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-153">Yes</span></span>|  
|<span data-ttu-id="d49c0-154">HostName</span><span class="sxs-lookup"><span data-stu-id="d49c0-154">HostName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-155">클라이언트에서 실행 중이며 해당 문을 제출한 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-155">Name of the computer on which the client is running which submitted this statement.</span></span> <span data-ttu-id="d49c0-156">클라이언트가 호스트 이름을 제공할 경우 이 데이터 열이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-156">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="d49c0-157">호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-157">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="d49c0-158">8</span><span class="sxs-lookup"><span data-stu-id="d49c0-158">8</span></span>|<span data-ttu-id="d49c0-159">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-159">Yes</span></span>|  
|<span data-ttu-id="d49c0-160">IntegerData2</span><span class="sxs-lookup"><span data-stu-id="d49c0-160">IntegerData2</span></span>|`int`|<span data-ttu-id="d49c0-161">다시 컴파일이 발생한 저장 프로시저 또는 일괄 처리 내에 있는 문의 끝 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-161">Ending offset of the statement within the stored procedure or batch that caused recompilation.</span></span> <span data-ttu-id="d49c0-162">문이 일괄 처리의 마지막 문인 경우 끝 오프셋은 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-162">Ending offset is -1 if the statement is the last statement in its batch.</span></span>|<span data-ttu-id="d49c0-163">55</span><span class="sxs-lookup"><span data-stu-id="d49c0-163">55</span></span>|<span data-ttu-id="d49c0-164">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-164">Yes</span></span>|  
|<span data-ttu-id="d49c0-165">IsSystem</span><span class="sxs-lookup"><span data-stu-id="d49c0-165">IsSystem</span></span>|`int`|<span data-ttu-id="d49c0-166">이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-166">Indicates whether the event occurred on a system process or a user process.</span></span><br /><br /> <span data-ttu-id="d49c0-167">1 = 시스템</span><span class="sxs-lookup"><span data-stu-id="d49c0-167">1 = system</span></span><br /><br /> <span data-ttu-id="d49c0-168">0 = 사용자</span><span class="sxs-lookup"><span data-stu-id="d49c0-168">0 = user</span></span>|<span data-ttu-id="d49c0-169">60</span><span class="sxs-lookup"><span data-stu-id="d49c0-169">60</span></span>|<span data-ttu-id="d49c0-170">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-170">Yes</span></span>|  
|<span data-ttu-id="d49c0-171">LineNumber</span><span class="sxs-lookup"><span data-stu-id="d49c0-171">LineNumber</span></span>|`int`|<span data-ttu-id="d49c0-172">일괄 처리에서 해당 문의 시퀀스 번호입니다(해당될 경우).</span><span class="sxs-lookup"><span data-stu-id="d49c0-172">Sequence number of this statement within the batch, if applicable.</span></span>|<span data-ttu-id="d49c0-173">5</span><span class="sxs-lookup"><span data-stu-id="d49c0-173">5</span></span>|<span data-ttu-id="d49c0-174">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-174">Yes</span></span>|  
|<span data-ttu-id="d49c0-175">LoginName</span><span class="sxs-lookup"><span data-stu-id="d49c0-175">LoginName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-176">이 일괄 처리를 제출한 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-176">Name of the login that submitted this batch.</span></span>|<span data-ttu-id="d49c0-177">11</span><span class="sxs-lookup"><span data-stu-id="d49c0-177">11</span></span>|<span data-ttu-id="d49c0-178">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-178">Yes</span></span>|  
|<span data-ttu-id="d49c0-179">LoginSid</span><span class="sxs-lookup"><span data-stu-id="d49c0-179">LoginSid</span></span>|`image`|<span data-ttu-id="d49c0-180">현재 로그인한 사용자의 SID(보안 ID)입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-180">Security identifier (SID) of the currently logged in user.</span></span> <span data-ttu-id="d49c0-181">이 정보는 sys.server_principals 카탈로그 뷰에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-181">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="d49c0-182">각 SID는 서버의 각 로그인마다 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-182">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="d49c0-183">41</span><span class="sxs-lookup"><span data-stu-id="d49c0-183">41</span></span>|<span data-ttu-id="d49c0-184">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-184">Yes</span></span>|  
|<span data-ttu-id="d49c0-185">NestLevel</span><span class="sxs-lookup"><span data-stu-id="d49c0-185">NestLevel</span></span>|`int`|<span data-ttu-id="d49c0-186">저장 프로시저 호출의 중첩 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-186">The nesting level of the stored procedure call.</span></span> <span data-ttu-id="d49c0-187">예를 들어 my_proc_a 저장 프로시저가 my_proc_b를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-187">For example, my_proc_a stored procedure calls my_proc_b.</span></span> <span data-ttu-id="d49c0-188">이 경우 my_proc_a의 NestLevel은 1이고 my_proc_b의 NestLevel은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-188">In this case, my_proc_a has a NestLevel of 1, my_proc_b has a NestLevel of 2.</span></span>|<span data-ttu-id="d49c0-189">29</span><span class="sxs-lookup"><span data-stu-id="d49c0-189">29</span></span>|<span data-ttu-id="d49c0-190">yes</span><span class="sxs-lookup"><span data-stu-id="d49c0-190">Yes</span></span>|  
|<span data-ttu-id="d49c0-191">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="d49c0-191">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-192">사용자가 속한 Windows 도메인입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-192">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="d49c0-193">7</span><span class="sxs-lookup"><span data-stu-id="d49c0-193">7</span></span>|<span data-ttu-id="d49c0-194">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-194">Yes</span></span>|  
|<span data-ttu-id="d49c0-195">NTUserName</span><span class="sxs-lookup"><span data-stu-id="d49c0-195">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-196">연결된 사용자의 Windows 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-196">Windows user name of connected user.</span></span>|<span data-ttu-id="d49c0-197">6</span><span class="sxs-lookup"><span data-stu-id="d49c0-197">6</span></span>|<span data-ttu-id="d49c0-198">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-198">Yes</span></span>|  
|<span data-ttu-id="d49c0-199">ObjectID</span><span class="sxs-lookup"><span data-stu-id="d49c0-199">ObjectID</span></span>|`int`|<span data-ttu-id="d49c0-200">다시 컴파일하도록 만든 문이 포함된 개체에 대해 시스템이 할당한 개체 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-200">System-assigned identifier of the object that contains the statement that caused the recompilation.</span></span> <span data-ttu-id="d49c0-201">이 개체는 저장 프로시저, 트리거 또는 사용자 정의 함수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-201">This object can be a stored procedure, trigger, or user-defined function.</span></span> <span data-ttu-id="d49c0-202">임시 일괄 처리나 준비된 SQL의 경우 ObjectID 및 ObjectName에서 NULL 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-202">For ad hoc batches or prepared SQL, ObjectID and ObjectName return a NULL value.</span></span>|<span data-ttu-id="d49c0-203">22</span><span class="sxs-lookup"><span data-stu-id="d49c0-203">22</span></span>|<span data-ttu-id="d49c0-204">yes</span><span class="sxs-lookup"><span data-stu-id="d49c0-204">Yes</span></span>|  
|<span data-ttu-id="d49c0-205">ObjectName</span><span class="sxs-lookup"><span data-stu-id="d49c0-205">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-206">ObjectID로 식별된 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-206">Name of the object identified by ObjectID.</span></span>|<span data-ttu-id="d49c0-207">34</span><span class="sxs-lookup"><span data-stu-id="d49c0-207">34</span></span>|<span data-ttu-id="d49c0-208">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-208">Yes</span></span>|  
|<span data-ttu-id="d49c0-209">ObjectType</span><span class="sxs-lookup"><span data-stu-id="d49c0-209">ObjectType</span></span>|`int`|<span data-ttu-id="d49c0-210">이벤트와 관련된 개체 유형을 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-210">Value that represents the type of object involved in the event.</span></span> <span data-ttu-id="d49c0-211">자세한 내용은 [ObjectType Trace Event Column](objecttype-trace-event-column.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d49c0-211">For more information, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="d49c0-212">28</span><span class="sxs-lookup"><span data-stu-id="d49c0-212">28</span></span>|<span data-ttu-id="d49c0-213">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-213">Yes</span></span>|  
|<span data-ttu-id="d49c0-214">Offset</span><span class="sxs-lookup"><span data-stu-id="d49c0-214">Offset</span></span>|`int`|<span data-ttu-id="d49c0-215">다시 컴파일이 발생한 저장 프로시저 또는 일괄 처리 내에 있는 문의 시작 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-215">Starting offset of the statement within the stored procedure or batch that caused recompilation.</span></span>|<span data-ttu-id="d49c0-216">61</span><span class="sxs-lookup"><span data-stu-id="d49c0-216">61</span></span>|<span data-ttu-id="d49c0-217">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-217">Yes</span></span>|  
|<span data-ttu-id="d49c0-218">RequestID</span><span class="sxs-lookup"><span data-stu-id="d49c0-218">RequestID</span></span>|`int`|<span data-ttu-id="d49c0-219">문을 포함하는 요청의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-219">ID of the request containing the statement.</span></span>|<span data-ttu-id="d49c0-220">49</span><span class="sxs-lookup"><span data-stu-id="d49c0-220">49</span></span>|<span data-ttu-id="d49c0-221">yes</span><span class="sxs-lookup"><span data-stu-id="d49c0-221">Yes</span></span>|  
|<span data-ttu-id="d49c0-222">ServerName</span><span class="sxs-lookup"><span data-stu-id="d49c0-222">ServerName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-223">추적할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-223">Name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="d49c0-224">26</span><span class="sxs-lookup"><span data-stu-id="d49c0-224">26</span></span>|<span data-ttu-id="d49c0-225">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-225">No</span></span>|  
|<span data-ttu-id="d49c0-226">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="d49c0-226">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="d49c0-227">세션을 시작한 사용자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-227">Login name of the user who originated the session.</span></span> <span data-ttu-id="d49c0-228">예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 SessionLoginName은 Login1을 표시하고 LoginName은 Login2를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-228">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="d49c0-229">이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-229">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="d49c0-230">64</span><span class="sxs-lookup"><span data-stu-id="d49c0-230">64</span></span>|<span data-ttu-id="d49c0-231">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-231">Yes</span></span>|  
|<span data-ttu-id="d49c0-232">SPID</span><span class="sxs-lookup"><span data-stu-id="d49c0-232">SPID</span></span>|`int`|<span data-ttu-id="d49c0-233">연결의 서버 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-233">Server process ID of the connection.</span></span>|<span data-ttu-id="d49c0-234">12</span><span class="sxs-lookup"><span data-stu-id="d49c0-234">12</span></span>|<span data-ttu-id="d49c0-235">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-235">Yes</span></span>|  
|<span data-ttu-id="d49c0-236">SqlHandle</span><span class="sxs-lookup"><span data-stu-id="d49c0-236">SqlHandle</span></span>|`varbinary`|<span data-ttu-id="d49c0-237">임시 쿼리 또는 데이터베이스의 텍스트 및 SQL 개체의 개체 ID를 기반으로 하는 64비트 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-237">64-bit hash based on the text of an ad hoc query or the database and object ID of an SQL object.</span></span> <span data-ttu-id="d49c0-238">이 값을 sys.dm_exec_sql_text에 전달하여 연결된 SQL 텍스트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-238">This value can be passed to sys.dm_exec_sql_text to retrieve the associated SQL text.</span></span>|<span data-ttu-id="d49c0-239">63</span><span class="sxs-lookup"><span data-stu-id="d49c0-239">63</span></span>|<span data-ttu-id="d49c0-240">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-240">No</span></span>|  
|<span data-ttu-id="d49c0-241">StartTime</span><span class="sxs-lookup"><span data-stu-id="d49c0-241">StartTime</span></span>|`datetime`|<span data-ttu-id="d49c0-242">이벤트가 시작된 시간입니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="d49c0-242">Time at which the event started, if available.</span></span>|<span data-ttu-id="d49c0-243">14</span><span class="sxs-lookup"><span data-stu-id="d49c0-243">14</span></span>|<span data-ttu-id="d49c0-244">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-244">Yes</span></span>|  
|<span data-ttu-id="d49c0-245">TextData</span><span class="sxs-lookup"><span data-stu-id="d49c0-245">TextData</span></span>|`ntext`|<span data-ttu-id="d49c0-246">다시 컴파일한 Transact-SQL 문의 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-246">Text of the Transact-SQL statement that recompiled.</span></span>|<span data-ttu-id="d49c0-247">1</span><span class="sxs-lookup"><span data-stu-id="d49c0-247">1</span></span>|<span data-ttu-id="d49c0-248">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-248">Yes</span></span>|  
|<span data-ttu-id="d49c0-249">TransactionID</span><span class="sxs-lookup"><span data-stu-id="d49c0-249">TransactionID</span></span>|`bigint`|<span data-ttu-id="d49c0-250">시스템이 할당한 트랜잭션의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-250">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="d49c0-251">4</span><span class="sxs-lookup"><span data-stu-id="d49c0-251">4</span></span>|<span data-ttu-id="d49c0-252">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-252">Yes</span></span>|  
|<span data-ttu-id="d49c0-253">XactSequence</span><span class="sxs-lookup"><span data-stu-id="d49c0-253">XactSequence</span></span>|`bigint`|<span data-ttu-id="d49c0-254">현재 트랜잭션을 설명하는 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="d49c0-254">Token that describes the current transaction.</span></span>|<span data-ttu-id="d49c0-255">50</span><span class="sxs-lookup"><span data-stu-id="d49c0-255">50</span></span>|<span data-ttu-id="d49c0-256">예</span><span class="sxs-lookup"><span data-stu-id="d49c0-256">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d49c0-257">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d49c0-257">See Also</span></span>  
 <span data-ttu-id="d49c0-258">[SP: Recompile 이벤트 클래스](sp-recompile-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="d49c0-258">[SP:Recompile Event Class](sp-recompile-event-class.md) </span></span>  
 [<span data-ttu-id="d49c0-259">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d49c0-259">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  