---
title: Syslockinfo 및 sp_lock의 동작에 대 한 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650517"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a>syslockinfo 및 sp_lock의 동작에 대한 변경입니다.
  **syslockinfo** 및 **sp_lock** 이 예기치 않은 값을 반환할 수 있으며 추가 행을 반환할 수도 있습니다. 반면에 이전 버전에서는 **syslockinfo** 및 **sp_lock** 이 잠금 리소스당 최대 두 개의 행을 반환했습니다.  
  
 **syslockinfo** 의 정보에 액세스하거나 **sp_lock** 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 **syslockinfo** 의 **rsc_objid** 및 **rsc_indid** 열과 **sp_lock** 의 **objid** 및 **indid** 열은 항상 개체 ID와 인덱스 ID를 반환합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 값 0이 반환될 수 있습니다.  
  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 **syslockinfo** 및 **sp_lock** 은 단일 트랜잭션에서 지정한 잠금 리소스에 대해 최대 두 개의 행을 반환합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 잠금 분할을 사용할 경우 한 트랜잭션에서 실행 중인 동일한 리소스에 대해 여러 개의 행이 반환될 수 있습니다. 최대 N + 1 개의 행이 반환 될 수 있습니다. 여기서 N은 Cpu의 수입니다. 또한 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 가능하지 않았지만 이제는 동일한 리소스에 대해 GRANTED 및 WAITING 요청을 표시할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
