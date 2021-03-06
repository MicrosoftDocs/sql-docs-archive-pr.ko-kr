---
title: 통화 변환 정의 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1c60b6ad6964060164e273004f59604fef6574a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639080"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>통화 변환 정의(비즈니스 인텔리전스 마법사)
  **통화 변환 정의** 페이지를 사용하여 비즈니스 인텔리전스 마법사에서 생성된 통화 변환 기능이 포함된 MDX(Multidimensional Expressions) 스크립트를 검토할 수 있습니다. 그런 다음 마법사에서 생성된 이 MDX 스크립트를 사용하여 큐브의 MDX 스크립트에 이전에 정의한 통화 변환 기능을 덮어쓰거나 추가할 수 있습니다.  
  
> [!NOTE]  
>  이 페이지는 비즈니스 인텔리전스 마법사가 큐브에 대한 MDX 스크립트에서 이전에 정의한 통화 변환을 하나 이상 검색한 경우에만 나타납니다. 큐브에 대한 MDX 스크립트에서 통화 변환은 다음 주석으로 묶여 있습니다.  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  이러한 주석을 변경 또는 제거하면 비즈니스 인텔리전스 마법사가 이전에 정의한 통화 변환을 검색할 수 없게 될 수 있습니다.  
  
## <a name="options"></a>옵션  
 **새 통화 변환 스크립트**  
 현재 비즈니스 인텔리전스 마법사 세션에서 생성된 MDX 스크립트를 표시합니다.  
  
 **기존 통화 변환 스크립트 덮어쓰기**  
 **기존 통화 변환 스크립트** 에 표시된 MDX 스크립트를 **새 통화 변환 스크립트**에 표시된 MDX 스크립트로 덮어쓰려면 선택합니다.  
  
 **추가 위치**  
 **새 통화 변환 스크립트** 에 표시된 MDX 스크립트를 **기존 통화 변환 스크립트**에 표시된 MDX 스크립트의 끝에 추가하려면 선택합니다. 추가된 스크립트는 새 섹션으로 나타납니다.  
  
 **기존 통화 변환 스크립트**  
 덮어쓰거나 추가할 이전에 정의한 통화 변환 기능을 포함하는 기존 MDX 스크립트의 섹션을 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md)   
 [큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
