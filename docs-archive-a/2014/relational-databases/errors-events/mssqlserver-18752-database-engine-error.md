---
title: MSSQLSERVER_18752 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a463e4019875f4a233ae2920f32bc2252376a41c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650074"
---
# <a name="mssqlserver_18752"></a>MSSQLSERVER_18752
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|18752|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|REPL_INUSE|  
|메시지 텍스트|한 번에 하나의 로그 판독기 에이전트 또는 로그 관련 프로시저(sp_repldone, sp_replcmds 및 sp_replshowcmds)만 데이터베이스에 연결할 수 있습니다. 로그 관련 프로시저를 실행한 경우 로그 판독기 에이전트를 시작하거나 다른 로그 관련 프로시저를 실행하기 전에 프로시저가 실행된 연결을 삭제하거나 해당 연결에 대해 sp_replflush를 실행하십시오.|  
  
## <a name="explanation"></a>설명  
 한 번에 하나의 로그 판독기 에이전트 또는 로그 관련 프로시저만 데이터베이스에 연결할 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 동일한 게시 데이터베이스에 대해 다른 로그 판독기가 실행되고 있지 않은지, 그리고 다른 활성 연결에서 연결을 끊거나 sp_replflush를 실행하지 않고 먼저 sp_replcmds/sp_repltrans/sp_repldone을 실행하지 않았는지 확인합니다.  
  
  
