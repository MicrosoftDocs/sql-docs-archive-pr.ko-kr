---
title: SQL Server에 대 한 Microsoft 전체 텍스트 엔진은 기본적으로 서명 되지 않은 타사 구성 요소를 로드 하지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661512"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>SQL Server용 Microsoft 전체 텍스트 엔진은 기본적으로 서명되지 않은 타사 구성 요소를 로드하지 않습니다.
  기본적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)]용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 엔진은 [!INCLUDE[msCoName](../../includes/msconame-md.md)]가 서명하지 않은 구성 요소를 로드하지 않습니다.  
  
## <a name="component"></a>구성 요소  
 전체 텍스트 검색  
  
## <a name="description"></a>Description  
 업그레이드 후에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)]용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 엔진이 현재 서버에 설치된 PDF 필터 등의 타사 필터를 기본적으로 로드하지 않습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 타사 필터를 로드 하려면 *load_os_resource* 설정 하 고 해당 인스턴스에 대 한 *verify_signature* 해제 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
