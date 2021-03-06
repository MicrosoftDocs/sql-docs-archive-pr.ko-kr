---
title: SQL Server Native Client의 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652075"
---
# <a name="components-of-sql-server-native-client"></a>SQL Server Native Client의 구성 요소
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에는 다음 구성 요소가 포함되어 있습니다.  
  
|구성 요소|Description|  
|---------------|-----------------|  
|sqlncli11.dll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 기능이 모두 포함된 DLL(동적 연결 라이브러리) 파일입니다. 여기에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버가 포함됩니다.|  
|sqlnclir11.rll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 라이브러리에 대한 리소스 파일입니다.|  
|s10ch_sqlncli.chm|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 원본을 만드는 방법을 문서화하는 데이터 원본 마법사 도움말 파일입니다.|  
|sqlncli.h|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 사용하는 데 필요한 모든 새 정의가 포함된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 헤더 파일입니다. 이 헤더 파일은 odbcss.h 및 sqloledb.h 헤더 파일을 모두 대체합니다. **참고:**  동일한 프로그램에서 sqlncli 및 odbcss.h를 참조할 수 없지만, 먼저 sqloledb가 정의 되어 있는 한 동일한 프로그램에서 sqlncli 및 sqloledb를 참조할 수 있습니다.|  
|sqlncli11.lib|Native Client ODBC 드라이버의 일부인 **bcp** 유틸리티 함수를 직접 호출 하는 데 필요한 라이브러리 파일 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 입니다. **참고:**  프로그래밍 코드의 sqlncli11 파일을 참조 하는 경우에는 sqlncli11.dll 파일이 시스템 경로 및 응용 프로그램을 사용 하는 사용자의 시스템 경로에 있는지 확인 해야 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Native Client를 사용하여 애플리케이션 빌드](building-applications-with-sql-server-native-client.md)  
  
  
