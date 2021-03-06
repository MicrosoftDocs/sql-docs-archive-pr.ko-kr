---
title: 큐브 뷰 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f385fd078500739d97394cd8856fc8bd6a3b87e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733231"
---
# <a name="perspectives"></a>큐브 뷰
  큐브 뷰는 큐브를 보다 간단하게 표시할 수 있는 정의로, 큐브 기능의 하위 집합입니다. 큐브 뷰를 사용하면 관리자가 큐브 뷰를 만들어 사용자가 가장 관련 있는 데이터에 집중하도록 할 수 있습니다. 큐브 뷰에는 모든 큐브 개체의 하위 집합이 포함됩니다. 그러나 상위 큐브에 정의되지 않은 요소는 큐브 뷰에 포함될 수 없습니다.  
  
 단순 <xref:Microsoft.AnalysisServices.Perspective> 개체는 기본 정보, 차원, 측정값 그룹, 계산, KPI 및 동작으로 구성되어 있습니다. 기본 정보에는 큐브 뷰의 이름과 기본 측정값이 포함됩니다. 차원은 큐브 차원의 하위 집합입니다. 측정값 그룹은 큐브 측정값 그룹의 하위 집합입니다. 계산은 큐브 계산의 하위 집합입니다. KPI는 큐브 KPI의 하위 집합입니다. 동작은 큐브 동작의 하위 집합입니다.  
  
 큐브 뷰를 사용하려면 먼저 큐브를 업데이트하고 처리해야 합니다.  
  
 큐브는 사용자가 탐색할 수 있는 매우 복잡 한 개체 일 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . 하나의 큐브는 완전한 데이터 웨어하우스의 내용을 나타낼 수 있으며 다수의 차원 테이블을 기반으로 하는 여러 개의 차원과 팩트 테이블을 나타내는 다양한 측정값 그룹을 포함할 수 있습니다. 이러한 큐브는 매우 복잡하고 강력할 수 있지만 주로 비즈니스 인텔리전스 및 보고 요구 사항을 충족하기 위해 큐브의 일부만 사용하는 사용자에게는 부담이 될 수 있습니다.  
  
 에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 큐브 뷰를 사용 하 여에서 큐브를 인식 하는 복잡성을 줄일 수 있습니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . 큐브 뷰는 특정 큐브에서 비즈니스 또는 애플리케이션의 특정 요구 사항에 맞춰 보기를 제공하는 큐브 하위 집합을 정의합니다. 큐브에 포함된 개체의 표시 유형은 큐브 뷰에 따라 달라집니다. 큐브 뷰에서 다음 개체를 표시하거나 숨길 수 있습니다.  
  
-   차원  
  
-   특성  
  
-   계층 구조  
  
-   측정값 그룹  
  
-   측정값  
  
-   KPI(핵심 성과 지표)  
  
-   계산(계산 멤버, 명명된 집합 및 스크립트 명령)  
  
-   작업  
  
 예를 들어 예제 데이터베이스의 **놀이 Works** 큐브에 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 판매, 판매 예측 및 재무 데이터를 나타내는 11 개의 측정값 그룹과 21 개의 서로 다른 큐브 차원이 포함 되어 있습니다. 클라이언트 애플리케이션에서 전체 큐브를 직접 참조할 수 있지만 기본 판매 예측 정보만 추출하려는 사용자에게 이러한 직접 참조는 너무 과도한 작업입니다. 대신 같은 사용자가 **판매 목표** 큐브 뷰를 사용 하 여 **놀이 Works** 큐브의 보기를 판매 예측과 관련 된 개체만으로 제한할 수 있습니다.  
  
 큐브 뷰를 통해 사용자에게 표시되지 않는 큐브의 개체도 XMLA(XML for Analysis), MDX(Multidimensional Expressions) 또는 DMX(Data Mining Extensions) 문을 사용하여 직접 참조하거나 검색할 수 있습니다. 큐브 뷰는 큐브의 개체에 대한 액세스를 제한하지 않으며 액세스를 제한할 목적으로 사용해서도 안 됩니다. 큐브에 액세스하는 사용자에게 더 나은 환경을 제공하는 용도로 큐브 뷰를 사용하십시오.  
  
 큐브 뷰는 큐브의 읽기 전용 뷰이므로 큐브 뷰를 사용하여 큐브의 개체를 변경하거나 이름을 바꿀 수 없습니다. 마찬가지로 큐브 뷰를 사용하여 보이는 값 합계 사용과 같은 큐브의 동작이나 기능을 변경할 수 없습니다.  
  
## <a name="security"></a>보안  
 큐브 뷰는 보안 수단이 아니라 비즈니스 인텔리전스 애플리케이션에 보다 나은 사용자 환경을 제공하기 위한 도구입니다. 특정 큐브 뷰에 대한 모든 보안은 기본 큐브에서 상속됩니다. 예를 들어 큐브 뷰에서 사용자에게 액세스 권한이 없는 큐브의 개체에 대한 액세스 권한을 부여할 수는 없습니다. 큐브 뷰를 통해 큐브의 개체에 대한 액세스를 제공하려면 먼저 큐브에 대한 보안을 해결해야 합니다.  
  
  
