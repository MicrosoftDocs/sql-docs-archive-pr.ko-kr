---
title: LTRIM(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650195"
---
# <a name="ltrim-ssis-expression"></a>LTRIM(SSIS 식)
  선행 공백을 제거하고 문자 식을 반환합니다.  
  
> [!NOTE]  
>  LTRIM은 탭이나 줄 바꿈 문자와 같은 공백 문자를 제거하지 않습니다. 유니코드는 많은 다른 공백 유형에 대해 코드 포인트를 제공하지만 이 함수는 유니코드 코드 포인트 0x0020만 인식합니다. DBCS(더블바이트 문자 집합) 문자열이 유니코드로 변환될 때 0x0020이 아닌 공백 문자를 포함할 수도 있는데 이 함수에서는 이러한 공백을 제거할 수 없습니다. 모든 종류의 공백을 제거하려면 스크립트 구성 요소의 스크립트 실행에서 Microsoft Visual Basic .NET LTrim 메서드를 사용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a>인수  
 *character_expression*  
 공백을 제거할 문자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_WSTR  
  
## <a name="remarks"></a>설명  
 LTRIM은 DT_WSTR 데이터 형식에서만 실행됩니다. 문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 LTRIM이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다. 다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다. 자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.  
  
 인수가 Null이면 LTRIM 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 문자열 리터럴에서 선행 공백을 제거합니다. 반환 결과는 "Hello"입니다.  
  
```  
LTRIM("    Hello")  
```  
  
 이 예에서는 **FirstName** 열에서 선행 공백을 제거합니다.  
  
```  
LTRIM(FirstName)  
```  
  
 이 예에서는 **FirstName** 변수에서 선행 공백을 제거합니다.  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>참고 항목  
 [RTRIM&#40;SSIS 식&#41;](trim-ssis-expression.md)   
 [TRIM&#40;SSIS 식&#41;](trim-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  
