---
title: 팜에 추가 보고서 서버 추가(SSRS 확장) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31fd7809c4085a90dc487f9091a7f9bd0aeab58e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647524"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>팜에 추가 보고서 서버 추가(SSRS 확장)
  SharePoint 팜에 두 번째 이상의 SharePoint 모드 보고서 서버를 추가하면 보고서 서버 처리 성능 및 응답 시간을 향상시킬 수 있습니다. 보고서 서버에 더 많은 사용자, 보고서 및 기타 애플리케이션을 추가할수록 성능이 저하되는 경우에는 보고서 서버를 추가하면 성능을 향상시킬 수 있습니다. 또한 하드웨어에 문제가 있거나 사용자 환경의 개별 서버에 대한 전반적인 관리를 수행하는 경우 보고서 서버의 가용성을 늘리기 위해 두 번째 보고서 서버를 추가하는 것이 좋습니다. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 릴리스부터는 SharePoint 모드에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 환경을 확장하는 단계는 표준 SharePoint 팜 배포를 따르며 SharePoint 부하 분산 기능을 이용합니다.  
  
> [!IMPORTANT]  
>  일부 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 버전에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]확장이 지원되지 않습니다. 자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)섹션을 참조 하세요.  
  
> [!TIP]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 부터는 서버를 추가하고 보고서 서버를 확장하는 데 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스가 포함된 SharePoint 서버가 팜에 추가되어 SharePoint 제품에서 보고서 서비스의 확장을 관리합니다.  
  
 기본 모드 보고서 서버를 확장하는 방법은 [기본 모드 보고서 서버 확장 배포 구성&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)을 참조하세요.  
  
