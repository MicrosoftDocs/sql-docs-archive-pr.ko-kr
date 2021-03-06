---
title: '예제: 읽기 전용 파일 온라인 복원(전체 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f493c88d64e6ed22e44f33f1442ae581daa8ed4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742327"
---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a>예제: 읽기 전용 파일의 온라인 복원(전체 복구 모델)
  이 항목에서는 여러 개의 파일 또는 파일 그룹이 있는 전체 복구 모델에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.  
  
 이 예에서는 전체 복구 모델을 사용하는 `adb`라는 데이터베이스에 3개의 파일 그룹이 포함되어 있습니다. 파일 그룹 `A` 는 읽기/쓰기가 가능하고 파일 그룹 `B` 와 파일 그룹 `C` 는 읽기 전용입니다. 처음에는 모든 파일 그룹이 온라인입니다.  
  
 `b1`데이터베이스의 파일 그룹 `B` 에 있는 읽기 전용 파일 `adb` 을 복원해야 합니다. 파일이 읽기 전용 상태가 된 이후 백업이 수행되었으므로 로그 백업은 필요하지 않습니다. 파일 그룹 `B` 는 복원 기간 중 오프라인 상태가 되지만 나머지 데이터베이스는 온라인 상태가 유지됩니다.  
  
## <a name="restore-sequence"></a>복원 시퀀스  
  
> [!NOTE]  
>  온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.  
  
 데이터베이스 관리자는 다음 복원 시퀀스에 따라 파일을 복원할 수 있습니다.  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 이제 파일 그룹 B가 온라인입니다.  
  
## <a name="additional-examples"></a>추가 예  
  
-   [예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a>참고 항목  
 [온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md)   
 [복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md)   
 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
