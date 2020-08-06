---
title: 등록 된 패키지에 대 한 이벤트 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5e3665a695bd3f40407a8680872c9b0dc79fbc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661277"
---
# <a name="view-the-events-for-registered-packages"></a><span data-ttu-id="17060-102">등록된 패키지에 대한 이벤트 보기</span><span class="sxs-lookup"><span data-stu-id="17060-102">View the Events for Registered Packages</span></span>
  <span data-ttu-id="17060-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 확장 이벤트 세션을 만들기 전에 등록된 패키지에서 사용할 수 있는 이벤트를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17060-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to find out what events are available in the registered packages.</span></span> <span data-ttu-id="17060-104">자세한 내용은 [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17060-104">For more information, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
 <span data-ttu-id="17060-105">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17060-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
 <span data-ttu-id="17060-106">이 프로시저의 문이 끝나면 쿼리 편집기의 **결과** 탭에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17060-106">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="17060-107">name.</span><span class="sxs-lookup"><span data-stu-id="17060-107">name.</span></span> <span data-ttu-id="17060-108">패키지 이름.</span><span class="sxs-lookup"><span data-stu-id="17060-108">The package name.</span></span>  
  
-   <span data-ttu-id="17060-109">event.</span><span class="sxs-lookup"><span data-stu-id="17060-109">event.</span></span> <span data-ttu-id="17060-110">이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="17060-110">The event name.</span></span>  
  
-   <span data-ttu-id="17060-111">keyword.</span><span class="sxs-lookup"><span data-stu-id="17060-111">keyword.</span></span> <span data-ttu-id="17060-112">내부 숫자 매핑 테이블에서 파생된 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="17060-112">A keyword derived from an internal numeric mapping table.</span></span>  
  
-   <span data-ttu-id="17060-113">channel.</span><span class="sxs-lookup"><span data-stu-id="17060-113">channel.</span></span> <span data-ttu-id="17060-114">이벤트의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="17060-114">The audience for an event.</span></span>  
  
-   <span data-ttu-id="17060-115">description.</span><span class="sxs-lookup"><span data-stu-id="17060-115">description.</span></span> <span data-ttu-id="17060-116">이벤트 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="17060-116">The event description.</span></span>  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a><span data-ttu-id="17060-117">쿼리 편집기를 사용하여 등록된 패키지에 대한 이벤트를 보려면</span><span class="sxs-lookup"><span data-stu-id="17060-117">To view the events for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="17060-118">쿼리 편집기에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="17060-118">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17060-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17060-119">See Also</span></span>  
 <span data-ttu-id="17060-120">[확장 이벤트 패키지 SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="17060-120">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="17060-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17060-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="17060-122">sys.dm_xe_packages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17060-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
