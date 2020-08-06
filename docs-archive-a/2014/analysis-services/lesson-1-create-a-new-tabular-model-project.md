---
title: '1 단원: 새 테이블 형식 모델 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8b18c18116d5a9dacdf49fe23f4f545bb3a0f987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740594"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a><span data-ttu-id="a7d48-102">1단원: 새 테이블 형식 모델 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="a7d48-102">Lesson 1: Create a New Tabular Model Project</span></span>
  <span data-ttu-id="a7d48-103">이 단원에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 새로운 빈 테이블 형식 모델 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-103">In this lesson, you will create a new, blank tabular model project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a7d48-104">새 프로젝트를 만든 후 테이블 가져오기 마법사를 사용하여 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-104">Once your new project is created, you can begin adding data by using the Table Import Wizard.</span></span> <span data-ttu-id="a7d48-105">이 단원에서는 새 프로젝트를 만들 뿐 아니라 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 테이블 형식 모델 제작 환경에 대해서도 간단히 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-105">In addition to creating a new project, this lesson also includes a brief introduction to the tabular model authoring environment in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="a7d48-106">다양한 유형의 테이블 형식 모델 프로젝트에 대한 자세한 내용은 [테이블 형식 모델 프로젝트&#40;SSAS 테이블 형식&#41;](tabular-models/tabular-model-projects-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d48-106">To learn more about the different types of tabular model projects, see [Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md).</span></span> <span data-ttu-id="a7d48-107">테이블 형식 모델 제작 환경에 대 한 자세한 내용은 [테이블 형식 모델 디자이너 &#40;SSAS 테이블 형식&#41;](tabular-model-designer-ssas-tabular.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d48-107">To learn more about the tabular model authoring environment, see [Tabular Model Designer &#40;SSAS Tabular&#41;](tabular-model-designer-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="a7d48-108">이 단원을 완료하기 위한 예상 시간: **10분**</span><span class="sxs-lookup"><span data-stu-id="a7d48-108">Estimated time to complete this lesson: **10 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7d48-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a7d48-109">Prerequisites</span></span>  
 <span data-ttu-id="a7d48-110">이 항목은 테이블 형식 모델 제작 자습서의 첫 번째 단원입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-110">This topic is the first lesson in a tabular model authoring tutorial.</span></span> <span data-ttu-id="a7d48-111">이 섹션을 완료하려면 SQL Server 인스턴스에 AdventureWorksDW 데이터베이스가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-111">To complete this lesson, you must have the AdventureWorksDW database installed on a SQL Server instance.</span></span> <span data-ttu-id="a7d48-112">자세한 내용은 [테이블 형식 모델링&#40;Adventure Works 자습서&#41;](tabular-modeling-adventure-works-tutorial.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d48-112">For more information, see [Tabular Modeling &#40;Adventure Works Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).</span></span>  
  
## <a name="create-a-new-tabular-model-project"></a><span data-ttu-id="a7d48-113">새 테이블 형식 모델 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="a7d48-113">Create a New Tabular Model Project</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project"></a><span data-ttu-id="a7d48-114">새 테이블 형식 모델 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a7d48-114">To create a new tabular model project</span></span>  
  
1.  <span data-ttu-id="a7d48-115">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="a7d48-116">**새 프로젝트** 대화 상자의 **설치 된 템플릿**에서 **비즈니스 인텔리전스**를 클릭 한 다음 **Analysis Services**를 클릭 하 고 **테이블 형식 프로젝트 Analysis Services**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-116">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, then click **Analysis Services**, and then click **Analysis Services Tabular Project**.</span></span>  
  
3.  <span data-ttu-id="a7d48-117">**이름**에를 입력 `AW Internet Sales Tabular Model` 하 고 프로젝트 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-117">In  **Name**, type `AW Internet Sales Tabular Model`, then specify a location for the project files.</span></span>  
  
     <span data-ttu-id="a7d48-118">기본적으로 **솔루션 이름**은 프로젝트 이름과 같게 되지만 다른 솔루션 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-118">By default, **Solution Name** will be the same as the project name; however, you can type a different solution name.</span></span>  
  
4.  <span data-ttu-id="a7d48-119">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-119">Click **OK**.</span></span>  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a><span data-ttu-id="a7d48-120">SQL Server Data Tools 테이블 형식 모델 제작 환경 이해</span><span class="sxs-lookup"><span data-stu-id="a7d48-120">Understanding the SQL Server Data Tools Tabular Model Authoring Environment</span></span>  
 <span data-ttu-id="a7d48-121">새 테이블 형식 모델 프로젝트를 만들었으므로 이제 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 이상)에서 테이블 형식 모델 제작 환경을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-121">Now that you've created a new tabular model project, let's take a moment to explore the tabular model authoring environment in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 or later).</span></span>  
  
 <span data-ttu-id="a7d48-122">프로젝트를 만들면 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-122">After your project is created, it opens in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="a7d48-123">모델 디자이너에 빈 모델이 표시되고 **솔루션 탐색기** 창에서 **Model.bim** 파일이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-123">An empty model will appear in the model designer and the **Model.bim** file will be selected in the **Solution Explorer** window.</span></span> <span data-ttu-id="a7d48-124">데이터를 추가하면 테이블과 열이 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-124">When you add data, tables and columns will appear in the designer.</span></span> <span data-ttu-id="a7d48-125">디자이너 (model.bim 탭이 있는 빈 창)가 표시 되지 않으면 **솔루션 탐색기**의에서 `AW Internet Sales Tabular Model` **model.bim** 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-125">If you don't see the designer (the empty window with the Model.bim tab), in **Solution Explorer**, under `AW Internet Sales Tabular Model`, double click the **Model.bim** file.</span></span>  
  
 <span data-ttu-id="a7d48-126">**속성** 창에서 기본 프로젝트 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-126">You can view the basic project properties in the **Properties** window.</span></span> <span data-ttu-id="a7d48-127">**솔루션 탐색기**에서를 클릭 `AW Internet Sales Tabular Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-127">In **Solution Explorer**, click `AW Internet Sales Tabular Model`.</span></span> <span data-ttu-id="a7d48-128">**속성** 창의 **프로젝트 파일**에 **AW Internet Sales Tabular Model.smproj**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-128">Notice in the **Properties** window, in **Project File**, you will see **AW Internet Sales Tabular Model.smproj**.</span></span> <span data-ttu-id="a7d48-129">이 이름은 프로젝트 파일 이름이며 프로젝트 파일 위치는 **프로젝트 폴더**에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-129">This is the project file name, and in **Project Folder**, you will see the project file location.</span></span>  
  
 <span data-ttu-id="a7d48-130">**솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 `AW Internet Sales Tabular Model` 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-130">In **Solution Explorer**, right-click the `AW Internet Sales Tabular Model` project, and then click **Properties**.</span></span> <span data-ttu-id="a7d48-131">**AW Internet Sales Tabular Model 속성 페이지** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-131">The **AW Internet Sales Tabular Model Property Pages** dialog box appears.</span></span> <span data-ttu-id="a7d48-132">다음은 고급 프로젝트 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-132">These are the advanced project properties.</span></span> <span data-ttu-id="a7d48-133">나중에 모델을 배포할 준비가 되었을 때 이러한 속성 중 일부를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-133">You will set some of these properties later when you are ready to deploy your model.</span></span>  
  
 <span data-ttu-id="a7d48-134">이제 모델 속성을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-134">Now, let's look at the model properties.</span></span> <span data-ttu-id="a7d48-135">**솔루션 탐색기**에서 **Model.bim**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-135">In **Solution Explorer**, click **Model.bim**.</span></span> <span data-ttu-id="a7d48-136">**속성** 창에 모델 속성이 표시되며 이 중 **DirectQuery 모드** 속성이 가장 중요한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-136">In the **Properties** window, you will now see the model properties, most important of which is the **DirectQuery Mode** property.</span></span> <span data-ttu-id="a7d48-137">이 속성은 모델이 메모리 내 모드(Off) 또는 DirectQuery 모드(On)로 배포되는지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-137">This property specifies whether or not the model is deployed in In-Memory mode (Off) or DirectQuery mode (On).</span></span> <span data-ttu-id="a7d48-138">이 자습서에서는 메모리 내 모드에서 모델을 제작하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-138">For this tutorial, you will author and deploy your model in In-Memory mode.</span></span>  
  
 <span data-ttu-id="a7d48-139">새 모델을 만들 때 특정 모델 속성은 데이터 모델링 설정에 따라 자동으로 설정됩니다. 데이터 모델링 설정은 도구\옵션 대화 상자에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-139">When you create a new model, certain model properties are set automatically according to the Data Modeling settings that can be specified in the Tools\Options dialog box.</span></span> <span data-ttu-id="a7d48-140">데이터 Backup, 작업 영역 보존 및 작업 영역 서버 속성은 작업 영역 데이터베이스가 백업되고 메모리 내 보존되며 빌드되는 방식과 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-140">Data Backup, Workspace Retention, and Workspace Server properties specify how and where the workspace database (your model authoring database) is backed up, retained in-memory, and built.</span></span> <span data-ttu-id="a7d48-141">필요한 경우 나중에 이러한 설정을 변경할 수 있지만 지금은 이러한 속성을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-141">You can change these settings later if necessary, but for now, just leave these properties as they are.</span></span>  
  
 <span data-ttu-id="a7d48-142">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]를 설치할 때 몇 가지 새 메뉴 항목이 Visual Studio 환경에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-142">When you installed [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], several new menu items were added to the Visual Studio environment.</span></span> <span data-ttu-id="a7d48-143">테이블 형식 모델 작성과 관련 된 새 메뉴 항목을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-143">Let's look at the new menu items that are specific to authoring tabular models.</span></span> <span data-ttu-id="a7d48-144">**모델** 메뉴를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-144">Click on the **Model** menu.</span></span> <span data-ttu-id="a7d48-145">이 메뉴에서는 테이블 가져오기 마법사를 시작하고, 기존 연결을 보거나 편집하고, 작업 영역 데이터를 새로 고치고, Excel에서 분석 기능을 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel에서 모델을 검색하고, 큐브 뷰와 역할을 만들고, 모델 뷰를 선택하고, 계산 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-145">From here, you can launch the Table Import Wizard, view and edit existing connections, refresh workspace data, browse your model in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel with the Analyze in Excel feature, create perspectives and roles, select the model view, and set calculation options.</span></span>  
  
 <span data-ttu-id="a7d48-146">**테이블** 메뉴를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-146">Click on the **Table** menu.</span></span> <span data-ttu-id="a7d48-147">이 메뉴에서 테이블 간 관계를 만들거나 관리하고, 날짜 테이블 설정을 만들고 관리하고 지정하고, 파티션을 만들고, 테이블 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-147">Here, you can create and manage relationships between tables, create and manage, specify date table settings, create partitions, and edit table properties.</span></span>  
  
 <span data-ttu-id="a7d48-148">**열** 메뉴를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-148">Click on the **Column** menu.</span></span> <span data-ttu-id="a7d48-149">이 메뉴에서 테이블에 열을 추가 및 삭제하고, 열을 고정하고, 정렬 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-149">Here, you can add and delete columns in a table, freeze columns, and specify sort order.</span></span> <span data-ttu-id="a7d48-150">자동 합계 기능을 사용하여 선택한 열에 대한 표준 집계 측정값을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-150">You can also use the AutoSum feature to create a standard aggregation measure for a selected column.</span></span> <span data-ttu-id="a7d48-151">다른 도구 모음 단추를 사용하면 자주 사용하는 기능과 명령에 빠르게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-151">Other toolbar buttons provide quick access to frequently used features and commands.</span></span>  
  
 <span data-ttu-id="a7d48-152">테이블 형식 모델 제작과 관련된 다양한 기능의 위치와 대화 상자를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="a7d48-152">Explore some of the dialogs and locations for various features specific to authoring tabular models.</span></span> <span data-ttu-id="a7d48-153">일부 항목은 아직 활성화되어 있지 않지만 테이블 형식 모델 제작 환경을 파악하는 데 도움이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d48-153">While some items will not yet be active, you can get a good idea of the tabular model authoring environment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7d48-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a7d48-154">Next Steps</span></span>  
 <span data-ttu-id="a7d48-155">이 자습서를 계속하려면 다음 단원인 [2단원: 데이터 추가](lesson-2-add-data.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d48-155">To continue this tutorial, go to the next lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
  