---
title: 0xFFFF 문자는 개체 식별자로 사용할 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650546"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF 문자는 개체 식별자로 사용할 수 없습니다.
  업그레이드 관리자가 개체 식별자에서 0xFFFF 문자를 검색했습니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 데이터베이스 호환성 모드가 90 이상으로 설정된 경우 해당 식별자에 이 문자가 들어 있는 데이터베이스, 테이블 및 열과 같은 개체를 참조하거나 이름을 바꿀 수 없습니다. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]로 업그레이드할 때 사용자 데이터베이스는 호환성 모드를 유지합니다. 데이터베이스 호환성 모드를 90 이상으로 변경하기 전에 0xFFFF 문자가 들어 있는 개체의 이름을 바꾸십시오.  
  
 식별자에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "식별자"를 참조하십시오. 데이터베이스 호환성 모드에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "sp_dbcmptlevel"을 참조하십시오.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
