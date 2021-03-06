---
title: 게시자 속성 SQL Server 복제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732572"
---
# <a name="sql-server-replication-publisher-properties"></a>게시자 속성 SQL Server 복제
  이 섹션에서는 배포자 및 게시자에서 사용할 수 있는 게시자 속성에 대 한 정보를 제공 합니다. 

## <a name="general"></a>일반  
  **게시자 속성** 대화 상자의 **일반** 페이지는 게시자가 사용하는 배포자 및 배포 데이터베이스에 대한 읽기 전용 정보를 표시합니다. 게시자에 대한 배포자 또는 배포 데이터베이스를 변경하려면 다음을 수행하십시오.  
  
1.  게시자에서 게시를 해제합니다. 자세한 내용은 [게시 및 배포 해제](disable-publishing-and-distribution.md)를 참조하세요.    
2.  게시 및 배포를 다시 구성합니다. 자세한 내용은 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)을 참조하세요.  

## <a name="distributor"></a>배포자
  **게시자 속성** 대화 상자를 사용하여 게시자와 이 게시자의 배포자 간 관계와 연결된 속성을 보고 수정할 수 있습니다.  
  
### <a name="options"></a>옵션  
 **에이전트에서 게시자 연결**  
 다음 에이전트가 배포자에서 게시자로 연결하는 컨텍스트를 지정합니다.  
  
-   지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트  
  
-   Oracle 게시에 대한 스냅샷 에이전트 및 로그 판독기 에이전트  
  
 이러한 에이전트가 실행되는 **Windows 계정의 컨텍스트를 사용하여 게시자에 연결하거나** SQL Server 인증 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 을 지정한 다음 **로그인**및 **암호** 에 값을 입력하려면 **에이전트 프로세스 계정 가장**을 선택합니다. **에이전트 프로세스 계정 가장**을 선택하는 것이 좋습니다. 에이전트 보안에 대한 자세한 내용은 [복제 에이전트 보안 모델](security/replication-agent-security-model.md)을 참조하세요.  
  
 이러한 에이전트가 실행되는 Windows 계정은 새 게시 마법사에서 지정합니다. 이 계정은 다음 대화 상자에서 변경할 수 있습니다.  
  
-   큐 판독기 에이전트의 **배포자 속성** 대화 상자  
  
-   스냅샷 에이전트 및 로그 판독기 에이전트의 **게시 속성** 대화 상자  
  
 **기타**  
 **게시자 유형** 및 **배포 데이터베이스 이름** 속성은 읽기 전용입니다. **기본 스냅샷 폴더** 속성은 변경할 수 있습니다. 스냅샷 폴더에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요.  
  

## <a name="publication-databases"></a>게시 데이터베이스
  **게시자 속성** 대화 상자의 **게시 데이터베이스** 페이지를 사용하여 **sysadmin** 고정 서버 역할의 사용자가 복제용 데이터베이스를 설정할 수 있습니다. 데이터베이스를 설정한다고 해서 그 데이터베이스가 게시되는 것은 아닙니다. 데이터베이스를 설정하면 설정된 데이터베이스에 대한 **db_owner** 고정 데이터베이스 역할의 사용자가 그 데이터베이스에 하나 이상의 게시를 만들 수 있습니다.  
  
### <a name="options"></a>옵션  
 **트랜잭션**  
 **db_owner** 고정 데이터베이스 역할의 사용자가 데이터베이스에 스냅샷 게시 또는 트랜잭션 게시를 만들 수 있게 하려면 이 확인란을 선택합니다. 
  
 **병합**  
 **db_owner** 고정 데이터베이스 역할의 사용자가 데이터베이스에 병합 게시를 만들 수 있게 하려면 이 확인란을 선택합니다.  

## <a name="subscribers"></a>게시자 속성

  **게시자 속성** 대화 상자의 **구독자** 페이지는  이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 게시자에 사용됩니다. 이 페이지를 사용하여 구독자가 이 게시자의 게시에서 데이터를 받도록 설정할 수 있습니다. 구독자가 이 게시자에서 데이터를 받도록 설정해도 이 게시자의 게시에 대한 구독이 생성되지 않습니다. 구독을 만들려면 새 구독 마법사를 사용해야 합니다.  
  
### <a name="options"></a>옵션  
 **게시자 속성**  
 **구독자** 속성 표에서는 이 게시자의 게시에서 데이터를 받도록 설정된 구독자를 표시합니다. 추가 속성을 보고 설정하려면 구독자 옆에 있는 속성 단추 (**...**)를 클릭합니다.  
  
 **추가**  
 구독자를 추가하려면 **추가** 를 클릭한 다음 **SQL Server 구독자 추가** 또는 **SQL Server 이외 구독자 추가**를 클릭합니다.  

## <a name="see-also"></a>참고 항목  
 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)   

  
  
