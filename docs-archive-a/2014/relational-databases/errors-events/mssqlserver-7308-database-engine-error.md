---
title: MSSQLSERVER_7308 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9978f35ebe41eeda1470220772f87e83ab1ad942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651013"
---
# <a name="mssqlserver_7308"></a>MSSQLSERVER_7308
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|7308|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|RMT_STA_DISABLED|  
|메시지 텍스트|OLE DB 공급자 '%ls'은(는) 단일 스레드 아파트 모드에서 실행되도록 구성되어 있으므로 분산 쿼리에 사용할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 STA(단일 스레드 아파트) 모드에서 실행되도록 구성된 OLE DB 공급자를 사용했습니다. STA(단일 스레드 아파트) 모드에서 실행되도록 구성된 OLE DB 공급자는 분산 쿼리에 사용할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 이 문제를 해결하려면 MTA(다중 스레드 아파트) 모드에서 실행되도록 OLE DB 공급자를 구성합니다. OLE DB 공급자가 MTA를 지원하지 않으며 MTA를 지원하는 버전으로 OLE DB 공급자를 업그레이드할 수 없는 경우 out-of-process를 실행하도록 OLE DB 공급자를 구성합니다. OLE DB 공급자가 MTA 또는 out-of-process 실행을 지원하는 경우 해당 OLE DB 공급자의 공급업체는 사용자에게 이를 알려줄 수 있어야 합니다.  
  
  
