---
title: Blob (binary large object)를 읽고 쓰는 UPDATETEXT 문을 수정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650467"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>BLOB(Binary Large Object) 읽기/쓰기를 수행하는 UPDATETEXT 문을 수정합니다.
  업그레이드 관리자가 동일한 텍스트 포인터를 사용하여 동일한 BLOB(Binary Large Object) 읽기/쓰기를 수행하는 UPDATETEXT 문을 검색했습니다. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 이러한 방식으로 텍스트 포인터를 사용하는 것을 지원하지 않습니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>수정 동작  
 BLOB을 임시 테이블 또는 테이블 변수로 복사한 다음 이 값을 다시 원래 열에 할당합니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
