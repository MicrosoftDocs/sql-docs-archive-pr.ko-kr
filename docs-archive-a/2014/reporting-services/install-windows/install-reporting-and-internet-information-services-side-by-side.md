---
title: Reporting Services 및 인터넷 정보 서비스 함께 설치 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], IIS
ms.assetid: 9b651fa5-f582-4f18-a77d-0dde95d9d211
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c16bb8e5cd8fd040e0048c17183d69bae68268ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728072"
---
# <a name="install-reporting-services-and-internet-information-services-side-by-side-ssrs-native-mode"></a>Reporting Services와 인터넷 정보 서비스 함께 설치(SSRS 기본 모드)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS) 및 인터넷 정보 서비스 (IIS)를 동일한 컴퓨터에 설치 하 고 실행할 수 있습니다. 사용하는 IIS 버전에 따라 해결해야 하는 상호 운용성 문제가 결정됩니다.  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드|  
  
|IIS 버전|문제|Description|  
|-----------------|------------|-----------------|  
|IIS 6.0, 7.0, 8.0, 8.5|한 애플리케이션을 대상으로 하는 요청이 다른 애플리케이션에 받아들여집니다.<br /><br /> HTTP.SYS는 URL 예약에 대한 선행 규칙을 적용합니다. URL 예약이 다른 애플리케이션의 URL 예약에 비해 약한 경우에는 가상 디렉터리 이름이 동일하며 포트 80을 함께 모니터링하는 애플리케이션으로 전송된 요청이 의도한 대상에 도달하지 않을 수 있습니다.|상황에 따라 URL 예약 스키마의 다른 URL 엔드포인트를 대체하는 등록된 엔드포인트가 다른 애플리케이션을 대상으로 하는 HTTP 요청을 받을 수 있습니다.<br /><br /> 보고서 서버 웹 서비스 및 보고서 관리자에 고유한 가상 디렉터리 이름을 사용하면 이러한 충돌이 발생하지 않도록 할 수 있습니다.<br /><br /> 이 시나리오에 대한 자세한 내용은 이 항목에 제공되어 있습니다.|  
  
## <a name="precedence-rules-for-url-reservations"></a>URL 예약에 대한 선행 규칙  
 IIS와 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]간 상호 운용성 문제를 해결하려면 먼저 URL 예약 선행 규칙을 이해해야 합니다. 선행 규칙은 다음과 같이 일반화할 수 있습니다. 더 명시적으로 정의된 값이 있는 URL 예약이 해당 URL과 일치하는 요청을 가장 먼저 받습니다.  
  
-   가상 디렉터리를 지정하는 URL 예약은 가상 디렉터리를 생략하는 URL 예약보다 명시적입니다.  
  
-   IP 주소, 정규화된 도메인 이름, 네트워크 컴퓨터 이름 또는 호스트 이름을 통해 단일 주소를 지정하는 URL 예약은 와일드카드보다 명시적입니다.  
  
-   강력한 와일드카드를 지정하는 URL 예약은 약한 와일드카드보다 명시적입니다.  
  
 다음 예에서는 가장 명시적인 것부터 차례로 URL 예약의 범위를 보여 줍니다.  
  
|예제|요청|  
|-------------|-------------|  
|http: \/ /123.234.345.456:80/reports|\/ \<computername> 도메인 이름 서비스가 해당 호스트 이름에 대 한 IP 주소를 확인할 수 있는 경우 http:/123.234.345.456/reports 또는 http:///reports로 전송 되는 모든 요청을 받습니다.|  
|http://+:80/reports|URL에 "reports" 가상 디렉터리 이름이 포함되어 있는 한 해당 컴퓨터에 대해 유효한 IP 주소 또는 호스트 이름으로 전송된 모든 요청을 받습니다.|  
|http: \/ /123.234.345.456:80|\/ \<computername> 도메인 이름 서비스가 해당 호스트 이름에 대 한 IP 주소를 확인할 수 있는 경우 http:/123.234.345.456 또는 http://를 지정 하는 모든 요청을 받습니다.|  
|http://+:80|**모두 할당됨**에 매핑된 애플리케이션 엔드포인트에 대해 다른 애플리케이션이 아직 받지 않은 요청을 받습니다.|  
|http://*:80|**모두 할당되지 않음**에 매핑된 애플리케이션 엔드포인트에 대해 다른 애플리케이션이 아직 받지 않은 요청을 받습니다.|  
  
 'System.IO.FileLoadException: 파일이 다른 프로세스에서 사용되고 있으므로 프로세스에서 파일에 액세스할 수 없습니다 (예외가 발생한 HRESULT: 0x80070020)'.라는 오류 메시지가 표시되면 포트 충돌이 발생한 것입니다.  
  
