---
title: 리프 멤버 준비 테이블(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members staging table [Master Data Services]
- database [Master Data Services], members staging table
ms.assetid: a8c953da-ec20-47dc-8656-ed5f0dfed89b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b4e66dbfa26ea1e6090d128756a9542d349c9929
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738475"
---
# <a name="leaf-member-staging-table-master-data-services"></a>리프 멤버 준비 테이블(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 리프 멤버 준비 테이블(stg.name_Leaf)을 사용하여 리프 멤버를 만들고, 업데이트하고, 비활성화하고, 삭제할 수 있습니다. 또한 리프 멤버에 대한 특성 값을 업데이트하기 위해 사용할 수도 있습니다.  
  
##  <a name="table-columns"></a><a name="TableColumns"></a>테이블 열  
 다음 표에서는 리프 준비 테이블에 나오는 각 필드의 용도에 대해 설명합니다.  
  
|열 이름|설명|  
|-----------------|-----------------|  
|**ID**|자동으로 할당된 식별자입니다. 이 필드에 값을 입력하지 마십시오. 일괄 처리를 처리하지 않은 경우 이 필드가 비어 있습니다.|  
|**ImportType**<br /><br /> 필수|다음 **ID** 값은 준비 된 데이터가 데이터베이스에 이미 있는 데이터와 일치 하는 경우 수행할 작업을 결정 합니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> **0**: 새 멤버를 만듭니다. 준비된 데이터가 NULL이 아닌 경우에만 기존 MDS 데이터를 준비된 데이터로 바꿉니다. NULL 값은 무시됩니다. string 특성 값을 NULL로 변경하려면 해당 값을 **~NULL~** 로 설정합니다. number 특성 값을 NULL로 변경하려면 해당 값을 **-98765432101234567890**으로 설정합니다. datetime 특성 값을 NULL로 변경하려면 해당 값을 **5555-11-22T12:34:56**으로 설정합니다.<br /><br /> **1**: 새 멤버만 만듭니다. 기존 MDS 데이터는 업데이트할 수 없습니다.<br /><br /> **2**: 새 멤버를 만듭니다. 기존 MDS 데이터를 준비된 데이터로 바꿉니다. NULL 값을 가져오는 경우 NULL 값이 기존 MDS 값을 덮어씁니다.<br /><br /> **3**: 코드 값을 기반으로 멤버를 비활성화합니다. 모든 특성, 계층 및 컬렉션 멤버 자격, 트랜잭션이 유지 관리되지만 더 이상 UI에서 사용할 수는 없습니다. 멤버가 다른 멤버의 도메인 기반 특성 값으로 사용되는 경우 비활성화할 수 없습니다. 대체 방법은 **ImportType5**를 참조하세요.<br /><br /> **4**: 코드 값을 기반으로 멤버를 영구적으로 삭제합니다. 모든 특성, 계층 및 컬렉션 멤버 자격, 트랜잭션이 영구적으로 삭제됩니다. 멤버가 다른 멤버의 도메인 기반 특성 값으로 사용되는 경우 삭제할 수 없습니다. 대체 방법은 **ImportType6**을 참조하세요.<br /><br /> **5**: **코드** 값을 기반으로 멤버를 비활성화합니다. 모든 특성, 계층 및 컬렉션 멤버 자격, 트랜잭션이 유지 관리되지만 더 이상 UI에서 사용할 수는 없습니다. 멤버가 다른 멤버의 도메인 기반 특성 값으로 사용되는 경우 관련 값이 NULL로 설정됩니다. ImportType 5는 리프 멤버 전용입니다.<br /><br /> **6**: **코드** 값을 기반으로 멤버를 영구적으로 삭제합니다. 모든 특성, 계층 및 컬렉션 멤버 자격, 트랜잭션이 영구적으로 삭제됩니다. 멤버가 다른 멤버의 도메인 기반 특성 값으로 사용되는 경우 관련 값이 NULL로 설정됩니다. ImportType 6은 리프 멤버 전용입니다.|  
|**ImportStatus_ID**<br /><br /> 필수|가져오기 프로세스의 상태입니다. 가능한 값은 다음과 같습니다.<br /><br /> **0**- 레코드를 준비할 수 있음을 나타냅니다.<br /><br /> **1**- 자동으로 할당되며 레코드 준비 프로세스가 성공했음을 나타냅니다.<br /><br /> **2**- 자동으로 할당되며 레코드 준비 프로세스가 실패했음을 나타냅니다.|  
|**Batch_ID**<br /><br /> 웹 서비스에만 필요|준비할 레코드를 그룹화하는 자동 할당 식별자입니다. 일괄 처리의 모든 멤버에는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ID **열의** 사용자 인터페이스에 표시되는 이 식별자가 할당됩니다.<br /><br /> 일괄 처리를 처리하지 않은 경우 이 필드가 비어 있습니다.|  
|**BatchTag**<br /><br /> 필수, 웹 서비스에서 사용하는 경우 제외|일괄 처리의 고유 이름으로, 최대 50자입니다.|  
|**ErrorCode**|오류 코드를 표시합니다. **ImportStatus_ID**가 **2**인 모든 레코드의 경우 [준비 프로세스 오류&#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)를 참조하세요.|  
|**코드**<br /><br /> 필수(단, **ImportType 1** 또는 **2**에 대해 코드가 자동으로 생성되는 경우는 제외). 자세한 내용은 [코드 자동 생성&#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)을 참조하세요.|멤버의 고유 코드입니다.|  
|**이름**<br /><br /> 선택 사항|멤버의 이름입니다.|  
|**NewCode**|멤버 코드를 변경하는 경우에만 사용합니다.|  
|\<Attribute name>|엔터티의 각 특성에 대해 열이 존재합니다. **ImportType****0** 또는 **2**에 사용합니다. 자유 형식 특성의 경우 특성의 새 텍스트 또는 문자열 값을 지정합니다. 도메인 기반 특성의 경우에는 특성이 될 멤버의 코드를 지정합니다. 링크 특성의 경우 URL이 **http://** 로 시작해야 합니다.<br /><br /> 참고: 파일 특성을 준비할 수 없습니다.|  
  
##  <a name="did-this-article-help-you-were-listening"></a><a name="feedback"></a>이 문서가 도움이 되었나요? 대기 중입니다.  
 어떤 정보를 찾고 계세요? 정보를 찾으셨나요? 사용자 의견을 듣고 콘텐츠를 개선 하 고 있습니다. 의견을 제출 하세요.[sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Leaf%20Member%20Staging%20Table%20page)  
  
## <a name="see-also"></a>참고 항목  
 [준비 프로세스를 사용 하 여 MDS(Master Data Services)에서 멤버 로드 또는 업데이트](add-update-and-delete-data-master-data-services.md)   
 [데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [준비 프로세스 중에 발생 하는 오류를 보려면 MDS(Master Data Services) &#40;&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [준비 프로세스 오류&#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
