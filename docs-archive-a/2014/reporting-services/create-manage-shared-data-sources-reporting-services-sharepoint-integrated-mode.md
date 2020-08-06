---
title: 공유 데이터 원본 만들기 및 관리 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], shared data sources
- shared data sources [Reporting Services]
ms.assetid: 2d3428e4-a810-4e66-a287-ff18e57fad76
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5eedb74dd5a24f40469b3ee6a4a24e97e6e59174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648327"
---
# <a name="create-and-manage-shared-data-sources-reporting-services-in-sharepoint-integrated-mode"></a>공유 데이터 원본 만들기 및 관리(SharePoint 통합 모드의 Reporting Services)
  SharePoint 라이브러리에서 보고서를 실행하는 경우 연결 정보는 보고서에 링크된 외부 파일에 또는 보고서 내에 정의될 수 있습니다. 연결 정보가 보고서 내에 포함되어 있는 경우 사용자 지정 데이터 원본이라고 하며 연결 정보가 외부 파일에 정의되어 있는 경우 공유 데이터 원본이라고 합니다. 외부 파일은 보고서 서버 데이터 원본 파일(.rsds)이나 Office 데이터 연결 파일(.odc)이 될 수 있습니다.  
  
 .rsds 파일은 .rds 파일과 비슷하지만 다른 스키마를 포함합니다. .rsds 파일을 만들기 위해 보고서 디자이너 또는 모델 디자이너에서 SharePoint 라이브러리로 .rds를 게시할 수 있습니다. 새 .rsds 파일은 원래 .rds 파일에서 생성됩니다. 또는 SharePoint 사이트에서 라이브러리에 새 파일을 만들 수 있습니다.  
  
 공유 데이터 원본을 만들거나 게시한 다음에는 연결 속성을 편집하거나 파일이 더 이상 사용되지 않는 경우 해당 파일을 삭제할 수 있습니다. 공유 데이터 원본을 삭제하기 전에 해당 원본이 보고서 및 보고서 모델에 사용되고 있는지 확인해야 합니다. 공유 데이터 원본을 참조하는 종속 항목을 확인하여 이 작업을 수행할 수 있습니다.  
  
 종속 항목 목록을 통해 공유 데이터 원본이 참조되고 있는지 여부를 확인할 수 있지만 해당 항목이 현재 사용되고 있는지는 확인할 수 없습니다. 공유 데이터 원본 또는 모델이 현재 사용되고 있는지를 확인하려면 보고서 서버 컴퓨터의 로그 파일을 검토합니다. 로그 파일에 대한 액세스 권한이 없거나 이 파일에 원하는 정보가 없는 경우 실제 상태를 확인하는 동안 보고서를 액세스할 수 없는 폴더로 이동합니다.  
  
### <a name="to-create-a-shared-data-source-rsds-file-sharepoint-2010"></a>SharePoint 2010에서 공유 데이터 원본 파일(.rsds)을 만들려면  
  
1.  라이브러리 리본 메뉴에 있는 **문서** 탭을 클릭합니다.  
  
2.  **새 문서** 메뉴에서 **보고서 데이터 원본**을 클릭합니다.  
  
    > [!NOTE]  
    >  메뉴에 **보고서 데이터 원본** 항목이 표시되지 않는 경우 보고서 데이터 원본의 콘텐츠 형식이 설정되어 있지 않은 것입니다. 자세한 내용은 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.  
  
3.  **이름**에 .rsds 파일을 설명하는 이름을 입력합니다.  
  
4.  **데이터 원본 유형**의 목록에서 데이터 원본 유형을 선택합니다. 자세한 내용은 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](create-deploy-and-manage-mobile-and-paginated-reports.md)을 참조하세요.  
  
5.  **연결 문자열**에 데이터 원본에 대한 포인터 및 외부 데이터 원본에 대한 연결을 설정하는 데 필요한 모든 기타 설정을 지정합니다. 사용하는 데이터 원본 유형에 따라 연결 문자열의 구문이 결정됩니다. 자세한 내용 및 예제는 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)을 참조 하세요.  
  
