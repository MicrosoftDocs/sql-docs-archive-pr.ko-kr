---
title: 다중 스레드 응용 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653298"
---
# <a name="multithreaded-applications"></a>다중 스레드 애플리케이션
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다중 스레드 드라이버입니다. 다중 스레드 애플리케이션을 작성하면 여러 ODBC 호출을 처리하기 위해 비동기 호출을 사용하는 방법을 대신할 수 있습니다. 스레드는 동기 ODBC 호출을 실행할 수 있으며 다른 스레드는 첫 번째 스레드가 호출에 대한 응답을 대기하면서 차단되는 동안 처리될 수 있습니다. 이 모델을 사용하면 네트워크 트래픽 및 SQL_STILL_EXECUTING을 테스트하기 위한 ODBC 함수의 반복적인 호출로 인해 발생하는 오버헤드 문제를 해결할 수 있기 때문에 비동기 호출을 실행하는 것보다 효율적입니다.  
  
 그러나 비동기 모드는 여전히 효과적인 처리 방법입니다. 다중 스레드 모델의 성능이 크게 향상되기는 했지만 비동기 애플리케이션을 다시 작성해야 할 정도는 아닙니다. DB-Library 비동기 모델을 사용하는 DB-Library 애플리케이션을 변환하는 경우에는 애플리케이션을 ODBC 비동기 모델로 변환하는 것이 쉽습니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Native Client ODBC 드라이버 애플리케이션 만들기](creating-a-driver-application.md)  
  
  
