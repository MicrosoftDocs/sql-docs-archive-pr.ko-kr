---
title: MSSQLSERVER_41396 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731620"
---
# <a name="mssqlserver_41396"></a>MSSQLSERVER_41396
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41396|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|MAX_SORT_ROWS_EXCEEDED|  
|메시지 텍스트|정렬 작업에서 버퍼 제한을 초과했습니다. 저장 프로시저 실행이 중단되었습니다. 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
 고유하게 컴파일된 저장 프로시저는 메모리에서 정렬 작업을 수행합니다. 정렬 버퍼 크기에 제한이 있습니다. 이 오류는 정렬 버퍼 크기가 이 제한을 초과했음을 의미합니다. 정렬 작업 및 저장 프로시저 실행이 중단되었습니다.  
  
 정렬 버퍼의 각 행 또는 항목의 크기는 정렬되는 행 수, 쿼리에 사용된 조인 수, 집계 함수의 수 및 유형에 따라 결정됩니다. 쿼리를 단순화하여 각 행의 크기를 줄이고 정렬 버퍼에 더 많은 행이 들어가도록 할 수 있습니다. 기본 테이블의 행 크기는 정렬 버퍼의 각 행 또는 항목의 크기에 영향을 주지 않습니다.  
  
## <a name="user-action"></a>사용자 동작  
 더 적은 수의 행을 선택하거나 조인 또는 집계 함수를 제거하여 쿼리를 단순화하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
