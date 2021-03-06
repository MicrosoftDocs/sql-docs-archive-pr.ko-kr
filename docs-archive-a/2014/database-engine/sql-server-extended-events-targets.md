---
title: SQL Server 확장 이벤트 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 010b7cc29543f266b77aaf180c50173ef9f70346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646607"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server Extended Events Targets
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 확장 이벤트 대상은 이벤트 소비자입니다. 대상은 파일에 기록하거나 이벤트 데이터를 메모리 버퍼에 저장하거나 이벤트 데이터를 집계할 수 있습니다. 대상은 동기적 또는 비동기적으로 데이터를 처리할 수 있습니다.  
  
 확장 이벤트는 대상이 세션당 단 한 번만 이벤트를 수신하도록 설계되어 있습니다.  
  
 확장 이벤트 세션에 사용할 수 있도록 확장 이벤트에서 제공하는 대상은 다음과 같습니다.  
  
-   [이벤트 카운터](../../2014/database-engine/event-counter-target.md)  
  
     확장 이벤트 세션 동안 발생하는 모든 지정된 이벤트의 수를 셉니다. 전체 이벤트 컬렉션의 오버헤드를 증가시키지 않으면서 작업 특성에 대한 정보를 얻는 데 사용합니다. 이 대상은 동기 대상입니다.  
  
-   [이벤트 파일](../../2014/database-engine/event-file-target.md)  
  
     완료된 메모리 버퍼에서 디스크로 이벤트 세션 출력을 쓰는 데 사용합니다. 이 대상은 비동기 대상입니다.  
  
-   [이벤트 쌍](../../2014/database-engine/event-pairing-target.md)  
  
     잠금 획득 및 잠금 해제와 같이 많은 종류의 이벤트는 쌍으로 발생합니다. 쌍을 이루는 집합에서 지정된 쌍 이벤트가 발생하지 않는 경우를 확인하는 데 사용합니다. 이 대상은 비동기 대상입니다.  
  
-   [ETW(Windows용 이벤트 추적)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이벤트와 Windows 운영 체제 또는 애플리케이션 이벤트 데이터의 상관 관계를 파악하는 데 사용합니다. 이 대상은 동기 대상입니다.  
  
-   [히스토그램](../../2014/database-engine/histogram-target.md)  
  
     지정된 이벤트 열 또는 동작을 기반으로 지정된 이벤트가 발생한 횟수를 계산하는 데 사용합니다. 이 대상은 비동기 대상입니다.  
  
-   [링 버퍼](../../2014/database-engine/ring-buffer-target.md)  
  
     FIFO(선입선출) 또는 이벤트별 FIFO 방식으로 메모리에 이벤트 데이터를 저장하는 데 사용합니다. 이 대상은 비동기 대상입니다.  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../relational-databases/extended-events/extended-events.md)   
 [확장 이벤트 패키지 SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [확장 이벤트 세션 SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [SQL Server 확장 이벤트 엔진](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
