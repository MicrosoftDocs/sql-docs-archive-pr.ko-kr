---
title: 패키지 저장 및 실행 (SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a23f69bf66ca3355f1e1c62cc42d51e4aea3da5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652920"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>패키지 저장 및 실행(SQL Server 가져오기 및 내보내기 마법사)
  **패키지 저장 및 실행** 대화 상자를 사용하여 패키지를 즉시 실행하거나 나중에 실행하도록 저장할 수 있고, 즉시 실행하는 동시에 저장할 수도 있습니다.  
  
> [!NOTE]  
>   패키지 실행이 완료되기 전에 패키지를 중지하면 **저장** 확인란을 선택했어도 패키지가 저장되지 않습니다.  
  
 이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요. 마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.  
  
 SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다. 이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다. 그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다. 자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.  
  
## <a name="options"></a>옵션  
 **즉시 실행**  
 패키지를 즉시 실행하려면 이 옵션을 선택합니다.  
  
 **SSIS 패키지 저장**  
 나중에 패키지를 즉시 실행하는 옵션으로 실행할 수 있도록 패키지를 저장합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서는 마법사가 만든 패키지를 저장하는 옵션을 사용할 수 없습니다.  
  
 **SQL Server**  
 패키지를 데이터베이스에 저장 하려면이 옵션을 선택 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 합니다.  
  
> [!NOTE]  
>   이 옵션은 **SSIS 패키지 저장** 옵션을 선택한 경우에만 사용할 수 있습니다.  
  
 **파일 시스템**  
 패키지를 확장자가 .dtsx인 파일로 저장하려면 이 옵션을 선택합니다.  
  
> [!NOTE]  
>   이 옵션은 **SSIS 패키지 저장** 옵션을 선택한 경우에만 사용할 수 있습니다.  
  
 **패키지 보호 수준**  
 목록에서 보호 수준을 선택합니다.  
  
 보호 수준은 보호 방법(암호 또는 사용자 키)과 패키지 보호의 범위를 결정합니다. 보호에는 모든 데이터를 포함시키거나 중요한 데이터만 포함시킬 수 있습니다. 패키지 보안의 요구 사항 및 옵션을 이해 하려면 [패키지의 중요 한 데이터 Access Control](../security/access-control-for-sensitive-data-in-packages.md) 및 [보안 개요 &#40;Integration Services&#41;](../security/security-overview-integration-services.md)를 참조 하세요.  
  
> [!NOTE]  
>   이 옵션은 **SSIS 패키지 저장** 옵션을 선택한 경우에만 사용할 수 있습니다.  
  
 **암호**  
 암호를 입력합니다.  
  
> [!NOTE]  
>   이 옵션은 **패키지 보호 수준** 옵션을 **암호로 중요한 데이터 암호화** 또는 **암호로 모든 데이터 암호화**로 설정한 경우에만 사용할 수 있습니다.  
  
 **암호 다시 입력**  
 암호를 다시 입력합니다.  
  
> [!NOTE]  
>   이 옵션은 **패키지 보호 수준** 옵션을 **암호로 중요한 데이터 암호화** 또는 **암호로 모든 데이터 암호화**로 설정한 경우에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 및 패키지 실행](../packages/run-integration-services-ssis-packages.md)   
 [패키지 저장](../save-packages.md)  
  
  
