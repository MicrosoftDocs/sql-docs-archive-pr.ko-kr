---
title: MSSQLSERVER_5554 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5095a50f257abafb6ebde97bb32c57bc71fc4e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651716"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|MSSQLSERVER|  
|이벤트 ID|5554|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|FS_MINIVER_OVERFLOW|  
|메시지 텍스트|단일 파일에 대한 총 버전 수가 파일 시스템에 설정된 최대치에 도달했습니다.|  
  
## <a name="explanation"></a>설명  
 MARS(Multiple Active Result Set) 또는 트리거 시나리오에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 운영 체제에서 지정하는 미니 버전을 사용합니다.  
  
## <a name="user-action"></a>사용자 동작  
 동일 트랜잭션의 데이터를 반복해서 업데이트하려 하지 마십시오.  
  
  
