---
title: Windows 애플리케이션 로그 보기(Windows) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731548"
---
# <a name="view-the-windows-application-log-windows"></a>Windows 애플리케이션 로그 보기(Windows)
  Windows 애플리케이션 로그를 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 구성한 경우 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 세션에서는 해당 로그에 새 이벤트를 씁니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와는 달리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 시작할 때마다 새 애플리케이션 로그가 생성되지는 않습니다.  
  
### <a name="to-view-the-windows-application-log"></a>Windows 애플리케이션 로그를 보려면  
  
1.  **시작** 메뉴에서 **모든 프로그램**, **관리 도구**를 차례로 가리킨 다음 **이벤트 뷰어**를 클릭합니다.  
  
2.  이벤트 뷰어에서 **애플리케이션**을 클릭합니다.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트는 **원본** 열에서 **MSSQLSERVER** 항목으로 식별됩니다(명명된 인스턴스는 **MSSQL$** _<instance_name>_ 으로 식별됨). SQL Server 에이전트 이벤트는 SQLSERVERAGENT 항목으로 식별됩니다. 명명된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트는 **SQLAgent$** \<*instance_name*>으로 식별됩니다. Microsoft Search 서비스 이벤트는 **Microsoft Search**항목으로 식별됩니다.  
  
4.  다른 컴퓨터의 로그를 보려면 **이벤트 뷰어**를 마우스 오른쪽 단추로 클릭 하 고 **다른 컴퓨터에 연결을** 클릭 한 다음 **컴퓨터 선택**대화 상자를 완료 합니다.  
  
5.  선택적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트만 표시하려면 **보기** 메뉴에서 **필터**를 클릭한 후 **이벤트 원본** 목록에서 **MSSQLSERVER**를 선택합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트만 표시하려면 **이벤트 원본** 목록에서 **SQLSERVERAGENT** 를 선택합니다.  
  
6.  이벤트에 대한 자세한 내용을 보려면 해당 이벤트를 두 번 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 오류 로그 보기&#40;SQL Server Management Studio&#41;](../../ssms/sql-server-management-studio-ssms.md)  
  
  
