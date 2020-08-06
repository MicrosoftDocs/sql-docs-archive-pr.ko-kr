---
title: affinity64 mask 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2ea6d2e364feaa67d91de0055617aac9dc285ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652346"
---
# <a name="affinity64-mask-server-configuration-option"></a><span data-ttu-id="df1b7-102">affinity64 mask 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="df1b7-102">affinity64 mask Server Configuration Option</span></span>
  <span data-ttu-id="df1b7-103">affinity64 mask는 프로세서를 특정 스레드에 바인딩하며 affinity mask 옵션과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="df1b7-103">The affinity64 mask binds processors to specific threads, similar to the affinity mask option.</span></span> <span data-ttu-id="df1b7-104">선호도 마스크를 사용하여 처음 32개 프로세서를 바인딩하고 affinity64 마스크를 사용하여 컴퓨터의 나머지 프로세서를 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1b7-104">Use affinity mask to bind the first 32 processors, and use affinity64 mask to bind the remaining processors on the computer.</span></span> <span data-ttu-id="df1b7-105">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]64비트 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1b7-105">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]<span data-ttu-id="df1b7-106">[ALTER SERVER CONFIGURATION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df1b7-106">Use [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1b7-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df1b7-107">See Also</span></span>  
 <span data-ttu-id="df1b7-108">[선호도 마스크 서버 구성 옵션](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="df1b7-108">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="df1b7-109">[리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="df1b7-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="df1b7-110">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df1b7-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="df1b7-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="df1b7-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="df1b7-112">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="df1b7-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
