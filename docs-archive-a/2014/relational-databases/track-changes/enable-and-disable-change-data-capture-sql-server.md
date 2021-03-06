---
title: 변경 데이터 캡처 설정 및 해제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: df0a2fd4a2c6ffb2de58d6b52360d1730d0fa7df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650859"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a>변경 데이터 캡처 설정 및 해제(SQL Server)
  이 항목에서는 데이터베이스 및 테이블에서 변경 데이터 캡처를 사용하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.  
  
## <a name="enable-change-data-capture-for-a-database"></a>데이터베이스에 변경 데이터 캡처 설정  
 개별 테이블에서 캡처 인스턴스를 만들려면 먼저 `sysadmin` 고정 서버 역할의 멤버가 데이터베이스에 변경 데이터 캡처를 설정해야 합니다. 이 작업은 데이터베이스 컨텍스트에서 [sys.sp_cdc_enable_db&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) 저장 프로시저를 실행하여 수행됩니다. 데이터베이스에 이 기능이 이미 설정되었는지 확인하려면 `is_cdc_enabled` 카탈로그 뷰의 `sys.databases` 열을 쿼리합니다.  
  
 데이터베이스에 변경 데이터 캡처가 설정되면 데이터베이스에 `cdc` 스키마, `cdc` 사용자, 메타데이터 테이블 및 다른 시스템 개체가 생성됩니다. `cdc` 스키마에는 변경 데이터 캡처 메타데이터 테이블이 포함되며 원본 테이블에 변경 데이터 캡처가 설정된 후에는 변경 데이터에 대한 리포지토리 역할을 수행하는 개별 변경 테이블이 포함됩니다. 변경 데이터를 쿼리하는 데 사용되는 관련 시스템 함수도 `cdc` 스키마에 포함됩니다.  
  
 변경 데이터 캡처를 사용하려면 `cdc` 스키마와 `cdc` 사용자를 배타적으로 사용해야 합니다. *cdc* 라는 스키마 또는 데이터베이스 사용자가 데이터베이스에 현재 있는 경우 해당 스키마 및/또는 사용자가 삭제되거나 이름이 바뀔 때까지 데이터베이스에 변경 데이터 캡처를 설정할 수 없습니다.  
  
 데이터베이스에서 이 기능을 사용하도록 설정하는 예는 데이터베이스의 변경 데이터 캡처 설정 템플릿을 참조하십시오.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 템플릿을 찾으려면 **보기**로 이동하고 **템플릿 탐색기**를 클릭한 다음 **SQL Server 템플릿**을 선택합니다. **변경 데이터 캡처** 는 하위 폴더입니다. 이 폴더 아래에는 이 항목에서 참조하는 모든 템플릿이 있습니다. 또한 **도구 모음에 있는** 템플릿 탐색기 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 아이콘을 사용할 수도 있습니다.  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a>데이터베이스의 변경 데이터 캡처 해제  
 `sysadmin`고정 서버 역할의 멤버는 데이터베이스 컨텍스트에서 [transact-sql&#41;&#40;sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) 저장 프로시저를 실행 하 여 데이터베이스에 대 한 변경 데이터 캡처를 사용 하지 않도록 설정할 수 있습니다. 개별 테이블에서 먼저 이 기능을 해제한 후 데이터베이스에서 이 기능을 해제할 필요는 없습니다. 데이터베이스에서 이 기능을 해제하면 `cdc` 사용자 및 스키마와 변경 데이터 캡처 작업을 포함하는 모든 연결된 변경 데이터 캡처 메타데이터가 제거됩니다. 하지만 변경 데이터 캡처로 생성된 모든 제어 역할은 자동으로 제거되지 않으며 명시적으로 삭제해야 합니다. 데이터베이스에 이 기능이 설정되었는지 확인하려면 sys.databases 카탈로그 뷰의 `is_cdc_enabled` 열을 쿼리합니다.  
  
 변경 데이터 캡처가 설정된 데이터베이스를 삭제하면 변경 데이터 캡처 작업이 자동으로 제거됩니다.  
  
 데이터베이스에서 이 기능을 사용하지 않도록 설정하는 예는 데이터베이스의 변경 데이터 캡처 해제 템플릿을 참조하십시오.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 템플릿을 찾으려면 **보기**로 이동하고 **템플릿 탐색기**를 클릭한 다음 **SQL Server 템플릿**을 클릭합니다. **변경 데이터 캡처** 하위 폴더에는 이 항목에서 참조되는 모든 템플릿이 있습니다. 또한 **도구 모음에 있는** 템플릿 탐색기 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 아이콘을 사용할 수도 있습니다.  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a>테이블의 변경 데이터 캡처 설정  
 데이터베이스에 변경 데이터 캡처를 설정한 후에는 `db_owner` 고정 데이터베이스 역할의 멤버가 `sys.sp_cdc_enable_table` 저장 프로시저를 사용하여 개별 원본 테이블에 캡처 인스턴스를 만들 수 있습니다. 원본 테이블에 변경 데이터 캡처가 이미 설정되었는지 확인하려면 `sys.tables` 카탈로그 뷰의 is_tracked_by_cdc 열을 살펴봅니다.  
  
 캡처 인스턴스를 만들 때에는 다음과 같은 옵션을 지정할 수 있습니다.  
  
 `Columns in the source table to be captured`.  
  
 기본적으로 원본 테이블의 모든 열은 캡처된 열로 식별됩니다. 개인 정보 보호 또는 성능상의 이유로 열의 하위 집합만 추적 해야 하는 경우 매개 변수를 사용 하 여 *@captured_column_list* 열의 하위 집합을 지정 합니다.  
  
 `A filegroup to contain the change table.`  
  
 기본적으로 변경 테이블은 데이터베이스의 기본 파일 그룹에 있습니다. 개별 변경 테이블의 배치를 제어 하려는 데이터베이스 소유자는 매개 변수를 사용 *@filegroup_name* 하 여 캡처 인스턴스와 연결 된 변경 테이블에 대해 특정 파일 그룹을 지정할 수 있습니다. 명명된 파일 그룹은 이미 존재해야 합니다. 일반적으로 변경 테이블은 원본 테이블과 별도의 파일 그룹에 배치하는 것이 좋습니다. `Enable a Table Specifying Filegroup Option`매개 변수를 사용 하는 방법을 보여 주는 예제는 템플릿을 참조 하십시오 *@filegroup_name* .  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 명명된 역할의 목적은 변경 데이터에 대한 액세스를 제어하는 것입니다. 지정된 역할은 기존의 고정 서버 역할 또는 데이터베이스 역할일 수 있습니다. 지정된 역할이 아직 없는 경우 해당 이름의 데이터베이스 역할이 자동으로 생성됩니다. `sysadmin` 또는 `db_owner` 역할의 멤버는 변경 테이블의 데이터에 대한 모든 액세스 권한을 가집니다. 다른 모든 사용자에게는 원본 테이블의 모든 캡처된 열에 대한 SELECT 권한이 있어야 합니다. 또한 역할이 지정되면 `sysadmin` 또는 `db_owner` 역할의 멤버가 아닌 사용자도 지정한 역할의 멤버여야 합니다.  
  
 제어 역할을 사용 하지 않으려면 매개 변수를 명시적으로 *@role_name* NULL로 설정 합니다. 제어 역할이 없는 테이블을 설정하는 예는 `Enable a Table Without Using a Gating Role` 템플릿을 참조하십시오.  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 캡처 인스턴스에는 항상 정의된 간격 내에서 발생한 모든 변경 테이블 항목을 반환하는 데 사용되는 테이블 반환 함수가 포함됩니다. 이 함수 이름은 "cdc.fn_cdc_get_all_changes_"에 캡처 인스턴스 이름을 추가하여 지정합니다. 자세한 내용은 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)를 참조하세요.  
  
 매개 변수가 *@supports_net_changes* 1로 설정 된 경우 캡처 인스턴스에 대 한 순 변경 함수도 생성 됩니다. 이 함수는 호출에 지정된 간격 내에 변경된 각 개별 행에 대해 하나의 변경만 반환합니다. 자세한 내용은 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)를 참조하세요.  
  
 순 변경 쿼리를 지원하기 위해 원본 테이블에는 행을 고유하게 식별하는 기본 키 또는 고유 인덱스가 있어야 합니다. 고유 인덱스를 사용 하는 경우 매개 변수를 사용 하 여 인덱스 이름을 지정 해야 합니다 *@index_name* . 기본 키 또는 고유 인덱스에 정의된 열은 캡처할 원본 열 목록에 포함되어야 합니다.  
  
 두 쿼리 함수로 캡처 인스턴스를 생성하는 방법을 보여 주는 예는 `Enable a Table for All and Net Changes Queries` 템플릿을 참조하십시오.  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  기존 기본 키가 있는 테이블에 변경 데이터 캡처가 설정 되어 있고 *@index_name* 매개 변수를 사용 하 여 대체 고유 인덱스를 식별 하지 않는 경우 변경 데이터 캡처 기능에서 기본 키를 사용 합니다. 기본 키에 대한 후속 변경 내용을 허용하려면 먼저 테이블의 변경 데이터 캡처를 해제해야 합니다. 이는 변경 데이터 캡처를 구성할 때 순 변경 쿼리에 대한 지원을 요청했는지 여부와 관계없이 적용됩니다. 테이블에 변경 데이터 캡처를 설정할 당시 기본 키가 없는 경우에는 기본 키에 대한 후속 추가 사항이 변경 데이터 캡처에 의해 무시됩니다. 변경 데이터 캡처는 테이블에 이 기능이 설정된 이후에 생성되는 기본 키를 사용하지 않으므로 키와 키 열을 제한 없이 제거할 수 있습니다.  
  