6.  **자격 증명**에서 보고서 서버가 외부 데이터 원본에 액세스하는 데 필요한 자격 증명을 얻는 방법을 지정합니다. 자격 증명은 저장 및 통합하거나 무인 보고서 처리를 위해 구성할 수 있으며 입력 메시지가 표시되도록 구성할 수도 있습니다.  
  
    -   보고서를 연 사용자의 자격 증명을 사용하여 데이터에 액세스하려면 **Windows 인증(통합)** 을 선택합니다. SharePoint 사이트 또는 팜에서 폼 인증을 사용하거나 트러스트된 계정을 통해 보고서 서버에 연결하는 경우 이 옵션을 선택하지 마십시오. 이 보고서에 대한 구독 또는 데이터 처리를 예약하려는 경우 이 옵션을 선택하지 마십시오. 이 옵션은 도메인에 Kerberos 인증을 설정한 경우나 데이터 원본이 보고서 서버와 같은 컴퓨터에 있는 경우에 가장 잘 작동합니다. Kerberos 인증을 해제하면 Windows 자격 증명이 하나의 다른 컴퓨터로만 전달될 수 있습니다. 따라서 추가 연결이 필요한 다른 컴퓨터에 외부 데이터 원본이 있는 경우 원하는 데이터 대신 오류가 표시됩니다.  
  
    -   사용자가 보고서를 실행할 때마다 자격 증명을 입력하도록 하려면 **자격 증명 확인** 을 선택합니다. 이 보고서에 대한 구독 또는 데이터 처리를 예약하려는 경우 이 옵션을 선택하지 마십시오.  
  
    -   단일 자격 증명 집합을 사용하여 데이터에 액세스하려면 **저장된 자격 증명** 을 선택합니다. 자격 증명은 저장되기 전에 암호화됩니다. 저장된 자격 증명의 인증 방법을 결정하는 옵션을 선택할 수 있습니다. 저장된 자격 증명이 Windows 사용자 계정에 속하면 Windows 자격 증명으로 사용을 선택합니다. 데이터베이스 서버에 대한 실행 컨텍스트를 설정하려면 **이 계정에 대한 실행 컨텍스트 설정** 을 선택합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 경우 이 옵션은 SETUSER 함수를 설정합니다. 자세한 내용은 [SETUSER&#40;Transact-SQL&#41;](/sql/t-sql/statements/setuser-transact-sql)를 참조하세요.  
  
    -   연결 문자열에 자격 증명을 지정하거나 보고서 서버에서 구성된 최소 권한 계정을 사용하여 보고서를 실행하려면 **자격 증명 필요 없음** 을 선택합니다. 보고서 서버에 이 계정이 구성되어 있지 않으면 사용자에게 자격 증명을 요청하는 메시지가 표시되며 보고서에 대해 정의한 예약된 작업이 실행되지 않습니다.  
  
7.  데이터 원본을 활성화 하려면 **이 데이터 원본 사용** 을 선택합니다. 데이터 원본이 구성되었으나 활성화되지 않았다면 사용자가 데이터 원본 기반의 보고서를 사용하려는 경우 오류 메시지가 표시됩니다.  
  
8.  **연결 테스트** 단추를 클릭하여 데이터 원본 구성의 유효성을 검사합니다.  
  
    > [!NOTE]  
    >  XML 데이터 원본 유형에서는 연결 테스트 단추를 지원하지 않습니다.  
  
9. **확인** 을 클릭하여 만들어진 공유 데이터 원본을 저장합니다.  
  
### <a name="to-view-dependent-items"></a>종속 항목을 보려면  
  
1.  .rsds 파일이 포함된 라이브러리를 엽니다.  
  
2.  공유 데이터 원본을 가리킵니다.  
  
3.  클릭하여 아래쪽 화살표를 표시하고 **종속 항목 보기**를 선택합니다.  
  
     보고서 모델의 경우 종속 항목 목록에 보고서 작성기에서 만든 보고서가 표시됩니다. 공유 데이터 원본의 경우에는 종속 항목 목록에 보고서와 보고서 모델이 모두 포함될 수 있습니다.  
  
### <a name="to-delete-a-shared-data-source-rsds-file"></a>공유 데이터 원본 파일(.rsds)을 삭제하려면  
  
1.  .rsds 파일이 포함된 라이브러리를 엽니다.  
  
2.  공유 데이터 원본을 가리킵니다.  
  
3.  클릭하여 아래쪽 화살표를 표시하고 **삭제**를 클릭합니다.  
  
 유지하려는 공유 데이터 원본을 실수로 삭제한 경우 동일한 연결 정보가 포함된 새 공유 데이터 원본을 만들 수 있습니다. 공유 데이터 원본을 다시 만든 다음에는 해당 데이터 원본을 사용하는 각 보고서와 모델을 열고 해당 공유 데이터 원본을 선택해야 합니다. 새 공유 데이터 원본 항목은 삭제한 항목과 다른 이름, 자격 증명 또는 연결 문자열 구문을 가질 수 있습니다. 연결이 동일한 데이터 원본으로 확인되는 한 데이터 원본 속성은 원래 값과 다를 수 있습니다.  
  
 보고서 모델을 삭제할 때는 주의해야 합니다. 모델을 삭제하면 해당 모델을 기반으로 하는 보고서를 보고서 작성기에서 더 이상 열고 수정할 수 없습니다. 기존 보고서에 사용되는 모델을 실수로 삭제한 경우 해당 모델을 다시 생성하고 이 모델을 사용하는 보고서를 다시 만들어 저장한 다음 사용할 모델 항목 보안을 다시 지정해야 합니다. 단순히 모델을 다시 생성한 다음 기존 보고서에 연결할 수는 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  