---
title: ~(비트 Not)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652961"
---
# <a name="-bitwise-not-ssis-expression"></a>~(비트 Not)(SSIS 식)
  정수의 비트 부정을 수행합니다. 이 연산자는 부호 있는 정수 또는 부호 없는 정수 데이터 형식에 적용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>인수  
 *integer_expression*  
 정수 데이터 형식의 유효한 식입니다. *integer*_*expression* 은 비트 연산을 위해 이진수로 변환되는 정수입니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
## <a name="result-types"></a>결과 형식  
 *integer_expression*의 데이터 형식을 반환합니다.  
  
## <a name="remarks"></a>설명  
 None  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 숫자 170(0000 0000 1010 1010)에 비트 ~(NOT) 연산을 수행합니다. 숫자는 부호 있는 정수입니다.  
  
```  
  
~ 170  
```  
  
 식은 -170(1111111101010101)으로 계산됩니다.  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>참고 항목  
 [연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md)   
 [연산자&#40;SSIS 식&#41;](operators-ssis-expression.md)  
  
  
