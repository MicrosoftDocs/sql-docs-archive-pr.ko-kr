---
title: SQL Server 오류 로그 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661357"
---
# <a name="configure-sql-server-error-logs"></a>SQL Server 오류 로그 구성
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그의 재활용 방법을 확인하거나 수정하는 방법에 대해 설명합니다.  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>SQL Server 오류 로그 구성 대화 상자를 열려면  
  
1.  개체 탐색기에서 SQL Server 인스턴스를 확장하고 **관리**를 확장한 다음 **SQL Server 로그**를 마우스 오른쪽 단추로 클릭하고 **구성**을 클릭합니다.  
  
2.  **SQL Server 오류 로그 구성** 대화 상자의 다음 옵션 중에서 선택합니다.  
  
     **재활용 이전의 오류 로그 파일 수 제한**  
     재활용하기 전의 오류 로그 수 제한을 두려면 선택합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작할 때마다 오류 로그가 새로 만들어집니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 최근 6개 로그의 백업을 보관합니다.  
  
     **최대 오류 로그 파일 수**  
     재활용하기 전의 오류 로그 파일 최대 개수를 지정합니다. 기본값은 6이며 이 값은 백업 로그를 재활용하기까지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 보유하는 이전 백업 로그의 수를 나타냅니다.  
  
  
