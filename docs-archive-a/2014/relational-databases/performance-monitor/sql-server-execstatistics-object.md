---
title: SQL Server, ExecStatistics 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647632"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, ExecStatistics 개체
  Microsoft SQL Server의 **SQLServer:ExecStatistics** 개체는 다양한 실행을 모니터링하는 카운터를 제공합니다.  
  
 이 표에서는 SQL Server **Exec Statistics** 카운터를 설명합니다.  
  
|SQL Server Exec Statistics 카운터|Description|  
|-----------------------------------------|-----------------|  
|**Distributed Query**|분산 쿼리의 실행과 관련된 통계입니다.|  
|**DTC calls**|DTC 호출의 실행과 관련된 통계입니다.|  
|**Extended Procedures**|확장 프로시저의 실행과 관련된 통계입니다.|  
|**OLEDB calls**|OLEDB 호출의 실행과 관련된 통계입니다.|  
  
 개체의 각 카운터는 다음 인스턴스를 포함합니다.  
  
|항목|Description|  
|----------|-----------------|  
|**평균 실행 시간(ms)**|선택된 실행 유형의 평균 실행 시간입니다.|  
|**초당 누적 실행 시간(ms)**|선택된 실행 유형의 초당 총 실행 시간입니다.|  
|**진행 중인 실행 작업**|선택된 실행 유형의 진행 중인 실행 작업 수입니다.|  
|**초당 시작된 실행 작업**|선택된 실행 유형의 초당 시작된 실행 작업 수입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](monitor-resource-usage-system-monitor.md)  
  
  
