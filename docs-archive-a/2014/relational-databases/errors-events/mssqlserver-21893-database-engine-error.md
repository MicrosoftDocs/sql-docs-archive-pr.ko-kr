---
title: MSSQLSERVER_21893 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92479d7727ac2300d6a60d02492667d99a69b022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653433"
---
# <a name="mssqlserver_21893"></a>MSSQLSERVER_21893
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21893|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21893|  
|메시지 텍스트|원래 게시자 '%s'의 구독자(%s)가 리디렉션된 게시자 '%s'에 원격 서버로 표시되지 않습니다. `sp_addlinkedserver`리디렉션된 게시자에서를 실행 하 여 이러한 구독자를 원격 서버로 추가 합니다.|  
  
## <a name="explanation"></a>설명  
 `sp_validate_redirected_publisher`는 원격 서버에 있는 게시자 데이터베이스의 구독 메타데이터 테이블을 사용하여 연관된 구독자를 식별하고 이러한 구독자에 대해 master.dbo.sysservers에 연관된 항목이 있는지 확인합니다. 이 오류는 식별된 구독자 중 하나라도 없는 경우에 반환됩니다.  
  
 이는 오류로 간주되지 않습니다. 이 오류가 발생한 에이전트에서는 이 오류를 정보로 기록하지만 에이전트가 종료되지는 않습니다. 이는 새 게시자에 적절한 구독자 항목이 없더라도 복제에 주는 영향이 적기 때문입니다. sysservers에 구독자에 대한 적절한 항목이 없으면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 통해 일부 구독 관리 작업을 수행할 경우 작업이 실패할 수 있습니다. 하지만 관리 저장 프로시저를 명시적으로 실행하여 동일한 작업을 수행할 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 리디렉션된 게시자에서 식별된 각 구독자에 대해 `sp_addlinkedserver`를 실행하여 각각을 원격 서버로 추가한 다음 `sp_serveroption`을 실행하여 서버에 대해 구독자 비트를 설정하십시오.  
  
  
