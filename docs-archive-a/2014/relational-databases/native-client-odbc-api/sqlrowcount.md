---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: rothja
ms.author: jroth
ms.openlocfilehash: 410023d960bad6dde1060a509cc1bf46f67d77cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660524"
---
# <a name="sqlrowcount"></a>SQLRowCount
  문 실행을 위해 매개 변수 값의 배열이 바인딩되는 경우 `SQLRowCount` 매개 변수 값의 행이 문 실행 시 오류 조건을 생성 하면 SQL_ERROR을 반환 합니다. 이 함수의 *RowCountPtr* 인수를 통해서는 값이 반환되지 않습니다.  
  
 애플리케이션에서는 SQL_ATTR_PARAMS_PROCESSED_PTR 매개 변수 특성을 사용하여 오류가 발생하기 전에 처리된 매개 변수 수를 캡처할 수 있습니다.  
  
 또한 애플리케이션에서는 SQL_ATTR_PARAM_STATUS_PTR 문 특성을 사용하여 바인딩된 상태 값의 배열을 사용하여 문제를 일으키는 매개 변수 행의 배열 오프셋을 캡처할 수도 있습니다. 애플리케이션에서는 상태 배열을 트래버스하여 처리된 실제 행 수를 확인할 수 있습니다.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Output 절이 있는 INSERT, UPDATE, DELETE 또는 MERGE 문을 실행 하면 output 절에 의해 생성 된 결과 집합의 모든 행이 소비 될 때까지 SQLRowCount는 영향을 받는 행 수를 반환 하지 않습니다. 이러한 행을 사용 하려면 SQLFetch 또는 SQLFetchScroll을 호출 합니다. SQLResultCols는 모든 결과 행이 소비 될 때까지-1을 반환 합니다. SQLFetch 또는 SQLFetchScroll SQL_NO_DATA 반환한 후 응용 프로그램은 Sqlfetch를 호출 하 여 다음 결과로 이동 하기 전에 SQLMoreResults를 호출 하기 전에 영향을 받는 행 수를 확인 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLRowCount 함수](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API 구현 정보](odbc-api-implementation-details.md)  
  
  
