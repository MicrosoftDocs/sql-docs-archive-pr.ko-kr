---
title: 단위 설정 및 구성(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c01523dad9a96d2d45b96474d36873bac2484343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639295"
---
# <a name="set-and-configure-measurement-units-report-builder-and-ssrs"></a>단위 설정 및 구성(보고서 작성기 및 SSRS)
  표시기는 백분율과 숫자라는 두 가지 측정 단위를 제공합니다. 표시기는 기본적으로 백분율을 단위로 사용하도록 구성됩니다. 즉, 표시기 집합에서 각 아이콘에 할당되는 표시기 값은 백분율 범위로 결정됩니다. 백분율 범위는 표시기 집합의 아이콘에 대해 균등하게 분할됩니다. 각 아이콘은 표시기 상태를 나타냅니다. 다른 시작 백분율 및 끝 백분율을 지정하여 표시기 집합의 각 아이콘에 대한 백분율을 변경할 수 있습니다 또한 표시기는 데이터의 최소값 및 최대값을 자동으로 검색합니다.  
  
 측정 단위를 숫자 값이 되도록 변경할 수 있습니다. 이 경우에는 데이터의 최소값 및 최대값을 지정하지 않습니다. 대신 표시기에 사용되는 각 아이콘의 시작 값과 끝 값만 제공하면 됩니다.  
  
 식을 사용하여 단위 등의 옵션을 설정할 수 있습니다. 자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-use-the-numeric-state-measurement-unit"></a>숫자 상태 단위를 사용하려면  
  
1.  변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.  
  
2.  왼쪽 창에서 **값 및 상태** 를 클릭합니다.  
  
3.  **상태 단위** 목록에서 **숫자**를 클릭합니다.  
  
     필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.  
  
4.  표시기 집합의 각 아이콘에 대해 **시작** 및 **끝** 입력란의 값을 업데이트합니다.  
  
     필요한 경우 **식** (*fx*) 단추를 클릭하여 **시작** 및 **끝** 옵션의 값을 설정하는 식을 편집합니다.  
  
    > [!NOTE]  
    >  **시작** 및 **끝** 입력란의 값은 숫자여야 합니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-percentage-measurement-unit"></a>백분율 단위를 사용하려면  
  
1.  변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.  
  
2.  왼쪽 창에서 **값 및 상태** 를 클릭합니다.  
  
3.  **상태 단위** 목록에서 **백분율**을 클릭합니다.  
  
     필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.  
  
4.  필요한 경우 **최소값** 및 **최대값** 옵션을 변경하여 표시기가 사용하는 데이터의 최소값 및 최대값을 자동으로 검색하는 대신 특정 값을 사용합니다. **최소값** 이 **최대값**보다 작아야 합니다.  
  
    > [!NOTE]  
    >  최소값 및 최대값을 명시적으로 설정하는 경우 데이터의 실제 최소값 및 최대값에 관계없이 표시기에서 해당 값 범위를 사용합니다. 즉, 최소값보다 작은 값과 최대값보다 큰 값은 보고서에 표시할 표시기 아이콘을 결정하는 평가에서 제외됩니다.  
  
     필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.  
  
5.  표시기 집합의 각 아이콘에 대해 **시작** 및 **끝** 입력란의 값을 업데이트합니다.  
  
     필요한 경우 **식** (*fx*) 단추를 클릭하여 **시작** 및 **끝** 옵션의 값을 설정하는 식을 편집합니다.  
  
    > [!NOTE]  
    >  **시작** 및 **끝** 입력란의 값은 숫자여야 합니다.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [표시기&#40;보고서 작성기 및 SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
