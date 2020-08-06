---
title: URL 구성(SSRS 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], syntax
ms.assetid: 851e163a-ad2a-491e-bc1e-4df92327092f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bebded7acc39c3cf98a082130594a4712068620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741559"
---
# <a name="configure-a-url--ssrs-configuration-manager"></a><span data-ttu-id="6c70c-102">URL 구성(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="6c70c-102">Configure a URL  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="6c70c-103">보고서 관리자 또는 보고서 서버 웹 서비스를 사용하려면 먼저 각 애플리케이션에 대한 URL을 한 개 이상 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-103">Before you can use Report Manager or the Report Server Web service, you must configure at least one URL for each application.</span></span> <span data-ttu-id="6c70c-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 "파일만" 모드(즉, 설치 마법사의 보고서 서버 설치 옵션 페이지에서 **서버 구성 없이 설치** 옵션을 선택한 경우)에서 설치한 경우에는 URL을 반드시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-104">Configuring the URLs is mandatory if you installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in "files-only" mode (that is, by selecting the **Install but do not configure the server** option on the Report Server Installation Options page in the Installation Wizard).</span></span> <span data-ttu-id="6c70c-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 기본 구성으로 설치한 경우 각 애플리케이션에 대해 URL이 이미 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-105">If you installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the default configuration, URLs are already configured for each application.</span></span> <span data-ttu-id="6c70c-106">보고서 서버가 SharePoint 통합 모드를 사용하도록 구성되어 있고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 보고서 서버 웹 서비스 URL을 업데이트하는 경우 SharePoint 중앙 관리에서도 URL을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-106">If you have a report server that is configured to use SharePoint Integrated mode and you update the Report Server Web Service URL by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, you must also update the URL in SharePoint Central Administration.</span></span>  
  
 <span data-ttu-id="6c70c-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하면 URL을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-107">Use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the URLs.</span></span> <span data-ttu-id="6c70c-108">URL의 모든 부분이 이 도구에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-108">All parts of the URL are defined in this tool.</span></span> <span data-ttu-id="6c70c-109">이전 릴리스와는 달리 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 이상 버전에서는 IIS(인터넷 정보 서비스) 웹 사이트에서 더 이상 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 애플리케이션에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-109">Unlike earlier releases, Internet Information Services (IIS) Web sites no longer provide access to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6c70c-110">는 다른 웹 서비스와 애플리케이션을 함께 배포하는 경우를 비롯한 대부분의 배포 시나리오에서 잘 작동하는 기본값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-110">provides default values that work well in most deployment scenarios, including side-by-side deployments with other Web services and applications.</span></span> <span data-ttu-id="6c70c-111">기본 URL은 인스턴스 이름을 통합함으로써 같은 컴퓨터에서 보고서 서버 인스턴스를 여러 개 실행하는 경우 URL이 충돌할 위험을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-111">Default URLs incorporate instance names, minimizing the risk of URL conflicts if you run multiple report server instances on the same computer.</span></span>  
  
 <span data-ttu-id="6c70c-112">이 항목에서는 다음 태스크에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-112">This topic provides instructions for the following tasks:</span></span>  
  
-   <span data-ttu-id="6c70c-113">보고서 서버 웹 서비스 URL 만들기</span><span class="sxs-lookup"><span data-stu-id="6c70c-113">Create a URL for the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="6c70c-114">보고서 관리자 URL 만들기</span><span class="sxs-lookup"><span data-stu-id="6c70c-114">Create a URL for Report Manager.</span></span>  
  
