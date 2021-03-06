---
title: SQL Server 에이전트 속성(작업 시스템 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 743a8d558e97e9ad83cfc66e9ef1adf2e1bc0c2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659771"
---
# <a name="sql-server-agent-properties-job-system-page"></a>SQL Server 에이전트 속성(작업 시스템 페이지)
  이 페이지를 사용 하 여 에이전트 서비스에서 작업을 관리 하는 방법을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.  
  
## <a name="options"></a>옵션  
 **시스템 종료 제한 시간 간격(초)**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 종료 전 작업 완료 대기 시간(초)을 지정합니다. 지정한 간격을 초과하여 작업이 실행되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 강제로 작업을 중지합니다.  
  
 **비관리자 프록시 계정 사용**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 대한 비관리자 프록시 계정을 설정합니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]이상 버전에서는 여러 프록시를 지원 하므로이 옵션은 관리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하는 경우에만 적용 됩니다. 이전 버전의 에이전트 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **사용자 이름**  
 비관리자 프록시 계정에 대한 사용자의 이름을 입력합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.  
  
 **암호**  
 비관리자 프록시 계정에 대한 사용자의 암호를 입력합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.  
  
 **도메인**  
 비관리자 프록시 계정에 대한 사용자의 도메인을 입력합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [작업 구현](implement-jobs.md)  
  
  
