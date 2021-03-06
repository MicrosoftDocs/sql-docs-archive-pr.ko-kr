---
title: IRow를 사용하여 단일 행 페치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653826"
---
# <a name="fetching-a-single-row-with-irow"></a>IRow를 사용하여 단일 행 인출
  Native Client OLE DB 공급자에서 **IRow** 인터페이스를 구현 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능을 향상 시킬 수 있습니다. **IRow**를 사용하여 단일 행 개체의 열에 직접 액세스할 수 있습니다. 명령 실행의 결과로 정확히 하나의 행이 생성된다는 것을 미리 알고 있는 경우 **IRow**는 해당 행의 열을 검색합니다. 결과 집합에 여러 행이 포함되는 경우 **IRow**는 첫 번째 행만 노출합니다.  
  
 **IRow** 구현에서는 행을 탐색할 수 없습니다. 한 가지 경우를 제외하고 행의 각 열은 한 번만 액세스할 수 있습니다. 한 가지 예외는 열 크기를 찾기 위해 열에 한 번 액세스하고 데이터를 인출하기 위해 다시 액세스할 수 있다는 점입니다.  
  
> [!NOTE]  
>  **IRow::Open**은 DBGUID_STREAM 및 DBGUID_NULL 개체 유형만 열 수 있습니다.  
  
 **ICommand::Execute** 메서드를 사용하여 행 개체를 가져오려면 IID_IRow를 전달해야 합니다. 여러 결과 집합을 처리하려면 **IMultipleResults** 인터페이스를 사용해야 합니다. **IMultipleResults**는 **IRow** 및 **IRowset**을 지원합니다. **IRowset**은 대량 작업에 사용합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [IRow::GetColumns 사용](using-irow-getcolumns.md)  
  
-   [IRow를 사용하여 BLOB 데이터 인출](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>참고 항목  
 [행 집합](rowsets.md)  
  
  
