---
title: MSSQLSERVER_2 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653923"
---
# <a name="mssqlserver_2"></a>MSSQLSERVER_2
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름||  
|메시지 텍스트|서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.  SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다. (공급자: 명명된 파이프 공급자, 오류: 40 - SQL Server에 대한 연결을 열 수 없습니다.)(.Net SqlClient 데이터 공급자)|  
  
## <a name="explanation"></a>설명  
 아마도 서버가 시작되지 않았기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 클라이언트 요청에 응답하지 않았습니다.  
  
## <a name="user-action"></a>사용자 동작  
 서버가 시작되었는지 확인합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 엔진 서비스 관리](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)   
 [네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md)   
 [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)   
 [서버 네트워크 프로토콜 설정 또는 해제](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
