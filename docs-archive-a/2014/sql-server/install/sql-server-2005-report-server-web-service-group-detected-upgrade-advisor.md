---
title: SQL Server 2005 보고서 서버 웹 서비스 그룹이 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742795"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>SQL Server 2005 보고서 서버 웹 서비스 그룹이 검색됨(업그레이드 관리자)
  업그레이드 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹과 연결 되어 있음을 발견 했습니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.|  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>설명  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]을 사용 하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹입니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 때 이러한 서비스 그룹은 삭제되며 이 그룹 또는 그룹에 속하는 사용자에 대한 사용자 지정 ACL(Access Control 목록)은 업그레이드 중에 보존되지 않습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 업그레이드를 시작하기 전에 사용자 지정 ACL이나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버 웹 서비스 그룹에 속한 사용자를 백업합니다. 이렇게 하려면 sp2 이상에서 **Icacls.exe** 명령줄 도구를 사용 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 하거나 sp2 이전 버전의 Windows 운영 체제에서 Cacls.exe 명령줄 도구를 사용할 수 있습니다 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] . 이들 도구를 사용하기 위한 구문에 대한 자세한 내용은 Windows 제품 설명서를 참조하십시오. 설치가 성공적으로 완료되면 사용자 지정 ACL이나 사용자를 보고서 서버 인스턴스에 대한 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버 Windows 그룹에 적용합니다. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]보고서 서버 Windows 그룹은 SQLServerReportServerUser $ 형식으로 사용 \<*computer_name*> $ \<*instance_name*> 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
