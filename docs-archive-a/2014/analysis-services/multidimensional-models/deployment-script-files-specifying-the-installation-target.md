---
title: 설치 대상 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651934"
---
# <a name="specifying-the-installation-target"></a>설치 대상 지정
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]배포 마법사는 deploymenttargets 파일에서 설치 대상 정보를 읽습니다. \<*project name*> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트를 빌드할 때이 파일을 만듭니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]속성 페이지 대화 상자의 **배포** 페이지에 지정 된 데이터베이스 및 서버를 사용 하 여 *\<project name>* **Properties Pages** \<*project name*> .targets 파일을 만듭니다.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>배포를 위한 설치 대상 수정  
 일부 경우에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 페이지에 지정된 것과 다른 데이터베이스 또는 **인스턴스에** 프로젝트를 배포해야 할 수 있습니다. 예를 들어 배포 전에 테스트를 위해 서버에 프로젝트를 배포한 다음 테스트를 마친 후에 프로덕션 서버에 배포할 수 있습니다. 또한 네트워크 로드 균형 조정 클러스터의 여러 프로덕션 서버나 준비 서버(staging server) 및 프로덕션 서버에 완료되고 테스트를 마친 프로젝트를 배포할 수 있습니다.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 다른 데이터베이스나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 배포할 경우 다음 절차에 설명된 방법 중 하나를 사용하여 입력 파일에 있는 설치 대상을 변경할 수 있습니다.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>입력 파일을 생성한 다음 설치 대상을 변경하려면  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 대화형으로 실행합니다. **설치 대상** 페이지에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 및 데이터베이스에 대한 새 대상을 지정합니다.  
  
     또는  
  
-   명령 프롬프트에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하여 응답 파일 모드에서 마법사를 실행하도록 설정합니다. 응답 파일 모드에 대한 자세한 내용은 [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md)을 참조하십시오.  
  
     또는  
  
-   \<*project name*>텍스트 편집기를 사용 하 여 deploymenttargets 파일을 수정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [파티션 및 역할 배포 옵션 지정](deployment-script-files-partition-and-role-deployment-options.md)   
 [솔루션 배포를 위한 구성 설정 지정](deployment-script-files-solution-deployment-config-settings.md)   
 [처리 옵션 지정](deployment-script-files-specifying-processing-options.md)  
  
  
