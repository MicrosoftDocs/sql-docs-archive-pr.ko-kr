---
title: Integration Services 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740727"
---
# <a name="integration-services-parameters"></a>Integration Services 매개 변수
  의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 컴퓨터의 패키지나 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 파일 시스템의 패키지 파일을 분석 하도록 결정할 수 있습니다. 파일 시스템에 있는 파일을 분석할 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 들어 있는 폴더의 경로를 제공합니다.  
  
## <a name="options"></a>옵션  
 **컴퓨터에 있는 SSIS 패키지 분석**  
 컴퓨터에 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 분석하려면 이 옵션을 선택합니다. 이 옵션은 기본적으로 선택됩니다.  
  
 **SSIS 패키지 파일 분석**  
 파일 시스템에 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 분석하려면 이 옵션을 선택합니다.  
  
 **SSIS 패키지의 경로**  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 들어 있는 UNC 또는 로컬 경로를 찾습니다. 파일 이름을 포함할 필요는 없습니다. 입력 한 경로에 액세스할 수 없으면 **다음**을 클릭할 수 없습니다. 기본적으로 경로는 비어 있습니다. 이 필드는 **SSIS 패키지 파일 분석**을 선택한 경우에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
