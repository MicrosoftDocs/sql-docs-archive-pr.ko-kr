---
title: SharePoint용 PowerPivot (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58ebcf004224d21ab5b47aaee1e2e7e3ef2047ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651323"
---
# <a name="powerpivot-for-sharepoint-ssas"></a>SharePoint용 PowerPivot(SSAS)
  SharePoint용 PowerPivot은 SharePoint 모드에서 실행되는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버입니다. SharePoint용 PowerPivot은 SharePoint 팜에서 PowerPivot 데이터의 서버 호스팅을 제공합니다. PowerPivot 데이터는 다음 중 하나를 사용하여 빌드하는 분석 데이터 모델입니다.  
  
-   PowerPivot for Excel 2010 추가 기능  
  
-   Excel 2013  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010  
  
 이 데이터의 서버 호스팅에는 SharePoint, Excel 서비스 및 SharePoint용 PowerPivot 설치가 필요합니다. 데이터는 SharePoint용 PowerPivot 인스턴스에 로드되며 여기서 서버가 Excel 2010 통합 문서용으로 제공하거나 SharePoint 2013 Excel 서비스가 Excel 2013 통합 문서용으로 제공하는 PowerPivot 데이터 새로 고침 기능을 사용하여 예약된 간격으로 데이터를 새로 고칠 수 있습니다.  
  
## <a name="powerpivot-for-sharepoint-2013"></a>SharePoint 2013용 PowerPivot  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]지원 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel 서비스는 데이터 모델 및 파워 뷰 보고서를 포함 하는 Excel 통합 문서를 사용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 합니다.  
  
 SharePoint 2013의 Excel Services에는 브라우저에서 PowerPivot 통합 문서와 상호 작용할 수 있도록 데이터 모델 기능이 포함되어 있습니다. SharePoint 2013용 PowerPivot 추가 기능을 팜에 배포하지 않아도 됩니다. SharePoint 모드의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버를 설치하고 Excel Services **데이터 모델** 설정 내에 서버를 등록해야 합니다.  
  
 SharePoint 2013용 PowerPivot 추가 기능을 배포하면 추가 기능 및 SharePoint 팜의 기능을 사용할 수 있습니다. 추가 기능에는 PowerPivot 갤러리, 데이터 새로 고침 예약 및 PowerPivot 관리 대시보드가 있습니다.  
  
 ![SSAS PowerPivot 모드 2 서버 배포](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot 모드 2 서버 배포")  
  
## <a name="powerpivot-for-sharepoint-2010"></a>SharePoint용 PowerPivot 2010  
 SharePoint용 PowerPivot 2010은 SharePoint 2010 팜에서 PowerPivot 데이터의 서버 호스팅을 제공합니다. PowerPivot 데이터는 PowerPivot for Excel 추가 기능을 사용하여 Excel에서 작성하는 분석 데이터 모델입니다. 이 데이터의 서버 호스팅에는 SharePoint 2010, Excel 서비스 및 SharePoint용 PowerPivot 설치가 필요합니다. 데이터는 팜에서 SharePoint용 PowerPivot 인스턴스에 로드되며 여기서 서버가 제공하는 PowerPivot 데이터 새로 고침 기능을 사용하여 예약된 간격으로 데이터를 새로 고칠 수 있습니다.  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a>SharePoint용 PowerPivot 2010의 구성 요소  
 SharePoint용 PowerPivot은 공유 서비스로 구현되므로 기본 제공 기능과 인프라를 사용하여 PowerPivot 서비스 애플리케이션을 관리, 보호 및 사용할 수 있습니다. 서버 및 데이터 검색, 리디렉션 및 연결 관리는 모두 팜 수준에서 관리됩니다. 중앙 관리는 서버 ID, 서버 상태 및 구성 속성을 관리하는 데 사용되는 서비스에 관리 인터페이스를 제공합니다.  
  
 SharePoint용 PowerPivot의 전체 배포에는 SharePoint 팜에서 Excel 및 Excel 서비스와 통합되는 클라이언트 및 서버 구성 요소가 포함됩니다. Excel 통합 문서 내부의 PowerPivot 데이터는 데이터를 로드하고 쿼리하기 위해 Analysis Services xVelocity 메모리 내 분석 엔진(VertiPaq)이 필요한 Analysis Services 데이터베이스입니다. 클라이언트 워크스테이션에서 xVelocity 엔진은 Excel 내에서 in-process로 실행됩니다. SharePoint 팜에서 Analysis Services는 PowerPivot 데이터에 대한 요청을 처리하는 관련 서비스와 함께 애플리케이션 서버에서 실행됩니다. 다음 다이어그램에서는 PowerPivot 클라이언트와 서버 구성 요소를 보여 줍니다.  
  
 ![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")  
  
 PowerPivot 웹 서비스는 웹 애플리케이션 서버에서 실행됩니다. 이 서비스는 웹 애플리케이션에서 팜의 PowerPivot 시스템 서비스 인스턴스로 요청을 리디렉션합니다.  
  
 PowerPivot 시스템 서비스는 Analysis Services에 대한 로드 요청을 실행하고 메모리에 이미 로드되어 있는 데이터에 대해 진행 중인 연결을 관리하며 데이터가 더 이상 사용되지 않거나 시스템 리소스에 대한 경합이 있는 경우 데이터를 캐시하거나 언로드합니다. 사용자 작업도 추적합니다. 서버 상태 데이터 및 기타 사용량 현황 데이터가 수집되고 보고서에 표시되어 시스템 성능을 파악할 수 있습니다.  
  
 SharePoint 통합 모드의 Analysis Service 서비스 인스턴스는 배포를 완료합니다. 이 인스턴스는 데이터를 로드, 쿼리 및 언로드합니다. 또한 이 인스턴스는 통합 문서가 PowerPivot 데이터 새로 고침에 대해 구성된 경우 데이터도 처리합니다.  각 인스턴스는 동일한 설치에 속하는 로컬 PowerPivot 시스템 서비스와 긴밀하게 결합됩니다.  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> 섹션 내용  
 [중앙 관리에서 PowerPivot 서버 관리 및 구성](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Windows PowerShell을 사용하여 PowerPivot 구성](power-pivot-configuration-using-windows-powershell.md)  
  
 [PowerPivot Configuration Tools](power-pivot-configuration-tools.md)  
  
 [PowerPivot 인증 및 권한 부여](power-pivot-authentication-and-authorization.md)  
  
 [PowerPivot 상태 규칙 - 구성](configure-power-pivot-health-rules.md)  
  
 [PowerPivot 관리 대시보드 및 사용량 현황 데이터](power-pivot-management-dashboard-and-usage-data.md)  
  
 [PowerPivot 갤러리](../../index.yml)  
  
 [PowerPivot 데이터 액세스](power-pivot-data-access.md)  
  
 [PowerPivot 데이터 새로 고침](power-pivot-data-refresh.md)  
  
 [PowerPivot 데이터 피드](power-pivot-data-feeds.md)  
  
 [PowerPivot BI 의미 체계 모델 연결 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md)  
  
 **다른 섹션**  
  
## <a name="additional-topics"></a>추가 항목  
 [SharePoint용 PowerPivot 업그레이드](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [SharePoint 2013용 PowerPivot 설치](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [SharePoint용 PowerPivot에 대한 PowerShell 참조](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [SQL Server 2014 셀프 서비스 비즈니스 인텔리전스에 대 한 예제 라이선스 토폴로지 및 비용](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a>참고 항목  
 [PowerPivot 계획 및 배포](https://go.microsoft.com/fwlink/?linkID=220972)   
 [SharePoint용 PowerPivot 재해 복구](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
