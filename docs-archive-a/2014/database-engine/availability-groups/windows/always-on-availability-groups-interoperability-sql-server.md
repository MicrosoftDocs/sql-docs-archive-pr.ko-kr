---
title: 'Always On 가용성 그룹: 상호 운용성(SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647250"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Always On 가용성 그룹: 상호 운용성(SQL Server)
  이 항목에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 다른 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]기능과의 상호 운용성에 대해 설명합니다.  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a>AlwaysOn 가용성 그룹와 상호 운용 하는 기능  
 다음 표에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 과 상호 운용하는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]기능이 나와 있습니다. **추가 정보** 열의 링크는 해당 기능에 대해 상호 운용성 고려 사항이 있음을 나타냅니다.  
  
|기능|추가 정보|  
|-------------|----------------------|  
|변경 데이터 캡처|[복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Change tracking|[복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|포함된 데이터베이스|[AlwaysOn 가용성 그룹에 포함된 데이터베이스(SQL Server)](always-on-availability-groups-sql-server.md)|  
|데이터베이스 암호화|[AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하는 암호화 된 데이터베이스&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|데이터베이스 스냅샷|[AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하는 데이터베이스 스냅숏&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM 및 FileTable|[AlwaysOn 가용성 그룹 &#40;SQL Server FILESTREAM 및 FileTable&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|전체 텍스트 검색|참고: 전체 텍스트 인덱스는 AlwaysOn 보조 데이터베이스와 동기화됩니다.|  
|로그 전달|[로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server로 마이그레이션하기 위한 필수 구성 요소&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|RBS(Remote Blob Store)|[RBS&#41; 및 AlwaysOn 가용성 그룹 &#40;SQL Server &#40;Remote Blob Store](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|복제에서[AlwaysOn 가용성 그룹에 대 한 복제 구성 (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [AlwaysOn 게시 데이터베이스를 유지 관리 하는 &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [복제 구독자 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[AlwaysOn 가용성 그룹이 포함된 Analysis Services](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|읽기 전용 보조 복제본을 보고 데이터 원본으로 사용하고 주 읽기/쓰기 주 복제본에 대한 부하를 줄일 수 있습니다.<br /><br /> [AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하 여 Reporting Services&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하 여 Service Broker&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server 에이전트||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a>AlwaysOn 가용성 그룹와 상호 운용 되지 않는 기능  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 다음 기능과 상호 운용되지 않습니다.  
  
-   데이터베이스 간 트랜잭션/분산 트랜잭션  
  
     해당 트랜잭션이 지원되지 않는 이유에 대한 자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.  
  
-   데이터베이스 미러링  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 관련 내용  
  
-   **블로그:**  
  
     [마이그레이션 가이드: 이전 클러스터링 및 미러링 배포에서 SQL Server 2012 장애 조치(Failover) 클러스터링 및 가용성 그룹으로 마이그레이션](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server 엔지니어 블로그](https://blogs.msdn.com/b/psssql/)  
  
-   **백서:**  
  
     [마이그레이션 가이드: 데이터베이스 미러링 및 로그 전달을 조합하는 이전 배포에서 AlwaysOn 가용성 그룹으로 마이그레이션](https://msdn.microsoft.com/library/jj635217)  
  
     [고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012에 대한 Microsoft 백서](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 고객 자문 팀 백서](http://sqlcat.com/)  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
