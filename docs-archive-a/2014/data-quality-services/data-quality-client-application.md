---
title: Data Quality Client 애플리케이션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 25d1547e-4113-4b34-a9f8-8897db1acf16
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6dd1038a14742103d7a774ff4632dd2ecf0e8f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647867"
---
# <a name="data-quality-client-application"></a><span data-ttu-id="c2f62-102">데이터 품질 클라이언트 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="c2f62-102">Data Quality Client Application</span></span>
  <span data-ttu-id="c2f62-103">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션을 사용하면 독립형 도구를 사용하여 데이터 품질 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-103">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application enables you to perform data quality operations using a standalone tool.</span></span> <span data-ttu-id="c2f62-104">이 애플리케이션을 사용하면 기술 자료를 만들고, 데이터 품질 프로젝트를 생성 및 실행하고, 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-104">This application enables you to create knowledge bases, create and run data quality projects, and perform administrative tasks.</span></span>  
  
 <span data-ttu-id="c2f62-105">데이터 자산 관리 및 높은 데이터 품질 표준 유지 관리 책임이 있는 데이터 관리자, 데이터 전문가 또는 IT 전문가는 세 가지 역할로 클라이언트 애플리케이션을 사용할 수 있습니다. DQS KB 운영자 역할은 데이터 품질 프로젝트를 편집 및 실행할 수 있습니다. DQS KB 편집자 역할은 프로젝트 기능을 수행하고 기술 자료를 생성 및 편집할 수 있습니다. DQS 관리자는 프로젝트 및 기술 자료 기능을 수행하고 시스템을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-105">Data stewards, data experts, or IT professionals who are responsible for managing data assets and maintaining high standards of data quality can use the client application in any of three roles: a DQS KB Operator who can edit and execute a data quality project; a DQS KB Editor who can perform project functions, and create and edit a knowledge base; and a DQS Administrator who can perform project and knowledge base functions and administer the system.</span></span> <span data-ttu-id="c2f62-106">자세한 내용은 [DQS Security](../../2014/data-quality-services/dqs-security.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2f62-106">For more information, see [DQS Security](../../2014/data-quality-services/dqs-security.md).</span></span>  
  
## <a name="installing-the-data-quality-client-application"></a><span data-ttu-id="c2f62-107">데이터 품질 클라이언트 애플리케이션 설치</span><span class="sxs-lookup"><span data-stu-id="c2f62-107">Installing the Data Quality Client Application</span></span>  
 <span data-ttu-id="c2f62-108">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션은 SQL Server 설치 프로그램을 사용하여 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-108">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is installed using the SQL Server setup.</span></span> <span data-ttu-id="c2f62-109">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]와 동일한 컴퓨터 또는 원격 컴퓨터에 클라이언트 애플리케이션을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-109">You can install the client application on the same computer as [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], or on a remote computer.</span></span> <span data-ttu-id="c2f62-110">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션 설치에 대한 자세한 내용은 [Data Quality Services 설치](install-windows/install-data-quality-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2f62-110">For more information about installing the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, see [Install Data Quality Services](install-windows/install-data-quality-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c2f62-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c2f62-111">Related Tasks</span></span>  
  
|<span data-ttu-id="c2f62-112">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="c2f62-112">Task Description</span></span>|<span data-ttu-id="c2f62-113">항목</span><span class="sxs-lookup"><span data-stu-id="c2f62-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c2f62-114">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-114">Describes how to use the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span>|[<span data-ttu-id="c2f62-115">데이터 품질 클라이언트 애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="c2f62-115">Run the Data Quality Client Application</span></span>](../../2014/data-quality-services/run-the-data-quality-client-application.md)|  
  
## <a name="related-content"></a><span data-ttu-id="c2f62-116">관련 내용</span><span class="sxs-lookup"><span data-stu-id="c2f62-116">Related Content</span></span>  
  
|<span data-ttu-id="c2f62-117">콘텐츠 설명</span><span class="sxs-lookup"><span data-stu-id="c2f62-117">Content Description</span></span>|<span data-ttu-id="c2f62-118">항목</span><span class="sxs-lookup"><span data-stu-id="c2f62-118">Topic</span></span>|  
|-------------------------|-----------|  
|<span data-ttu-id="c2f62-119">DQS에서 기술 자료 및 도메인을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-119">Describes how to use knowledge bases and domains in DQS.</span></span>|[<span data-ttu-id="c2f62-120">DQS 기술 자료 및 도메인</span><span class="sxs-lookup"><span data-stu-id="c2f62-120">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)|  
|<span data-ttu-id="c2f62-121">DQS에서 데이터를 정리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-121">Describes how to cleanse your data in DQS.</span></span>|[<span data-ttu-id="c2f62-122">데이터 정리</span><span class="sxs-lookup"><span data-stu-id="c2f62-122">Data Cleansing</span></span>](../../2014/data-quality-services/data-cleansing.md)|  
|<span data-ttu-id="c2f62-123">DQS에서 일치 작업을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-123">Describes how to perform matching in DQS.</span></span>|[<span data-ttu-id="c2f62-124">데이터 일치</span><span class="sxs-lookup"><span data-stu-id="c2f62-124">Data Matching</span></span>](../../2014/data-quality-services/data-matching.md)|  
|<span data-ttu-id="c2f62-125">DQS를 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f62-125">Describes how to administer DQS.</span></span>|[<span data-ttu-id="c2f62-126">dqs 관리</span><span class="sxs-lookup"><span data-stu-id="c2f62-126">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c2f62-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2f62-127">See Also</span></span>  
 [<span data-ttu-id="c2f62-128">데이터 품질 클라이언트 홈 화면</span><span class="sxs-lookup"><span data-stu-id="c2f62-128">Data Quality Client Home Screen</span></span>](../../2014/data-quality-services/data-quality-client-home-screen.md)  
  
  
