---
title: server trigger recursion 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23a4997bd1a6f8b2c04af34d5cdc3229575901a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740413"
---
# <a name="server-trigger-recursion-server-configuration-option"></a><span data-ttu-id="7c5b4-102">server trigger recursion 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="7c5b4-102">server trigger recursion Server Configuration Option</span></span>
  <span data-ttu-id="7c5b4-103">**server trigger recursion** 옵션을 사용하여 서버 수준 트리거가 재귀적으로 발생할 수 있는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-103">Use the **server trigger recursion** option to specify whether to allow server-level triggers to fire recursively.</span></span> <span data-ttu-id="7c5b4-104">이 옵션을 1(ON)로 설정하면 서버 수준 트리거가 재귀적으로 발생할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="7c5b4-104">When this option is set to 1 (ON), server-level triggers will be allowed to fire recursively.</span></span> <span data-ttu-id="7c5b4-105">0(OFF)으로 설정하면 재귀적으로 발생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-105">When set to 0 (OFF), server-level triggers cannot be fired recursively.</span></span> <span data-ttu-id="7c5b4-106">server trigger recursion 옵션이 0(OFF)일 때는 직접 재귀만 차단되며</span><span class="sxs-lookup"><span data-stu-id="7c5b4-106">Only direct recursion is prevented when the server trigger recursion option is set to 0 (OFF).</span></span> <span data-ttu-id="7c5b4-107">간접 재귀를 막으려면 **nested triggers** 옵션을 0으로 설정해야 합니다. 이 옵션의 기본값은 1(ON)이며</span><span class="sxs-lookup"><span data-stu-id="7c5b4-107">(To disable indirect recursion, set the **nested triggers** option to 0.) The default value for this option is 1 (ON).</span></span> <span data-ttu-id="7c5b4-108">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-108">The setting takes effect immediately (without a server restart).</span></span>  
  
 <span data-ttu-id="7c5b4-109">자세한 내용은 [중첩 트리거 만들기](../../relational-databases/triggers/create-nested-triggers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-109">For more information, see [Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5b4-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c5b4-110">See Also</span></span>  
 <span data-ttu-id="7c5b4-111">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7c5b4-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="7c5b4-112">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7c5b4-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="7c5b4-113">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7c5b4-113">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  