## <a name="url-reservations-for-iis-60-70-80-85-with-sssql14-reporting-services"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Reporting Services가 있는 IIS 6.0, 7.0, 8.0, 8.5에 대한 URL 예약  
 이전 섹션에 요약된 우선 순위 규칙을 기반으로 Reporting Services 및 IIS에 대해 정의된 URL 예약이 상호 운용성을 향상시키는 방식을 이해할 수 있습니다. Reporting Services는 해당 애플리케이션의 가상 디렉터리 이름을 명시적으로 지정하는 요청을 받습니다. IIS는 나머지 요청을 모두 받은 다음 이를 IIS 프로세스 모델 내에서 실행되는 애플리케이션으로 전송할 수 있습니다.  
  
|애플리케이션|URL 예약|Description|요청 수신|  
|-----------------|---------------------|-----------------|---------------------|  
|보고서 서버|http://+:80/ReportServer|포트 80에서 ReportServer 가상 디렉터리가 있는 강력한 와일드카드입니다.|포트 80에서 ReportServer 가상 디렉터리를 지정하는 모든 요청을 받습니다. Http:///reportserver에 대 한 모든 요청을 보고서 서버 웹 서비스에서 받습니다. \<computername>|  
|보고서 관리자|http://+:80/Reports|포트 80에서 Reports 가상 디렉터리가 있는 강력한 와일드카드입니다.|포트 80에서 Reports 가상 디렉터리를 지정하는 모든 요청을 받습니다. 보고서 관리자 http:///reports에 대 한 모든 요청을 받습니다. \<computername>|  
|IIS|http://*:80/|포트 80의 약한 와일드카드입니다.|포트 80에서 다른 애플리케이션이 받지 않은 모든 나머지 요청을 받습니다.|  
  
## <a name="side-by-side-deployments-of-sscurrent-and-sql-server-2005-reporting-services-on-iis-60-70-80-85"></a>IIS 6.0, 7.0, 8.0, 8.5에 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]와 SQL Server 2005 Reporting Services 함께 배포  
 IIS와 Reporting Services 간 상호 운용성 문제는 IIS 웹 사이트의 가상 디렉터리 이름이 Reporting Services에 사용되는 가상 디렉터리 이름과 같을 경우 발생합니다. 예를 들어 다음과 같은 구성이 있다고 가정합니다.  
  
-   포트 80에 할당된 IIS의 웹 사이트 및 "Reports"라는 가상 디렉터리  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]기본 구성으로 설치 된 보고서 서버 인스턴스. 여기서 URL 예약은 포트 80를 지정 하 고 보고서 관리자 응용 프로그램은 가상 디렉터리 이름으로 "Reports"도 사용 합니다.  
  
 이 구성을 고려할 때 http://: 80/reports로 전송 되는 요청은 \<computername> 보고서 관리자에서 수신 됩니다. IIS의 Reports 가상 디렉터리를 통해 액세스되는 애플리케이션은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버 인스턴스가 설치된 후 더 이상 요청을 받지 않습니다.  
  
 이전 버전 및 최신 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]배포를 함께 실행하는 경우 방금 설명한 라우팅 문제가 발생할 가능성이 높습니다. 이는 모든 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]가 &quot;ReportServer&quot; 및 &quot;Reports&quot;를 보고서 서버 및 보고서 관리자 애플리케이션의 가상 디렉터리 이름으로 사용하여 IIS에 &quot;reports&quot; 및 &quot;reportserver&quot; 가상 디렉터리가 있을 가능성이 높아지기 때문입니다.  
  
 모든 애플리케이션이 요청을 받도록 하려면 다음 지침을 따릅니다.  
  
-   Reporting Services 설치의 경우 Reporting Services와 동일한 포트에서 IIS 웹 사이트에 아직 사용되지 않은 가상 디렉터리 이름을 사용합니다. 충돌이 발생하면 설치 완료 후 가상 디렉터리를 구성할 수 있도록 Reporting Services를 "파일만" 모드로 설치합니다(설치를 사용하지만 설치 마법사에서 서버 옵션 구성 안 함). System.IO.FileLoadException: 파일이 다른 프로세스에서 사용되고 있으므로 프로세스에서 파일에 액세스할 수 없습니다. (예외가 발생한 HRESULT: 0x80070020).라는 오류 메시지가 표시되면 구성 충돌이 발생한 것입니다.  
  
-   수동으로 구성하는 설치의 경우 구성하는 URL에 기본 명명 규칙을 적용합니다. [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 를 명명된 인스턴스로 설치하는 경우 가상 디렉터리를 만들 때 인스턴스 이름을 포함합니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [SSRS Configuration Manager &#40;URL 구성&#41;](configure-a-url-ssrs-configuration-manager.md)   
 [Reporting Services 기본 모드 보고서 서버 설치](install-reporting-services-native-mode-report-server.md)  
  
  
