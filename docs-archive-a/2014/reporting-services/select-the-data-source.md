---
title: 데이터 원본 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730075"
---
# <a name="select-the-data-source"></a>데이터 원본 선택
  보고서 마법사의 데이터 원본 선택 페이지를 사용하여 보고서의 데이터 원본을 정의할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **공유 데이터 원본**  
 사용할 데이터 원본 연결 정보가 이미 있는 미리 정의된 공유 데이터 원본을 사용하려면 **공유 데이터 원본** 을 선택합니다. 목록에는 프로젝트에 포함된 모든 공유 데이터 원본이 포함됩니다.  
  
 **새 데이터 원본**  
 새 데이터 원본을 정의하려면 **새 데이터 원본** 을 선택합니다. 해당 데이터 원본 정보는 현재 보고서에만 사용됩니다.  
  
 **이름**  
 데이터 원본에 대한 연결의 이름을 입력합니다. 데이터 원본 이름은 보고서 내에서 중복되지 않아야 합니다.  
  
 **형식**  
 사용 중인 데이터 원본의 유형을 선택 합니다. 예를 들어 데이터베이스를 사용 하는 경우를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 선택 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.  
  
 **연결 문자열**  
 데이터 원본에 대한 연결 문자열을 입력합니다. 연결 문자열에 대 한 자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)을 참조 하세요.  
  
 **편집** 을 클릭하면 **연결 속성** 대화 상자에서 데이터 원본 서버를 지정할 수 있습니다. 로컬 데이터 원본이나 원격 데이터 원본을 지정할 수 있습니다.  
  
 **자격 증명** 을 클릭하면 데이터베이스 자격 증명을 제공할 수 있습니다. 지정하는 자격 증명은 최소한 보고서 디자인을 위해 데이터 원본에 연결하기에 충분해야 합니다. 보고서 서버에 보고서를 배포할 때에는 데이터베이스 자격 증명이 보고서의 모든 사용자를 수용해야 합니다. 예를 들어 모든 보고서 사용자가 자격 증명을 사용하여 데이터 원본에 연결하도록 하려면 **Windows 인증 사용(통합 보안)** 을 선택합니다. 지정하는 자격 증명은 데이터 원본에 대해 유효해야 하므로 Windows 인증을 선택할 경우 보고서를 실행할 모든 사용자 계정으로 데이터 원본에 연결할 수 있는지 확인합니다. 데이터베이스 자격 증명은 보고서와 별도로 관리할 수 있습니다. 자세한 내용은 [보고서 데이터 원본 관리](report-data/manage-report-data-sources.md)를 참조하세요.  
  
 **공유 데이터 원본으로 설정**  
 데이터 원본을 보고서 대신 공유 데이터 원본으로 프로젝트에 저장하려면 이 옵션을 선택합니다. 이렇게 저장된 공유 데이터 원본은 프로젝트에 있는 다른 보고서의 데이터 원본으로 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [포함 된 데이터 연결 및 공유 데이터 연결 또는 데이터 원본 &#40;보고서 작성기 및 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services 보고서 서버](../../2014/reporting-services/reporting-services-report-server.md)   
 [Rsreportdesigner.config 구성 파일](report-server/rsreportdesigner-configuration-file.md)   
 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [보고서 마법사 도움말](../../2014/reporting-services/report-wizard-help.md)  
  
  