## <a name="disable-change-data-capture-for-a-table"></a>테이블의 변경 데이터 캡처 해제  
 `db_owner` 고정 데이터베이스 역할의 멤버는 `sys.sp_cdc_disable_table` 저장 프로시저를 사용하여 개별 원본 테이블의 캡처 인스턴스를 제거할 수 있습니다. 원본 테이블에 현재 변경 데이터 캡처가 설정되었는지 확인하려면 `is_tracked_by_cdc` 카탈로그 뷰의 `sys.tables` 열을 살펴봅니다. 해제를 수행한 후 데이터베이스에 변경 데이터 캡처 기능이 설정된 테이블이 없으면 변경 데이터 캡처 작업도 제거됩니다.  
  
 변경 데이터 캡처가 설정된 테이블을 삭제하면 이 테이블과 연결된 변경 데이터 캡처 메타데이터도 자동으로 제거됩니다.  
  
 테이블에서 이 기능을 사용하지 않도록 설정하는 예는 테이블의 캡처 인스턴스 해제 템플릿을 참조하십시오.  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터 변경 내용 추적&#40;SQL Server&#41;](track-data-changes-sql-server.md)   
 [변경 데이터 캡처 정보&#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md)   
 [변경 데이터 작업&#40;SQL Server&#41;](work-with-change-data-sql-server.md)   
 [변경 데이터 캡처 관리 및 모니터링&#40;SQL Server&#41;](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
