---
title: 디스크 기반 테이블 스토리지와 메모리 액세스에 최적화된 테이블 스토리지 비교 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47cf84427b2f4f26a29f732575530b384d9c4fc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741011"
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a><span data-ttu-id="5bad4-102">디스크 기반 테이블 스토리지와 메모리 액세스에 최적화된 테이블 스토리지 비교</span><span class="sxs-lookup"><span data-stu-id="5bad4-102">Comparing Disk-Based Table Storage to Memory-Optimized Table Storage</span></span>
  
  
|<span data-ttu-id="5bad4-103">범주</span><span class="sxs-lookup"><span data-stu-id="5bad4-103">Categories</span></span>|<span data-ttu-id="5bad4-104">디스크 기반 테이블</span><span class="sxs-lookup"><span data-stu-id="5bad4-104">Disk-based Table</span></span>|<span data-ttu-id="5bad4-105">메모리 액세스에 최적화된 내구성이 있는 테이블</span><span class="sxs-lookup"><span data-stu-id="5bad4-105">Durable Memory-Optimized Table</span></span>|  
|----------------|-----------------------|-------------------------------------|  
|<span data-ttu-id="5bad4-106">DDL</span><span class="sxs-lookup"><span data-stu-id="5bad4-106">DDL</span></span>|<span data-ttu-id="5bad4-107">메타데이터 정보는 데이터베이스의 기본 파일 그룹에 있는 시스템 테이블에 저장되고 카탈로그 보기를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-107">Metadata information is stored in system tables in the primary filegroup of the database and is accessible through catalog views.</span></span>|<span data-ttu-id="5bad4-108">메타데이터 정보는 데이터베이스의 기본 파일 그룹에 있는 시스템 테이블에 저장되고 카탈로그 보기를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-108">Metadata information is stored in system tables in the primary filegroup of the database and is accessible through catalog views.</span></span>|  
|<span data-ttu-id="5bad4-109">구조</span><span class="sxs-lookup"><span data-stu-id="5bad4-109">Structure</span></span>|<span data-ttu-id="5bad4-110">행은 8K 페이지에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-110">Rows are stored in 8K pages.</span></span> <span data-ttu-id="5bad4-111">페이지는 같은 테이블의 행만 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-111">A page stores only rows from the same table.</span></span>|<span data-ttu-id="5bad4-112">행은 개별 행으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-112">Rows are stored as individual rows.</span></span> <span data-ttu-id="5bad4-113">페이지 구조는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-113">There is no page structure.</span></span> <span data-ttu-id="5bad4-114">데이터 파일에 있는 두 연속 행은 다른 메모리 최적화 테이블에 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-114">Two consecutive rows in a data file can belong to different memory-optimized tables.</span></span>|  
|<span data-ttu-id="5bad4-115">인덱스</span><span class="sxs-lookup"><span data-stu-id="5bad4-115">Indexes</span></span>|<span data-ttu-id="5bad4-116">인덱스는 데이터 행과 비슷한 페이지 구조로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-116">Indexes are stored in a page structure similar to data rows.</span></span>|<span data-ttu-id="5bad4-117">인덱스 정의만 유지됩니다(인덱스 행은 유지되지 않음).</span><span class="sxs-lookup"><span data-stu-id="5bad4-117">Only the index definition is persisted (not index rows).</span></span> <span data-ttu-id="5bad4-118">인덱스는 메모리 내에 유지되며 메모리 최적화 테이블이 데이터베이스를 다시 시작할 때 메모리로 로드되면 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-118">Indexes are maintained in-memory and are regenerated when the memory-optimized table is loaded into memory as part of restarting a database.</span></span> <span data-ttu-id="5bad4-119">인덱스 행은 유지되지 않으므로 인덱스 변경에 대한 로깅은 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-119">Since index rows are not persisted, no logging is done for index changes.</span></span>|  
|<span data-ttu-id="5bad4-120">DML 작업</span><span class="sxs-lookup"><span data-stu-id="5bad4-120">DML operation</span></span>|<span data-ttu-id="5bad4-121">첫 번째 단계는 페이지를 찾은 다음 버퍼 풀로 로드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-121">The first step is to find the page and then load it into buffer-pool.</span></span><br /><br /> <span data-ttu-id="5bad4-122">삽입</span><span class="sxs-lookup"><span data-stu-id="5bad4-122">Insert</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5bad4-123">은 클러스터형 인덱스의 경우 행 순서에 대한 페이지 계정에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-123">inserts the row on the page accounting for row ordering in case of clustered index.</span></span><br /><br /> <span data-ttu-id="5bad4-124">DELETE</span><span class="sxs-lookup"><span data-stu-id="5bad4-124">Delete</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5bad4-125">은 페이지에서 삭제할 행을 찾아 삭제됨으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-125">locates the row to be deleted on the page and marks it deleted.</span></span><br /><br /> <span data-ttu-id="5bad4-126">업데이트</span><span class="sxs-lookup"><span data-stu-id="5bad4-126">Update</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5bad4-127">은 페이지에서 행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-127">locates the row on the page.</span></span> <span data-ttu-id="5bad4-128">업데이트는 키가 아닌 열에 대해 현재 위치에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-128">The update is done in-place for non-key columns.</span></span> <span data-ttu-id="5bad4-129">키 열 업데이트는 삭제 및 삽입 작업에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-129">Key-column update is done by a delete and insert operation.</span></span><br /><br /> <span data-ttu-id="5bad4-130">DML 작업이 완료된 후 영향을 받는 페이지는 로깅 작업을 최소화하기 위해 버퍼 풀 정책, 검사점 또는 트랜잭션 커밋의 의 일부로 디스크에 플러시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-130">After the DML operation completes, the affected pages are flushed to disk as part of buffer pool policy, checkpoint or transaction commit for minimally-logged operations.</span></span> <span data-ttu-id="5bad4-131">페이지에 읽고 쓰는 작업은 불필요한 I/O를 초래합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-131">Both read/write operations on pages leads to unnecessary I/O.</span></span>|<span data-ttu-id="5bad4-132">메모리 최적화 테이블의 경우 데이터가 메모리에 있기 때문에 DML 작업은 직접 메모리에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-132">For memory-optimized tables, since the data resides in memory, the DML operations are done directly in memory.</span></span> <span data-ttu-id="5bad4-133">메모리 최적화 테이블에 대한 로그 레코드를 읽고 데이터 및 델타 파일에 유지시키는 백그라운드 스레드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-133">There is a background thread that reads the log records for memory-optimized tables and persist them into data and delta files.</span></span> <span data-ttu-id="5bad4-134">업데이트는 새로운 행 버전을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-134">An update generates a new row version.</span></span> <span data-ttu-id="5bad4-135">하지만 업데이트는 삭제 후 삽입으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-135">But an update is logged as a delete followed by an insert.</span></span>|  
|<span data-ttu-id="5bad4-136">데이터 조각화</span><span class="sxs-lookup"><span data-stu-id="5bad4-136">Data Fragmentation</span></span>|<span data-ttu-id="5bad4-137">데이터 조작은 데이터를 조각화하여 부분적으로 채워진 페이지와 디스크에 연속되지 않고 논리적으로 연속된 페이지가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-137">Data manipulation fragments data leading to partially filled pages and logically consecutive pages that are not contiguous on disk.</span></span> <span data-ttu-id="5bad4-138">이로 인해 데이터 액세스 성능이 저하되고 데이터 조각 모음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-138">This degrades data access performance and requires you to defragment data.</span></span>|<span data-ttu-id="5bad4-139">메모리 액세스에 최적화된 데이터는 페이지에 저장되지 않으므로 데이터 조각화가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-139">Memory-optimized data is not stored in pages so there is no data fragmentation.</span></span> <span data-ttu-id="5bad4-140">그러나 행이 업데이트되고 삭제됨에 따라 데이터 및 델타 파일을 압축해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-140">However, as rows are updated and deleted, the data and delta files need to be compacted.</span></span> <span data-ttu-id="5bad4-141">이런 작업은 병합 정책에 따라 백그라운드 MERGE 스레드에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bad4-141">This is done by a background MERGE thread based on a merge policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bad4-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bad4-142">See Also</span></span>  
 [<span data-ttu-id="5bad4-143">메모리 최적화 개체에 대한 스토리지 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="5bad4-143">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  