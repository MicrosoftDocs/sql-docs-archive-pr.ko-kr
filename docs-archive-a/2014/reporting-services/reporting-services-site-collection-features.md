---
title: Reporting Services 사이트 모음 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9475ee323222b800a9c4b9a86e737fdd161e7a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732404"
---
# <a name="reporting-services-site-collection-features"></a><span data-ttu-id="58870-102">Reporting Services 사이트 모음 기능</span><span class="sxs-lookup"><span data-stu-id="58870-102">Reporting Services Site Collection Features</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="58870-103">SharePoint 모드는 세 가지 SharePoint 사이트 모음 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-103">SharePoint mode provides three SharePoint site collection features.</span></span> <span data-ttu-id="58870-104">이 기능은 일반적인 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 모드 보고 환경, [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition용 추가 기능 및 SharePoint 중앙 관리의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에 대한 관리 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-104">The features support the general [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode reporting environment, [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], a feature of the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition, and management operations for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint Central Administration.</span></span>  
  
## <a name="site-collection-features"></a><span data-ttu-id="58870-105">사이트 모음 기능</span><span class="sxs-lookup"><span data-stu-id="58870-105">Site Collection Features</span></span>  
 <span data-ttu-id="58870-106">다음 표에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 사이트 모음 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-106">The following table describes the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features.</span></span>  
  
|<span data-ttu-id="58870-107">기능</span><span class="sxs-lookup"><span data-stu-id="58870-107">Feature</span></span>|<span data-ttu-id="58870-108">설명</span><span class="sxs-lookup"><span data-stu-id="58870-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58870-109">**보고서 서버 중앙 관리 기능**</span><span class="sxs-lookup"><span data-stu-id="58870-109">**Report Server Central Administration Feature**</span></span>|<span data-ttu-id="58870-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버와의 통합을 관리하기 위한 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-110">Enables Features for managing integration with a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="58870-111">이 기능은 SharePoint 중앙 관리 사이트 모음에서만 설치 및 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58870-111">This feature is only installed and used in the SharePoint Central Administration site collection.</span></span><br /><br /> <span data-ttu-id="58870-112">[!INCLUDE[msCoName](../includes/msconame-md.md)]Sharepoint 제품용 추가 기능을 설치 하면 보고서 서버 통합 기능이 Sharepoint 중앙 관리 사이트 모음에서 자동으로 활성화 됩니다 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="58870-112">The Report server integration feature is automatically activated in SharePoint Central Administration Site collection after you install the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span> <span data-ttu-id="58870-113">일부 경우에는 기능을 수동으로 활성화해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58870-113">In some situations you will need to manually activate the feature.</span></span> <span data-ttu-id="58870-114">보고서 서버 기능을 활성화하려면 SharePoint 중앙 관리의 사이트 설정 페이지에서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-114">To activate the report server feature, use the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pages in SharePoint Central Administration's Site Settings page.</span></span><br /><br /> <span data-ttu-id="58870-115">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 버전 이상의 SharePoint 제품용 추가 기능은 추가 기능이 설치될 때 기존의 모든 사이트 모음에 대해 보고서 서버 통합 기능을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-115">The [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] version and later of the Add-in for SharePoint products will activate the report server integration feature for all existing site collections when the Add-in is installed.</span></span> <span data-ttu-id="58870-116">또한 이 기능은 새 사이트 모음에 대해 자동으로 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="58870-116">Additionally, the feature will be automatically active for new site collections.</span></span>|  
|<span data-ttu-id="58870-117">**보고서 서버 통합 기능**</span><span class="sxs-lookup"><span data-stu-id="58870-117">**Report Server Integration Feature**</span></span>|<span data-ttu-id="58870-118">을 사용 하 여 [!INCLUDE[msCoName](../includes/msconame-md.md)] 다양 한 보고 기능 사용[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58870-118">Enables rich reporting using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span></span><br /><br /> <span data-ttu-id="58870-119">이 기능은 기본적으로 활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58870-119">This feature is Active by default.</span></span>|  
|<span data-ttu-id="58870-120">**파워 뷰 통합 기능**</span><span class="sxs-lookup"><span data-stu-id="58870-120">**Power View Integration Feature**</span></span>|<span data-ttu-id="58870-121">PowerPivot 통합 문서 및 Analysis Services 테이블 형식 데이터베이스에 대해 대화형 데이터 탐색 및 시각적 표현을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-121">Enables interactive data exploration and visual presentation against PowerPivot work books and Analysis services tabular databases.</span></span><br /><br /> <span data-ttu-id="58870-122">이 기능은 다음 데이터 원본의 상황에 맞는 메뉴에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58870-122">The feature can be accessed by the context menus of the following data sources:</span></span><br /><br /> <span data-ttu-id="58870-123">.rdlx</span><span class="sxs-lookup"><span data-stu-id="58870-123">.rdlx</span></span><br /><br /> <span data-ttu-id="58870-124">.rsds</span><span class="sxs-lookup"><span data-stu-id="58870-124">.rsds</span></span><br /><br /> <span data-ttu-id="58870-125">.bism 연결 파일</span><span class="sxs-lookup"><span data-stu-id="58870-125">.bism connection file</span></span><br /><br /> <br /><br /> <span data-ttu-id="58870-126">상황에 맞는 메뉴에 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] 가 표시되지 않으면 **파워 뷰 통합 기능** 이 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="58870-126">If [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] does not appear in the context menus, verify the **Power View Integration Feature** is activated.</span></span><br /><br /> <span data-ttu-id="58870-127">이 기능은 기본적으로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58870-127">This feature is deactivated by default.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58870-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58870-128">See Also</span></span>  
 <span data-ttu-id="58870-129">[SharePoint에서 보고서 서버 활성화 및 통합 기능 파워 뷰](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="58870-129">[Activate the Report Server and Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span></span>  
 <span data-ttu-id="58870-130">[SharePoint 모드&#40;사이트 설정 및 사이트 기능을 Reporting Services&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="58870-130">[Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md) </span></span>  
 [<span data-ttu-id="58870-131">SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="58870-131">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  