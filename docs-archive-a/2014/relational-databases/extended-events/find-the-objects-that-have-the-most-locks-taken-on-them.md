---
title: 가장 많은 잠금이 발생한 개체 찾기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- objects [SQL Server], extended events
- xe
- extended events [SQL Server], locks
- objects [SQL Server], locks
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
author: rothja
ms.author: jroth
ms.openlocfilehash: 345c5f179358bd7b8df587b76c9c6053235d3a73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646462"
---
# <a name="find-the-objects-that-have-the-most-locks-taken-on-them"></a>가장 많은 잠금이 발생한 개체 찾기
  데이터베이스 관리자는 종종 데이터베이스 성능을 저하시키는 잠금의 원인을 파악해야 합니다.  
  
 예를 들어 프로덕션 서버에서 병목 상태가 발생할 수 있는지 모니터링하고 있는데 경쟁이 심한 리소스가 있다고 의심되어 이러한 개체에 대해 수행할 수 있는 잠금 수를 확인하려고 합니다. 가장 빈번하게 잠기는 개체가 식별되면 경쟁하는 개체에 대한 액세스를 최적화하는 조치를 취할 수 있습니다.  
  
 이렇게 하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기를 사용합니다.  
  
### <a name="to-find-the-objects-that-have-the-most-locks"></a>가장 많은 잠금이 발생한 개체를 찾으려면  
  
1.  쿼리 편집기에서 다음 문을 실행합니다.  
  
    ```  
    -- Find objects in a particular database that have the most  
    -- lock acquired. This sample uses AdventureWorksDW2012.  
    -- Create the session and add an event and target.  
    --   
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')  
    DROP EVENT session LockCounts ON SERVER  
    GO  
    DECLARE @dbid int  
  
    SELECT @dbid = db_id('AdventureWorksDW2012')  
  
    DECLARE @sql nvarchar(1024)  
    SET @sql = '  
    CREATE event session LockCounts ON SERVER  
    ADD EVENT sqlserver.lock_acquired (WHERE database_id =' + CAST(@dbid AS nvarchar) +')  
    ADD TARGET package0.histogram(   
    SET filtering_event_name=''sqlserver.lock_acquired'', source_type=0, source=''resource_0'')'  
  
    EXEC (@sql)  
    GO  
    ALTER EVENT session LockCounts ON SERVER   
    STATE=start  
    GO  
    --   
    -- Create a simple workload that takes locks.  
    --   
    USE AdventureWorksDW2012  
    GO  
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems  
    GO  
    -- The histogram target output is available from the   
    -- sys.dm_xe_session_targets dynamic management view in  
    -- XML format.  
    -- The following query joins the bucketizing target output with  
    -- sys.objects to obtain the object names.  
    --  
    SELECT name, object_id, lock_count FROM   
    (SELECT objstats.value('.','bigint') AS lobject_id,   
    objstats.value('@count', 'bigint') AS lock_count  
    FROM (  
    SELECT CAST(xest.target_data AS XML)  
    LockData  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'  
    ) Locks  
    CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)  
     ) LockedObjects   
    INNER JOIN sys.objects o  
    ON LockedObjects.lobject_id = o.object_id  
    WHERE o.type != 'S' AND o.type = 'U'  
    ORDER BY lock_count desc  
    GO  
    --   
    -- Stop the event session.  
    --   
    ALTER EVENT SESSION LockCounts ON SERVER  
    state=stop  
    GO  
  
    ```  
  
 이 프로시저의 문이 끝나면 쿼리 편집기의 **결과** 탭에 다음 열이 표시됩니다.  
  
-   name  
  
-   object_id  
  
-   lock_count  
  
## <a name="see-also"></a>참고 항목  
 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [dm_xe_sessions &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)   
 [sys.server_event_sessions&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)  
  
  
