---
title: 구독 다시 초기화 - 단일 구독 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.reinit.single.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43f59a5de54a36f69a522c5b09bad26ce510bd3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741767"
---
# <a name="reinitialize-subscriptions---one-subscription"></a><span data-ttu-id="e7fa4-102">구독 다시 초기화 - 단일 구독</span><span class="sxs-lookup"><span data-stu-id="e7fa4-102">Reinitialize Subscription(s) - One Subscription</span></span>
  <span data-ttu-id="e7fa4-103">**구독 다시 초기화** 대화 상자를 사용하여 구독을 다시 초기화하도록 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-103">The **Reinitialize Subscription(s)** dialog box allows you to mark a subscription for reinitialization.</span></span> <span data-ttu-id="e7fa4-104">다시 초기화에는 스냅샷을 구독자에 적용하는 작업이 포함됩니다. 이 작업은 트랜잭션 게시의 구독에 대한 배포 에이전트 또는 병합 게시의 구독에 대한 병합 에이전트에서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-104">Reinitialization involves applying a snapshot to the Subscriber; it is performed by the Distribution Agent for subscriptions to transactional publications and by the Merge Agent for subscriptions to merge publications.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7fa4-105">옵션</span><span class="sxs-lookup"><span data-stu-id="e7fa4-105">Options</span></span>  
 <span data-ttu-id="e7fa4-106">**현재 스냅샷 사용**</span><span class="sxs-lookup"><span data-stu-id="e7fa4-106">**Use the current snapshot**</span></span>  
 <span data-ttu-id="e7fa4-107">다음에 배포 에이전트 또는 병합 에이전트가 실행될 때 현재 스냅샷을 구독자에 적용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-107">Select to apply the current snapshot to the Subscriber the next time the Distribution Agent or Merge Agent runs.</span></span> <span data-ttu-id="e7fa4-108">유효한 스냅샷이 없으면 이 옵션을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-108">If there is no valid snapshot available, this option cannot be selected.</span></span>  
  
 <span data-ttu-id="e7fa4-109">**새 스냅샷 사용**</span><span class="sxs-lookup"><span data-stu-id="e7fa4-109">**Use a new snapshot**</span></span>  
 <span data-ttu-id="e7fa4-110">새 스냅샷으로 구독을 다시 초기화하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-110">Select to reinitialize the subscription with a new snapshot.</span></span> <span data-ttu-id="e7fa4-111">스냅샷 에이전트에 의해 스냅샷이 생성된 후에만 스냅샷을 구독자에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-111">The snapshot can be applied to the Subscriber only after it has been generated by the Snapshot Agent.</span></span> <span data-ttu-id="e7fa4-112">스냅샷 에이전트가 예약 실행되도록 설정한 경우에는 예약된 다음 스냅샷 에이전트가 실행될 때까지 구독이 다시 초기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-112">If the Snapshot Agent is set to run on a schedule, the subscription will not be reinitialized until after the next scheduled Snapshot Agent run.</span></span>  
  
 <span data-ttu-id="e7fa4-113">스냅샷 에이전트를 바로 시작하려면 **지금 새 스냅샷 생성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-113">Select **Generate the new snapshot now** to start the Snapshot Agent immediately.</span></span>  
  
 <span data-ttu-id="e7fa4-114">**다시 초기화하기 전에 동기화되지 않은 변경 내용 업로드**</span><span class="sxs-lookup"><span data-stu-id="e7fa4-114">**Upload unsynchronized changes before reinitialization**</span></span>  
 <span data-ttu-id="e7fa4-115">병합 복제에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-115">Merge replication only.</span></span> <span data-ttu-id="e7fa4-116">구독자의 데이터를 스냅샷으로 덮어쓰기 전에 보류 중인 구독 데이터베이스의 변경 내용을 업로드하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-116">Select to upload any pending changes from the subscription database before the data at the Subscriber is overwritten with a snapshot.</span></span>  
  
 <span data-ttu-id="e7fa4-117">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-117">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e7fa4-118">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-118">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
 <span data-ttu-id="e7fa4-119">**다시 초기화 표시**</span><span class="sxs-lookup"><span data-stu-id="e7fa4-119">**Mark for Reinitialization**</span></span>  
 <span data-ttu-id="e7fa4-120">구독을 다시 초기화하도록 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-120">Click to mark the subscription for reinitialization.</span></span> <span data-ttu-id="e7fa4-121">유효한 스냅샷을 사용할 수 있으면 다음에 배포 에이전트 또는 병합 에이전트가 해당 구독에 대해 실행될 때 이 스냅샷이 구독자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7fa4-121">After a valid snapshot is available, the next time the Distribution Agent or Merge Agent runs for the subscription, the snapshot is applied at the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fa4-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7fa4-122">See Also</span></span>  
 [<span data-ttu-id="e7fa4-123">구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="e7fa4-123">Reinitialize Subscriptions</span></span>](reinitialize-subscriptions.md)  
  
  