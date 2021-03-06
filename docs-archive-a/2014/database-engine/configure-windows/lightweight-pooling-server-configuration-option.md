---
title: lightweight pooling 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 549ff7451a31b48459b5a290b94ad406c3768a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651897"
---
# <a name="lightweight-pooling-server-configuration-option"></a>경량 풀링 서버 구성 옵션
  **경량 풀링** 옵션을 사용하여 SMP(대칭적 다중 처리) 환경에서 가끔 발생하는 과도한 컨텍스트 전환과 관련된 시스템 오버헤드를 줄이는 방법을 제공할 수 있습니다. 과도한 컨텍스트 전환이 일어나면 lightweight pooling이 컨텍스트 전환을 인라인으로 수행하여 사용자/커널 링 전환을 줄임으로써 처리량을 향상시킬 수 있습니다.  
  
 파이버 모드는 UMS 작업자의 컨텍스트 전환으로 인해 심각한 성능 병목 상태가 발생하는 특정한 상황을 위한 것입니다. 이런 경우는 드물기 때문에 파이버 모드가 일반 시스템의 성능이나 확장성을 향상시키는 경우는 거의 없습니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]에서는 컨텍스트 전환이 향상되어 파이버 모드에 대한 필요성도 감소되었습니다. 일상 작업을 예약하는 데에는 파이버 모드를 사용하지 않는 것이 좋습니다. 파이버 모드를 사용하면 컨텍스트 전환을 활용하지 못해 성능이 저하될 수 있으며 TLS(스레드 로컬 스토리지) 또는 스레드 소유 개체(예: 뮤텍스 - Win32 커널 개체 유형)를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 일부 구성 요소가 파이버 모드에서 제대로 작동하지 않을 수 있습니다.  
  
 **lightweight pooling** 을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 파이버 모드 일정으로 전환됩니다. 이 옵션의 기본값은 0입니다.  
  
 **lightweight pooling** 은 고급 옵션입니다. **sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하는 경우 **고급 옵션 표시** 를 1로 설정할 때만 **경량 풀링** 을 변경할 수 있습니다. 이 설정은 서버를 다시 시작한 후에 적용됩니다.  
  
> [!NOTE]  
>  경량 풀링은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP에서 지원되지 않습니다. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 에서는 경량 풀링을 완벽하게 지원합니다.  
  
> [!NOTE]  
>  경량 풀링에서는 CLR(공용 언어 런타임) 실행이 지원되지 않습니다. 두 옵션, 즉 "clr enabled" 또는 "lightweight pooling" 중 하나를 해제합니다. CLR에 의존하며 파이버 모드에서 제대로 작동하지 않는 기능에는 hierarchy 데이터 형식, 복제, 정책 기반 관리 등이 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [clr enabled 서버 구성 옵션](clr-enabled-server-configuration-option.md)   
 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CRL 사용 서버 구성 옵션](clr-enabled-server-configuration-option.md)  
  
  
