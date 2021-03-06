---
title: '5단원: 필드 TDE를 사용 하 여 데이터베이스 암호화 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 613b66c04a69364f3c9be1059f95021dd3eff595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652113"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>5단원: (선택 사항) TDE를 사용하여 데이터베이스 암호화
  선택적 단계로, 새로 만든 데이터베이스를 암호화할 수 있습니다. TDE(투명한 데이터 암호화)를 통해 데이터 및 로그 파일의 실시간 I/O 암호화 및 암호 해독을 수행합니다. 이러한 종류의 암호화에서는 DEK(데이터베이스 암호화 키)를 사용하며 이 키는 복구하는 동안 사용할 수 있도록 데이터베이스 부트 레코드에 저장됩니다. 자세한 내용은 [투명한 데이터 암호화 &#40;tde&#41;](security/encryption/transparent-data-encryption.md) 및 [Tde로 보호 되는 데이터베이스를 다른 SQL Server로 이동](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)을 참조 하세요.  
  
 이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.  
  
-   Azure Storage 계정이 있습니다.  
  
-   Azure Storage 계정으로 컨테이너를 만들었습니다.  
  
-   읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다. SAS 키도 생성했습니다.  
  
-   원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.  
  
-   4단원에서 설명한 단계를 수행하여 데이터베이스를 만들었습니다.  
  
 데이터베이스를 암호화하려면 다음 단계를 수행합니다.  
  
1.  원본 컴퓨터의 쿼리 창에서 다음 문을 수정하여 실행합니다.  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  다음 단계를 수행하여 원본 컴퓨터에서 새 데이터베이스를 암호화합니다.  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 데이터베이스의 암호화 상태와 연결된 데이터베이스 암호화 키를 알아보려면 다음 문을 실행합니다.  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 이 단원에서 사용 된 Transact-sql 문에 대 한 자세한 내용은 [CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql), create [MASTER KEY &#40;](/sql/t-sql/statements/create-master-key-transact-sql)Transact-sql&#41;, [create CERTIFICATE &#40;transact-sql ](/sql/t-sql/statements/create-certificate-transact-sql)&#41;및 dm_database_encryption_keys [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)을 참조 하십시오.  
  
 **다음 단원:**  
  
 [6단원: 온-프레미스의 원본 머신에서 Azure의 대상 머신으로 데이터베이스 마이그레이션](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
