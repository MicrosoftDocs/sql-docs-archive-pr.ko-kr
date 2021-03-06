---
title: 예약 키워드 다음에 콜론 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742812"
---
# <a name="remove-colon-following-reserved-keyword"></a>예약 키워드 다음에 나오는 콜론을 제거합니다.
  업그레이드 관리자가 예약 키워드 뒤에서 콜론(:)이 포함된 스크립트를 감지했습니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 구문이 무시되고 문이 성공적으로 실행되지만 이제는 데이터베이스 호환성 모드가 100 이상으로 설정된 경우 이 구문 때문에 문이 실패합니다.  
  
 사용자 데이터베이스는 호환성 모드를 유지합니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>수정 동작  
 데이터베이스 호환성 모드를 100 이상으로 설정하기 전에 예약 키워드 뒤에 있는 콜론을 제거하여 스크립트를 수정합니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "sp_dbcmptlevel"을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
