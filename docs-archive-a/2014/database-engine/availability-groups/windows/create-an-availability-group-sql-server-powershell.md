---
title: 가용성 그룹 만들기(SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3af9bf896b954e6849c0d491f9ed267655369ccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743459"
---
# <a name="create-an-availability-group-sql-server-powershell"></a>가용성 그룹 만들기(SQL Server PowerShell)
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 PowerShell cmdlet을 사용하여 AlwaysOn 가용성 그룹을 만들고 구성하는 방법에 대해 설명합니다. *가용성 그룹* 은 단일 단위로 장애 조치(Failover)될 사용자 데이터베이스 집합과 장애 조치(Failover)를 지원하는 장애 조치(Failover) 파트너 집합( *가용성 복제본*이라고 함)을 정의합니다.  
  
> [!NOTE]  
>  가용성 그룹에 대한 소개는 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.  

> [!NOTE]  
>  PowerShell cmdlet을 사용하는 대신 가용성 그룹 만들기 마법사나 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용할 수도 있습니다. 자세한 내용은 [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 또는 [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)에서 PowerShell cmdlet을 사용하여 Always On 가용성 그룹을 만들고 구성하는 방법에 대해 설명합니다.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
 가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a> 필수 구성 요소, 제한 사항 및 권장 사항  
  
-   가용성 그룹을 만들기 전에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 호스트 인스턴스가 각각 단일 WSFC 장애 조치(Failover) 클러스터 내의 다른 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는지 확인합니다. 또한 해당 서버 인스턴스가 다른 서버 인스턴스의 사전 요구 사항을 충족하는지와 다른 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 요구 사항을 충족하는지, 그리고 현재 권장 사항을 알고 있는지 확인합니다. 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.  
  
###  <a name="summary-of-tasks-and-corresponding-powershell-cmdlets"></a><a name="SummaryPSStatements"></a>태스크 및 해당 PowerShell Cmdlet 요약  
 다음 표에서는 가용성 그룹을 구성하는 데 필요한 기본 태스크와 PowerShell cmdlet이 지원하는 기능을 보여 줍니다. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 태스크는 표에 나오는 순서대로 수행해야 합니다.  
  
|Task|PowerShell cmdlet(사용 가능한 경우) 또는 Transact-SQL 문|태스크를 수행할 위치**<sup>*</sup>**|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스당 하나의 데이터베이스 미러링 엔드포인트 만들기|`New-SqlHadrEndPoint`|데이터베이스 미러링 엔드포인트가 없는 각 서버 인스턴스에서 실행합니다.<br /><br /> 참고: 기존 데이터베이스 미러링 엔드포인트를 변경하려면 `Set-SqlHadrEndpoint`를 사용합니다.|  
|가용성 그룹 만들기|먼저 `New-SqlAvailabilityReplica` cmdlet과 `-AsTemplate` 매개 변수를 사용하여 가용성 그룹에 포함할 두 개의 각 가용성 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.<br /><br /> 그런 다음 `New-SqlAvailabilityGroup` cmdlet을 사용하고 가용성 복제본 개체를 참조하여 가용성 그룹을 만듭니다.|초기 주 복제본을 호스트할 서버 인스턴스에서 실행합니다.|  
|가용성 그룹에 보조 복제본 조인|`Join-SqlAvailabilityGroup`|보조 복제본을 호스트할 각 서버 인스턴스에서 실행합니다.|  
|보조 데이터베이스 준비|`Backup-SqlDatabase` 및 `Restore-SqlDatabase`|주 복제본을 호스트하는 서버 인스턴스에 백업을 만듭니다.<br /><br /> `NoRecovery` 복원 매개 변수를 사용하여 보조 복제본을 호스팅하는 각 서버 인스턴스에 백업을 복원합니다. 또한 주 복제본을 호스팅하는 컴퓨터와 대상 보조 복제본을 호스팅하는 컴퓨터의 파일 경로가 다른 경우 `RelocateFile` 복원 매개 변수를 사용합니다.|  
|가용성 그룹에 각 보조 데이터베이스를 조인하여 데이터 동기화 시작|`Add-SqlAvailabilityDatabase`|보조 복제본을 호스트하는 각 서버 인스턴스에서 실행합니다.|  
  
 **<sup>*</sup>** 지정 된 태스크를 수행 하려면 디렉터리를 `cd` 표시 된 서버 인스턴스로 변경 합니다 ().  
  
###  <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><a name="PsProviderLinks"></a>SQL Server PowerShell 공급자를 설정 하 고 사용 하려면  
  
-   [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="using-powershell-to-create-and-configure-an-availability-group"></a><a name="PowerShellProcedure"></a>PowerShell을 사용 하 여 가용성 그룹 만들기 및 구성  
  
> [!NOTE]  
>  특정 cmdlet의 구문 및 예를 보려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 환경에서 `Get-Help` cmdlet을 사용합니다. 자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.  
  
1.  주 복제본을 호스팅할 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.  
  
2.  주 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.  
  
3.  각 보조 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.  
  
4.  가용성 그룹을 만듭니다.  
  
    > [!NOTE]  
    >  가용성 그룹 이름의 최대 길이는 128자입니다.  
  
5.  새 보조 복제본을 가용성 그룹에 조인합니다. 자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.  
  
6.  가용성 그룹의 각 데이터베이스에 대해 RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 백업을 복원하는 방법으로 보조 데이터베이스를 만듭니다.  
  
7.  모든 새 보조 데이터베이스를 가용성 그룹에 조인합니다. 자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.  
  
8.  필요한 경우 Windows `dir` 명령을 사용하여 새 가용성 그룹의 내용을 확인합니다.  
  
> [!NOTE]  
>  서버 인스턴스의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정이 다른 도메인 사용자 계정으로 실행되는 경우에는 각 서버 인스턴스에서 다른 서버 인스턴스에 대한 로그인을 만들고 로컬 데이터베이스 미러링 엔드포인트에 이 로그인 CONNECT 권한을 부여합니다.  
  
##  <a name="example-using-powershell-to-create-an-availability-group"></a><a name="ExampleConfigureGroup"></a>예: PowerShell을 사용 하 여 가용성 그룹 만들기  
 다음 PowerShell 예에서는 가용성 복제본 두 개와 가용성 데이터베이스 한 개가 포함된 `MyAG` 라는 단순한 가용성 그룹을 만들고 구성합니다. 예:  
  
1.  `MyDatabase` 와 해당 트랜잭션 로그를 백업합니다.  
  
2.  `-NoRecovery` 옵션을 사용하여 `MyDatabase` 및 해당 트랜잭션 로그를 복원합니다.  
  
3.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에 의해 호스트될 주 복제본의 메모리 내 표현을 만듭니다( `PrimaryComputer\Instance`).  
  
4.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 의해 호스트될 보조 복제본의 메모리 내 표현을 만듭니다( `SecondaryComputer\Instance`).  
  
5.  `MyAG`라는 가용성 그룹을 만듭니다.  
  
6.  보조 복제본을 가용성 그룹에 조인합니다.  
  
7.  보조 데이터베이스를 가용성 그룹에 조인합니다.  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 관련 작업  
 **AlwaysOn 가용성 그룹에 대한 서버 인스턴스를 구성하려면**  
  
-   [AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
 **가용성 그룹 및 복제본 속성을 구성하려면**  
  
-   [가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치의 상태 제어(AlwaysOn 가용성 그룹)](configure-flexible-automatic-failover-policy.md)  
  
-   [가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [가용성 복제본에 백업 구성&#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **가용성 그룹 구성을 완료하려면**  
  
-   [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **가용성 그룹을 만드는 다른 방법**  
  
-   [가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
 **AlwaysOn 가용성 그룹 구성 문제를 해결하려면**  
  
-   [삭제 된 SQL Server (AlwaysOn 가용성 그룹 구성) 문제 해결](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 관련 내용  
  
-   **블로그:**  
  
     [AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server PowerShell을 사용하여 AlwaysOn 구성](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server 엔지니어 블로그](https://blogs.msdn.com/b/psssql/)  
  
-   **비디오:**  
  
     [Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **백서:**  
  
     [고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012에 대한 Microsoft 백서](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 고객 자문 팀 백서](http://sqlcat.com/)  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
