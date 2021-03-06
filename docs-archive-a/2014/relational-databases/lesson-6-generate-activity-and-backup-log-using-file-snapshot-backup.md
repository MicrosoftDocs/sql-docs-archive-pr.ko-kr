---
title: '7 단원: 데이터 파일을 Azure Storage로 이동 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 753863d7b8b8d8fa554f1579bee6837c525efd9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653365"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a>7단원: Azure Storage에 데이터 파일 이동
  이 단원에서는 데이터 파일을 Azure Storage로 이동 하는 방법에 대해 설명 합니다 (SQL Server 인스턴스는 아님). 이 단원을 수행하기 위해 4, 5, 6단원을 완료할 필요는 없습니다.  
  
 데이터 파일을 Azure Storage로 이동 하려면 문을 사용 하 여 `ALTER DATABASE` 데이터 파일의 위치를 변경 하는 것이 좋습니다.  
  
 이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.  
  
-   Azure Storage 계정이 있습니다.  
  
-   Azure Storage 계정으로 컨테이너를 만들었습니다.  
  
-   읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다. SAS 키도 생성했습니다.  
  
-   원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.  
  
 다음 단계를 사용 하 여 데이터 파일을 Azure Storage로 이동 합니다.  
  
1.  먼저 원본 컴퓨터에서 테스트 데이터베이스를 만들고 일부 데이터를 추가합니다.  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  다음 코드를 실행하세요.  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  이를 실행 하면 "" TestDB1Alter "파일이 시스템 카탈로그에서 수정 되었습니다. 라는 메시지가 표시 됩니다. 새 경로는 다음에 데이터베이스가 시작 될 때 사용 됩니다. "  
  
4.  데이터베이스를 오프라인으로 설정합니다.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  이제 [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx)또는 타사 저장소 탐색기 도구 중 하나를 사용 하 여 데이터 파일을 Azure Storage에 복사 해야 합니다.  
  
     **중요** : 이 새로운 향상된 기능을 사용할 때는 항상 블록 Blob이 아니라 페이지 Blob을 만들어야 합니다.  
  
6.  데이터베이스를 온라인으로 설정합니다.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **다음 단원:**  
  
 [단원 8. Azure Storage로 데이터베이스 복원](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
