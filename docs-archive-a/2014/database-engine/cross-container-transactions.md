---
title: 크로스 컨테이너 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28437f0903459616a574e713c0f138e8bb459870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651247"
---
# <a name="cross-container-transactions"></a>크로스 컨테이너 트랜잭션
  크로스 컨테이너 트랜잭션은 메모리 최적화 테이블에서 고유하게 컴파일된 저장 프로시저 또는 작업에 대한 호출을 포함하는 암시적이거나 명시적인 사용자 트랜잭션입니다.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 저장 프로시저에 대한 호출은 트랜잭션을 시작하지 않습니다. 자동 모드에서 고유하게 컴파일된 프로시저의 실행(사용자 트랜잭션의 컨텍스트가 아님)은 크로스 컨테이너 트랜잭션으로 간주되지 않습니다.  
  
 메모리 최적화 테이블을 참조하는 해석된 쿼리는 명시적이거나 암시적인 트랜잭션 또는 자동 커밋 모드에서 실행되는지 여부에 관계없이 크로스 컨테이너 트랜잭션의 일부로 간주됩니다.  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a>개별 작업의 격리  
 각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 트랜잭션마다 격리 수준이 있습니다. 기본 격리 수준은 커밋된 읽기입니다. 다른 격리 수준을 사용 하려면 [트랜잭션 격리 수준 설정 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)를 사용 하 여 격리 수준을 설정할 수 있습니다.  
  
 따라서 디스크 기반 테이블과는 다른 격리 수준의 메모리 최적화 테이블에서 작업을 수행해야 하는 경우가 있습니다. 트랜잭션에서는 문의 컬렉션 또는 개별 읽기 작업에 대해 다른 격리 수준을 설정할 수 있습니다.  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a>개별 작업의 격리 수준 지정  
 트랜잭션의 문 집합에 대해 다른 격리 수준을 설정하려면 `SET TRANSACTION ISOLATION LEVEL`을 사용할 수 있습니다. 트랜잭션의 다음 예제는 기본적으로 직렬화 격리 수준을 사용합니다. t3, t2 및 t1의 삽입 및 선택 작업은 반복 가능 읽기 격리에서 실행됩니다.  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 트랜잭션 기본값과 다른 개별 읽기 작업에 대한 격리 수준을 설정하려면 테이블 힌트(예: 직렬화 가능)를 사용할 수 있습니다. 행을 업데이트하거나 삭제하려면 항상 먼저 행을 읽어야 하므로 모든 선택 작업은 읽기 작업에 해당하고 모든 업데이트 및 삭제 작업은 읽기 작업에 해당합니다. 쓰기는 항상 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 격리되므로 삽입 작업에는 격리 수준이 없습니다. 다음 예제에서 트랜잭션의 기본 격리 수준은 커밋된 읽기이지만 테이블 t1은 직렬화 가능에서 액세스되고 t2는 스냅샷 격리에서 액세스됩니다.  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a>개별 작업에 대한 격리 의미  
 직렬화 트랜잭션 T는 완벽한 격리 상태에서 실행됩니다. 이런 상황은 다른 모든 트랜잭션이 T가 시작되기 전에 커밋되거나 T가 커밋된 후에 시작된 것과 같습니다. 따라서 트랜잭션의 작업마다 격리 수준이 다르면 더 복잡해집니다.  
  
 의 트랜잭션 격리 수준에 대 한 일반적인 의미 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 와 잠금에 대 한 의미는 [트랜잭션 격리 수준 설정 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)에 설명 되어 있습니다.  
  
 작업마다 다른 격리 수준을 가질 수 있는 크로스 컨테이너 트랜잭션의 경우 개별 읽기 작업의 격리에 대한 의미를 이해해야 합니다. 쓰기 작업은 항상 격리됩니다. 다른 트랜잭션의 쓰기는 서로 간에 영향을 미치지 않습니다.  
  
 데이터 읽기 작업은 필터 조건을 충족하는 행의 개수를 반환합니다.  
  
 읽기는 트랜잭션 T의 일부로 수행 됩니다. 읽기 작업의 격리 수준은를 기준으로 이해 될 수 있습니다.  
  
 커밋 상태  
 커밋 상태는 데이터 읽기 커밋이 보증되는지 여부를 나타냅니다.  
  
 (트랜잭션) 일관성  
 읽기 집합에 대한 트랜잭션 일관성은 행 버전 읽기가 트랜잭션의 정확히 동일한 집합의 업데이트를 포함하도록 보장되는지 여부를 나타냅니다.  
  
 안정성은 시스템이 데이터 읽기에 대해 트랜잭션 T에 제공하는 것을 보장합니다.  
 안정성은 트랜잭션의 읽기가 반복 가능한 지 여부를 나타냅니다. 즉, 읽기가 반복될 때 동일한 행 및 행 버전이 반환되는지 여부를 나타냅니다.  
  
 특정 보증은 트랜잭션의 논리적 종료 시간을 나타냅니다. 일반적으로 논리적 종료 시간은 트랜잭션이 데이터베이스에 커밋되는 시간입니다. 메모리 최적화 테이블이 트랜잭션에 의해 액세스되는 경우 논리적 종료 시간은 기술적으로 유효성 검사 단계의 시작 시간입니다. (자세한 내용은 메모리 액세스에 [최적화 된 테이블의 트랜잭션에](../relational-databases/in-memory-oltp/memory-optimized-tables.md)있는 트랜잭션 수명 설명을 참조 하세요.  
  
 격리 수준에 관계없이 트랜잭션(T)은 항상 자체 업데이트를 확인합니다.  
  
 READ UNCOMMITTED  
 데이터 읽기는 커밋, 일관성 또는 안정적 어느 것도 아닐 수 있습니다. 그러나 T에서 수행한 이전의 쓰기 작업을 포함합니다.  
  
 READ COMMITTED  
 데이터 읽기가 커밋됩니다.  
  
 SNAPSHOT  
 스냅샷 격리에서 T가 수행한 모든 읽기 작업은 트랜잭션의 시작과 동일한 논리적 읽기 시간을 갖습니다. 데이터 읽기는 반드시 커밋되며 논리적 읽기 시간과 일치합니다. 원래 읽기 시간에 읽기를 반복하면 같은 반드시 같은 결과를 반환하게 됩니다.  
  
 REPEATABLE READ  
 데이터 읽기는 커밋을 보장하며 트랜잭션의 논리적 종료 시간이 될 때까지 안정적입니다.  
  
 직렬화 가능  
 에서 수행 하는 모든 직렬화 가능 읽기 작업과 관련 하 여 반복 읽기와 가상 방지 및 트랜잭션 일관성을 보장 합니다. 팬텀 방지는 검색 작업에서 T가 작성 한 추가 행만 반환할 수 있지만 다른 트랜잭션에 의해 기록 된 행은 반환할 수 없음을 의미 합니다.  
  
 다음과 같은 트랜잭션이 있다고 합시다.  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 이 트랜잭션은 커밋된 읽기 격리에서 t3의 모든 행을 삭제하고 직렬화 격리 상태에서 t1의 모든 행을 t3으로 복사한 다음 t1과 t3을 비교합니다. 일부 행[t1에는 없음]은 테이블이 비어 있기 때문에 t3에 추가되었을 수 있습니다. 복사본은 직렬화될 수 있기 때문에 t1에는 행이 추가되지 않았습니다.  
  
 트랜잭션 끝에 있는 t 1의 읽기는 구문상 읽기 커밋 이지만 직렬화 가능 격리 상태에서 트랜잭션 앞부분에서 읽기를 수행 했기 때문에 실제로는 serialize 할 수 있습니다. 순차성는 트랜잭션의 이후 시점에서 읽기가 수행 될 경우 동일한 행이 반환 되도록 보장 합니다.  
  
## <a name="cross-container-transactions-and-isolation-levels"></a>크로스 컨테이너 트랜잭션 및 격리 수준  
 크로스 컨테이너 트랜잭션은 디스크 기반 측면 (디스크 기반 테이블에 대 한 작업의 경우) 및 메모리 최적화 측면 (메모리 최적화 테이블에 대 한 작업의 경우)의 두 면으로 볼 수 있습니다. 이러한 두 가지 측면은 다른 격리 수준을 가질 수 있습니다. 사실, 각 측면에서 개별 읽기 작업마다 다른 격리 수준을 가질 수 있습니다.  
  
 지정된 트랜잭션 T의 디스크 기반 측면은 다음 조건 중 하나가 충족되는 경우 특정 격리 수준에 도달합니다.  
  
-   X로 시작 합니다. 즉,를 실행 했기 때문에 세션 기본값은 X이 고 `SET TRANSACTION ISOLATION LEVEL` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 기본값입니다.  
  
-   트랜잭션 동안 `SET TRANSACTION ISOLATION LEVEL`을 사용하여 기본 격리 수준이 X로 변경되었습니다.  
  
-   디스크 기반 테이블의 읽기 작업은 구문 `WITH (X)`를 사용하여 격리 수준 X에서 실행됩니다.  
  
 T의 메모리 최적화 측면은 T를 실행하는 동안 메모리 최적화 테이블 또는 고유하게 컴파일된 저장 프로시저의 읽기 작업이 격리 수준 Y에서 실행된 경우 격리 수준 Y에 도달합니다.  
  
 한 예로 다음 트랜잭션을 고려하십시오. 여기에서 t1과 t2는 디스크 기반 테이블이고 t3과 t4는 메모리 최적화 테이블입니다.  
  
 트랜잭션의 디스크 기반 측면은 이 수준에서 시작하므로 격리 수준 커밋된 읽기에 도달합니다. 또한 디스크 기반 측면은 첫 번째 읽기 작업이 격리 수준 상태에서 실행되므로 반복 읽기에 도달합니다. 트랜잭션이 끝날 때 커밋된 읽기 격리 수준 상태에서 삭제가 실행되므로 새로운 격리 수준이 도입되지 않습니다.  
  
 트랜잭션의 메모리 최적화 측면은 두 수준 중 하나에 도달할 수 있습니다. 즉, condition1이 true 이면 직렬화 가능 하 고, false 이면 메모리 최적화 쪽은 스냅숏 격리에만 도달 합니다.  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a>크로스 컨테이너 트랜잭션에 지원되는 격리 수준  
 크로스 컨테이너 트랜잭션의 메모리 최적화 테이블에서 작업에 사용되는 격리 수준에는 제한이 있습니다.  
  
 메모리 액세스에 최적화된 테이블은 격리 수준 SNAPSHOT, REPEATABLE READ 및 SERIALIZABLE을 지원합니다. 자동 커밋 트랜잭션의 경우 메모리 최적화 테이블은 격리 수준 READ COMMITTED를 지원합니다.  
  
 다음과 같은 시나리오가 지원됩니다.  
  
-   READ UNCOMMITTED, READ COMMITTED 및 READ_COMMITTED_SNAPSHOT 크로스 컨테이너 트랜잭션은 SNAPSHOT, REPEATABLE READ 및 SERIALIZABLE 격리 상태에서 메모리 최적화 테이블에 액세스할 수 있습니다. READ COMMITTED 보증이 트랜잭션에 적용되며 트랜잭션에서 읽은 모든 행이 데이터베이스에 커밋되었습니다.  
  
-   REPEATABLE READ 및 SERIALIZABLE 트랜잭션은 SNAPSHOT 격리 상태에서 메모리 최적화 테이블에 액세스할 수 있습니다.  
  
## <a name="read-only-cross-container-transactions"></a>읽기 전용 크로스 컨테이너 트랜잭션  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 있는 대부분의 읽기 전용 트랜잭션은 커밋할 때 롤백됩니다. 데이터베이스 커밋에는 변경 내용이 없기 때문에 시스템은 트랜잭션에서 사용한 리소스를 해제합니다. 읽기 전용 디스크 기반 트랜잭션의 경우 트랜잭션이 수행한 모든 잠금이 이 때 해제됩니다. 단일의 고유하게 컴파일된 프로시저 실행을 포함하는 읽기 전용 메모리 최적화 트랜잭션의 경우 유효성 검사가 수행되지 않습니다.  
  
 자동 커밋 모드의 크로스 컨테이너 읽기 전용 트랜잭션은 트랜잭션이 끝날 때 롤백됩니다. 유효성 검사가 수행되지 않습니다.  
  
 명시적 또는 암시적 크로스 컨테이너 읽기 전용 트랜잭션은 REPEATABLE READ 또는 SERIALIZABLE 격리 상태에서 트랜잭션이 메모리 최적화 테이블에 액세스하는 경우 커밋할 때 유효성 검사를 수행합니다. 유효성 검사에 대 한 자세한 내용은 [메모리 최적화 테이블의 트랜잭션에서](../relational-databases/in-memory-oltp/memory-optimized-tables.md)충돌 검색, 유효성 검사 및 커밋 종속성 확인에 대 한 섹션을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [메모리 액세스에 최적화 된 테이블의 트랜잭션 이해](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [메모리 액세스에 최적화 된 테이블이 있는 트랜잭션 격리 수준에 대 한 지침](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)   
 [메모리 액세스에 최적화된 테이블의 트랜잭션에 대한 재시도 논리 지침](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
