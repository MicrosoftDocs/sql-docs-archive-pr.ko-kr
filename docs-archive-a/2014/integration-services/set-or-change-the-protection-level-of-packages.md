---
title: 패키지의 보호 수준을 설정 하거나 변경 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da8e63028498097b4321e4ef1383fbc8aa5845b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741127"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>패키지 보호 수준 설정 또는 변경
  패키지 내용과 패키지에 포함된 중요한 값(예: 암호)에 대한 액세스를 제어하려면 `ProtectionLevel` 속성의 값을 설정합니다. 프로젝트에 포함된 패키지는 프로젝트 생성을 위해 프로젝트와 보호 수준이 동일해야 합니다. 프로젝트에서 `ProtectionLevel` 속성을 변경한 경우 패키지에 대한 프록시 설정을 수동으로 업데이트해야 합니다.  
  
 `ProtectionLevel`패키지 수명 주기의 여러 단계에서 패키지에 적합 한 설정을 확인 하는 방법에 대 한 자세한 내용은 [패키지의 중요 한 데이터에 대 한 Access Control](security/access-control-for-sensitive-data-in-packages.md)를 참조 하세요. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 보안 기능에 대한 개요는 [보안 개요&#40;Integration Services&#41;](security/security-overview-integration-services.md)를 참조하세요.  
  
 이 항목의 절차에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 또는 dtutil 명령 프롬프트 유틸리티를 사용하여 `ProtectionLevel` 속성을 변경하는 방법에 대해 설명합니다.  
  
> [!NOTE]  
>  이 항목의 절차 외에도 일반적으로 패키지를 가져오거나 내보낼 때 패키지의 `ProtectionLevel` 속성을 설정하거나 변경할 수 있습니다. 또한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 사용하여 패키지를 저장할 때도 패키지의 `ProtectionLevel` 속성을 변경할 수 있습니다.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>SQL Server Data Tools에서 패키지 보호 수준을 설정하거나 변경하려면  
  
1.  항목의 속성에 사용할 수 있는 값을 검토 하 `ProtectionLevel` 고 패키지 [의 보호 수준을 설정](security/access-control-for-sensitive-data-in-packages.md)하 고 패키지에 대 한 적절 한 값을 결정 합니다.  
  
2.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 패키지를 엽니다.  
  
4.  속성 창에 패키지 속성이 표시되지 않으면 디자인 화면을 클릭합니다.  
  
5.  속성 창의 **보안** 그룹에서 속성에 대 한 적절 한 값을 선택 `ProtectionLevel` 합니다.  
  
     암호가 필요한 보호 수준을 선택한 경우 암호를 **PackagePassword** 속성의 값으로 입력합니다.  
  
6.  **파일** 메뉴에서 **선택한 항목 저장** 을 선택하여 수정한 패키지를 저장합니다.  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>명령 프롬프트에서 패키지 보호 수준을 설정하거나 변경하려면  
  
1.  항목의 속성에 사용할 수 있는 값을 검토 하 `ProtectionLevel` 고 패키지 [의 보호 수준을 설정](security/access-control-for-sensitive-data-in-packages.md)하 고 패키지에 대 한 적절 한 값을 결정 합니다.  
  
2.  `Encrypt` [Dtutil 유틸리티](dtutil-utility.md)항목에서 옵션에 대 한 매핑을 검토 하 고 선택한 속성의 값으로 사용할 적절 한 정수를 결정 합니다 `ProtectionLevel` .  
  
3.  명령 프롬프트 창을 엽니다.  
  
4.  명령 프롬프트에서 `ProtectionLevel` 속성을 설정할 패키지가 들어 있는 폴더로 이동합니다.  
  
     다음 단계에 나오는 구문 예에서는 이 폴더가 현재 폴더라고 가정합니다.  
  
5.  다음 예 중 하나와 비슷한 명령을 사용하여 패키지 보호 수준을 설정하거나 변경합니다.  
  
    -   다음 명령은 파일 시스템에 있는 개별 패키지의 `ProtectionLevel` 속성을 수준 2, "암호로 중요한 데이터 암호화"로 설정하고 암호로 "strongpassword"를 사용합니다.  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   다음 명령은 파일 시스템의 특정 폴더에 있는 모든 패키지의 `ProtectionLevel` 속성을 수준 2, "암호로 중요한 데이터 암호화"로 설정하고 암호로 "strongpassword"를 사용합니다.  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         배치 파일에서 비슷한 명령을 사용할 경우 배치 파일에 파일 자리 표시자로 "%f" 대신 "%%f"를 입력합니다.  
  
## <a name="see-also"></a>참고 항목  
 [dtutil 유틸리티](dtutil-utility.md)  
  
  
