---
title: MSSQLSERVER_21889 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734096"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21889|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21889|  
|메시지 텍스트|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 '%s'이(가) 복제 게시자가 아닙니다. 이 인스턴스에서 게시 데이터베이스 '%s'을(를) 호스팅하도록 설정하려면 배포자가 '%s'인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 '%s'에서 `sp_adddistributor`를 실행하십시오. 이때 원래 게시자에 사용된 것과 동일한 로그인 및 암호를 지정해야 합니다.|  
  
## <a name="explanation"></a>설명  
 게시자 데이터베이스를 호스팅하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 게시자여야 합니다. `sp_validate_redirected_publisher`는 원격 서버에서 `sp_helpdistributor`를 호출하여 서버가 복제 게시자인지 여부를 확인합니다. 이 오류는 `sp_helpdistributor` 저장 프로시저를 실행할 때 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 게시자가 아닌 것으로 나타난 경우에 반환됩니다.  
  
## <a name="user-action"></a>사용자 동작  
 게시자 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 `sp_adddistributor`를 실행하십시오. 올바른 배포자를 지정하여 `sp_adddistributor`를 실행하십시오. *@password* `sp_adddistributor` 처음에 배포자에서를 실행할 때 사용 된 매개 변수와 동일한 값을 사용 합니다.  
  
  