-   <span data-ttu-id="6c70c-115">추가 URL을 정의하는 고급 URL 속성 설정</span><span class="sxs-lookup"><span data-stu-id="6c70c-115">Set advanced URL properties to define additional URLs.</span></span>  
  
 <span data-ttu-id="6c70c-116">Url을 저장 하 고 유지 관리 하는 방법에 대 한 자세한 내용 및 상호 운용성 문제에 대 한 자세한 내용은 온라인 설명서의 [Url 예약 및 등록 &#40;ssrs Configuration Manager&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md) 및 [설치 Reporting Services 및 인터넷 정보 서비스 함께 ssrs 기본 모드 ](install-reporting-and-internet-information-services-side-by-side.md)&#40;을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6c70c-116">For more information about how URLs are stored and maintained or interoperability issues, see [About URL Reservations and Registration  &#40;SSRS Configuration Manager&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md) and [Install Reporting Services and Internet Information Services Side-by-Side &#40;SSRS Native Mode&#41;](install-reporting-and-internet-information-services-side-by-side.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="6c70c-117">Reporting Services 설치에 자주 사용되는 URL에 대한 예를 검토하려면 이 항목에 포함된 [URL 예](#URLExamples) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-117">To review examples of URLs often used in a Reporting Services installation, see [Examples of URLs](#URLExamples) in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c70c-118">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6c70c-118">Prerequisites</span></span>  
 <span data-ttu-id="6c70c-119">URL을 만들거나 수정하기 전에 다음 사항을 유념하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-119">Before you create or modify a URL, remember the following points:</span></span>  
  
-   <span data-ttu-id="6c70c-120">보고서 서버 컴퓨터에서 로컬 관리자 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-120">You must be a member of the local Administrators group on the report server computer.</span></span>  
  
-   <span data-ttu-id="6c70c-121">IIS 6.0 또는 7.0이 같은 컴퓨터에 설치되어 있는 경우 포트 80을 사용하는 웹 사이트의 가상 디렉터리 이름을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-121">If IIS 6.0 or 7.0 is installed on the same computer, check the names of virtual directories on any Web site that uses port 80.</span></span> <span data-ttu-id="6c70c-122">기본 Reporting Services 가상 디렉터리 이름("Reports" 및 "ReportServer")을 사용하는 가상 디렉터리가 존재하는 경우 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL에 대해 다른 가상 디렉터리 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-122">If you see any virtual directories that use the default Reporting Services virtual directory names (that is, "Reports" and "ReportServer"), choose different virtual directory names for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs that you configure.</span></span>  
  
-   <span data-ttu-id="6c70c-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 URL을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-123">You must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the URL.</span></span> <span data-ttu-id="6c70c-124">시스템 유틸리티를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-124">Do not use a system utility.</span></span> <span data-ttu-id="6c70c-125">RSReportServer.config 파일의 `URLReservations` 섹션에서 URL 예약을 직접 수정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-125">Never modify URL reservations in the `URLReservations` section of the RSReportServer.config file directly.</span></span> <span data-ttu-id="6c70c-126">내부에 저장된 기본 URL 예약을 업데이트하고 RSReportServer.config 파일에 저장된 URL 설정을 동기화하려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-126">Using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool is necessary to update both the underlying URL reservation that is stored internally and synchronize the URL settings stored in the RSReportServer.config file.</span></span>  
  
-   <span data-ttu-id="6c70c-127">보고서 작업이 적은 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-127">Choose a time that has low report activity.</span></span> <span data-ttu-id="6c70c-128">URL 예약이 변경될 때마다 보고서 서버 웹 서비스 및 보고서 관리자에 대한 애플리케이션 도메인이 재활용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-128">Each time the URL reservation changes, you can expect that the application domains for Report Server Web service and Report Manager might be recycled.</span></span>  
  
-   <span data-ttu-id="6c70c-129">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 URL 생성 및 사용에 대한 개요는 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](configure-report-server-urls-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c70c-129">For an overview of URL construction and usage in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).</span></span>  
  
### <a name="to-configure-a-url-for-the-report-server-web-service"></a><span data-ttu-id="6c70c-130">보고서 서버 웹 서비스 URL을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6c70c-130">To configure a URL for the Report Server Web service</span></span>  
  
1.  <span data-ttu-id="6c70c-131">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 다음 로컬 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-131">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to a local report server instance.</span></span>  
  
2.  <span data-ttu-id="6c70c-132">**웹 서비스 URL**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-132">Click **Web Service URL**.</span></span>  
  
3.  <span data-ttu-id="6c70c-133">가상 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-133">Specify the virtual directory.</span></span> <span data-ttu-id="6c70c-134">가상 디렉터리 이름으로 요청을 수신할 애플리케이션을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-134">The virtual directory name identifies which application receives the request.</span></span> <span data-ttu-id="6c70c-135">IP 주소와 포트는 여러 애플리케이션에서 공유할 수 있으므로 가상 디렉터리 이름이 요청을 수신할 애플리케이션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-135">Because an IP address and port can be shared by multiple applications, the virtual directory name specifies which application receives the request.</span></span>  
  
     <span data-ttu-id="6c70c-136">요청이 원하는 대상에 도달하게 하려면 이 값이 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-136">This value must be unique to ensure that the request reaches its intended destination.</span></span> <span data-ttu-id="6c70c-137">이 값은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-137">This value is required.</span></span> <span data-ttu-id="6c70c-138">대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-138">It is case-insensitive.</span></span> <span data-ttu-id="6c70c-139">가상 디렉터리 이름과 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 애플리케이션의 인스턴스는 일 대 일 대응됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-139">There is a one-to-one correspondence between a virtual directory name and an instance of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application.</span></span> <span data-ttu-id="6c70c-140">같은 애플리케이션 인스턴스에 대한 URL을 여러 개 만든 경우 이 애플리케이션 인스턴스에 대해 정의한 모든 URL에 같은 가상 디렉터리 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-140">If you create multiple URLs to the same application instance, you must use the same virtual directory name in all of the URLs you define for this application instance.</span></span>  
  
     <span data-ttu-id="6c70c-141">보고서 서버 웹 서비스의 기본 가상 디렉터리 이름은 **ReportServer**입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-141">For the Report Server Web service, the default virtual directory name is **ReportServer**.</span></span>  
  
4.  <span data-ttu-id="6c70c-142">네트워크에서 보고서 서버 컴퓨터를 고유하게 식별하는 IP 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-142">Specify the IP address that uniquely identifies the report server computer on the network.</span></span> <span data-ttu-id="6c70c-143">호스트 헤더를 지정하거나 같은 애플리케이션 인스턴스에 대한 URL을 추가로 정의하려는 경우 **고급**을 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-143">If you want to specify a host header or define additional URLs for the same application instance, you must click **Advanced**.</span></span> <span data-ttu-id="6c70c-144">고급 URL 속성을 설정하는 방법은 이 항목의 뒷부분에 나오는 지침을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c70c-144">For instructions on how to set advanced properties on the URL, see the instructions later in this topic.</span></span> <span data-ttu-id="6c70c-145">또는 **웹 서비스 URL** 페이지에서 다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-145">Otherwise, use the **Web Service URL** page to select from the following values:</span></span>  
  
    -   <span data-ttu-id="6c70c-146">**모두 할당됨** - 컴퓨터에 할당된 모든 IP 주소를 보고서 서버 애플리케이션을 가리키는 URL에 사용할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-146">**All Assigned** specifies that any of the IP addresses that are assigned to the computer can be used in a URL that points to a report server application.</span></span> <span data-ttu-id="6c70c-147">또한 이 값은 도메인 이름 서버에서 확인할 수 있는 호스트 이름(예: 컴퓨터 이름)부터 컴퓨터에 할당된 IP 주소까지 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-147">This value also encompasses friendly host names (such as computer names) that can be resolved by a domain name server to an IP address that is assigned to the computer.</span></span> <span data-ttu-id="6c70c-148">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL에 대한 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-148">This is the default value for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL.</span></span>  
  
    -   <span data-ttu-id="6c70c-149">**모두 할당되지 않음** - 다른 애플리케이션에서 처리하지 않은 모든 요청을 보고서 서버에서 수신하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-149">**All Unassigned** specifies that the report server will receive any request that has not been handled by another application.</span></span> <span data-ttu-id="6c70c-150">이 옵션은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-150">We recommend that you avoid this option.</span></span> <span data-ttu-id="6c70c-151">이 옵션을 선택하면 보다 강력한 URL 예약을 사용하는 다른 애플리케이션이 보고서 서버에서 처리해야 할 요청을 가로챌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-151">If you select this option, it becomes possible for another application that has a stronger URL reservation to intercept requests intended for the report server.</span></span>  
  
    -   <span data-ttu-id="6c70c-152">**127.0.0.1** - localhost 액세스에 사용되는 IPv4 주소로서</span><span class="sxs-lookup"><span data-stu-id="6c70c-152">**127.0.0.1** is the IPv4 address used to access to localhost.</span></span> <span data-ttu-id="6c70c-153">보고서 서버 컴퓨터에 대한 로컬 관리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-153">It supports local administration on the report server computer.</span></span> <span data-ttu-id="6c70c-154">이 값만 선택할 경우 보고서 서버 컴퓨터에 로컬로 로그온한 사용자만 애플리케이션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-154">If you select only this value, only users who are logged on locally to the report server computer will have access to the application.</span></span>  
  
    -   <span data-ttu-id="6c70c-155">**::1** - IPv6 형식의 루프백 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-155">**::1** is the loopback address in IPv6 format.</span></span>  
  
    -   <span data-ttu-id="6c70c-156">특정 IP 주소가 이 목록에 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-156">Specific IP addresses also appear in this list.</span></span> <span data-ttu-id="6c70c-157">IP 주소는 IPv4 및 IPv6 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-157">IP addresses can be in IPv4 and IPv6 formats.</span></span> <span data-ttu-id="6c70c-158">*Nnn.nnn.nnn.nnn* 는 컴퓨터에 설치된 네트워크 어댑터 카드의 32비트 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-158">*Nnn.nnn.nnn.nnn* is the 32-bit IPv4 address of a network adapter card on your computer.</span></span> <span data-ttu-id="6c70c-159">IPv6 주소는 128 비트 이며 8 개의 4 바이트 필드가 콜론: \<prefix> :*nnnn: nnnn: nnnn: nnnn* : nnnn: nnnn으로 구분 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-159">IPv6 addresses are 128-bit, with eight 4-byte fields separated by colons: \<prefix>:*nnnn:nnnn:nnnn:nnnn:nnnn:nnnn*</span></span>  
  
         <span data-ttu-id="6c70c-160">카드가 여러 개 있거나 네트워크에서 IPv4와 IPv6 주소를 모두 지원하는 경우 IP 주소가 여러 개 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-160">If you have multiple cards or if your network supports both IPv4 and IPv6 addresses, you will see multiple IP addresses.</span></span> <span data-ttu-id="6c70c-161">IP 주소를 한 개만 선택할 경우 선택한 IP 주소(및 도메인 이름 서버가 이 IP 주소에 매핑한 호스트 이름)만 애플리케이션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-161">If you select only one IP address, it will limit application access to the just the IP address (and any host name that a domain name server maps to that address).</span></span> <span data-ttu-id="6c70c-162">localhost를 사용하여 보고서 서버에 액세스할 수 없으며, 보고서 서버 컴퓨터에 설치된 다른 네트워크 어댑터 카드의 IP 주소를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-162">You cannot use localhost to access a report server, and you cannot use the IP addresses of other network adapter cards that are installed on the report server computer.</span></span> <span data-ttu-id="6c70c-163">일반적으로 이 값을 선택하는 경우는 명시적 IP 주소 또는 호스트 이름도 지정하는 URL 예약을 여러 개 구성하고 있기 때문입니다. 예를 들면 한 개는 인트라넷 연결에 사용되는 네트워크 어댑터 카드용으로, 다른 한 개는 익스트라넷 연결에 사용되는 네트워크 어댑터 카드용으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-163">Typically, if you select this value, it is because you are configuring multiple URL reservations that also specify explicit IP addresses or host names (for example, one for a network adapter card used for intranet connections and a second one used for extranet connections).</span></span>  
  
5.  <span data-ttu-id="6c70c-164">포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-164">Specify the port.</span></span> <span data-ttu-id="6c70c-165">포트 80은 다른 애플리케이션과 공유할 수 있기 때문에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 및 Windows Server 2008에서 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] 에 대한 기본 포트는 포트 80입니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-165">Port 80 is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] and Windows Server 2008 because it can be shared with other applications.</span></span> <span data-ttu-id="6c70c-166">사용자 지정 포트 번호를 사용하려는 경우에는 보고서 서버에 액세스할 때 사용되는 URL에 항상 포트 번호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-166">If you want to use a custom port number, remember that you will have to always specify it in the URL used to access the report server.</span></span> <span data-ttu-id="6c70c-167">사용 가능한 포트를 찾을 때 사용할 수 있는 기술은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-167">You can use the following techniques to find an available port:</span></span>  
  
    -   <span data-ttu-id="6c70c-168">명령 프롬프트에서 사용 중인 TCP 포트를 반환하는 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-168">From a command prompt, type the following command to return a list of TCP ports that are being used:</span></span>  
  
         `netstat -a -n -p tcp`  
  
    -   <span data-ttu-id="6c70c-169">Microsoft 고객 지원 문서 [TCP/IP 포트 할당에 대한 정보](https://support.microsoft.com/kb/174904)에서 TCP 포트 할당 및 잘 알려진 포트(0 - 1023), 등록된 포트(1024 - 49151), 동적 또는 프라이빗 포트(49152 - 65535) 간의 차이를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-169">Review the Microsoft Support article, [Information about TCP/IP port assignments](https://support.microsoft.com/kb/174904), to read about TCP port assignments and the differences between Well Known Ports (0 through 1023), Registered Ports (1024 through 49151), and Dynamic or Private Ports (49152 through 65535).</span></span>  
  
    -   <span data-ttu-id="6c70c-170">Windows 방화벽을 사용하고 있는 경우 포트를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-170">If you are using Windows Firewall, you must open the port.</span></span> <span data-ttu-id="6c70c-171">자세한 내용은 [Configure a Firewall for Report Server Access](../report-server/configure-a-firewall-for-report-server-access.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c70c-171">For instructions, see [Configure a Firewall for Report Server Access](../report-server/configure-a-firewall-for-report-server-access.md).</span></span>  
  
6.  <span data-ttu-id="6c70c-172">아직 확인하지 않은 경우 사용하려는 이름과 동일한 가상 디렉터리 이름을 IIS(설치된 경우)에서 사용하고 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-172">If you have not done so already, verify that IIS (if it is installed) does not have virtual directory with the same name you plan to use.</span></span>  
  
7.  <span data-ttu-id="6c70c-173">SSL 인증서를 설치한 경우 지금 이 인증서를 선택하여 컴퓨터에 설치된 SSL 인증서에 URL을 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-173">If you installed an SSL certificate, you can select it now to bind the URL to the SSL certificate that is installed on your computer.</span></span>  
  
8.  <span data-ttu-id="6c70c-174">SSL 인증서를 선택하면 선택적으로 사용자 지정 포트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-174">Optionally, if you select an SSL certificate, you can specify a custom port.</span></span> <span data-ttu-id="6c70c-175">기본 포트는 443이지만 사용 가능한 포트라면 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-175">The default is 443 but you can use any port that is available.</span></span>  
  
9. <span data-ttu-id="6c70c-176">**적용** 을 클릭하여 URL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-176">Click **Apply** to create the URL.</span></span>  
  
10. <span data-ttu-id="6c70c-177">페이지의 **URL** 섹션에 있는 링크를 클릭하여 URL을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-177">Test the URL by clicking the link in the **URLs** section of page.</span></span> <span data-ttu-id="6c70c-178">URL을 테스트하려면 먼저 보고서 서버 데이터베이스를 만들어 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-178">Note that the report server database must be created and configured before you can test the URL.</span></span> <span data-ttu-id="6c70c-179">자세한 내용은 [기본 모드 보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;](ssrs-report-server-create-a-native-mode-report-server-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c70c-179">For instructions, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
11. <span data-ttu-id="6c70c-180">또한 보고서 서버가 SharePoint 통합 모드를 사용하도록 구성된 경우 SharePoint 중앙 관리에서 보고서 서버 웹 서비스 URL을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-180">Additionally, if your report server is configured to use SharePoint Integrated mode, configure the Report Server Web service URL in SharePoint Central Administration.</span></span> <span data-ttu-id="6c70c-181">SharePoint 중앙 관리에서 보고서 서버 웹 서비스 URL을 업데이트 하는 방법에 대 한 자세한 내용은 sharepoint 모드 [&#41;Reporting Services 보고서 서버의 구성 및 관리 &#40;](../configure-administer-report-server-reporting-services-sharepoint-mode.md) 하 고 [보고서 서버 &#40;sharepoint 모드&#41;를 Reporting Services ](../reporting-services-report-server-sharepoint-mode.md).</span><span class="sxs-lookup"><span data-stu-id="6c70c-181">For more information about how to update the Report Server Web service URL in SharePoint Central Administration, see [Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../reporting-services-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-create-a-url-reservation-for-report-manager"></a><span data-ttu-id="6c70c-182">보고서 관리자에 대한 URL 예약을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6c70c-182">To create a URL reservation for Report Manager</span></span>  
  
1.  <span data-ttu-id="6c70c-183">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 다음 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-183">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance.</span></span>  
  
2.  <span data-ttu-id="6c70c-184">**보고서 관리자 URL**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-184">Click **Report Manager URL**.</span></span>  
  
3.  <span data-ttu-id="6c70c-185">가상 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-185">Specify the virtual directory.</span></span> <span data-ttu-id="6c70c-186">보고서 관리자는 보고서 서버 웹 서비스와 동일한 IP 주소와 포트를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-186">Report Manager listens on the same IP address and port as the Report Server Web service.</span></span> <span data-ttu-id="6c70c-187">다른 보고서 서버 웹 서비스를 가리키도록 보고서 관리자를 구성한 경우 RSReportServer.config 파일에서 보고서 관리자 URL 설정을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-187">If you configured Report Manager to point to a different Report Server Web service, you must modify the Report Manager URL settings in the RSReportServer.config file.</span></span> <span data-ttu-id="6c70c-188">지침은 온라인 설명서의 [&#41;보고서 관리자 &#40;기본 모드 구성](../report-server/configure-web-portal.md) 을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6c70c-188">For instructions, see [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="6c70c-189">SSL 인증서를 설치한 경우 지금 이 인증서를 선택하여 보고서 관리자에 대한 모든 요청이 HTTPS를 통해 라우팅되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-189">If you installed an SSL certificate, you can select it to require that all requests to Report Manager are routed over HTTPS.</span></span>  
  
     <span data-ttu-id="6c70c-190">SSL 인증서를 선택하면 선택적으로 사용자 지정 포트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-190">Optionally, if you select an SSL certificate, you can specify a custom port.</span></span> <span data-ttu-id="6c70c-191">기본 포트는 443이지만 사용 가능한 포트라면 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-191">The default is 443 but you can use any port that is available.</span></span>  
  
5.  <span data-ttu-id="6c70c-192">**적용** 을 클릭하여 URL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-192">Click **Apply** to create the URL.</span></span>  
  
6.  <span data-ttu-id="6c70c-193">페이지의 **URL** 섹션에 있는 링크를 클릭하여 URL을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-193">Test the URL by clicking the link in the **URLs** section of page.</span></span>  
  
## <a name="setting-advanced-properties-to-specify-additional-urls"></a><span data-ttu-id="6c70c-194">추가 URL을 지정하는 고급 속성 설정</span><span class="sxs-lookup"><span data-stu-id="6c70c-194">Setting Advanced Properties to Specify Additional URLs</span></span>  
 <span data-ttu-id="6c70c-195">포트 또는 호스트 이름(도메인 이름 서버가 컴퓨터에 할당된 IP 주소로 확인할 수 있는 호스트 헤더 이름 또는 IP 주소)을 여러 개 지정하여 보고서 서버 웹 서비스 또는 보고서 관리자에 대한 URL을 여러 개 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-195">You can reserve multiple URLs for the Report Server Web service or Report Manager by specifying different ports or host names (either an IP address or a host header name that a domain name server can resolve to an IP address assigned to the computer).</span></span> <span data-ttu-id="6c70c-196">URL을 여러 개 만들면 같은 보고서 서버 인스턴스에 대해 서로 다른 액세스 경로를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-196">By creating multiple URLs, you can set up different access paths to the same report server instance.</span></span> <span data-ttu-id="6c70c-197">예를 들어 보고서 서버에 대한 인트라넷 및 익스트라넷 액세스가 사용 가능하도록 하기 위해 다음과 같이 인트라넷을 통한 액세스에 대해서는 기본 URL을 사용하고 익스트라넷 액세스에 대해서는 정규화된 추가 호스트 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-197">For example, to enable intranet and extranet access to a report server, you might use the default URL for access across the intranet, and an additional fully qualified host name for extranet access:</span></span>  
  
-   `http://myserver01/reportserver`
  
-   `http://www.adventure-works.com/reportserver`  
  
 <span data-ttu-id="6c70c-198">같은 애플리케이션 인스턴스에 대해서는 가상 디렉터리 이름을 여러 개 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-198">You cannot set multiple virtual directory names for the same application instance.</span></span> <span data-ttu-id="6c70c-199">각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 애플리케이션 인스턴스는 한 개의 가상 디렉터리 이름에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-199">Each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application instance is mapped to a single virtual directory name.</span></span> <span data-ttu-id="6c70c-200">같은 컴퓨터에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스가 여러 개 있는 경우 각 요청이 원하는 대상에 도달하게 하려면 애플리케이션에 대한 가상 디렉터리 이름에 인스턴스 이름이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-200">If you have multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer, the virtual directory name for an application should include the instance name to ensure that each request reaches its intended target.</span></span>  
  
#### <a name="to-set-advanced-properties-on-a-url"></a><span data-ttu-id="6c70c-201">고급 URL 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="6c70c-201">To set advanced properties on a URL</span></span>  
  
1.  <span data-ttu-id="6c70c-202">**웹 서비스 URL** 또는 **보고서 관리자 URL** 페이지에서 **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-202">On either the **Web Service URL** or **Report Manager URL** page, click **Advanced**.</span></span>  
  
2.  <span data-ttu-id="6c70c-203">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-203">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="6c70c-204">IP 주소 또는 호스트 헤더 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-204">Click IP Address or Host Header Name.</span></span> <span data-ttu-id="6c70c-205">호스트 헤더를 지정한 경우 DNS 서비스가 확인할 수 있는 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-205">If you specify a host header, be sure to specify a name that the DNS service can resolve.</span></span> <span data-ttu-id="6c70c-206">공용으로 사용 가능한 도메인 이름을 지정한 경우 http://www를 포함한 전체 URL을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-206">If you are specifying publicly available domain name, include the whole URL, including http://www.</span></span>  
  
4.  <span data-ttu-id="6c70c-207">포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-207">Specify the port.</span></span> <span data-ttu-id="6c70c-208">사용자 지정 포트를 지정한 경우 애플리케이션 URL에 항상 포트 번호가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-208">If you specify a custom port, the URL to the application must always include the port number.</span></span>  
  
5.  <span data-ttu-id="6c70c-209">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-209">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6c70c-210">브라우저 창을 열고 URL을 입력하여 URL을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-210">Test the URL by opening a browser window and entering the URL.</span></span>  
  
## <a name="urls-for-multiple-report-server-instances-on-the-same-computer"></a><span data-ttu-id="6c70c-211">같은 컴퓨터에 있는 여러 보고서 서버 인스턴스에 대한 URL</span><span class="sxs-lookup"><span data-stu-id="6c70c-211">URLs for Multiple Report Server Instances on the Same Computer</span></span>  
 <span data-ttu-id="6c70c-212">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 여러 인스턴스에 대한 URL을 예약할 경우 이름이 충돌하지 않도록 다음 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-212">If you are reserving URLs for multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you should follow naming conventions so that you can avoid naming conflicts.</span></span> <span data-ttu-id="6c70c-213">자세한 내용은 [다중 인스턴스 보고서 서버 배포를 위한 URL 예약&#40;SSRS 구성 관리자&#41;](url-reservations-for-multi-instance-report-server-deployments.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c70c-213">For more information, see [URL Reservations for Multi-Instance Report Server Deployments  &#40;SSRS Configuration Manager&#41;](url-reservations-for-multi-instance-report-server-deployments.md).</span></span>  
  
##  <a name="examples-of-url-configurations"></a><a name="URLExamples"></a> <span data-ttu-id="6c70c-214">URL 구성 예</span><span class="sxs-lookup"><span data-stu-id="6c70c-214">Examples of URL Configurations</span></span>  
 <span data-ttu-id="6c70c-215">다음 목록에서는 보고서 서버 URL의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-215">The following list shows some examples of what a report server URL might resemble:</span></span>  
  
-   http://localhost/reportserver  
  
-   http://localhost/reportserver_SQLEXPRESS  
  
-   http://sales01/reportserver  
  
-   http://sales01:8080/reportserver  
  
-   `https://sales.adventure-works.com/reportserver`  
  
-   `https://www.adventure-works.com:8080/reportserver01`  
  
 <span data-ttu-id="6c70c-216">보고서 관리자에 액세스하는 데 사용하는 URL은 비슷한 형식으로 구성되며 일반적으로 보고서 서버를 호스팅하는 동일한 웹 사이트에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-216">URLs that you use to access Report Manager share a similar format and are typically created under the same Web site that hosts the report server.</span></span> <span data-ttu-id="6c70c-217">가상 디렉터리 이름만 다릅니다. 이 경우에는 **reports** 이지만 원하는 이름으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c70c-217">The only difference is the virtual directory name (in this case, it is **reports** but you can configure it to use whatever name that you want):</span></span>  
  
-   http://localhost/reports  
  
-   http://localhost/reports_SQLEXPRESS  
  
-   http://sales01/reports  
  
-   http://sales01:8080/reports  
  
-   `https://sales.adventure-works.com/reports`  
  
-   `https://www.adventure-works.com:8080/reports`  
  
## <a name="see-also"></a><span data-ttu-id="6c70c-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c70c-218">See Also</span></span>  
 <span data-ttu-id="6c70c-219">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="6c70c-219">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 [<span data-ttu-id="6c70c-220">보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="6c70c-220">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](configure-report-server-urls-ssrs-configuration-manager.md)  
  
  