---
title: MSSQLSERVER_21871 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731643"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21871|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21871|  
|메시지 텍스트|데이터베이스 %s의 게시자 %s이(가) 리디렉션되지 않았습니다.|  
  
## <a name="explanation"></a>설명  
 `sp_validate_replica_hosts_as_publishers`는 식별된 게시자 및 게시자 데이터베이스에 대한 항목이 있는지 확인하기 위해 배포 데이터베이스의 MSredirected_publishers 테이블을 확인합니다.  항목이 없으면 `sp_validate_replica_hosts_as_publishers`가 오류 21871을 반환합니다.  
  
## <a name="user-action"></a>사용자 동작  
 `sp_validate_replica_hosts_as_publishers`는 리디렉션된 게시자와만 관련됩니다. 게시자 데이터베이스가 가용성 그룹의 멤버인 경우에는 `sp_redirect_publisher` 저장 프로시저를 사용하여 게시자 및 게시자 데이터베이스에 가용성 그룹의 가용성 그룹 수신기 이름을 연결하십시오.  
  
  
