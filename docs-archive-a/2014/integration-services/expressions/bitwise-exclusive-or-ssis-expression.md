---
title: ^(배타적 비트 OR)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d86c3d810e9e5572af93c97f82c2275db2c979b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652969"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a>^(배타적 비트 OR)(SSIS 식)
  두 정수 값의 배타적 비트 OR 연산을 수행합니다. 그런 후 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다. 두 비트 중 하나가 0이고 다른 비트가 1이면 해당 결과 비트는 1로 설정됩니다. 두 비트가 모두 0 또는 1이면 해당 결과 비트는 0으로 설정됩니다.  
  
 두 조건이 모두 부호 있는 정수 데이터 형식이거나 두 조건이 모두 부호 없는 정수 데이터 형식이어야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a>인수  
 *integer_expression1, integer_expression2*  
 부호가 있거나 부호가 없는 정수 데이터 형식의 유효한 식입니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
## <a name="result-types"></a>결과 형식  
 두 인수의 데이터 형식에 따라 결정됩니다. 자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.  
  
## <a name="remarks"></a>설명  
 둘 중 한 조건이 Null이면 식 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 변수 **NumberA** 와 **NumberB**사이에 배타적 비트 OR 연산을 수행합니다. **NumberA** 에는 3(00000011)이 포함되고 **NumberB** 에는 7(00000111)이 포함됩니다.  
  
```  
@NumberA ^ @NumberB  
```  
  
 식은 4(00000100)로 계산됩니다.  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000100  
  
 이 예에서는 **ReorderPoint** 열과 **SafetyStockLevel** 열 사이에 배타적 비트 OR 연산을 수행합니다.  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 **ReorderPoint** 가 10이고 **SafetyStockLevel** 이 8이면 식은 2(00000010)로 계산됩니다.  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00000010  
  
 이 예에서는 두 정수 사이에 배타적 비트 OR 연산을 수행합니다.  
  
```  
3 ^ 5   
```  
  
 식은 6(00000110)으로 계산됩니다.  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000110  
  
## <a name="see-also"></a>참고 항목  
 [&#124;&#124;&#40;논리적 OR&#41;&#40;SSIS 식&#41;](logical-or-ssis-expression.md)   
 [&#124;&#40;포괄적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md)   
 [연산자&#40;SSIS 식&#41;](operators-ssis-expression.md)  
  
  
