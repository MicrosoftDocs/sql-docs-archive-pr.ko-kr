---
title: MSSQLSERVER_41359 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659974"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41359|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|메시지 텍스트|데이터베이스 옵션 READ_COMMITTED_SNAPSHOT이 ON으로 설정된 경우 READ COMMITTED 격리 수준을 사용하여 메모리 액세스에 최적화된 테이블에 액세스하는 쿼리가 디스크 기반 테이블에 액세스할 수 없습니다. WITH (SNAPSHOT) 같은 테이블 힌트를 사용하여 메모리 액세스에 최적화된 테이블에 대해 지원되는 격리 수준을 제공합니다.|  
  
## <a name="explanation"></a>설명  
 READ_COMMITTED_SNAPSHOT이 ON으로 설정된 데이터베이스는 메모리 최적화 테이블과 디스크 기반 테이블에 모두 액세스하는 트랜잭션을 지원하지 않습니다.  
  
## <a name="user-action"></a>사용자 동작  
 READ_COMMITTED_SNAPSHOT을 OFF로 설정하거나 WITH (SNAPSHOT) 같은 테이블 수준 힌트를 사용하여 메모리 최적화 테이블에 대해 지원되는 격리 수준을 제공합니다. 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
