---
title: 기본 모드 보고서 서버 스케일 아웃 배포 구성 (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], deployments
- deploying [Reporting Services], scale-out deployment model
- scale-out deployments [Reporting Services]
ms.assetid: b30d0308-4d9b-4f85-9f83-dece4dcb2775
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6855769d36632ce60b7cf299291d58d5f136d120
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653745"
---
# <a name="configure-a-native-mode-report-server-scale-out-deployment-ssrs-configuration-manager"></a>기본 모드 보고서 서버 확장 배포 구성(SSRS 구성 관리자)

  Reporting Services 기본 모드에서는 단일 보고서 서버 데이터베이스를 공유하는 여러 보고서 서버 인스턴스 실행을 허용하는 스케일 아웃 배포 모델을 사용할 수 있습니다. 확장 배포는 더 많은 동시 사용자와 보고서 실행 부하를 처리할 수 있도록 보고서 서버의 확장성을 개선하는 데 사용됩니다. 또한 특정 서버가 대화형 보고서나 예약된 보고서를 처리하도록 지정하는 데도 사용할 수 있습니다.

 SharePoint 모드 보고서 서버는 확장을 위해 SharePoint 제품 인프라를 활용 합니다. Sharepoint 모드 확장은 sharepoint 팜에 sharepoint 모드 보고서 서버를 더 추가 하 여 수행 됩니다. SharePoint 모드의 확장에 대한 자세한 내용은 [팜에 추가 보고서 서버 추가&#40;SSRS 확장&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)를 참조하세요.

 **확장 배포는 다음과 같은 항목으로 구성됩니다.**

-   단일 보고서 서버 데이터베이스를 공유하는 두 개 이상의 보고서 서버 인스턴스

-   (선택 사항) 대화형 사용자 부하를 여러 보고서 서버 인스턴스에 분산하기 위한 NLB(네트워크 로드 균형 조정) 클러스터

 NLB 클러스터에 Reporting Services를 배포하는 경우에는 보고서 서버 URL의 구성에 NLB 가상 서버 이름을 사용하고 해당 서버가 같은 뷰 상태를 공유하도록 구성해야 합니다.

 Reporting Services는 Microsoft Cluster Services 클러스터에 참여하지 않습니다. 그러나 장애 조치(Failover) 클러스터의 일부인 데이터베이스 엔진 인스턴스에 보고서 서버 데이터베이스를 만들 수는 있습니다.

 **스케일 아웃 배포를 계획, 설치 및 구성하려면 다음 단계를 수행합니다.**

-   보고서 서버 인스턴스를 설치 하는 방법에 대 한 지침은 설치 마법사의 설치 [SQL Server 2014 &#40;설치 마법사에서 설치&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) 를 검토 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.

-   NLB(네트워크 로드 균형 조정) 클러스터에 스케일 아웃 배포를 호스트하려는 경우 스케일 아웃 배포를 구성하기 전에 MLB 클러스터를 구성해야 합니다. 자세한 내용은 [네트워크 부하 분산 클러스터에서 보고서 서버 구성](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md)을 참조하세요.

-   보고서 서버 데이터베이스를 공유하고 보고서 서버를 확장 배포에 조인하는 방법은 이 항목의 절차를 참조하십시오.

     절차에서는 두 개의 노드로 구성된 보고서 서버 스케일 아웃 배포를 구성하는 방법에 대해 설명합니다. 보고서 서버 노드를 배포에 추가하려면 이 항목에 설명된 단계를 반복하십시오.

    -   스케일 아웃 배포에 조인될 보고서 서버 인스턴스를 각각 설치하려면 설치 프로그램을 사용합니다.

         서버 인스턴스를 공유 데이터베이스에 연결할 때 데이터베이스 호환성 오류가 발생하지 않도록 하려면 모든 인스턴스가 동일한 버전인지 확인합니다. 예를 들어 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버 인스턴스를 사용하여 보고서 서버 데이터베이스를 만드는 경우 동일한 배포 내의 다른 모든 인스턴스도 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]이어야 합니다.

    -   공유 데이터베이스에 각 보고서 서버를 연결하려면 Reporting Services 구성 관리자를 사용합니다. 한 번에 하나의 보고서 서버에만 연결하여 구성할 수 있습니다.

    -   보고서 서버 데이터베이스에 이미 연결된 첫 번째 보고서 서버 인스턴스에 새 보고서 서버 인스턴스를 조인하여 확장 배포를 완료하려면 Reporting Services 구성 도구를 사용합니다.

### <a name="to-install-a-sql-server-instance-to-host-the-report-server-databases"></a>보고서 서버 데이터베이스를 호스팅하는 SQL Server 인스턴스를 설치하려면

1.  보고서 서버 데이터베이스를 호스팅할 컴퓨터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 설치합니다. 최소한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 설치해야 합니다.

2.  필요한 경우 원격 연결을 사용할 수 있도록 보고서 서버를 설정합니다. 일부 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 기본적으로 원격 TCP/IP 및 명명된 파이프 연결을 활성화하지 않습니다. 원격 연결이 허용되는지 여부를 확인하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도구를 사용하여 대상 인스턴스의 네트워크 구성 설정을 확인합니다. 원격 인스턴스도 명명된 인스턴스인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스가 대상 서버에서 활성화되어 실행되고 있는지 확인합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser는 명명된 인스턴스에 연결할 때 사용되는 포트 번호를 제공합니다.

### <a name="to-install-the-first-report-server-instance"></a>첫 번째 보고서 서버 인스턴스를 설치하려면

1.  배포에 포함할 첫 번째 보고서 서버 인스턴스를 설치합니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 설치할 때 보고서 서버 설치 옵션 페이지에서 **서버 구성 없이 설치** 옵션을 선택합니다.

2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작합니다.

3.  보고서 서버 웹 서비스 URL, 보고서 관리자 URL 및 보고서 서버 데이터베이스를 구성합니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 [보고서 서버 구성&#40;Reporting Services 기본 모드&#41;](../report-server/configure-a-report-server-reporting-services-native-mode.md)을 참조하세요.

4.  보고서 서버가 작동하는지 확인합니다. 자세한 내용은 [온라인 설명서의](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) Reporting Services 설치 확인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.

### <a name="to-install-and-configure-the-second-report-server-instance"></a>두 번째 보고서 서버 인스턴스를 설치 및 구성하려면

1.  설치 프로그램을 실행하여 두 번째 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 다른 컴퓨터에 설치하거나 같은 컴퓨터에 명명된 인스턴스로 설치합니다. Reporting Services를 설치할 때 보고서 서버 설치 옵션 페이지에서 **서버 구성 없이 설치** 옵션을 선택합니다.

2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작하고 방금 설치한 새 인스턴스에 연결합니다.

3.  첫 번째 보고서 서버 인스턴스에 사용한 것과 같은 데이터베이스에 보고서 서버를 연결합니다.

    1.  **데이터베이스** 를 클릭하여 데이터베이스 페이지를 엽니다.

    2.  **데이터베이스 변경**을 클릭합니다.

    3.  **기존 보고서 서버 데이터베이스 선택**을 클릭합니다.

    4.  사용할 보고서 서버 데이터베이스를 호스팅하는 SQL Server 데이터베이스 엔진 인스턴스의 서버 이름을 입력합니다. 이 인스턴스는 이전 지침에서 연결한 서버와 같아야 합니다.

    5.  **연결 테스트**를 클릭한 후 **다음**을 클릭합니다.

    6.  **보고서 서버 데이터베이스**에서 첫 번째 보고서 서버용으로 만든 데이터베이스를 선택한 후 **다음**을 클릭합니다. 기본 이름은 ReportServer입니다. ReportServerTempDB는 보고서를 처리할 때 임시 데이터를 저장하는 용도로만 사용되므로 선택하지 마십시오. 데이터베이스 목록이 비어 있는 경우 이전 네 단계를 반복하여 서버에 대한 연결을 설정합니다.

    7.  자격 증명 페이지에서 보고서 서버가 보고서 서버 데이터베이스에 연결하는 데 사용할 자격 증명 및 계정의 유형을 선택합니다. 첫 번째 보고서 서버 인스턴스와 같은 자격 증명을 사용하거나 다른 자격 증명을 사용할 수 있습니다. **다음**을 클릭합니다.

    8.  **요약** 을 클릭한 다음 **마침**을 클릭합니다.

4.  보고서 서버 웹 서비스 URL을 구성합니다. 아직 URL을 테스트하지 마십시오. 보고서 서버가 스케일 아웃 배포에 조인될 때까지 URL은 확인되지 않습니다.

5.  보고서 관리자 URL을 구성합니다. 아직 URL을 테스트하거나 배포를 확인하지 마십시오. 보고서 서버가 스케일 아웃 배포에 조인될 때까지 보고서 서버를 사용할 수 없습니다.

### <a name="to-join-the-second-report-server-instance-to-the-scale-out-deployment"></a>스케일 아웃 배포에 두 번째 보고서 서버 인스턴스를 조인하려면

1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 열고 첫 번째 보고서 서버 인스턴스에 다시 연결합니다. 첫 번째 보고서 서버는 해독 가능한 암호화 작업을 위해 이미 초기화되었으므로 추가 보고서 서버 인스턴스를 스케일 아웃 배포에 조인하는 데 사용할 수 있습니다.

2.  **확장 배포** 를 클릭하여 확장 배포 페이지를 엽니다. 보고서 서버 데이터베이스에 연결되어 있는 각 보고서 서버 인스턴스당 하나씩 두 개의 항목이 표시되어야 합니다. 첫 번째 보고서 서버 인스턴스는 조인되어야 하고 두 번째 보고서 서버는 "조인될 때까지 기다려야" 합니다. 배포에 비슷한 항목이 보이지 않을 경우 보고서 서버 데이터베이스를 사용하도록 이미 구성되고 초기화된 첫 번째 보고서 서버에 연결된 것입니다.

     ![스케일 아웃 배포 페이지의 부분 스크린샷](../../../2014/sql-server/install/media/scaloutscreen.gif "스케일 아웃 배포 페이지의 부분 스크린샷")

3.  스케일 아웃 배포 페이지에서 배포에 조인 되기를 기다리고 있는 보고서 서버 인스턴스를 선택 하 고 **서버 추가**를 클릭 합니다.

    > [!NOTE]
    >  **문제:** Reporting Services 보고서 서버 인스턴스를 스케일 아웃 배포에 조인 하려고 할 때 ' 액세스가 거부 되었습니다. '와 유사한 오류 메시지가 표시 될 수 있습니다.
    > 
    >  **해결 방법:** 첫 번째 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 암호화 키를 백업하고 이 키를 두 번째 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에 복원합니다. 그런 다음 두 번째 서버를 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 스케일 아웃 배포에 조인합니다.

4.  이제 두 보고서 서버 인스턴스가 작동하는지 확인할 수 있습니다. 두 번째 인스턴스를 확인하려면 Reporting Services 구성 도구를 사용하여 보고서 서버에 연결한 다음 웹 서비스 URL 또는 보고서 관리자 URL을 클릭합니다.

 로드 균형이 조정된 서버 클러스터에서 보고서 서버를 실행하려는 경우 추가 구성이 필요합니다. 자세한 내용은 [네트워크 부하 분산 클러스터에서 보고서 서버 구성](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md)을 참조하세요.

## <a name="see-also"></a>참고 항목
 Ssrs [Configuration Manager &#40;하는 서비스 계정 구성](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) Ssrs Configuration Manager [기본 모드 보고서 서버 데이터베이스 만들기](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)&#41;ssrs &#40;[&#40;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)&#41;보고서 서버 데이터베이스 연결 [구성 Configuration Manager](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md) ssrs&#41;[보고서 서버 데이터베이스 연결](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) 구성 &#40;Configuration Manager&#41;[배포에 대 한 암호화 키 추가 및 제거 &#40;ssrs Configuration Manager](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)&#41;[기본 모드 보고서 서버 관리](../report-server/manage-a-reporting-services-native-mode-report-server.md)


