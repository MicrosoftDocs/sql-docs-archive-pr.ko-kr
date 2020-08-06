---
title: 보고서 관리자 (보고서 작성기 및 SSRS)에서 보고서 찾기 및 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8556807e-f2e2-4a7b-bb1b-ac5ea1872e51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c0cd78793dd03034fed4bf36296716bf99730e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739448"
---
# <a name="finding-and-viewing-reports-in-report-manager-report-builder-and-ssrs"></a><span data-ttu-id="0d8ef-102">보고서 관리자에서 보고서 찾기 및 보기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0d8ef-102">Finding and Viewing Reports in Report Manager (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0d8ef-103">보고서 관리자는 보고서 보기 및 관리 기능을 제공하는 웹 기반 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-103">Report Manager is a Web-based tool that includes features for viewing and managing reports.</span></span> <span data-ttu-id="0d8ef-104">이 도구는 보고서 서버를 설치할 때 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-104">It is part of a report server installation.</span></span> <span data-ttu-id="0d8ef-105">보고서 관리자를 열려면 브라우저 창에 보고서 관리자 URL을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-105">To open Report Manager, type the Report Manager URL in a browser window.</span></span> <span data-ttu-id="0d8ef-106">브라우저 요구 사항에 대 한 자세한 내용은 [Reporting Services 계획 및 파워 뷰 브라우저 지원 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-106">For information on browser requirements, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span> <span data-ttu-id="0d8ef-107">보고서 서버에서 보고서 관리자 URL을 구성하는 방법에 대한 자세한 내용은 시스템 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-107">For more information about how a Report Manager URL might be configured on your report server, contact your system administrator.</span></span> <span data-ttu-id="0d8ef-108">자세한 내용은 [보고서 관리자 구성&#40;기본 모드&#41;](../report-server/configure-web-portal.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-108">For more information, see [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md).</span></span>  
  
 <span data-ttu-id="0d8ef-109">시스템 관리자가 보고서 서버에서 설정한 사용 권한에 따라 사용자가 보고서 관리자를 사용할 때 표시되는 기능이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-109">The permissions that the system administrator set on the report server determine what you can see when you use Report Manager.</span></span> <span data-ttu-id="0d8ef-110">사용 권한은 역할 할당을 통해 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-110">Permissions are granted via a role assignment.</span></span> <span data-ttu-id="0d8ef-111">보고서를 찾고 볼 수 있으려면 역할 할당에 보고서 보기 태스크가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-111">To find and view reports, your role assignment must include the View Reports task.</span></span> <span data-ttu-id="0d8ef-112">보고서 서버에서 보고서를 찾으려면 이름 또는 설명을 기준으로 보고서를 검색하거나 보고서 서버 폴더를 탐색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-112">To find a report on a report server, search for it by name or description, or browse report server folders.</span></span> <span data-ttu-id="0d8ef-113">보고서 서버에 게시 또는 업로드된 보고서만 검색하거나 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-113">You can only search or browse for reports that have been published or uploaded to the report server.</span></span> <span data-ttu-id="0d8ef-114">보고서를 검색하는 방법에 대한 자세한 내용은 [보고서 및 기타 항목 검색&#40;보고서 작성기 및 SSRS&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-114">For more information about how to search for a report, see [Searching for Reports and Other Items &#40;Report Builder  and SSRS&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-the-folder-hierarchy-in-report-manager"></a><span data-ttu-id="0d8ef-115">보고서 관리자에서 폴더 계층 구조 탐색</span><span class="sxs-lookup"><span data-stu-id="0d8ef-115">Navigating the Folder Hierarchy in Report Manager</span></span>  
 <span data-ttu-id="0d8ef-116">보고서 관리자를 시작하고 폴더 계층 구조에서 임의의 폴더를 열 때 자동으로 표시되는 홈 페이지를 사용하면 실행할 보고서를 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-116">To browse for the reports that you want to run, you can use the Home page, which appears automatically when you start Report Manager and when you open any folder in the folder hierarchy.</span></span> <span data-ttu-id="0d8ef-117">홈 페이지에는 사용자가 보기 권한을 갖고 있는 항목만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-117">The Home page shows only the items that you have permission to view.</span></span> <span data-ttu-id="0d8ef-118">폴더 경로는 홈 페이지 위쪽에 링크 행으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-118">The folder path is displayed as a row of links at the top of the Home page.</span></span> <span data-ttu-id="0d8ef-119">폴더 이름은 루트 폴더(홈)부터 순서대로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-119">Folder names are listed in sequence, starting with the root folder (Home).</span></span> <span data-ttu-id="0d8ef-120">추가 폴더를 열 때마다 해당 폴더 이름이 페이지 위쪽의 폴더 경로에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-120">As you open each additional folder, the folder name is added to the folder path at the top of the page.</span></span> <span data-ttu-id="0d8ef-121">아래 이미지의 **(1)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-121">**(1)** in the image below.</span></span> <span data-ttu-id="0d8ef-122">또한 보고서를 열면 해당 보고서 이름이 폴더 경로에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-122">When you open a report, the name of the report is also added to the folder path.</span></span>  
  
 <span data-ttu-id="0d8ef-123">![보고서 관리자 리본 및 탐색](../media/rs-reportmanager-ribbon.gif "보고서 관리자 리본 및 탐색")</span><span class="sxs-lookup"><span data-stu-id="0d8ef-123">![Report Manager Ribbon and Navigation](../media/rs-reportmanager-ribbon.gif "Report Manager Ribbon and Navigation")</span></span>  
<span data-ttu-id="0d8ef-124">보고서 관리자 리본</span><span class="sxs-lookup"><span data-stu-id="0d8ef-124">Report Manager Ribbon</span></span>  
  
 <span data-ttu-id="0d8ef-125">다음과 같은 방법으로 폴더 계층을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-125">Use the following techniques to navigate through a folder hierarchy:</span></span>  
  
-   <span data-ttu-id="0d8ef-126">폴더의 내용을 보려면 홈 페이지에서 폴더 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-126">To view the contents of a folder, click the folder name on the Home page.</span></span> <span data-ttu-id="0d8ef-127">폴더 페이지가 열리고 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-127">A folder page opens, displaying the contents of the folder.</span></span>  
  
-   <span data-ttu-id="0d8ef-128">폴더 계층에서 하위 수준을 탐색하려면 현재 폴더의 하위 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-128">To navigate down through the folder hierarchy, open a subfolder of the current folder.</span></span> <span data-ttu-id="0d8ef-129">폴더에는 보고서, 리소스, 공유 데이터 원본 항목 및 기타 폴더가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-129">Folders contain reports, resources, shared data source items, and other folders.</span></span> <span data-ttu-id="0d8ef-130">폴더 아이콘을 클릭하면 폴더가 열리고 한 수준 아래 계층의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-130">Clicking a folder icon opens the folder, showing the contents of the hierarchy one level down.</span></span>  
  
-   <span data-ttu-id="0d8ef-131">폴더 계층에서 상위 수준을 탐색하려면 페이지 위쪽의 링크 행에서 내용을 보려는 폴더 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-131">To navigate up through the folder hierarchy, in the row of links at the top of the page, click the name of the folder whose contents you want to see.</span></span> <span data-ttu-id="0d8ef-132">위 이미지의 **(1)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-132">**(1)** in the above image.</span></span>  
  
## <a name="opening-a-report"></a><span data-ttu-id="0d8ef-133">보고서 열기</span><span class="sxs-lookup"><span data-stu-id="0d8ef-133">Opening a Report</span></span>  
 <span data-ttu-id="0d8ef-134">보고서를 찾은 다음 보고서 이름을 클릭하면 해당 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-134">After you find a report, click the report name to open it.</span></span> <span data-ttu-id="0d8ef-135">보고서는 HTML로 렌더링되고 보고서 관리자의 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-135">The report is rendered in HTML and appears in the Contents page in Report Manager.</span></span> <span data-ttu-id="0d8ef-136">보고서는 항상 브라우저 세션에서 캐시되기 때문에 보고서를 연 경우 **뒤로** 단추를 클릭하여 보고서로 되돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-136">Reports are always cached by the browser session, so if you open a report, you can usually return to it by clicking the **Back** button.</span></span> <span data-ttu-id="0d8ef-137">보고서 실행을 위해 사용자 이름과 암호를 입력해야 하는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-137">This is true even if you were required to supply a user name and password to run the report.</span></span> <span data-ttu-id="0d8ef-138">렌더링된 보고서를 완전히 닫으려면 브라우저를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-138">You cannot fully close a rendered report until you close the browser.</span></span>  
  
 <span data-ttu-id="0d8ef-139">폴더 계층 구조에 표시되는 보고서 중 일부에는 곧바로 액세스하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-139">Not all reports that are visible in the folder hierarchy are immediately accessible.</span></span> <span data-ttu-id="0d8ef-140">보고서의 데이터 원본에 대한 액세스 권한이 있는지 확인하기 위해 사용자 이름과 암호를 입력해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-140">Some reports may prompt you for your user name and password to determine whether you can access the data source for the report.</span></span> <span data-ttu-id="0d8ef-141">보고서 관리자에서 보고서 열기에 대한 자세한 내용은 [보고서 열기 및 닫기&#40;보고서 관리자&#41;](../reports/open-and-close-a-report-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-141">For more information about opening reports in Report Manager, see [Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md).</span></span>  
  
 <span data-ttu-id="0d8ef-142">보고서 작성기에서 직접 보고서 서버의 보고서를 탐색하거나 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-142">You can also browse to and open a report from the report server directly from Report Builder.</span></span> <span data-ttu-id="0d8ef-143">자세한 내용은 [보고서 및 기타 항목 검색&#40;보고서 작성기 및 SSRS&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-143">For more information, see [Searching for Reports and Other Items &#40;Report Builder  and SSRS&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md).</span></span>  
  
## <a name="to-search-for-a-items"></a><span data-ttu-id="0d8ef-144">항목을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="0d8ef-144">To Search for a Items</span></span>  
  
-   <span data-ttu-id="0d8ef-145">보고서 관리자에서 항목을 검색하려면 페이지 위쪽의 **Search** 입력란에 검색 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-145">To search for items in Report Manager, type a search string in the **Search** text box at the top of the page.</span></span> <span data-ttu-id="0d8ef-146">위 이미지의 **(2)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-146">**(2)** in the above image.</span></span> <span data-ttu-id="0d8ef-147">검색은 폴더 계층의 최상위 노드에서 시작되어 모든 분기를 따라 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-147">Searches begin at the top node in the folder hierarchy and then proceed through every branch.</span></span> <span data-ttu-id="0d8ef-148">특정 분기에 대한 액세스 권한이 없는 경우 해당 분기는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-148">If you do not have permission to access a specific branch, that branch is skipped.</span></span> <span data-ttu-id="0d8ef-149">다른 사용자에게 속한 내 보고서 폴더와 일반적으로 사용할 수 없는 다른 폴더도 같은 방식으로 검색을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-149">This applies to My Reports folders that belong to other users, and to other folders that are not generally available.</span></span> <span data-ttu-id="0d8ef-150">보기 권한이 있는 보고서와 항목만 검색 결과에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-150">Only reports and items that you have permission to view are included in the search results.</span></span>  
  
-   <span data-ttu-id="0d8ef-151">이름이나 설명을 기준으로 항목을 검색하려면 검색할 텍스트 전부 또는 일부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-151">To search for an item by name or description, specify all or part of the text that you want to match.</span></span> <span data-ttu-id="0d8ef-152">검색 문자열은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-152">The search string is not case-sensitive.</span></span> <span data-ttu-id="0d8ef-153">검색 조건을 포함하거나 제외하기 위해 더하기(+) 또는 빼기(-) 기호와 같은 검색 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-153">You cannot use search operators such as plus (+) or minus (-) symbols to require or exclude search criteria.</span></span>  
  
-   <span data-ttu-id="0d8ef-154">보고서에서 특정 텍스트를 검색하려면 보고서 위쪽의 도구 모음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8ef-154">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8ef-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d8ef-155">See Also</span></span>  
 <span data-ttu-id="0d8ef-156">[보고서 작성기 및 SSRS &#40;보고서 및 기타 항목 검색&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0d8ef-156">[Searching for Reports and Other Items &#40;Report Builder  and SSRS&#41;](searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0d8ef-157">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0d8ef-157">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  