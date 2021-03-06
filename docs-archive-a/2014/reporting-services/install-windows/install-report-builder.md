---
title: 보고서 작성기 (보고서 작성기)의 독립 실행형 버전을 설치 합니다. Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ba8c132125f56ad833a71a1c82221e2bf28d13e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652627"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a>독립 실행형 버전의 보고서 작성기 설치(보고서 작성기)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=53613) 의 기능 팩에 있는 보고서 작성기를 설치 하거나 ReportBuilder3_x86.msi, 보고서 작성기 용 Windows Installer 패키지가 다운로드 된 공용 폴더 등의 위치를 설치할 수 있습니다.  
  
 보고서 작성기의 명령줄 설치를 수행하고 인수를 제공하여 설치를 사용자 지정할 수도 있습니다. 표준 MSI 내장 매개 변수 외에도 RBINSTALLDIR 및 REPORTSERVERURL 보고서 작성기 제공 하는 사용자 지정 매개 변수를 사용할 수 있습니다. RBINSTALLDIR은 보고서 작성기의 루트 설치 폴더를 지정합니다. REPORTSERVERURL은 보고서 작성기에서 보고서를 서버에 저장하기 위해 사용하는 기본 보고서 서버를 지정합니다.  
  
 사용자 인터페이스의 상호 작용이 필요 없는 완전 자동 설치를 수행하려면 **/quiet** 옵션을 지정합니다. 기본적으로 quiet 옵션 플래그를 사용하면 설치 오류가 표시되지 않습니다. 따라서 quite 옵션을 사용할 때는 로깅을 지정하는 **/l** 옵션을 함께 사용하는 것이 좋습니다.  
  
> [!IMPORTANT]  
>  Windows Vista 및 Windows 7의 경우 보안 기능으로 인해 명령줄 작업을 실행하려면 높은 권한이 필요합니다. 따라서 명령줄을 실행할 경우 사용 권한을 요청하는 메시지가 표시되므로 자동 설치를 수행할 수 없습니다. 자동 설치를 수행하려면 관리자 권한으로 명령줄을 실행해야 합니다.  
  
### <a name="to-install-report-builder-from-the-download-site"></a>다운로드 사이트에서 보고서 작성기를 설치하려면  
  
