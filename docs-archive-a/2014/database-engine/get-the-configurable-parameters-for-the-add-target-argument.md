---
title: ADD TARGET 인수에 대해 구성 가능한 매개 변수를 가져옵니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30644bc30c0bd8c4ccbc17c616c6f24bf9455dc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732935"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>ADD TARGET 인수에 대한 구성 가능한 매개 변수 가져오기
  이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 쿼리 편집기를 사용합니다.  
  
 이 프로시저의 문이 끝나면 쿼리 편집기의 **결과** 탭에 다음 열이 표시됩니다.  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   필수  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 확장 이벤트 세션을 만들기 전에 CREATE EVENT SESSION 또는 ALTER EVENT SESSION에 ADD TARGET 인수를 사용할 경우에 어떤 매개 변수를 설정할 수 있는지 확인하는 것이 좋습니다.  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>쿼리 편집기를 사용하여 ADD TARGET 인수에 대해 구성 가능한 매개 변수를 가져오려면  
  
-   쿼리 편집기에서 다음 문을 실행합니다.  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
