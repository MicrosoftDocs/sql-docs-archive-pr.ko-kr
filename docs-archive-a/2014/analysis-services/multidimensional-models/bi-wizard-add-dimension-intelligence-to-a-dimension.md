---
title: 차원에 차원 인텔리전스 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648659"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a>차원에 차원 인텔리전스 추가
  큐브나 차원에 차원 인텔리전스 기능을 추가하여 차원에 대한 표준 비즈니스 유형을 지정할 수 있습니다. 이 기능은 차원 특성에 해당하는 유형도 지정합니다. 클라이언트 애플리케이션은 데이터를 분석할 때 이러한 유형 지정을 사용할 수 있습니다.  
  
 차원 인텔리전스를 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **차원 인텔리전스 정의** 옵션을 선택합니다. 그런 다음 마법사의 안내를 따라 차원 인텔리전스를 적용할 차원을 선택하고 선택한 차원에 대한 특성을 식별합니다.  
  
## <a name="selecting-a-dimension"></a>차원 선택  
 마법사의 첫 번째 **차원 인텔리전스 옵션 설정** 페이지에서 차원 인텔리전스를 적용할 차원을 지정합니다. 선택한 차원에 차원 인텔리전스 기능을 추가하면 차원이 변경됩니다. 이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.  
  
> [!NOTE]  
>  차원으로 **계정** 을 선택한 경우 차원에 대한 계정 인텔리전스를 지정합니다. 자세한 내용은 [차원에 계정 인텔리전스 추가](bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.  
  
## <a name="specifying-dimension-attributes"></a>차원 특성 지정  
 차원 **인텔리전스 정의** 페이지의 **차원 유형** 목록에서 선택한 항목은 차원의 속성을 설정 합니다 `Type` . `Type` 속성을 설정하는 것은 서버와 클라이언트 애플리케이션에 차원 내용에 대한 정보를 제공하는 것입니다. 일부 설정은 클라이언트 애플리케이션에서 안내 역할만 합니다. 이러한 설정은 선택적입니다. 그러나 계정, 시간 등의 설정은 특정 동작을 결정하며 특정 비즈니스 인텔리전스 기능을 구현하기 위해 반드시 필요합니다. 예를 들어 SQL Server Management Studio에서 차원 유형을 사용하여 통화 차원을 식별하고 해당 통화 변환 규칙을 설정합니다. **차원 유형** 의 기본 설정은 **일반**이며 차원 내용에 대해 어떠한 가정도 하지 않습니다.  
  
 차원 유형을 선택한 후에는 **차원 특성**의 **포함** 열에서 차원의 해당 특성이 있는 각 표준 특성 유형 옆의 확인란을 선택합니다. 마지막으로 **차원 특성** 열에서 드롭다운 목록을 확장하고 선택한 특성 유형에 해당하는 차원의 특성을 선택합니다. 이 목록에서 특성을 선택하면 해당 특성의 `Type` 속성이 설정됩니다.  
  
 예를 들어 계정 차원에 차원 인텔리전스를 추가하려면 **차원 유형**에서 **계정**을 선택합니다. 차원에 **계정 유형** 및 **계정 설명** 특성이 있는 경우 **포함** 열에서 **계정 이름** 및 **계정 유형** 계정 유형에 대한 확인란을 선택합니다. 그런 다음 **차원 특성** 열에서 이러한 계정 유형을 차원의 **계정 설명** 및 **계정 유형** 특성에 각각 연결합니다.  
  
## <a name="see-also"></a>참고 항목  
 [비즈니스 인텔리전스 마법사를 사용하여 시간 인텔리전스 계산 정의](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
