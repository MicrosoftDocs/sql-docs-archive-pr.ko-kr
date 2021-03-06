---
title: 지도 뷰포트 속성 대화 상자, 일반 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639392"
---
# <a name="map-viewport-properties-dialog-box-general"></a>지도 뷰포트 속성 대화 상자, 일반
  **지도 뷰포트 속성** 대화 상자에서 **일반** 을 선택하여 좌표계, 도법 및 경계 옵션을 변경할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **좌표계**  
 지도 데이터가 사용하는 좌표계의 유형을 지정합니다.  
  
-   **평면** 건물 계획과 같이 지도 데이터가 X 및 Y 좌표에 있는 경우 이 옵션을 선택합니다.  
  
-   **지리** 도시 위치와 같이 지도 데이터가 경도 및 위도 좌표에 있는 경우 이 옵션을 선택합니다.  
  
 **프로젝션**  
 지리 좌표를 2차원 표면에 투영하는 데 사용할 방법을 지정합니다. 시각화하는 데이터와 호환되는 도법을 선택합니다. 도법의 영향을 받는 4가지 공간 속성은 영역, 모양, 거리 및 방향입니다. 지구를 보는 경우 도법에 적합한 선택은 보기 중심, 지도 경계 및 확대/축소 비율에 따라 달라집니다.  
  
 아래에 있는 각 도법은 이러한 공간 속성 중 하나 이상을 유지합니다.  
  
-   **등장방형** 경도와 위도를 사각형 좌표로 사용하려면 이 옵션을 선택합니다.  
  
-   **메르카토르** 작은 지역의 경우, 적도 주위의 왜곡을 줄이려는 경우 또는 메르카토르 도법을 사용하는 기존 타일 계층이 포함된 지도 계층을 추가하려는 경우 널리 사용되는 이 도법을 선택합니다.  
  
-   **로빈슨** 적도에서 극지방까지 걸쳐 있는 큰 지역의 왜곡을 줄이려는 경우 이 옵션을 선택합니다. 1963년에 Arthur H. Robinson이 개발했습니다.  
  
-   **파헤이** 적도에서 극지방까지 걸쳐 있는 큰 지역의 왜곡을 줄이려는 경우 이 옵션을 선택합니다. 1975년에 Lawrence Fahey가 개발했습니다.  
  
-   **에케르트1** 위도에서 간격이 동일한 위도선을 사용하고 경도의 자오선에 직선을 사용하려면 이 옵션을 선택합니다.  
  
-   **에케르트 3** 위도에서 간격이 동일한 위도선을 사용하고 경도의 자오선에 곡선을 사용하려면 이 옵션을 선택합니다.  
  
-   **해머아이토프** 극지방 지도나 세계 지도의 경우 이 옵션을 선택합니다.  
  
-   **바그너3** 세계 지도의 경우 이 옵션을 선택합니다.  
  
-   **본느** 지도책에 나타나는 대로 세계를 보려면 이 옵션을 선택합니다.  
  
 **페이지 나누기 옵션**  
 보고서 페이지에 내용을 맞추는 방법을 지정하는 옵션을 선택합니다.  
  
 **경계 옵션**  
 보고서에 표시되는 지도의 부분을 제어하려면 좌표의 하한과 상한을 지정합니다.  
  
 **최소 X**  
 가장 작은 X 값입니다. **평면** 에만 사용할 수 있습니다.  
  
 **최대 X**  
 가장 큰 X 값입니다. **평면** 에만 사용할 수 있습니다.  
  
 **최소 Y**  
 가장 작은 Y 값입니다. **평면** 에만 사용할 수 있습니다.  
  
 **최대 Y**  
 가장 큰 Y 값입니다. **평면** 에만 사용할 수 있습니다.  
  
 **최소 경도**  
 가장 작은 경도 값입니다. **지리** 에만 사용할 수 있습니다.  
  
 **최대 경도**  
 가장 큰 경도 값입니다. **지리** 에만 사용할 수 있습니다.  
  
 **최소 위도**  
 가장 작은 위도 값입니다. **지리** 에만 사용할 수 있습니다.  
  
 **최대 위도**  
 가장 큰 위도 값입니다. **지리** 에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [지도&#40;보고서 작성기 및 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
