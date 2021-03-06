---
title: 사용자 지정 보고서 항목 구현 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69fdf58eb385e819b524b9c5b5178997257c797c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741643"
---
# <a name="custom-report-item-implementation-requirements"></a>사용자 지정 보고서 항목 구현 요구 사항
  이 항목에서는 사용자 지정 보고서 항목을 개발하고 배포하기 위한 선행 조건에 대해 설명합니다.  
  
## <a name="development-and-deployment-requirements"></a>개발 및 배포 요구 사항  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대한 사용자 지정 보고서 항목을 개발하려면 다음이 필요합니다.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및를 사용 하 여를 실행 하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 대 한 관리 액세스  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK (소프트웨어 개발 키트)가 설치 되어 있어야 합니다.  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서에 대한 액세스  
  
-   구성 요소 제작 및 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 구성 요소 모델 네임스페이스에 대한 지식. 자세한 내용은 msdn.microsoft.com에서 "구성 요소 제작" 및 "Visual Studio의 구성 요소 모델 네임스페이스"를 참조하십시오.  
  
## <a name="language-and-namespace-requirements"></a>언어 및 네임스페이스 요구 사항  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 지정 보고서 항목은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 완벽하게 지원합니다. 원하는 .NET 호환 언어를 사용하여 사용자 지정 보고서 항목을 개발할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서는 코딩, 디버깅, 테스트 등의 반복되는 주기를 단순화 및 가속화하고 쉽게 배포할 수 있도록 다양한 도구와 기능을 개발자에게 제공합니다. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK에는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 과 C# 컴파일러 및 관련 도구가 포함되어 있습니다.  
  
-   사용자 지정 보고서 항목에서는 `Microsoft.ReportDesigner` 및 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스가 사용되며, 이 네임스페이스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 일부로 설치되는 Microsoft.ReportingServices.Designer.DLL 및 Microsoft.ReportingServices.Interfaces.DLL 어셈블리에 저장됩니다.  
  
-   사용자 지정 보고서 항목 디자인 타임 구성 요소는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 <xref:System.ComponentModel> 네임스페이스에서 인터페이스를 구현해야 합니다. <xref:System.ComponentModel>은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조하십시오.  
  
> [!IMPORTANT]  
>  기본적으로 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 설치되지만 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK는 설치되지 않습니다. 컴퓨터에 SDK가 설치되지 않아 SDK 설명서가 온라인 설명서 컬렉션에 포함되어 있지 않을 경우 이 섹션의 SDK 내용에 대한 링크가 작동하지 않습니다. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK를 설치한 후 [SQL Server 제품 설명서 추가 또는 제거](../../index.yml)의 지침에 따라 온라인 설명서 컬렉션과 목차에 SDK 설명서를 추가할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 보고서 항목 런타임 구성 요소 만들기](creating-a-custom-report-item-run-time-component.md)   
 [사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기](creating-a-custom-report-item-design-time-component.md)   
 [방법: 사용자 지정 보고서 항목 배포](how-to-deploy-a-custom-report-item.md)   
 [사용자 지정 보고서 항목 클래스 라이브러리](custom-report-item-class-libraries.md)  
  
  
