---
title: 데이터 처리 확장 프로그램 코드 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bf7490145f91ee8b3cfc2357c34010bed593ed9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649935"
---
# <a name="debugging-data-processing-extension-code"></a>데이터 처리 확장 프로그램 코드 디버깅
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에서는 데이터 처리 확장 프로그램 코드를 분석하여 오류를 찾는 데 유용한 디버깅 도구를 다수 제공합니다. 작업하기 가장 좋은 도구는 수행하려는 작업에 따라 달라집니다. 이 예에서는 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 사용합니다.  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>데이터 처리 확장 프로그램 코드를 디버깅하려면  
  
1.  [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 시작하고 데이터 처리 확장 프로그램 프로젝트를 엽니다.  
  
2.  프로젝트를 빌드하고 데이터 처리 확장 프로그램 어셈블리 및 해당하는 .pdb 파일을 보고서 디자이너에 배포합니다. 배포에 대 한 자세한 내용은 [방법: 보고서 디자이너에 데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension-to-report-designer.md)를 참조하세요.  
  
3.  데이터 처리 확장 프로그램 코드를 별도의 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 창에 열어 둔 상태로 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 새 보고서 프로젝트를 엽니다.  
  
4.  데이터 처리 확장 프로그램 프로젝트를 포함하는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 창으로 이동하고 코드에서 중단점을 설정합니다.  
  
5.  데이터 처리 확장 프로그램 프로젝트 창을 활성 상태로 두고 **디버그** 메뉴에서 **프로세스에 연결**을 클릭합니다.  
  
     **프로세스에 연결** 대화 상자가 열립니다.  
  
6.  프로세스 목록에서 보고서 프로젝트에 해당하는 devenv.exe 프로세스를 선택하고 **연결**을 클릭합니다.  
  
7.  보고서 프로젝트의 **보고서 데이터** 탭을 사용하여 보고서 데이터 원본을 정의합니다. 대개 일반 쿼리 디자이너를 사용하여 사용자 지정 데이터 원본에 대해 쿼리를 실행합니다. 그러면 디버거가 호출되고 중단점에 해당하는 코드가 실행됩니다.  
  
8.  F11 키를 사용하여 코드를 단계별로 실행합니다. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]를 사용하여 디버깅하는 방법은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 설명서를 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension.md)   
 [Reporting Services 확장 프로그램](../reporting-services-extensions.md)   
 [데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md)   
 [Reporting Services 확장 라이브러리](../reporting-services-extension-library.md)  
  
  
