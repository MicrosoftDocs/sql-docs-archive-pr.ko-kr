---
title: SQL Server 에이전트 속성(기록 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d67ff3da97e11292abcac03958fe1e423b35d7d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659773"
---
# <a name="sql-server-agent-properties-history-page"></a>SQL Server 에이전트 속성(기록 페이지)
  이 페이지를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에이전트 서비스 기록 로그 관리에 대 한 설정을 확인 하 고 수정할 수 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.  
  
## <a name="options"></a>옵션  
 **작업 기록 로그 크기 제한**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 로그에 보존할 작업 기록 정보의 크기 제한을 설정합니다.  
  
 **작업 기록 로그의 최대 크기(행 수)**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 보존할 최대 행 수를 설정합니다. 로그의 행 수가 이 수에 도달한 경우 새 행을 입력하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 가장 오래된 행을 제거합니다.  
  
 **작업당 작업 기록의 최대 행 수**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업당 보존할 최대 행 수를 설정합니다. 특정 작업 기록의 행 수가 이 수에 도달한 경우 새 행을 입력하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 로그에서 가장 오래된 행을 제거합니다.  
  
 **에이전트 기록 제거**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 지정된 기간보다 오래된 항목을 로그에서 제거하도록 지정합니다. 이 작업은 기록을 제거하는 일회 실행 작업입니다. 작업을 되풀이해야 하는 경우에는 정리 작업을 사용하여 유지 관리 계획을 만들고 예약하십시오.  
  
 **다음보다 오래된 항목**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 항목을 보존하는 기간을 설정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 에이전트 오류 로그](sql-server-agent-error-log.md)  
  
  
