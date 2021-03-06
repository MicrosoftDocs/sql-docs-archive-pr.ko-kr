---
title: 고급 연결 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8dc844d1fdfb1e82f0ffa8de93a6a1060ef190cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652980"
---
# <a name="advanced-connection-properties"></a>고급 연결 속성
  **고급 연결 속성** 대화 상자를 사용하여 연결 문자열에 연결 매개 변수를 추가할 수 있습니다.  
  
 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 지원되는 모든 ODBC 연결 매개 변수를 추가할 수 있습니다.  
  
 **고급 연결 속성** 대화 상자를 사용하여 추가한 매개 변수는 **SQL Server에 연결** 대화 상자에서 선택한 매개 변수에 추가됩니다.  
  
 제공된 각 매개 변수의 마지막 인스턴스는 매개 변수의 이전 인스턴스보다 우선합니다. **고급 연결 매개 변수** 대화 상자를 사용하여 추가한 매개 변수가 그 다음이고 **SQL Server 연결** 대화 상자에서 제공한 매개 변수를 대체합니다. 예를 들어 **SQL Server 연결** 대화 상자에서 SERVER1을 서버 이름으로 지정하고 **추가 연결 매개 변수** 페이지에 ;SERVER=SERVER2가 있으면 SERVER2에 연결됩니다.  
  
 **고급 연결 속성** 대화 상자를 사용하여 추가한 매개 변수는 일반 텍스트로 전달됩니다.  
  
> [!IMPORTANT]  
>  **고급 연결 속성** 대화 상자에 로그인 자격 증명을 포함하지 마십시오. 이러한 정보는 네트워크로 전달될 때 암호화되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [CDC Designer 콘솔 액세스](access-the-cdc-designer-console.md)   
 [인스턴스를 만들기 위한 SQL Server 연결](sql-server-connection-for-instance-creation.md)  
  
  
