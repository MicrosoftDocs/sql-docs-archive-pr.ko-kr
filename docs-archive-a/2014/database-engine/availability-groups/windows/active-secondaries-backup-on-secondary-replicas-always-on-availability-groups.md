---
title: '활성 보조: 보조 복제본에 백업 (Always On 가용성 그룹) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0cf899cdbeb1ae4ede6c9196b8eb93a9d9e54f05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733168"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a>활성 보조: 보조 복제본에 백업(Always On 가용성 그룹)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 활성 보조 기능에는 보조 복제본에서의 백업 작업 수행 지원이 포함됩니다. 백업 작업은 백업 압축과 함께 I/O 및 CPU에 상당한 부담을 줄 수 있습니다. 백업을 동기화되었거나 동기화 중인 보조 복제본으로 오프로드하면 계층 1 작업에 대한 주 복제본을 호스팅하는 서버 인스턴스에서 리소스를 사용할 수 있습니다.  
  
> [!NOTE]  
>  RESTORE 문은 가용성 그룹의 주 데이터베이스나 보조 데이터베이스에서 허용되지 않습니다.  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> 보조 복제본에서 지원되는 백업 유형  
  
-   `BACKUP DATABASE`는 보조 복제본에서 실행될 때 데이터베이스, 파일 또는 파일 그룹의 복사 전용 전체 백업만 지원합니다. 복사 전용 백업은 로그 체인에 영향을 미치거나 차등 비트맵을 지우지 않습니다.  
  
-   차등 백업은 보조 복제본에서 지원되지 않습니다.  
  
-   **BACKUP LOG** 는 정기적인 로그 백업만 지원합니다(COPY_ONLY 옵션은 보조 복제본의 로그 백업에 지원되지 않음).  
  
     가용성 모드(동기 커밋 또는 비동기 커밋)에 관계없이 모든 복제본(주 또는 보조)에서 수행되는 로그 백업에 대해 일관된 로그 체인이 보장됩니다.  
  
-   보조 데이터베이스를 백업하려면 보조 복제본이 주 복제본과 통신할 수 있어야 하고 `SYNCHRONIZED` 또는 `SYNCHRONIZING` 상태여야 합니다.  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a>백업 작업이 실행 되는 위치 구성  
 보조 복제본에서 백업을 수행하여 주 프로덕션 서버에서 백업 작업을 오프로드하면 많은 이점이 있습니다. 그러나 보조 복제본에서 백업을 수행하면 백업 작업이 실행되어야 하는 위치를 결정하는 프로세스가 상당히 복잡해집니다. 이 문제를 해결하려면 백업 작업이 실행되는 위치를 다음과 같이 구성합니다.  
  
1.  가용성 그룹을 구성하여 백업을 수행할 가용성 복제본을 지정합니다. 자세한 내용은 *CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;* 또는 *ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;* 에서 [CREATE AVAILABILITY GROUP&amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/create-availability-group-transact-sql) 또는 [ALTER AVAILABILITY GROUP&amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)상태여야 합니다.  
  
2.  백업을 수행할 후보 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 모든 가용성 데이터베이스에 대한 스크립트 백업 작업을 만듭니다. 자세한 내용은 [가용성 복제본에 백업 구성&#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)상태여야 합니다.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 관련 작업  
 **보조 복제본에 백업을 구성하려면**  
  
-   [가용성 복제본에 백업 구성&#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 **현재 복제본이 선호 백업 복제본인지 여부를 확인하려면**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 **백업 작업을 만들려면**  
  
-   [유지 관리 계획 마법사 사용](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [작업 구현](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [복사 전용 백업&#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
