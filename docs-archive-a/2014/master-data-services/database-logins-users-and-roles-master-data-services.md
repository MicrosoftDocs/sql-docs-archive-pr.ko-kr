---
title: 데이터베이스 로그인, 사용자 및 역할(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eadd6fb4d5b9798920d65119386aa2c58afebfa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736465"
---
# <a name="database-logins-users-and-roles-master-data-services"></a>데이터베이스 로그인, 사용자 및 역할(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에는 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅하는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 자동으로 설치되는 로그인, 사용자 및 역할이 포함되어 있습니다. 이러한 로그인, 사용자 및 역할은 수정하면 안 됩니다.  
  
## <a name="logins"></a>로그인  
  
|로그인|설명|  
|-----------|-----------------|  
|`mds_dlp_login`|UNSAFE 어셈블리 만들기를 허용합니다.<br /><br /> -임의로 생성된 암호를 가진 비활성화된 로그인입니다.<br /><br /> - [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 경우 dbo에 매핑됩니다.<br /><br /> -msdb의 경우 mds_clr_user가 이 로그인에 매핑됩니다.<br /><br /> <br /><br /> 자세한 내용은 [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)을 참조하세요.|  
|`mds_email_login`|알림에 사용되는 활성화된 로그인입니다.<br /><br /> msdb 및 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 경우 mds_email_user가 이 로그인에 매핑됩니다.|  
  
## <a name="msdb-users"></a>msdb 사용자  
  
|사용자|설명|  
|----------|-----------------|  
|`mds_clr_user`|사용되지 않습니다.<br /><br /> mds_dlp_login에 매핑됩니다.|  
|`mds_email_user`|알림에 사용됩니다.<br /><br /> mds_email_login에 매핑됩니다.<br /><br /> DatabaseMailUserRole 역할의 멤버입니다.|  
  
## <a name="master-data-services-database-users"></a>Master Data Services 데이터베이스 사용자  
  
|사용자|설명|  
|----------|-----------------|  
|`mds_email_user`|알림에 사용됩니다.<br /><br /> mdm 스키마에 대한 SELECT 권한을 가집니다.<br /><br /> mdm.MemberGetCriteria 사용자 정의 테이블 형식에 대한 EXECUTE 권한을 가집니다.<br /><br /> mdm.udpNotificationQueueActivate 저장 프로시저에 대한 EXECUTE 권한을 가집니다.|  
|**mds_schema_user**|mdm 및 mdq 스키마를 소유합니다. 기본 스키마는 mdm입니다.<br /><br /> 매핑되는 로그인이 없습니다.|  
|**mds_ssb_user**|Service Broker 태스크를 실행하는 데 사용됩니다.<br /><br /> 모든 스키마에 대한 DELETE, INSERT, REFERENCES, SELECT 및 UPDATE 권한을 가집니다.<br /><br /> 매핑되는 로그인이 없습니다.|  
  
## <a name="master-data-services-database-role"></a>Master Data Services 데이터베이스 역할  
  
|역할|설명|  
|----------|-----------------|  
|`mds_exec`|이 역할은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 웹 애플리케이션을 만들고 애플리케이션 풀의 계정을 지정하는 경우 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에 지정하는 계정을 포함합니다. mds_exec 역할은 다음을 가집니다.<br /><br /> 모든 스키마에 대 한 **EXECUTE** 권한<br /><br /> 이러한 테이블에 대 한 **ALTER**, **INSERT**및 **SELECT** 권한:<br />mdm.tblStgMember<br />mdm.tblStgMemberAttribute<br />mdm.tbleStgRelationship<br /><br /> 다음 테이블에 대 한 **SELECT** 권한:<br />mdm.tblUser<br />mdm.tblUserGroup<br />mdm.tblUserPreference<br /><br /> 이러한 보기에 대 한 **SELECT** 권한:<br />mdm.viw_SYSTEM_SECURITY_NAVIGATION<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br />mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>스키마  
  
|역할|설명|  
|----------|-----------------|  
|`mdm`|mdq 스키마에 포함된 함수 이외의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 및 Service Broker 개체를 모두 포함합니다.|  
|`mdq`|정규식 또는 유사성에 따라 멤버 결과를 필터링하는 데 관련이 있으며 알림 전자 메일의 서식을 지정하기 위한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 함수를 포함합니다.|  
|**stg**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 테이블, 저장 프로시저 및 준비 프로세스와 관련된 뷰를 포함합니다. 이러한 개체는 삭제하지 마십시오. 준비 프로세스에 대 한 자세한 내용은 [데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md)를 참조 하세요.|  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 개체 보안&#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
