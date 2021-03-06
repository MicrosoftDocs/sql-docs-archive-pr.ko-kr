---
title: 데이터베이스 복원(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.general.f1
ms.assetid: 160cf58c-b06a-475f-9a69-2b051e5767ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a497e6a6e4584aa064783eba2076b7e50b36e8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653455"
---
# <a name="restore-database-general-page"></a>데이터베이스 복원(일반 페이지)
  **일반** 페이지를 사용하여 데이터베이스 복원 작업의 대상 및 원본 데이터베이스를 지정할 수 있습니다.  
  
 **SQL Server Management Studio를 사용하여 데이터베이스 백업을 복원하려면**  
  
-   [데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  를 사용 하 여 복원 태스크를 지정할 때는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] **스크립트** 를 클릭 한 다음 스크립트의 대상을 선택 하 여 해당 하는 [restore](/sql/t-sql/statements/restore-statements-transact-sql) 스크립트를 생성할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다. 데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다.  
  
 멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다. 고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.  
  
 암호화된 백업에서 복원하려면 백업 중에 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 `VIEW DEFINITION` 권한이 필요합니다.  
  
## <a name="options"></a>옵션  
  
### <a name="source"></a>원본  
 **복원할 원본 위치**패널의 옵션은 데이터베이스의 백업 세트 위치 및 복원하려는 백업 세트를 식별합니다.  
  
|용어|정의|  
|----------|----------------|  
|**Database**|복원할 데이터베이스를 드롭다운 목록에서 선택합니다. 목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.|  
|**디바이스**|복원할 백업을 포함하는 논리적 또는 물리적 백업 디바이스(테이프, URL 또는 파일)를 선택합니다. 데이터베이스 백업을 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 가져온 경우에 필요합니다.<br /><br /> 하나 이상의 논리적 또는 물리적 백업 디바이스를 선택하려면 **백업 디바이스 선택** 대화 상자를 여는 찾아보기 단추를 클릭합니다. 이 대화 상자에서 단일 미디어 세트에 속하는 최대 64개의 디바이스를 선택할 수 있습니다. 테이프 디바이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 실행하는 컴퓨터에 물리적으로 연결되어야 합니다. 백업 파일은 로컬 또는 이동식 디스크 디바이스에 존재할 수 있습니다. 자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요. 또한 **URL**을 Azure Storage에 저장된 백업 파일에 대한 디바이스 유형으로 선택할 수 있습니다.<br /><br /> **백업 디바이스 선택** 대화 상자를 종료하면 선택한 디바이스가 **디바이스** 목록에서 읽기 전용 값으로 표시됩니다.|  
|**Database**|드롭다운 목록에서 백업을 복원하는 데 사용할 데이터베이스 이름을 선택합니다.<br /><br /> 참고: 이 목록은 **디바이스** 를 선택한 경우에만 사용할 수 있습니다. 선택한 디바이스에 백업이 있는 데이터베이스만 사용할 수 있습니다.|  
  
### <a name="destination"></a>대상  
 **복원 위치** 패널의 옵션은 데이터베이스 및 복원 지점을 식별합니다.  
  
|용어|정의|  
|----------|----------------|  
|**Database**|목록에서 복원할 데이터베이스를 입력합니다. 새 데이터베이스를 입력하거나 드롭다운 목록에서 기존 데이터베이스를 선택할 수 있습니다. 이 목록에는 시스템 데이터베이스인 **master** 및 **tempdb**를 제외한 서버의 모든 데이터베이스가 포함되어 있습니다.<br /><br /> 참고: 암호로 보호된 백업을 복원하려면 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용해야 합니다.|  
|**복원 위치**|**복원 위치** 상자는 기본적으로 "마지막으로 수행된 백업으로"로 설정됩니다. **시간대** 를 클릭하여 **백업 시간대** 대화 상자를 표시할 수도 있습니다. 이 대화 상자에는 데이터베이스 백업 기록이 시간대 형식으로 표시됩니다. **시간대** 를 클릭 하 여 데이터베이스를 복원 하려는 특정을 지정 합니다 `datetime` . 그러면 데이터베이스가 여기서 지정한 시점의 상태로 복원됩니다. [Backup Timeline](backup-timeline.md)을 참조하세요.|  
  
### <a name="restore-plan"></a>복원 계획  
  
|용어|정의|  
|----------|----------------|  
|**복원에 사용할 백업 세트**|지정한 위치에서 사용 가능한 백업 세트가 표시됩니다. 단일 백업 작업의 결과인 각 백업 세트가 미디어 세트의 모든 디바이스에서 배포됩니다. 기본적으로 필요한 백업 세트 선택을 기반으로 하는 복원 작업 목표를 달성하도록 복구 계획이 제안됩니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 는 **msdb** 의 백업 기록을 사용하여 데이터베이스를 복원하는 데 필요한 백업을 식별하고 복원 계획을 만듭니다. 예를 들어 데이터베이스 복원의 경우 복원 계획은 가장 최근의 후속 차등 데이터베이스 백업이 계속 수행되는 가장 최근의 전체 데이터베이스 백업을 선택합니다(있는 경우). 전체 복구 모델에서 복원 계획은 모든 후속 로그 백업을 선택합니다.<br /><br /> 제안 된 복구 계획을 재정의 하려면 표에서 다음 선택 항목을 변경할 수 있습니다. 선택 취소된 백업에 의존하는 모든 백업은 자동으로 선택 취소됩니다.<br /><br /> **복원**:<br />                          확인란이 선택되어 있으면 백업 세트가 복원됩니다.<br />**이름**: 백업 세트의 이름입니다.<br />**구성 요소**: 백업 된 구성 요소입니다. **데이터베이스**, **파일**또는 **\<blank>** (트랜잭션 로그의 경우)입니다.<br />**형식**: 수행된 백업 유형: **전체**, **차등** 또는 **트랜잭션 로그**가 될 수 있습니다.<br />**서버**: 백업 작업을 수행한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.<br />**데이터베이스**: 백업 작업과 관련 된 데이터베이스의 이름입니다.<br />**위치**: 볼륨에 있는 백업 세트의 위치입니다.<br />**첫 번째 LSN**: 백업 세트에 있는 첫 번째 트랜잭션의 로그 시퀀스 번호입니다. 파일 백업의 경우 비워 둡니다.<br />**마지막 LSN**: 백업 세트에 있는 마지막 트랜잭션의 로그 시퀀스 번호입니다. 파일 백업의 경우 비워 둡니다.<br />**검사점 LSN**: 백업을 만들 때 가장 최근 검사점의 lsn (로그 시퀀스 번호)입니다.<br />**FULL LSN**: 가장 최근의 전체 데이터베이스 백업의 로그 시퀀스 번호입니다.<br />**시작 날짜**: 클라이언트의 국가별 설정으로 표시 되는 백업 작업이 시작 된 날짜 및 시간입니다.<br />**완료 날짜**: 클라이언트의 국가별 설정으로 표시 되는 백업 작업 완료 날짜 및 시간입니다.<br />**크기**: 백업 세트의 크기 (바이트)입니다.<br />**사용자 이름**: 백업 작업을 수행한 사용자의 이름입니다.<br /><br /> **만료**: 백업 세트가 만료 되는 날짜와 시간입니다.<br /><br /> 이 확인란은 **수동 선택** 확인란을 선택하는 경우에만 사용할 수 있습니다. 이 확인란을 선택하면 복원할 백업 세트를 선택할 수 있습니다.<br /><br /> **수동 선택** 확인란을 선택하면 복원 계획을 수정할 때마다 계획의 정확도를 확인합니다. 백업 순서가 잘못된 경우에는 오류 메시지가 나타납니다.|  
|**백업 미디어 확인**|선택한 백업 세트에 대해 RESTORE VERIFY_ONLY 문을 호출합니다.<br /><br /> 참고: 이 작업은 장기 실행 작업입니다. 대화 상자 프레임워크의 진행률 모니터를 사용하여 해당 진행률을 추적하고 작업을 취소할 수 있습니다.<br /><br /> 이 단추를 사용하면 선택한 백업 파일을 복원하기 전에 파일의 무결성을 검사할 수 있습니다.<br /><br /> 백업 세트의 무결성을 검사할 때는 대화 상자 왼쪽 아래의 진행률 상태가 "실행 중"이 아닌 "확인 중"으로 표시됩니다.|  
  
## <a name="compatibility-support"></a>호환성 지원  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 사용하여 만든 데이터베이스 백업에서 사용자 데이터베이스를 복원할 수 있습니다. 그러나 **에서**까지를 사용하여 만든 **master** , **model** 및 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] msdb [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 의 백업은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 복원할 수 없습니다. 또한 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 만든 백업은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복원할 수 없습니다.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 이전 버전과는 다른 기본 경로를 사용합니다. 따라서 이전 버전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 위치에 만든 데이터베이스를 복원하려면 MOVE 옵션을 사용해야 합니다.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 이전 버전 데이터베이스를 복원하면 데이터베이스가 자동으로 업그레이드됩니다. 일반적으로 데이터베이스는 즉시 사용할 수 있습니다. 그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는 **전체 텍스트 업그레이드 옵션** 서버 속성의 설정에 따라 인덱스를 가져오거나, 다시 설정하거나, 다시 작성합니다. 업그레이드 옵션이 **가져오기** 또는 **다시 작성**으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다. 인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다. 업그레이드 옵션이 **가져오기**로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.  
  
## <a name="restoring-from-an-encrypted-backup"></a>암호화된 백업에서 복원  
 복원하려면 원래 백업을 만드는 데 사용된 인증서 또는 비대칭 키가 사용자가 복원 중인 인스턴스에서 사용 가능해야 합니다. 복원을 수행하는 계정에는 인증서나 비대칭 키에 대한 `VIEW DEFINITIONS` 권한이 있어야 합니다. 백업을 암호화하는 데 사용된 인증서는 갱신되거나 업데이트되지 않아야 합니다.  
  
## <a name="restoring-from-azure-storage"></a>Azure Storage에서 복원  
 Azure 저장소에 저장 된 백업을 복원 하는 경우 복원 UI에는 새로운 백업 장치 옵션이 있습니다. **백업 디바이스 선택** 대화 상자의 **URL** . **추가**를 클릭 하면 저장소 계정에 인증 하기 위한 SQL 자격 증명 정보를 지정할 수 있는 **Azure에 연결** 대화 상자가 표시 됩니다.  저장소 계정에 연결 되 면 백업 파일이 복원에 사용할 파일을 선택할 수 있는 **Azure에서 백업 파일 찾기** 대화 상자에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [디바이스에서 백업 복원&#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)   
 [데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)   
 [논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  
