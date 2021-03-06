---
title: '1 단원: Azure Storage 개체 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d46c6d22ffd92dbf8035bff140960af8ef56122d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647393"
---
# <a name="lesson-1-create-azure-storage-objects"></a>1단원: Azure Storage 개체 만들기
  클라우드 스토리지에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업을 만들려면 먼저 스토리지 계정을 만든 다음 blob 컨테이너를 만들어야 합니다. 1 단원에서는 Azure 관리 포털에 로그인 하 여 저장소 계정 및 blob 컨테이너를 만드는 단계를 안내 합니다.  
  
## <a name="create-a-storage-account"></a>스토리지 계정 만들기  
 Azure 관리 포털에서 저장소 계정을 만들려면 다음 단계를 사용 합니다.  
  
1.  자신의 계정을 사용하여 Azure 관리 포털에 로그인합니다. Azure 계정이 없는 경우 [azure 3 개월 무료 평가판을 방문](https://go.microsoft.com/fwlink/?LinkId=271927)하세요.  
  
     ![Azure 로그인 화면](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure 로그인 화면")  
  
2.  [여기](https://go.microsoft.com/fwlink/?LinkId=271926)에서 자세한 단계별 지침을 사용하여 스토리지 계정을 만드십시오.  
  
3.  이전 단계에서 만든 스토리지 계정으로 이동합니다. 웹 페이지의 아래쪽 가운데에서 **키 관리**를 클릭합니다. 계정 정보가 표시됩니다. 스토리지 계정 이름과 액세스 키를 복사합니다. 이 정보는 SQL 저장된 자격 증명을 만드는 데 필요합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 이 정보를 사용하여 스토리지 계정에 액세스하여 백업을 만들 수 있습니다.  
  
     ![Azure Storage 계정 키 스크린샷](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Azure Storage 계정 키 스크린샷")  
  
    > [!NOTE]  
    >  또한 REST API를 사용하여 프로그래밍 방식으로 스토리지 계정을 만들 수도 있습니다. 자세한 내용은 [스토리지 계정 만들기](https://go.microsoft.com/fwlink/?LinkId=271928)를 참조하십시오.  
  
### <a name="create-a-blob-container"></a>Blob 컨테이너 만들기  
 컨테이너는 Blob 집합의 그룹화를 제공합니다. 모든 Blob은 컨테이너에 있어야 합니다. 계정에는 개수에 제한 없이 컨테이너를 포함할 수 있지만 적어도 하나 이상 포함해야 합니다. 한 컨테이너에 저장될 수 있는 Blob 수에도 제한이 없습니다.  
  
 컨테이너를 만들려면 다음 절차를 따르십시오.  
  
1.  스토리지 계정을 선택하고 **컨테이너** 탭을 클릭한 다음 화면 맨 아래에서 **컨테이너 추가** 를 클릭하면 새 대화 상자가 열립니다.  
  
     ![관리 포털에서 컨테이너 만들기](../../2014/tutorials/media/backuptocloud.gif "관리 포털에서 컨테이너 만들기")  
  
2.  컨테이너 이름을 입력합니다. 지정한 컨테이너 이름을 적어 둡니다. 이 정보는 3, 4단원에서 T-SQL 문의 URL(백업 파일 경로)에 사용됩니다.  
  
3.  **액세스 형식**에서 프라이빗을 선택합니다. 백업 파일을 보호하기 위한 프라이빗 컨테이너를 만드는 것이 좋습니다.  
  
     ![새 BLOB 컨테이너 만들기](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "새 BLOB 컨테이너 만들기")  
  
    > [!NOTE]  
    >  공용 컨테이너를 만들도록 선택한 경우에도 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원에 스토리지 계정 인증이 필요합니다.  
    >   
    >  또한 REST API를 사용하여 프로그래밍 방식으로 컨테이너를 만들 수도 있습니다. 자세한 내용은 [컨테이너 만들기](https://go.microsoft.com/fwlink/?LinkId=271946)를 참조 하세요.  
  
### <a name="next-lesson"></a>다음 단원  
 [2 단원: SQL Server 자격 증명 만들기](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)  
  
  
