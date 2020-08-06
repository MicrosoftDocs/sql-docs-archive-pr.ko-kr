---
title: Analysis Server 속성(로그온 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8db5576e48e7f12ef1733175875d2cd065e376fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741515"
---
# <a name="analysis-server-properties-log-on-tab"></a><span data-ttu-id="d0c67-102">분석 서버 속성(로그온 탭)</span><span class="sxs-lookup"><span data-stu-id="d0c67-102">Analysis Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="d0c67-103">**분석 서버 속성** 대화 상자의 **로그온** 탭을 사용하여 [!INCLUDE[ssAS](../../includes/ssas-md.md)] 서비스에서 사용할 계정을 지정할 수 있으며 서비스를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-103">Use the **Log On** tab of the **Analysis Server Properties** dialog box to specify the account used by the [!INCLUDE[ssAS](../../includes/ssas-md.md)] service, and to start and stop the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0c67-104">클러스터형 인스턴스의 서비스에서 사용하는 **계정 이름** 을 변경하는 경우 새 계정은 변경되는 서비스의 설치 중에 지정한 도메인 그룹의 멤버여야 합니다. 그렇지 않으면 해당 그룹에 멤버를 추가할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-104">When changing the **Account Name** used by a service on a clustered instance, the new account must either be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="d0c67-105">그룹 멤버 자격을 수정할 권한이 없을 경우 도메인 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c67-105">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0c67-106">옵션</span><span class="sxs-lookup"><span data-stu-id="d0c67-106">Options</span></span>  
 <span data-ttu-id="d0c67-107">**로컬 시스템 계정**</span><span class="sxs-lookup"><span data-stu-id="d0c67-107">**Local System account**</span></span>  
 <span data-ttu-id="d0c67-108">암호를 요구하지 않는 로컬 시스템 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-108">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="d0c67-109">그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 다른 서버와 상호 작용하지 못하도록 서비스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-109">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="d0c67-110">**계정 지정**</span><span class="sxs-lookup"><span data-stu-id="d0c67-110">**This account**</span></span>  
 <span data-ttu-id="d0c67-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-111">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d0c67-112">에서는 서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-112">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="d0c67-113">계정 선택 방법은 온라인 설명서에서 "Windows 서비스 계정 설정" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0c67-113">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="d0c67-114">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="d0c67-114">**Account Name**</span></span>  
 <span data-ttu-id="d0c67-115">로컬 또는 도메인 사용자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-115">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="d0c67-116">**암호**</span><span class="sxs-lookup"><span data-stu-id="d0c67-116">**Password**</span></span>  
 <span data-ttu-id="d0c67-117">계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-117">Type the password of the account.</span></span>  
  
 <span data-ttu-id="d0c67-118">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="d0c67-118">**Confirm password**</span></span>  
 <span data-ttu-id="d0c67-119">계정의 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-119">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="d0c67-120">**시작**</span><span class="sxs-lookup"><span data-stu-id="d0c67-120">**Start**</span></span>  
 <span data-ttu-id="d0c67-121">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-121">Start the service.</span></span>  
  
 <span data-ttu-id="d0c67-122">**중지**</span><span class="sxs-lookup"><span data-stu-id="d0c67-122">**Stop**</span></span>  
 <span data-ttu-id="d0c67-123">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-123">Stop the service.</span></span>  
  
 <span data-ttu-id="d0c67-124">**일시 중지**</span><span class="sxs-lookup"><span data-stu-id="d0c67-124">**Pause**</span></span>  
 <span data-ttu-id="d0c67-125">서비스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-125">Pause the service.</span></span>  
  
 <span data-ttu-id="d0c67-126">**재개**</span><span class="sxs-lookup"><span data-stu-id="d0c67-126">**Resume**</span></span>  
 <span data-ttu-id="d0c67-127">일시 중지한 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c67-127">Resume a paused service.</span></span>  
  
  