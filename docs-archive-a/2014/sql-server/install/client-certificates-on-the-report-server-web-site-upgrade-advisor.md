---
title: 보고서 서버 웹 사이트의 클라이언트 인증서 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650504"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>보고서 서버 웹 사이트의 클라이언트 인증서(업그레이드 관리자)
  업그레이드 관리자가 보고서 서버 또는 보고서 관리자 가상 디렉터리를 호스팅하는 IIS 웹 사이트에서 하나 이상의 클라이언트 인증서를 검색했습니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.|  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서는 클라이언트 인증서를 사용 하 여 사용자를 인증할 수 없습니다. 업그레이드를 계속 진행할 수는 있지만 클라이언트 인증서는 업그레이드된 보고서 서버에서 사용되지 않습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 ISA Server와 같은 별도의 솔루션을 사용하여 클라이언트 인증서 인증 요구 사항을 해결합니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
