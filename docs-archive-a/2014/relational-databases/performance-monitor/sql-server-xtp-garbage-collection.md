---
title: XTP 가비지 수집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 341a45c1c103f154672bb01a0648339562ee9750
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730580"
---
# <a name="xtp-garbage-collection"></a>XTP 가비지 수집
  XTP 가비지 수집 성능 개체에는 XTP 엔진의 가비지 수집기와 관련된 카운터가 포함됩니다.  
  
 이 표에서는 **XTP 가비지 수집** 카운터에 대해 설명합니다.  
  
|카운터|Description|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (GC-issued)**|가비지 수집기에 의해 실행된 불량 영역 청소(dusty corner sweeps) 중 발생한 초당 검색 재시도 횟수입니다(평균). 이 카운터는 사용자용이 아닌 매우 낮은 수준의 카운터입니다.|  
|**Main GC work items/sec**|기본 GC 스레드에서 처리되는 작업 항목 수입니다.|  
|**Parallel GC work item/sec**|병렬 스레드가 GC 작업 항목을 실행한 횟수입니다.|  
|**Rows processed/sec**|가비지 수집기에서 처리된 초당 행 수입니다(평균).|  
|**Rows processed/sec (first in bucket and removed)**|처음에 해당 해시 버킷에 포함되었고 즉시 제거할 수 있었던 가비지 수집기에서 처리된 초당 행 수입니다(평균).|  
|**Rows processed/sec (first in bucket)**|처음에 해당 해시 버킷에 포함되었던 가비지 수집기에서 처리된 초당 행 수입니다(평균).|  
|**Rows processed/sec (marked for unlink)**|이미 연결 해제로 표시된 가비지 수집기에서 처리된 초당 행 수입니다(평균).|  
|**Rows processed/sec (no sweep needed)**|불량 영역 청소(dusty corner sweep)가 필요하지 않은 가비지 수집기에 의해 처리된 초당 행 수입니다(평균).|  
|**Sweep expired rows removed/sec**|불량 영역 청소(dusty corner sweeps) 중 제거된 만료된 초당 행 수입니다(평균).|  
|**Sweep expired rows touched/sec**|불량 영역 청소(dusty corner sweeps) 중 처리된 만료된 초당 행 수입니다(평균).|  
|**Sweep expiring rows touched/sec**|불량 영역 청소(dusty corner sweeps) 중 처리된 만료되는 초당 행 수입니다(평균).|  
|**Sweep rows touched/sec**|불량 영역 청소(dusty corner sweeps) 중 처리된 초당 행 수입니다(평균).|  
|**Sweep scans started/sec**|시작된 초당 불량 영역 청소(dusty corner sweeps) 검사 수입니다(평균).|  
  
## <a name="see-also"></a>참고 항목  
 [XTP &#40;메모리 내 OLTP&#41; 성능 카운터](../../integration-services/performance/performance-counters.md)  
  
  
