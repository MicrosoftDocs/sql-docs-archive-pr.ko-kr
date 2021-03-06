---
title: Reporting Services 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650430"
---
# <a name="uninstall-reporting-services"></a>Reporting Services 제거
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 제거해도 사용자가 만든 콘텐츠나 수정한 구성은 제거되지 않습니다. 그러나 제거를 완료한 후에도 필요한 콘텐츠가 있는 경우 제거 프로세스를 시작하기 전에 콘텐츠를 복사하는 것이 좋습니다.

## <a name="uninstall-sharepoint-mode"></a>SharePoint 모드 제거
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 제거하면

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 및 서비스 프록시 항목이 제거됩니다.

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에 사용된 파일

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션은 제거되지 않습니다. 더 이상 사용하지 않으려는 서비스 애플리케이션은 Windows PowerShell 또는 SharePoint 중앙 관리를 사용하여 삭제합니다.

 보고서 항목 및 관련 메타데이터는 제거되지 않습니다. 이 정보는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션과 관련된 콘텐츠 및 구성 데이터베이스에 포함되어 있습니다. 데이터베이스는 제거되지 않으며 SharePoint 모드의 다른 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에 데이터베이스를 수동으로 마이그레이션할 수 있습니다. 해당 정보가 더 이상 필요하지 않으면 데이터베이스를 삭제합니다. 자세한 내용은 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)을 참조하세요.

 다음은 제거되지 않는 세 가지 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터베이스의 이름 예입니다.

-   **보고서 서버 데이터베이스:** eportingService_7f616e2d253040e8ab5653b3c09a065e

-   **보고서 서버 임시 데이터베이스:** portingService_7f616e2d253040e8ab5653b3c09a065eTempDB

-   **보고서 서버 경고 데이터베이스:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting

### <a name="uninstall-the-add-in-for-sharepoint-products"></a>SharePoint 제품을 위한 추가 기능을 제거합니다.
 컴퓨터에서 추가 기능을 제거할 때는 파일만 제거하거나 팜에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능도 제거할지를 선택할 수 있습니다. SharePoint 제품용 추가 기능을 제거 하는 방법에 대 한 자세한 내용은 sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [2010 및 sharepoint 2013&#41;&#40;Reporting Services 추가 기능 설치 또는 제거 ](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)를 참조 하세요.

## <a name="uninstall-native-mode"></a>기본 모드 제거
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드를 제거하면 설치 후에 **만들었거나** 또는 **수정한** 내용은 그대로 남아 있습니다. 예를 들어 데이터베이스 파일, 로그 파일, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 파일 및 보고서와 데이터 원본 파일과 같은 콘텐츠 항목이 포함됩니다.

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 인스턴스 기능이므로 Windows 제어판, 프로그램 및 기능 목록에 표시되지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native 모드를 제거하려면

1.  Windows 제어판에서 **프로그램 및 기능**을 클릭합니다.

2.  **프로그램 및 기능** 에서 **Microsoft SQL Server 2012**를 선택합니다.

3.  제거 마법사에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 기능 **RS**를 포함하는 인스턴스를 선택합니다.

     ![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")

4.  인스턴스를 선택한 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 선택합니다.

     ![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")

5.  마법사를 완료합니다.

## <a name="see-also"></a>참고 항목
 [설치 &#40;SQL Server의 기존 인스턴스를 제거&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) sharepoint 2013 &#40;추가 기능을 [설치 또는 SharePoint용 PowerPivot 제거&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) sharepoint [2010 및 sharepoint 2013 Reporting Services 추가 기능을 설치 하거나 제거](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) &#40;


