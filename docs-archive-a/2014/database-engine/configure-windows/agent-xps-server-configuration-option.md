---
title: Agent XPs 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652345"
---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs 서버 구성 옵션
  **Agent XPs** 옵션을 사용하여 이 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 설정할 수 있습니다. 이 옵션을 해제하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 탐색기에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에이전트 노드를 사용할 수 없습니다.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 시작하면 이러한 확장 저장 프로시저가 자동으로 설정됩니다. 자세한 내용은 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)을 참조하세요.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 상태에 관계없이 이러한 확장 저장 프로시저가 활성화되어 있지 않으면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드의 콘텐츠를 표시하지 않습니다.  
  
 사용 가능한 값은  
  
-   **0**은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 사용할 수 없음을 나타냅니다(기본값).  
  
-   **1**은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 사용할 수 있음을 나타냅니다.  
  
 이 설정은 서버를 중지했다가 다시 시작하지 않아도 즉시 적용됩니다.  
  
## <a name="examples"></a>예제  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 설정합니다.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [관리 태스크 자동화&#40;SQL Server 에이전트&#41;](../../ssms/agent/sql-server-agent.md)   
 [SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
