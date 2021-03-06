---
title: Data Quality Services 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d2544df341a831f2f676ec58150ed64a800fb96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649159"
---
# <a name="upgrade-data-quality-services"></a>Data Quality Services 업그레이드
  이 항목에서는 기존 DQS(Data Quality Services) 설치를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2로 업그레이드하는 방법을 설명합니다. DQS의 Data Quality 서버를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 때 DQS 데이터베이스 스키마도 업그레이드해야 합니다.  
  
> [!IMPORTANT]
>  -   스키마 업그레이드 중에 데이터 손실을 방지하기 위해 DQS를 업그레이드하기 전에 DQS 데이터베이스를 백업해야 합니다. DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)을 참조하십시오.  
> -   데이터 품질 태스크를 수행하기 위해 Integration Services의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] DQS 정리 변환 편집기 [나 최신 또는 이전 버전의 Data Quality 클라이언트를 사용하여](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) 버전의 Data Quality 서버에 연결할 수 있습니다.  
> -   Data Quality Services 및 MDS(Master Data Services)를 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] CTP2로 업그레이드한 후 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 버전의 Excel용 MDS(Master Data Services) 추가 기능을 계속 사용할 수 있습니다. 하지만 SQL Server 2014 CTP2로 업그레이드한 후에는 이전 버전의 Excel용 MDS(Master Data Services) 추가 기능이 모두 작동하지 않습니다. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 버전의 Excel용 MDS(Master Data Services) 추가 기능은 [여기](https://go.microsoft.com/fwlink/?LinkId=328664)서 다운로드할 수 있습니다.  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> 필수 조건  
  
-   [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 컴퓨터에서 Administrators 그룹의 멤버로 로그온해야 합니다.  
  
-   Windows 사용자 계정은 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 가 설치된 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.  
  
##  <a name="upgrading-dqs"></a><a name="Upgrade"></a> DQS 업그레이드  
 DQS를 업그레이드하려면:  
  
1.  업그레이드 프로세스를 시작하기 전에 DQS 데이터베이스를 백업합니다. DQS 데이터베이스 백업에 대한 자세한 내용은 [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)을 참조하십시오.  
  
2.  DQS가 설치된 SQL Server 인스턴스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드합니다.  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사를 실행합니다.  
  
    2.  왼쪽 창에서 **설치**를 클릭합니다.  
  
    3.  오른쪽 창에서 **SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 또는 SQL Server 2012에서 업그레이드**를 클릭 합니다.  
  
    4.  설치 마법사를 완료합니다.  
  
        > [!NOTE]  
        >  SQL Server 인스턴스가 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 로 업그레이드되고 Data Quality 클라이언트가 이 컴퓨터에 설치되어 있지 않은 경우 최신 Data Quality 클라이언트도 설치됩니다. Data Quality 클라이언트가 다른 컴퓨터에 설치되어 있으면 해당 컴퓨터에서 2단계의 하위 단계를 실행하여 최신 버전의 Data Quality 클라이언트를 설치해야 합니다. 설치 마법사는 기존 버전의 Data Quality 클라이언트와 함께 최신 버전의 Data Quality 클라이언트를 설치합니다. DQS 데이터베이스 스키마를 업그레이드한 후 최신 또는 이전 버전의 Data Quality 클라이언트를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 Data Quality 서버에 연결할 수 있습니다.  
  
3.  DQS 데이터베이스 스키마를 업그레이드합니다.  
  
    1.  관리자로 명령 프롬프트를 시작합니다.  
  
    2.  명령 프롬프트에서 디렉터리를 DQSInstaller.exe가 있는 위치로 변경합니다. 기본 SQL Server 인스턴스의 경우 DQSInstaller.exe 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn에 있습니다.  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  명령 프롬프트에 다음 명령을 입력하고 Enter 키를 누릅니다.  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  설치 관리자에서 계속하기 전에 DQS 데이터베이스를 백업하라는 메시지를 표시합니다. DQS 데이터베이스를 이미 백업했으면 `Y` 또는 `Yes`를 입력한 후 ENTER 키를 눌러 업그레이드를 계속하십시오.  
  
    5.  DQS 데이터베이스 스키마 업그레이드에 성공하면 완료 메시지가 표시됩니다.  
  
##  <a name="verifying-the-dqs-databases-schema-upgrade"></a><a name="Verify"></a> DQS 데이터베이스 스키마 업그레이드 확인  
 DQS 데이터베이스 스키마가 성공적으로 업그레이드되었는지 확인하려면 DQS_MAIN 및 DQS_PROJECTS 데이터베이스에서 A_DB_VERSION 테이블을 쿼리하여 각 데이터베이스의 현재 버전을 확인하면 됩니다. 이렇게 하려면 다음을 수행합니다.  
  
1.  SQL Server Management Studio를 시작하고 업그레이드된 DQS 데이터베이스 스키마가 포함된 SQL Server 인스턴스에 연결합니다.  
  
2.  다음 쿼리를 실행합니다.  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  출력에는 업그레이드 날짜와 함께 각 업그레이드에 대한 항목이 표시됩니다. 최신 날짜의 최대 VERSION_ID 및 ASSEMBLY_VERSION이 현재 버전입니다. STATUS 열의 값이 2이면 성공을 나타냅니다. 오류가 발생한 경우 ERROR 열에 오류가 표시됩니다. 예제 출력:  
  
    |ID|UPGRADE_DATE|VERSION_ID|ASSEMBLY_VERSION|USER_NAME|상태|오류|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |1000|2013-08-11 05:26:39.567|1200|11.0.3000.0|\<DOMAIN\UserName>|2||  
    |1001|2013-09-19 15:09:37.750|1600|12.0.xxxx.0|\<DOMAIN\UserName>|2||  
  
## <a name="see-also"></a>참고 항목  
 [Data Quality Services 설치](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Data Quality 서버 개체 제거](../../sql-server/install/remove-data-quality-server-objects.md)   
 [SQL Server 2014로 업그레이드](upgrade-sql-server.md)  
  
  
