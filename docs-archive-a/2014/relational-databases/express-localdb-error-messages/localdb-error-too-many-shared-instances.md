---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646471"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|287|  
|이벤트 원본|SQL Server 로컬 데이터베이스 런타임 12.0|  
|구성 요소|로컬 데이터베이스 런타임 API|  
|메시지 텍스트|공유 인스턴스가 너무 많아 고유한 사용자 인스턴스 이름을 생성할 수 없습니다. 기존 공유 인스턴스 중 일부의 공유를 해제하십시오.|  
  
## <a name="explanation"></a>설명  
 공유 인스턴스가 너무 많아 고유한 사용자 인스턴스 이름을 생성할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 하나 이상의 공유 로컬 데이터베이스 런타임 인스턴스의 공유를 해제하고 다시 시도하십시오.  
  
  
