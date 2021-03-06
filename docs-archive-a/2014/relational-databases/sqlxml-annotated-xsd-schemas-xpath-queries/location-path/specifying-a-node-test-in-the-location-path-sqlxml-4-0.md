---
title: 위치 경로에 노드 테스트 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d8535154f4b481c8a47bfdb8b801e3136a1ef0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651583"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>위치 경로에 노드 테스트 지정(SQLXML 4.0)
  노드 테스트는 위치 단계에서 선택되는 노드 유형을 지정합니다. 모든 축(`child`, `parent`, `attribute` 또는 `self`)에는 주 노드 유형이 있습니다. 축의 경우 `attribute` 주 노드 형식은 **\<attribute>** 입니다. `parent`, `child` 및 `self` 축의 경우 주 노드 형식은 **\<element>** 입니다.  
  
> [!NOTE]  
>  와일드카드 노드 테스트 *(예: `child::*`)는 지원되지 않습니다.  
  
## <a name="node-test-example-1"></a>노드 테스트: 예 1  
 위치 경로는 `child::Customer` **\<Customer>** 컨텍스트 노드의 요소 자식을 선택 합니다.  
  
 이 예에서는 `child`가 축이고 `Customer`가 노드 테스트입니다. 축에 대 한 주 노드 유형은 `child` **\<element>** 입니다. 따라서 노드가 노드인 경우 노드 테스트는 TRUE입니다 **\<Customer>** **\<element>** . 컨텍스트 노드에 **\<Customer>** 자식이 없으면 빈 노드 집합이 반환 됩니다.  
  
## <a name="node-test-example-2"></a>노드 테스트: 예 2  
 위치 경로는 `attribute::CustomerID` 컨텍스트 노드의 **CustomerID** 특성을 선택 합니다.  
  
 이 예에서는 `attribute`가 축이고 `CustomerID`가 노드 테스트입니다. 축의 주 노드 형식은 `attribute` **\<attribute>** 입니다. 따라서 **CustomerID** 가 노드인 경우 노드 테스트는 TRUE입니다 **\<attribute>** . 컨텍스트 노드에 **CustomerID**가 없으면 빈 노드 집합이 반환 됩니다.  
  
> [!NOTE]  
>  이 XPath 구현에서 위치 단계가 **\<element>** 스키마에 선언 되지 않은 또는 유형을 참조 하는 경우 **\<attribute>** 오류가 발생 합니다. 이 동작은 빈 노드 집합을 반환하는 MSXML에서의 XPath 구현과는 다릅니다.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>축의 축약형 구문  
 위치 경로에 대한 다음 축약형 구문이 지원됩니다.  
  
-   `attribute::`는 `@` 기호로 축약할 수 있습니다.  
  
     위치 경로 `Customer[@CustomerID="ALFKI"]`는 `child::Customer[attribute::CustomerID="ALFKI"]`와 같습니다.  
  
-   `child::`는 위치 단계에서 생략할 수 있습니다.  
  
     따라서 기본 축은 `child`이고, 위치 경로 `Customer/Order`는 `child::Customer/child::Order`와 같습니다.  
  
-   `self::node()`는 한 개의 마침표(.)로 축약할 수 있으며, `parent::node()`는 두 개의 마침표(..)로 축약할 수 있습니다.  
  
  
