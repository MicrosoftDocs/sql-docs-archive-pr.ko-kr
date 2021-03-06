---
title: Transact-SQL 코드 단계별 실행
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: rothja
ms.author: jroth
ms.openlocfilehash: 48cb307130c65729640864a26bdf1dfaf344b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653799"
---
# <a name="step-through-transact-sql-code"></a>Transact-SQL 코드 단계별 실행
  [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거를 사용하면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기 창에서 실행되는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 문을 제어할 수 있습니다. 개별 문에서 디버거를 일시 중지한 다음 해당 지점에서의 코드 요소 상태를 볼 수 있습니다.  
  
## <a name="breakpoints"></a>중단점  
 중단점은 디버거에게 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 실행을 일시 중지하라는 신호를 보냅니다. 중단점에 대한 자세한 내용은 Transact-SQL 중단점 사용을 참조하십시오.  
  
## <a name="controlling-statement-execution"></a>문 실행 제어  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드의 현재 문에서 실행하기 위해 다음 옵션을 지정할 수 있습니다.  
  
-   다음 중단점까지 실행합니다.  
  
-   다음 문을 한 단계씩 코드 실행합니다.  
  
     다음 문에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저, 함수 또는 트리거를 호출하면 디버거에서 모듈 코드가 포함된 새 쿼리 편집기 창을 표시합니다. 창이 디버그 모드에 있으며 모듈의 첫 번째 문에서 실행이 일시 중지됩니다. 그리고 나서 중단점을 설정하거나 코드를 단계별로 실행하여 모듈 코드를 이동할 수 있습니다.  
  
-   다음 문을 프로시저 단위로 실행합니다.  
  
     다음 문이 실행됩니다. 그러나 문에서 저장 프로시저, 함수 또는 트리거를 호출하면 모듈 코드가 완료될 때까지 실행되고 결과가 호출 코드에 반환됩니다. 저장 프로시저에 오류가 없으면 저장 프로시저를 프로시저 단위로 실행할 수 있습니다. 저장 프로시저, 함수 또는 트리거를 호출한 후 문에서 실행이 일시 중지됩니다.  
  
-   저장 프로시저, 함수 또는 트리거 프로시저를 나갑니다.  
  
     저장 프로시저, 함수 또는 트리거를 호출한 후 문에서 실행이 일시 중지됩니다.  
  
-   현재 위치에서 포인터의 현재 위치로 실행하고 모든 중단점을 무시합니다.  
  
 다음 표에서는 문이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 실행되는 방법을 제어하는 여러 방법을 나열합니다.  
  
|작업|절차|  
|------------|---------------|  
|현재 문부터 다음 중단점까지 모든 문을 실행합니다.|**디버그** 메뉴에서 **계속**을 클릭합니다.<br /><br /> **디버그** 도구 모음에서 **계속** 단추를 클릭 합니다.|  
|다음 문 또는 모듈을 한 단계씩 코드 실행합니다.|**디버그** 메뉴에서 한 **단계씩 코드 실행**을 클릭 합니다.<br /><br /> **디버그** 도구 모음에서 한 **단계씩 코드 실행** 단추를 클릭 합니다.<br /><br /> F11 키를 누릅니다.|  
|다음 문 또는 모듈을 프로시저 단위로 실행합니다.|**디버그** 메뉴에서 **프로시저 단위 실행**을 클릭합니다.<br /><br /> **디버그** 도구 모음에서 **프로시저 단위 실행** 단추를 클릭 합니다.<br /><br /> F10 키를 누릅니다.|  
|모듈 프로시저를 나갑니다.|**디버그** 메뉴에서 **프로시저 아웃**을 클릭 합니다.<br /><br /> **디버그** 도구 모음에서 **프로시저 아웃** 단추를 클릭 합니다.<br /><br /> Shift+F11을 누릅니다.|  
|현재 커서 위치까지 실행합니다.|쿼리 편집기 창에서 마우스 오른쪽을 클릭한 다음 **커서까지 실행**을 클릭합니다.<br /><br /> Ctrl+F10을 누릅니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Transact-SQL 디버거 정보](transact-sql-debugger-information.md)  
  
  
