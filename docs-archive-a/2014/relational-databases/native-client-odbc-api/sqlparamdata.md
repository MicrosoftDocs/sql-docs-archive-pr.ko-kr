---
title: SQLParamData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: rothja
ms.author: jroth
ms.openlocfilehash: a4e0e8b31a65f28ce83e0d114231bdedd7a35a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660529"
---
# <a name="sqlparamdata"></a>SQLParamData
  SQLParamData가 테이블 반환 매개 변수와 연결 된 *Valueptrptr* 을 반환 하는 경우 응용 프로그램은 *StrLen_Or_Ind*를 사용 하 여 sqlparamdata를 호출 해야 합니다. *StrLen_Or_Ind* 의 값이 0보다 크면 애플리케이션에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 사용하여 다음 테이블 반환 매개 변수에 대한 데이터를 수집할 준비가 되었음을 나타냅니다. *StrLen_Or_Ind* 의 값이 0이면 테이블 반환 매개 변수에 대한 데이터의 행이 더 이상 없음을 나타냅니다. 자세한 내용은 [테이블 반환 매개 변수 및 열 값의 바인딩 및 데이터 전송](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)을 참조 하세요.  
  
 테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [ODBC API 구현 정보](odbc-api-implementation-details.md)  
  
  
