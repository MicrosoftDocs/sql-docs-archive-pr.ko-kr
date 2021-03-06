---
title: 소스 제어에서 파일 제외 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732940"
---
# <a name="exclude-files-from-source-control"></a>원본 제어에서 파일 제외
  작업 중인 솔루션에 원본 제어 서비스가 필요 하지 않은 파일이 포함 된 경우 소스 제어 **에서 제외** 명령을 사용 하 여 소스 제어에서 파일을 제외할 수 있습니다. 이렇게 하면 파일이 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 데이터베이스에 남아 있지만 더 이상 프로젝트와 함께 체크 인 또는 체크 아웃되지 않습니다.  
  
 생성 된 파일 에서만 **소스 제어에서 제외** 명령을 사용 해야 합니다. 생성 된 파일은 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 솔루션에 있는 다른 파일의 내용을 기반으로 하 여 완전히 다시 만들 수 있는 파일입니다.  
  
### <a name="to-exclude-a-file-from-source-control"></a>원본 제어에서 파일을 제외하려면  
  
1.  솔루션 탐색기에서 제외할 파일을 선택합니다.  
  
2.  **파일** 메뉴에서 **소스 제어**를 가리킨 다음 **Exclude** *\<file name>* **소스 제어에서**제외를 클릭 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 기본 사항](../../2014/database-engine/source-control-basics.md)   
 [원본 제어 옵션 설정](../../2014/database-engine/set-source-control-options.md)   
 [원본 제어 연결 변경](../../2014/database-engine/change-source-control-connections.md)  
  
  
