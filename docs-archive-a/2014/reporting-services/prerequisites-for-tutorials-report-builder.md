---
title: 자습서의 사전 요구 사항(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1f037d1a19fdce566a5a22c7e6a3274fb10ed7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639390"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>자습서의 사전 요구 사항(보고서 작성기)
  보고서 작성기 자습서에서는 사용자가 보고서 서버와 통합된 SharePoint 사이트 또는 보고서 서버에서 보고서를 보고 저장할 수 있는 것으로 간주합니다. 모든 자습서에서는 데이터에 대해 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]인스턴스에서 처리해야 하는 리터럴 쿼리를 사용합니다.  
  
 보고서 서버, SharePoint 사이트 또는 데이터 원본에 대한 액세스 권한이 없는 경우에는 오프라인 보고서 작성을 통해 보고서 작성기에 대해 배울 수 있습니다. [자습서: 오프라인에서 빠른 차트 보고서 만들기&#40;보고서 작성기&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)를 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
 보고서 작성기 자습서를 완료하려면 다음이 필요합니다.  
  
-   보고서 작성기에 대 한 액세스 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . 보고서 관리자나 SharePoint 사이트에서 사용할 수 있는 독립 실행형 버전의 보고서 작성기 또는 ClickOnce 버전을 사용하여 보고서 작성기를 실행할 수 있습니다. ClickOnce 버전의 경우 첫 번째 단계, 즉 보고서 작성기를 여는 방법만 다릅니다.  
  
     보고서 관리자을 사용 하려면 보고서 관리자를 열고 **보고서 작성기**를 클릭 합니다. 기본적으로 보고서 관리자의 URL은 http:///reports입니다. \<*servername*>  
  
     SharePoint 사이트를 사용하려면 해당 사이트로 이동하고 문서 탭과 새 문서를 차례로 클릭한 다음 드롭다운 목록에서 보고서 작성기 보고서를 클릭합니다. 예: http:// \<servername> /sites/mySite/reports. SharePoint 관리자는 각 문서 라이브러리에서 보고서 작성기 보고서를 사용할 수 있도록 설정해야 합니다.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 보고서 서버와 통합된 SharePoint 사이트 또는 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 보고서 서버의 URL. 보고서, 공유 데이터 원본, 공유 데이터 세트, 보고서 파트 및 모델을 저장하고 볼 수 있는 권한이 있어야 합니다. 기본적으로 보고서 서버에 대 한 URL은 http:///reportserver입니다. \<servername> 기본적으로 SharePoint 사이트의 URL은 http:// \<sitename> 또는 http:// \<server> /site입니다.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 인스턴스의 이름과 모든 데이터베이스에 대한 읽기 전용 액세스에 필요한 자격 증명. 자습서의 데이터 세트 쿼리에서는 리터럴 데이터를 사용하지만 보고서 데이터 세트에 필요한 메타데이터가 반환되도록 하려면 각 쿼리를 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 인스턴스에서 처리해야 합니다. 예를 들어 연결 문자열 `data source=<servername>`은 서버만 지정합니다. 서버에 액세스할 수 있는 권한을 부여하는 시스템 관리자가 할당한 기본 데이터베이스에 대한 읽기 권한이 있어야 합니다. 연결 문자열 `data source=<servername>;initial catalog=<database>`에 표시된 것처럼 데이터베이스를 지정할 수도 있습니다.  
  
-   지도가 포함된 자습서의 경우 Bing Maps를 배경으로 지원하도록 보고서 서버를 구성해야 합니다. 자세한 내용은 msdn.microsoft.com의 온라인 설명서에 있는 설명서에서 [지도 보고서 지원 계획](plan-for-map-report-support.md) 을 참조 하세요 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) .  
  
-   자습서 [: 드릴스루 보고서 및 주 보고서 &#40;보고서 작성기&#41;만들기 ](tutorial-creating-drillthrough-and-main-reports-report-builder.md)에서는 Contoso business intelligence 데모 데이터 집합을 사용 합니다. 이 데이터 세트은 ContosoDW 데이터 웨어하우스와 Contoso_Retail OLAP(온라인 분석 처리) 데이터베이스로 구성되어 있습니다. 이 자습서에서 만들 보고서는 Contoso Sales 큐브에서 보고서 데이터를 검색합니다. Contoso_Retail OLAP 데이터베이스는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=18279)에서 다운로드할 수 있습니다. ContosoBIdemoABF.exe 파일만 다운로드하면 됩니다. 이 파일에 OLAP 데이터베이스가 포함되어 있습니다.  
  
     다른 파일인 ContosoBIdemoBAK.exe는 ContosoDW 데이터 웨어하우스를 위한 것으로, 이 자습서에서는 사용되지 않습니다.  
  
     ContosoRetail.abf 백업 파일을 추출하여 Contoso_Retail OLAP 데이터베이스로 복원하기 위한 지침은 이 웹 사이트에 포함되어 있습니다.  
  
     사용자는 OLAP 데이터베이스를 설치할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 액세스할 수 있어야 합니다.  
  
 보고서 서버 관리자는 보고서 서버에서 필요한 권한을 부여하고, [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 폴더 위치를 구성하고, 보고서 작성기 기본 옵션을 구성해야 합니다. 자세한 내용은 [설치, 제거 및 보고서 작성기 지원](install-uninstall-and-report-builder-support.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md)  
  
  
