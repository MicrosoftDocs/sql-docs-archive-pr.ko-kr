---
title: MSSQLSERVER_10519 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736364"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|10519|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|메시지 텍스트|`@hints`에 지정된 힌트를 `@stmt` 또는 `@statement_start_offset`으로 지정된 문에 적용할 수 없으므로 계획 지침 '%.\*ls'을(를) 만들 수 없습니다. 힌트를 문에 적용할 수 있는지 확인하십시오.|  
  
## <a name="explanation"></a>설명  
 `@hints`에 지정된 힌트를 `@stmt` 또는 `@statement_start_offset`으로 지정된 문에 적용할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 문에 적용할 수 있는 힌트를 지정하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [계획 지침](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
