---
title: '2단계: 배포 번들 확인 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f452a87154175ac05a050761d8f12b6bfe61cd8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647112"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>2단계: 배포 번들 확인
  1단원에서는 Deployment Tutorial 프로젝트를 만들고 패키지와 보조 파일을 프로젝트에 추가했습니다. 이전 태스크에서는 프로젝트를 위한 배포 유틸리티를 작성했습니다.  
  
 이 태스크에서는 배포 번들의 내용을 확인합니다. 배포 번들은 대상 컴퓨터에 복사하고 패키지를 설치하는 데 사용하는 폴더입니다. 배포 유틸리티의 위치로 기본값인 bin\Deployment를 사용한 경우 배포 번들은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 Deployment Tutorial 폴더 내에 있는 Bin\Deployment 폴더입니다.  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>배포 번들의 내용을 확인하려면  
  
1.  컴퓨터에서 bin\Deployment 폴더를 찾습니다.  
  
2.  다음 파일이 있는지 확인합니다.  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  Deployment Tutorial.SSISDeploymentManifest를 마우스 오른쪽 단추로 클릭하고 **연결 프로그램**을 가리킨 다음 **Internet Explorer**를 클릭합니다. 또한 메모장과 같은 텍스트 편집기에서 파일을 열 수도 있습니다. 파일의 XML 코드는 다음과 같아야 합니다.  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  `AllowConfigurationChanges`특성 값이 **true** 이 고 xml에 두 패키지 각각에 대 한 요소 `Package` , 두 개의 `MiscellaneousFile` 비 패키지 파일에 대 한 요소, `ConfigurationFile` 두 xml 구성 파일 각각에 대 한 요소가 포함 되어 있는지 확인 합니다.  
  
5.  Internet Explorer 또는 텍스트 편집기를 종료합니다.  
  
## <a name="next-lesson"></a>다음 단원  
 [3단원: 패키지 설치](../integration-services/lesson-3-install-ssis-package.md)  
  
![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**<br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지를 방문하세요.](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
  