-   [부하 분산](#bkmk_loadbalancing)  
  
-   [필수 구성 요소](#bkmk_prerequisites)  
  
-   [단계](#bkmk_steps)  
  
-   [추가 구성](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a>부하 분산  
 사용자 환경에 사용자 지정 또는 타사 부하 분산 솔루션이 없는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 부하 분산은 SharePoint에서 자동으로 관리됩니다. 기본 SharePoint 부하 분산 동작은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 시작한 모든 애플리케이션 서버에서 각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 부하를 분산하는 것입니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스가 설치되고 시작되었는지 확인하려면 SharePoint 중앙 관리에서 **서버의 서비스 관리** 를 클릭합니다.  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> 필수 조건  
  
-   SQL Server 설치 프로그램을 실행하려면 로컬 관리자여야 합니다.  
  
-   컴퓨터가 도메인에 조인되어 있어야 합니다.  
  
-   SharePoint 구성과 콘텐츠 데이터베이스를 호스팅하는 기존 데이터베이스 서버의 이름을 알고 있어야 합니다.  
  
-   원격 데이터베이스 연결을 허용하도록 데이터베이스 서버를 구성해야 합니다.  이렇게 하지 않으면 새 서버는 SharePoint 구성 데이터베이스에 연결할 수 없기 때문에 새 서버를 팜에 조인할 수 없습니다.  
  
-   현재 팜 서버에서 실행하고 있는 것과 같은 버전의 SharePoint가 새 서버에 설치되어 있어야 합니다. 예를 들어 팜에 이미 SharePoint 2010 SP1(서비스 팩 1)이 설치된 경우 팜을 조인하려면 새 서버에도 SP1을 설치해야 합니다.  
  
-   시스템 및 버전 요구 사항을 이해하려면 다음 항목을 검토하십시오.  
  
     [SharePoint 2010 팜에서 SQL Server BI 기능을 사용하기 위한 지침](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a>위한  
 이 항목의 단계에서는 SharePoint 팜 관리자가 서버를 설치하고 구성한다고 가정합니다. 다이어그램은 일반적인 3계층 환경을 보여주고 다이어그램의 번호가 매겨진 항목이 다음 목록에 설명됩니다.  
  
-   (1) 여러 WFE(웹 프런트 엔드) 서버. WFE 서버에는 SharePoint 2010용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능이 필요합니다.  
  
-   (2) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 실행하는 단일 애플리케이션 서버 및 중앙 관리 같은 웹 사이트. 다음 단계에서는 두 번째 애플리케이션 서버를 이 계층에 추가합니다.  
  
-   (3) 두 SQL Server 데이터베이스 서버.  
  
-   (4) 소프트웨어 또는 하드웨어 네트워크 부하 분산 솔루션(NLB)을 나타냅니다.  
  
 ![Reporting Services 애플리케이션 서버 추가](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Reporting Services 애플리케이션 서버 추가")  
  
 다음 단계에서는 관리자가 서버를 설치하고 구성한다고 가정합니다. 서버는 팜에 새 애플리케이션 서버로 설치되고 WFE(웹 프런트 엔드)로 사용되지 않습니다.  
  
|단계|설명 및 링크|  
|----------|--------------------------|  
|SharePoint 2010 제품 준비 도구 실행|SharePoint 2010 설치 미디어가 있어야 합니다. 준비 도구는 설치 미디어의 **PrerequisiteInstaller.exe** 입니다.|  
|SharePoint 2010 제품 설치|1) **서버 팜** 설치 유형을 선택 합니다.<br /><br /> 2) 서버 유형에 대해 **완료** 를 선택 합니다.<br /><br /> 3) 기존 SharePoint 팜에 SharePoint 2010 SP1이 설치되어 있으면 설치가 완료된 후 SharePoint 제품 구성 마법사를 실행하지 마세요. SharePoint 제품 구성 마법사를 실행하기 전에 SharePoint SP1을 설치해야 합니다.|  
|SharePoint Server 2010 SP1 설치|기존 SharePoint 팜에 SharePoint 2010 s p 1이 설치 되어 있는 경우에서 SharePoint 2010 SP1을 다운로드 하 여 설치 [https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697) 합니다.<br /><br /> SharePoint 2010 SP1에 대한 자세한 내용은 [Office 2010 SP1 및 SharePoint 2010 SP1을 설치할 때의 알려진 문제](https://support.microsoft.com/kb/2532126)를 참조하십시오.|  
|SharePoint 제품 구성 마법사를 실행하여 팜에 서버 추가|1) **Microsoft sharepoint 2010 products** 프로그램 그룹에서 **Microsoft Sharepoint 2010 products 구성 마법사**를 클릭 합니다.<br /><br /> 2) **서버 팜에 연결** 페이지에서 **기존 팜에 연결** 을 선택 하 고 **다음**을 클릭 합니다.<br /><br /> 3) **구성 데이터베이스 설정 지정** 페이지에서 기존 팜에 사용 되는 데이터베이스 서버의 이름과 구성 데이터베이스의 이름을 입력 합니다. **다음**을 클릭합니다.<br />** \* \* 중요 \* 다음과 \* ** 비슷한 오류 메시지가 표시 되 고 권한이 있는지 확인 한 경우 **SQL Server Configuration Manager**: "데이터베이스 서버에 연결 하지 못했습니다."에서 SQL Server 네트워크 구성에 대해 사용 하도록 설정 된 프로토콜을 확인 합니다. 데이터베이스가 존재 하 고 Sql Server 이며 서버에 액세스할 수 있는 적절 한 권한이 있는지 확인 하십시오. "<br />** \* \* 중요 \* 페이지 \* ** **서버 팜 제품 및 패치 상태가**표시 되는 경우 서버를 팜에 조인 하기 전에 페이지의 정보를 검토 하 고 필요한 파일로 서버를 업데이트 해야 합니다.<br /><br /> 4) **팜 보안 설정 지정** 페이지에서 팜 암호를 입력 하 고 **다음**을 클릭 합니다. 확인 페이지에서 **다음** 을 클릭하여 마법사를 실행합니다.<br /><br /> 5) **다음** 을 클릭 하 여 **팜 구성 마법사**를 실행 합니다.|  
|서버가 SharePoint 팜에 추가되었는지 확인|1) SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **이 팜의 서버 관리** 를 클릭합니다.<br /><br /> 2) 새 서버가 추가되었고 상태가 올바른지 확인합니다.<br /><br /> 3) 서비스를 실행 하는 서비스 **SQL Server Reporting Services** 표시 되지 않습니다. 다음 단계에서 서비스가 설치됩니다.<br /><br /> 4) WFE 역할에서이 서버를 제거 하려면 **서버의 서비스 관리** 를 클릭 하 고 **Microsoft SharePoint Foundation 웹 응용 프로그램**서비스를 중지 합니다.|  
|Reporting Services SharePoint 모드 설치 및 구성|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치를 실행합니다. Sharepoint 모드 설치에 대 한 자세한 내용은 sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [2010에 대 한 Sharepoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) 를 참조 하세요. 서버가 응용 프로그램 서버로만 사용 되 고 WFE로 사용 되지 않는 경우에는 SharePoint 용 Reporting Services sharepoint 모드 설치를 참조 하세요 .에서 **sharepoint 제품용 Reporting Services 추가 기능** 을 선택할 필요가 없습니다.<br /><br /> **설치 역할** 페이지에서 **SQL Server 기능 설치** 를 선택 합니다.<br /><br /> **기능 선택** 페이지에서 **Reporting Services-SharePoint** 를 선택 합니다.<br /><br /> 또는<br /><br /> **Reporting Services 구성** 페이지 **Reporting Services SharePoint 모드**에 대해 **설치만** 옵션이 선택 되었는지 확인 합니다.|  
|Reporting Services가 작동하는지 확인|1) SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **이 팜의 서버 관리** 를 클릭합니다.<br /><br /> 2) **SQL Server Reporting Services 서비스**를 확인합니다.<br /><br /> 자세한 내용은 [Reporting Services 설치 확인](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) 을 참조 하세요.|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a>추가 구성  
 확장된 배포에서 백그라운드 처리만 수행하도록 개별 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버를 최적화하여 대화형 보고서 실행과 리소스를 두고 경합하지 않도록 할 수 있습니다. 백그라운드 처리에는 일정, 구독 및 데이터 경고가 포함됩니다.  
  
 개별 보고서 서버의 동작을 변경 하려면 **\<IsWebServiceEnable>** **RSreportServer.config** 구성 파일에서를 false로 설정 합니다.  
  
 기본적으로 보고서 서버는 \<IsWebServiceEnable> 를 TRUE로 설정 하 여 구성 됩니다. 모든 서버가 TRUE로 구성된 경우 팜의 모든 노드에서 대화형 및 백그라운드의 로드 균형이 조정됩니다.  
  
 을 False로 설정 하 여 모든 보고서 서버를 구성 하면 \<IsWebServiceEnable> 기능을 사용 하려고 할 때 다음과 비슷한 오류 메시지가 표시 됩니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Reporting Services 웹 서비스를 사용할 수 없습니다. Reporting Services SharePoint 서비스의 인스턴스를 하나 이상 구성 하 여 \<IsWebServiceEnable> true로 설정 합니다. 자세한 내용은 [RSreportserver.config &#40;Reporting Services 구성 파일 수정](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) 을 참조 하세요&#41;  
  
## <a name="see-also"></a>참고 항목  
 [SharePoint 2013의 팜에 웹 또는 응용 프로그램 서버 추가](https://technet.microsoft.com/library/cc261752.aspx)   
 [서비스 구성(SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
