---
title: Deadlock Graph 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deadlock Graph event class
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078e125136643958a1cd9203d07f632c3023a9de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661130"
---
# <a name="deadlock-graph-event-class"></a>Deadlock Graph 이벤트 클래스
  **Deadlock Graph** 이벤트 클래스는 교착 상태의 XML에 대해 설명합니다. 이 클래스는 **Lock:Deadlock** 이벤트 클래스와 동시에 발생합니다.  
  
## <a name="deadlock-graph-event-class-data-columns"></a>Deadlock Graph 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|이벤트 유형 = 148|27|예|  
|**EventSequence**|**int**|요청 내에 지정된 이벤트 시퀀스입니다.|51|예|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자 이 값은 이 이벤트의 경우 항상 1입니다.|60|yes|  
|**LoginName**|**nvarchar**|사용자 로그인 이름(DOMAIN\username 형식의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 보안 로그인)입니다. 이 값은 항상 이 이벤트의 시스템 사용자입니다.|11|yes|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 sys.server_principals 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다. 이 값은 항상 이 이벤트의 시스템 사용자 SID입니다.|41|yes|  
|**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|예|  
|**SessionLoginName**|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|yes|  
|**SPID**|**int**|이벤트가 발생한 세션의 ID입니다.|12|yes|  
|**StartTime**|**datetime**|교착 상태가 감지된 시간입니다.|14|yes|  
|**TextData**|**ntext**|교착 상태에 대한 XML 설명입니다.|1|yes|  
|**TransactionID**|**bigint**|사용되지 않습니다.|4|yes|  
  
## <a name="see-also"></a>참고 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Lock:Deadlock 이벤트 클래스](lock-deadlock-event-class.md)  
  
  