1.  [Microsoft SQL Server 2012 보고서 작성기](https://go.microsoft.com/fwlink/?LinkID=219138) 으로 이동 하 여 웹 페이지의 보고서 작성기 섹션을 찾습니다.  
  
2.  **X86 패키지**를 클릭 합니다.  
  
3.  **파일 다운로드** 대화 상자에서 **실행**을 클릭 합니다.  
  
    > [!IMPORTANT]  
    >  신뢰할 수 있는 출처에서 제공하는 파일만 다운로드합니다.  
  
4.  Internet Explorer 대화 상자에서 **실행**을 클릭 합니다.  
  
    > [!IMPORTANT]  
    >  신뢰할 수 있는 출처에서 제공하는 파일만 실행합니다.  
  
5.  Microsoft SQL Server 보고서 작성기 마법사가 시작됩니다.  
  
6.  **설치 마법사 시작** 페이지에서 **다음**을 클릭 합니다.  
  
7.  **사용권 계약** 페이지에서 규약을 읽은 **다음 동의 함 옵션을** 선택 합니다. **다음**을 클릭합니다.  
  
8.  사용자 이름과 회사 이름을 입력합니다. **다음**을 클릭합니다.  
  
9. **기능 선택** 페이지에서 필요에 따라 **찾아보기** 또는 **디스크 비용**을 클릭 합니다. **다음**을 클릭합니다.  
  
    -   **찾아보기** 를 클릭 하 보고서 작성기 기본 위치를 확인 하 고 업데이트 합니다.  
  
        > [!NOTE]  
        >  보고서 작성기의 기본 설치 폴더는 \<drive> Program Files\Microsoft SQL Server입니다.  
  
    -   **디스크** 공간을 클릭 하 보고서 작성기 사용 하는 디스크 공간 크기를 확인 합니다.  
  
        > [!NOTE]  
        >  볼륨에 디스크 여유 공간이 충분하지 않은 경우 해당 볼륨이 강조 표시됩니다.  
  
10. **기본 대상 서버** 페이지에서 필요 시 대상 보고서 서버의 URL을 제공합니다(기본값과 다른 경우). **다음**을 클릭합니다.  
  
    > [!NOTE]  
    >  보고서 서버에 연결되었을 때 보고서 작성기로 작업할 계획이라면 이 단계에서 서버의 URL을 제공하는 것이 좋습니다. 그러나 보고서 작성기에서 작업할 때 **옵션** 대화 상자에서이 작업을 수행할 수도 있습니다.  
  
11. **설치** 를 클릭 하 보고서 작성기 설치를 완료 합니다.  
  
### <a name="to-install-report-builder-from-a-share"></a>공유에서 보고서 작성기를 설치하려면  
  
1.  로컬 컴퓨터에 보고서 작성기를 설치하기 위해 실행하는 ReportBuilder3_x86.msi.msi의 위치는 관리자에게 문의하십시오.  
  
2.  보고서 작성기의 Windows Installer 패키지(MSI)인 ReportBuilder3_x86.msi.msi를 찾아서 클릭합니다.  
  
     Microsoft SQL Server 보고서 작성기 마법사가 시작됩니다.  
  
3.  **설치 마법사 시작** 페이지에서 **다음**을 클릭 합니다.  
  
4.  **사용권 계약** 페이지에서 규약을 읽은 **다음 동의 함 옵션을** 선택 합니다. **다음**을 클릭합니다.  
  
5.  사용자 이름과 회사 이름을 입력합니다. **다음**을 클릭합니다.  
  
6.  **기능 선택** 페이지에서 필요에 따라 **찾아보기** 또는 **디스크 비용**을 클릭 합니다. **다음**을 클릭합니다.  
  
    -   **찾아보기** 를 클릭 하 보고서 작성기 기본 위치를 확인 하 고 업데이트 합니다.  
  
        > [!NOTE]  
        >  보고서 작성기의 기본 설치 폴더는 \<drive> Program Files\Microsoft SQL Server입니다.  
  
    -   **디스크** 공간을 클릭 하 보고서 작성기 사용 하는 디스크 공간 크기를 확인 합니다.  
  
        > [!NOTE]  
        >  볼륨에 디스크 여유 공간이 충분하지 않은 경우 해당 볼륨이 강조 표시됩니다.  
  
7.  **기본 대상 서버** 페이지에서 필요 시 대상 보고서 서버의 URL을 제공합니다(기본값과 다른 경우). **다음**을 클릭합니다.  
  
    > [!NOTE]  
    >  보고서 서버에 연결되었을 때 보고서 작성기로 작업할 계획이라면 이 단계에서 서버의 URL을 제공하는 것이 좋습니다. 그러나 보고서 작성기에서 작업할 때 **옵션** 대화 상자에서이 작업을 수행할 수도 있습니다.  
  
8.  **설치** 를 클릭 하 보고서 작성기 설치를 완료 합니다.  
  
### <a name="to-install-report-builder-from-the-command-line"></a>명령줄에서 보고서 작성기를 설치하려면  
  
1.  [Microsoft SQL Server 2012 보고서 작성기](https://go.microsoft.com/fwlink/?LinkID=219138) 으로 이동 하 여 보고서 작성기 섹션을 찾습니다.  
  
2.  **X86 패키지**를 클릭 합니다.  
  
3.  저장을 클릭합니다.  
  
4.  필요에 따라 저장할 위치로 이동 하 고 다른 **이름으로 저장** 옵션이 **패키지 Windows Installer**있는지 확인 한 다음 **저장**을 클릭 합니다.  
  
5.  **시작** 메뉴에서 **실행**을 클릭합니다.  
  
6.  열기 입력란에 을(를) 입력합니다.`cmd.`  
  
7.  명령 프롬프트 창에서 ReportBuilder3_x86.msi를 저장한 폴더로 이동합니다.  
  
8.  다음 형식으로 명령을 입력합니다.  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     보고서 작성기 설치와 관련 된 두 가지 옵션은 RBINSTALLDIR 및 REPORTSERVERURL입니다. 이러한 인수는 명령줄에 포함하지 않아도 됩니다. 기본 명령은 다음과 같습니다.  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. 명령을 실행하려면 Enter 키를 누릅니다.  
  
## <a name="see-also"></a>참고 항목  
 [설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md)   
 [독립 실행형 버전의 보고서 작성기 &#40;보고서 작성기을 제거&#41;](install-report-builder.md)  
  
  
