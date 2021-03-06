---
title: MSSQLSERVER_511 | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b69d2c043997e2947563de119bc4ee89fdf4e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730700"
---
# <a name="mssqlserver_511"></a>MSSQLSERVER_511
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|511|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|ROW_TOOBIG|  
|메시지 텍스트|최대 허용 크기(%d)보다 큰 행(%d)을 만들 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 시도한 작업이 최대 행 크기를 초과했습니다. 일반적으로 최대 행 크기는 8,060바이트입니다. 데이터에 사용할 수 있는 행 크기를 줄일 수 있는 오버헤드가 일부 스토리지 형식에 포함되어 있습니다. 예를 들어 스파스 열을 사용할 경우 최대 행 크기는 8,018바이트입니다. 행을 추가하거나 제거하는 일부 작업과 열의 데이터 형식을 변경하는 일부 작업을 수행하려면 데이터 페이지에서 행을 다시 작성한 다음 원래 행을 제거해야 합니다. 이 작업에서 유효한 행 크기 한계는 최대 한계의 절반입니다. 이는 원래 행과 수정된 행 모두 단기간 데이터 페이지에 포함되어 있어야 하기 때문입니다.  
  
> [!WARNING]  
>  Null이 아닌 각 **varchar (max)** 또는 **nvarchar (max)** 열은 24 바이트의 추가 고정 할당을 필요로 하며이는 정렬 작업 동안 8060 바이트 행 제한에 대해 계산 됩니다. 이를 통해 테이블에서 만들 수 있는 null이 아닌 **varchar (max)** 또는 **nvarchar (max)** 열의 수에 대 한 암시적 제한을 만들 수 있습니다. 테이블 생성 시 또는 데이터 삽입 시점에 특별한 오류(최대 행의 크기가 최대로 허용된 8060바이트를 초과한다는 일반적인 경고 외의 메시지)가 표시되지 않습니다. 이렇게 크기가 큰 행은 클러스터형 인덱스 키 업데이트 같은 일부 정상 작업이나 전체 열 집합 정렬에서 오류(오류 512 등)를 발생시킬 수 있고 사용자는 이러한 오류를 작업을 수행하기 전에는 예측할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 가능하면 행 크기를 줄입니다.  
  
 행을 현재 위치에서 업데이트한 결과로 문제가 발생한 경우 여러 단계를 수행하여 테이블을 변경해야 합니다. 새 테이블을 만들고 데이터를 새 테이블로 전송합니다. 그런 다음 원래 테이블을 삭제하고 새 테이블의 이름을 바꾸거나 원래 테이블을 자르고 원래 테이블의 행을 수정한 후 해당 테이블로 데이터를 다시 이동합니다.  
  
  
