---
title: SQL Server 2014의 SQL Server Reporting Services에서 사용 되지 않는 기능 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651535"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>SQL Server 2014의 SQL Server Reporting Services에서 지원되지 않는 기능
  이 항목에서는 지원되지 않는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능에 대해 설명합니다. 이러한 기능은 지원되지 않는 버전에서 계속 사용할 수 있지만 이후 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 기능이 제거될 예정입니다. 새 애플리케이션에는 이러한 기능을 사용하면 안 됩니다.  
  
 이 항목의 내용:  
  
-   [SQL Server 2014 R2 Reporting Services에서 지원되지 않는 기능](#bkmk_2014)  
  
-   [SQL Server 2012 SP1 Reporting Services에서 지원되지 않는 기능](#bkmk_2012sp1)  
  
-   [SQL Server 2012 R2 Reporting Services에서 지원되지 않는 기능](#bkmk_2012)  
  
-   [SQL Server 2008 R2 Reporting Services에서 지원되지 않는 기능](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a>SQL Server 2014 Reporting Services 사용 되지 않는 기능  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>다음 버전의 SQL Server에서 지원되지 않는 기능  
 다음 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은의 **다음** 버전에서 지원 되지 않습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . 새 개발 작업에서는 이러한 기능을 사용하지 말고, 현재 이러한 기능을 사용하는 애플리케이션은 가능한 한 빨리 수정하십시오.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>HTML 렌더링 확장 프로그램 디바이스 정보 설정  
 HTML 렌더링 확장 프로그램에 대한 다음 디바이스 정보 설정은 지원되지 않습니다.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 HTML 렌더링 확장 프로그램에 자세한 내용은 [HTML Device Information Settings](html-device-information-settings.md)을 참조하세요.  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Microsoft Word 및 Microsoft Excel 1997-2003 렌더링  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 렌더링 확장 프로그램은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 및 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 이진 교환 파일 형식으로 보고 합니다. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 형식으로 렌더링 되는 확장 프로그램이 포함 되어 있습니다.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>RDL(Report Definition Language) 2005 및 이전  
 RDL(Report Definition Language) 2005 및 이전 버전은 지원되지 않습니다. RDL에 대 한 자세한 내용은 [SSRS&#41;&#40;Report Definition Language ](reports/report-definition-language-ssrs.md)를 참조 하세요.  
  
 보고서 업그레이드에 대한 자세한 내용은 [Upgrade Reports](install-windows/upgrade-reports.md)를 참조하세요.  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 및 이전 사용자 지정 보고서 항목  
 2005 및 이전 버전에 대해 컴파일된 CRI (사용자 지정 보고서 항목) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 더 이상 사용 되지 않습니다.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services 스냅샷 2005 및 이전 버전  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 및 이전 버전으로 렌더링 된 스냅숏은 더 이상 사용 되지 않습니다.  
  
#### <a name="report-models"></a>보고서 모델  
 SMDL(Semantic Modeling Language) 보고서 모델은 더 이상 사용되지 않습니다. 보고서에서 기존 보고서 모델을 데이터 원본으로 계속 사용할 수 있지만 보고서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 모델에 대 한 종속성을 제거 하기 위해 보고서를 업데이트 하는 것을 고려해 야 합니다.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에는 보고서 모델을 만들거나 업데이트 하기 위한 도구가 포함 되어 있지 않습니다. 자세한 내용은 [2014 SQL Server SQL Server Reporting Services의 주요 변경 내용](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)을 참조 하세요.  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>웹 서비스 엔드포인트에서 사용되지 않는 메서드  
 다음 작업은 <xref:ReportService2010.ReportingService2010> 웹 서비스 엔드포인트에서 더 이상 사용되지 않습니다.  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>SharePoint 웹 파트  
 cab 파일에서 추출할 수 있는 설치 캐비닛 파일 **RSWebParts.cab** 및 SharePoint 웹 파트는 사용되지 않습니다. 사용 되지 않는 웹 파트는 보고서 탐색기 (**Spexplorer. .dwp**) 및 보고서 뷰어 (**spexplorer**)입니다.  
  
 사용 되지 않는 웹 파트에 대 한 자세한 내용은 [SharePoint 웹 파트를 사용 하 여 기본 모드 보고서 보기 및 탐색 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 을 참조 하세요.  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>이후 버전의 SQL Server에서 지원되지 않는 기능  
 아래의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 다음 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 지원되지만 이후 버전에서는 제거될 예정입니다. 어떤 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 제거될지는 결정되지 않았습니다.  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 사용되지 않는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]기능은 없습니다.  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a>SQL Server 2012 SP1 Reporting Services 사용 되지 않는 기능  
 이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 지원되지 않는 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]기능에 대해 설명합니다. 아래의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 다음 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 지원되지만 이후 버전에서는 제거될 예정입니다. 어떤 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 제거될지는 결정되지 않았습니다.  
  
### <a name="sharepoint-web-parts"></a>SharePoint 웹 파트  
 cab 파일에서 추출할 수 있는 설치 캐비닛 파일 **RSWebParts.cab** 및 SharePoint 웹 파트는 사용되지 않습니다. 사용 되지 않는 웹 파트는 보고서 탐색기 (**Spexplorer. .dwp**) 및 보고서 뷰어 (**spexplorer**)입니다.  
  
 사용 되지 않는 웹 파트에 대 한 자세한 내용은 [SharePoint 웹 파트를 사용 하 여 기본 모드 보고서 보기 및 탐색 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 을 참조 하세요.  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a>SQL Server 2012 Reporting Services 사용 되지 않는 기능  
 이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 지원되지 않는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]기능에 대해 설명합니다.  
  
### <a name="html-rendering-extension-device-information-settings"></a>HTML 렌더링 확장 프로그램 디바이스 정보 설정  
 HTML 렌더링 확장 프로그램에 대한 다음 디바이스 정보 설정은 지원되지 않습니다.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 HTML 렌더링 확장 프로그램에 자세한 내용은 [HTML Device Information Settings](html-device-information-settings.md)을 참조하세요.  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Microsoft Word 및 Microsoft Excel 1997-2003 렌더링  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 렌더링 확장 프로그램은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 및 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 이진 교환 파일 형식으로 보고 합니다. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 형식으로 렌더링 되는 확장 프로그램이 포함 되어 있습니다.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>RDL(Report Definition Language) 2005 및 이전  
 RDL(Report Definition Language) 2005 및 이전 버전은 지원되지 않습니다. RDL에 대 한 자세한 내용은 [SSRS&#41;&#40;Report Definition Language ](reports/report-definition-language-ssrs.md)를 참조 하세요.  
  
 보고서 업그레이드에 대한 자세한 내용은 [Upgrade Reports](install-windows/upgrade-reports.md)를 참조하세요.  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 및 이전 사용자 지정 보고서 항목  
 2005 및 이전 버전에 대해 컴파일된 CRI (사용자 지정 보고서 항목) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 더 이상 사용 되지 않습니다.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services 스냅샷 2005 및 이전 버전  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 및 이전 버전으로 렌더링 된 스냅숏은 더 이상 사용 되지 않습니다.  
  
### <a name="report-models"></a>보고서 모델  
 SMDL(Semantic Modeling Language) 보고서 모델은 더 이상 사용되지 않습니다. 보고서에서 기존 보고서 모델을 데이터 원본으로 계속 사용할 수 있지만 보고서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 모델에 대 한 종속성을 제거 하기 위해 보고서를 업데이트 하는 것을 고려해 야 합니다.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에는 보고서 모델을 만들거나 업데이트 하기 위한 도구가 포함 되어 있지 않습니다. 자세한 내용은 [2014 SQL Server SQL Server Reporting Services의 주요 변경 내용](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)을 참조 하세요.  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>웹 서비스 엔드포인트에서 사용되지 않는 메서드  
 다음 작업은 <xref:ReportService2010.ReportingService2010> 웹 서비스 엔드포인트에서 더 이상 사용되지 않습니다.  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services 사용 되지 않는 기능  
  
> [!NOTE]  
>  SQL Server 2008 R2는 SQL Server 2008의 부 버전 업그레이드이므로 SQL Server 2008 섹션의 내용도 검토하는 것이 좋습니다.  
  
### <a name="report-server-web-service-endpoints"></a>보고서 서버 웹 서비스 엔드포인트  
 이 릴리스에서는 웹 서비스 <xref:ReportService2005.ReportingService2005> 및 <xref:ReportService2006.ReportingService2006>이 사용되지 않습니다. 이러한 엔드포인트는 새 엔드포인트인 <xref:ReportService2010.ReportingService2010>로 대체되었습니다.  
  
 새 엔드포인트에는 사용되지 않는 엔드포인트에서 제공하던 모든 기능과 SQL Server 2008 R2에 추가된 새 기능이 모두 포함됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [새로운 기능 &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [이전 버전과의 호환성](../getting-started/backward-compatibility.md)   
 [SQL Server 2014의 SQL Server Reporting Services에 대 한 동작 변경 내용](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [SQL Server 2014의 SQL Server Reporting Services에서 중단된 기능](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
