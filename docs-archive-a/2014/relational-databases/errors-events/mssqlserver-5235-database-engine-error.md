---
title: MSSQLSERVER_5235 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740024"
---
# <a name="mssqlserver_5235"></a>MSSQLSERVER_5235
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|5235|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|메시지 텍스트|[응급] USER_NAME이(가) 실행한 DBCC DBCC_COMMAND_DETAILS이(가) 오류 상태 ERROR_STATE(으)로 인해 비정상적으로 종료되었습니다. 경과된 시간: HOURS 시간 MINUTES 분 SECONDS 초|  
  
## <a name="explanation"></a>설명  
 이는 명령이 실행되는 동안 예기치 않게 종료되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 인쇄되는 DBCC 요약 메시지입니다. 메시지에 보고되는 오류 상태는 예기치 않은 종료 유형을 정의합니다.  
  
 다음 표에서는 오류 상태를 나열 및 정의합니다.  
  
|오류 상태|정의|  
|-----------------|----------------|  
|상태 0|메타데이터가 손상되어 문이 종료되었습니다. 이 메시지는 하나 이상의 오류 8930과 함께 표시됩니다.|  
|상태 1|내부 검사에 실패하여 문이 종료되었습니다. 이 메시지는 하나 이상의 오류 8967과 함께 표시됩니다.|  
|상태 2|핵심 스토리지 엔진 시스템 테이블에 대한 기본 시스템 테이블 검사가 실패했습니다. 이 메시지는 하나 이상의 오류 [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md) 또는 [7988](mssqlserver-7988-database-engine-error.md)과 함께 표시됩니다.|  
|상태 3|트랜잭션 로그를 다시 작성한 후 데이터베이스를 시작할 수 없어 DBCC 응급 모드 복구가 실패했습니다. 이 메시지는 오류 7909와 함께 표시됩니다.|  
|상태 4|명령을 실행하는 동안 어설션 오류나 액세스 위반이 발생했습니다.|  
|상태 5|알 수 없는 오류가 발생하여 DBCC 명령이 예기치 않게 종료되었습니다.|  
  
## <a name="user-action"></a>사용자 동작  
 다음 표에서는 특정 오류 상태에 적합한 사용자 동작을 설명합니다.  
  
|오류 상태|사용자 조치|  
|-----------------|-----------------|  
|상태 0|백업에서 복원합니다.|  
|상태 1|[!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS(고객 서비스 지원 센터)에 문의합니다.|  
|상태 2|백업에서 복원합니다.|  
|상태 3|백업에서 복원합니다.|  
|상태 4|CSS에 문의합니다.|  
|상태 5|명령을 다시 실행합니다. 문제가 지속되면 CSS에 문의합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [DBCC&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
