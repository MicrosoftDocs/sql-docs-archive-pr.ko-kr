---
title: 결과 집합 정보 검색 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649039"
---
# <a name="retrieve-result-set-information-odbc"></a>결과 집합 정보 검색(ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>결과 집합에 대한 정보를 가져오려면  
  
1.  [Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md) 를 호출 하 여 결과 집합의 열 수를 가져옵니다.  
  
2.  결과 집합의 각 열에 대해 다음을 수행합니다.  
  
    -   [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) 를 호출 하 여 결과 열에 대 한 정보를 가져옵니다.  
  
     또는  
  
    -   [Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md) 를 호출 하 여 결과 열에 대 한 특정 설명자 정보를 가져옵니다.  
  
## <a name="see-also"></a>참고 항목  
 [결과 처리 방법 도움말 항목 &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [ODBC&#41;&#40;결과 집합의 특징 확인](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
