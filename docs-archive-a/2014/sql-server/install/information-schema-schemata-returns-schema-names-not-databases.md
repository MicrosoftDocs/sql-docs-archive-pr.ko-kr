---
title: INFORMATION_SCHEMA. SCHEMATA는 인스턴스의 데이터베이스가 아니라 데이터베이스의 스키마 이름을 반환 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cb2a34a59bf6257c188210fc7bf2aeacb70f6b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660295"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA는 인스턴스의 데이터베이스가 아니라 데이터베이스의 스키마 이름을 반환합니다.
  업그레이드 관리자가 INFORMATION_SCHEMA.SCHEMATA 뷰를 참조하는 문을 검색했습니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 뷰가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 데이터베이스를 반환했지만 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 데이터베이스의 모든 스키마를 반환합니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 INFORMATION_SCHEMA.SCHEMATA 뷰가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 데이터베이스를 반환했지만 이제 뷰에서 SQL 표준을 준수하는 데이터베이스의 모든 스키마가 반환됩니다.  
  
## <a name="corrective-action"></a>수정 동작  
 인스턴스의 모든 데이터베이스를 반환 하도록 응용 프로그램을 수정 하 여 **sys.debug** 카탈로그 뷰를 참조 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
