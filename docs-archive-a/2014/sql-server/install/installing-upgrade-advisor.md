---
title: 업그레이드 관리자 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730047"
---
# <a name="installing-upgrade-advisor"></a>업그레이드 관리자 설치
  SQL Server 2014 업그레이드 관리자 설치 위치는 분석 대상에 따라 달라집니다. 업그레이드 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외하고 모든 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소의 원격 분석을 지원합니다. 인스턴스를 검색 하지 않는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 연결할 수 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있고 [업그레이드 관리자의 필수 구성 요소](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)를 충족 하는 모든 컴퓨터에 업그레이드 관리자를 설치할 수 있습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 인스턴스를 검색하는 경우에는 보고서 서버에 업그레이드 관리자를 설치해야 합니다.  
  
 **SQLUA.msi** 파일을 실행 하 여 업그레이드 관리자를 설치 합니다. 명령 프롬프트를 사용하여 무인 및 자동 설치를 수행할 수 있습니다. 구문 및 예제 [는 명령 프롬프트에서 업그레이드 관리자 설치를](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) 참조 하세요.  
  
 SQLUA.msi를  
  
-   제품 미디어의 **redist** 폴더에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.  
  
-   [SQL 2014 기능 팩 다운로드](https://www.microsoft.com/download/details.aspx?id=42295)의 일부로 다운로드 합니다.  
  
## <a name="uninstalling-upgrade-advisor"></a>업그레이드 관리자 제거  
 **프로그램 추가/제거**를 사용 하 여 업그레이드 관리자를 제거할 수 있습니다. 명령 프롬프트 구문도 제거/설치 제거를 지원합니다.  
  
  
