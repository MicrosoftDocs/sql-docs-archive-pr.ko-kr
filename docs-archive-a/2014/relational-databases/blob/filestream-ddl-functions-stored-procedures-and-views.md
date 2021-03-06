---
title: FILESTREAM DDL, 함수, 저장 프로시저 및 뷰 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dffcc454d21a0a8dea0e98c4db2c19a4af29e948
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638844"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a>FILESTREAM DDL, 함수, 저장 프로시저 및 뷰
  FILESTREAM을 지원하는 Transact-SQL 문 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체를 나열합니다.  
  
 FileTable 기능을 지원하는 데이터베이스 개체 목록은 [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md)를 참조하세요.  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Transact-SQL DDL(데이터 정의 언어) 문  
  
-   [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [DROP INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX  
  
##  <a name="system-functions"></a><a name="func"></a> 시스템 함수  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT&#40;Transact-SQL&#41;](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [PathName&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> 시스템 저장 프로시저  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [sp_filestream_force_garbage_collection&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> 시스템 뷰 - 카탈로그 뷰  
  
-   [sys.database_filestream_options&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> 시스템 뷰 - 동적 관리 뷰  
  
-   [sys.dm_filestream_file_io_handles&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [sys.dm_filestream_file_io_requests&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="programming-apis"></a><a name="api"></a> 프로그래밍 API  
  
-   [OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스](access-filestream-data-with-opensqlfilestream.md)  
  
-   [관리되는 API - SqlFileStream 클래스](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
