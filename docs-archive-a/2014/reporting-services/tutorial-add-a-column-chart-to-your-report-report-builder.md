---
title: '자습서: 보고서에 세로 막대형 차트 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737863"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>자습서: 보고서에 세로 막대형 차트 추가(보고서 작성기)
  세로 막대형 차트에서 계열은 범주별로 그룹화된 일련의 세로 막대로 표시됩니다. 다음과 같은 경우에 세로 막대형 차트가 유용할 수 있습니다.  
  
-   일정 시간 동안의 데이터 변화 표시  
  
-   여러 계열의 상대 값 비교  
  
-   추세를 나타내기 위해 이동 평균 표시  
  
 다음 그림에서는 이동 평균을 사용하여 만들려는 세로 막대형 차트를 보여 줍니다.  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>학습 내용  
 이 자습서에서는 다음 작업 방법을 배웁니다.  
  
1.  [차트 마법사에서 차트 만들기](#Chart)  
  
2.  [차트 종류 선택](#ChartType)  
  
3.  [가로 축의 서식 및 레이블 지정](#Horizontal)  
  
4.  [범례 이동](#Legend)  
  
5.  [차트 제목 지정](#ChartTitle)  
  
6.  [세로 축의 서식 및 레이블 지정](#Vertical)  
  
7.  [이동 평균 추가](#Average)  
  
8.  [보고서 제목 추가](#Title)  
  
9. [보고서 저장](#Save)  
  
> [!NOTE]  
>  이 자습서에서 마법사의 단계는 하나의 절차로 통합됩니다. 보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만드는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.  
  
 이 자습서에 소요되는 예상 시간: 15분  
  
## <a name="requirements"></a>요구 사항  
 요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. 차트 마법사에서 차트 보고서 만들기  
 **시작** 대화 상자에서 차트 마법사를 사용 하 여 포함 된 데이터 집합을 만들고, 공유 데이터 원본을 선택 하 고, 세로 막대형 차트를 만듭니다.  
  
> [!NOTE]  
>  이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다. 따라서 쿼리가 상당히 길어집니다. 비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다. 이 자습서의 쿼리는 학습용으로만 제공됩니다.  
  
#### <a name="to-create-a-new-chart-report"></a>새 차트 보고서를 만들려면  
  
1.  **시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.  
  
     **시작** 대화 상자가 나타납니다.  
  
    > [!NOTE]  
    >  **시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.  
  
2.  왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.  
  
3.  오른쪽 창에서 **차트 마법사**를 클릭합니다.  
  
4.  **데이터 집합 선택 페이지**에서 **데이터 집합 만들기**를 클릭 하 고 **다음**을 클릭 합니다.  
  
5.  **데이터 원본에 대한 연결 선택** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버를 찾아 데이터 원본을 선택하고 **다음**을 클릭합니다. 사용자 이름과 암호를 입력해야 할 수 있습니다.  
  
    > [!NOTE]  
    >  적절한 권한만 가지고 있으면 선택하는 데이터 원본은 중요하지 않습니다. 데이터를 데이터 원본에서 가져오는 것은 아니기 때문입니다. 자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.  
  
6.  **쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.  
  
7.  쿼리 창에 다음 쿼리를 붙여 넣습니다.  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  (옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.  
  
9. **다음**을 클릭합니다.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. 차트 종류 선택  
 미리 정의된 다양한 차트 종류 중에서 선택할 수 있습니다.  
  
#### <a name="to-add-a-column-chart"></a>세로 막대형 차트를 추가하려면  
  
1.  **차트 종류 선택** 페이지에서 기본 차트 종류는 세로 막대형 차트입니다. **다음**을 클릭합니다.  
  
2.  **차트 필드 정렬** 페이지에서 SalesDate 필드를 **범주**창으로 끌어옵니다. 가로 축에 범주가 표시됩니다.  
  
3.  Sales 필드를 **값**으로 끌어옵니다. 매출 합계 값의 합은 각 날짜에 대해 집계되기 때문에 **값** 상자에는 Sum(Sales)가 표시됩니다. 세로 축에 값이 표시됩니다.  
  
4.  **다음**을 클릭합니다.  
  
5.  스타일 **선택** 페이지의 스타일 상자에서 스타일을 선택 합니다.  
  
     스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다. 스타일을 선택하면 미리 보기 창에 해당 스타일이 적용된 예제 차트가 표시됩니다.  
  
6.  **Finish**를 클릭합니다.  
  
     디자인 화면에 차트가 추가됩니다.  
  
7.  차트를 클릭하여 차트 핸들을 표시합니다. 차트의 오른쪽 아래 모퉁이를 끌어 차트의 크기를 늘립니다. 보고서 디자인 화면이 차트 크기에 맞게 늘어납니다.  
  
8.  **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>3. 가로 축의 서식 및 레이블 지정  
 기본적으로 가로 축에는 차트 크기에 맞게 자동으로 늘어나는 일반 형식으로 값이 표시됩니다.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>가로 축의 날짜에 형식을 지정하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  가로 축을 마우스 오른쪽 단추로 클릭 한 다음 **가로 축 속성**을 클릭 합니다.  
  
3.  **숫자**를 클릭 합니다.  
  
4.  **범주**에서 **날짜**를 선택 합니다.  
  
5.  **형식** 상자에서 **Jan 31, 2000**을 선택합니다.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  홈 탭에서 **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
 선택한 날짜 형식으로 날짜가 표시됩니다. 차트에서 가로 축의 범주 중 일부에는 레이블이 지정되지 않습니다. 기본적으로 축 옆에 맞는 레이블만 포함됩니다.  
  
 레이블을 회전하고 간격을 지정하여 레이블 표시를 사용자 지정할 수 있습니다.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>축 레이블을 회전하고 가로 축의 표시 간격을 변경하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  가로 축 제목을 마우스 오른쪽 단추로 클릭 한 다음 **축 제목 표시** 를 클릭 하 여 제목을 제거 합니다. 가로 축에는 날짜가 표시되므로 제목이 필요하지 않습니다.  
  
3.  가로 축을 마우스 오른쪽 단추로 클릭 한 다음 **가로 축 속성**을 클릭 합니다.  
  
4.  축 **옵션** 페이지의 **축 범위 및 간격**아래에서 **간격**에 **3** 을 입력 합니다. 차트에 3일 단위로 날짜가 표시됩니다.  
  
5.  **레이블**을 클릭 합니다.  
  
6.  **축 레이블 자동 맞춤 옵션 변경**에서 **자동 맞춤 사용 안 함**을 선택 합니다.  
  
7.  **레이블 회전 각도**에서 **-90**을 선택합니다.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     가로 축의 샘플 텍스트가 90도 회전합니다.  
  
9. **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
 차트에서는 레이블이 회전하고 레이블이 3일 단위로 표시됩니다.  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a>4. 범례 이동  
 범례는 범주와 계열 데이터에서 자동으로 만들어집니다.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>세로 막대형 차트의 차트 영역 아래로 범례를 이동하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  차트의 범례를 마우스 오른쪽 단추로 클릭 한 다음 **범례 속성**을 클릭 합니다.  
  
3.  **레이아웃 및 위치**에서 다른 위치를 선택 합니다. 예를 들어 아래쪽 가운데 옵션으로 위치를 설정합니다.  
  
     범례가 차트의 위쪽이나 아래쪽에 배치될 경우 범례 레이아웃은 세로에서 가로로 변경됩니다. **레이아웃** 드롭다운 목록에서 다른 레이아웃을 선택할 수 있습니다.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (옵션) 이 자습서에는 범주가 하나만 있기 때문에 범례가 필요하지 않습니다. 범례를 제거 하려면 범례를 마우스 오른쪽 단추로 클릭 한 다음 **범례 삭제**를 클릭 합니다.  
  
6.  **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a>5. 차트 제목  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>차트 영역 위쪽에 있는 차트 제목을 변경하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  차트 위쪽의 **차트 제목** 단어를 선택 하 고 다음 텍스트를 입력 합니다. **매장 판매 주문 합계**.  
  
3.  **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a>6. 세로 축의 서식 및 레이블 지정  
 기본적으로 세로 축에는 차트 크기에 맞게 자동으로 늘어나는 일반 형식으로 값이 표시됩니다.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>세로 축의 숫자를 통화 형식으로 지정하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  차트 측면의 세로 축에 있는 레이블을 두 번 클릭하여 선택합니다.  
  
3.  리본 메뉴의 **홈** 탭에 있는 **숫자** 그룹에서 **통화** 단추를 클릭 합니다. 축 레이블이 변경되어 통화 형식이 표시됩니다.  
  
4.  리본 메뉴의 **홈** 탭에 있는 **숫자** 그룹에서 **소수 자릿수 줄이기** 단추를 두 번 클릭 하 여 가장 가까운 원화로 반올림 한 숫자를 표시 합니다.  
  
5.  세로 축을 마우스 오른쪽 단추로 클릭 하 고 **세로 축 속성**을 클릭 합니다.  
  
6.  **숫자**를 클릭 합니다. **범주** 상자에서 **통화** 는 이미 선택 되어 있으며 **소수 자릿수** 는 이미 **0** 입니다.  
  
7.  **값 표시 위치** 상자에서 **천**을 클릭 합니다.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. 차트의 측면을 따라 세로 축 제목을 마우스 오른쪽 단추로 클릭 하 고 **축 제목 속성**을 클릭 합니다.  
  
10. **제목 텍스트** 필드의 텍스트를 **Sales Total (천 단위)** 텍스트로 바꿉니다. 제목의 형식을 지정하는 방법과 관련된 다양한 옵션을 지정할 수도 있습니다.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a>7. 이동 평균 추가  
  
#### <a name="to-add-a-moving-average"></a>이동 평균을 추가하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  차트를 두 번 클릭하여 **차트 데이터** 창을 표시합니다.  
  
3.  **값** 영역에 있는 **[Sum (Sales)]** 필드를 마우스 오른쪽 단추로 클릭 한 다음 **계산 된 계열 추가**를 클릭 합니다.  
  
4.  **수식**에서 **이동 평균** 이 선택되어 있는지 확인합니다.  
  
5.  **수식 매개 변수 설정**의 **기간**에서 **4**를 선택합니다.  
  
6.  **테두리**를 클릭 합니다.  
  
7.  **선 두께**에서 **3pt**를 선택 합니다.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
 차트에 4일 단위로 평균이 계산된 날짜별 총 판매액의 이동 평균을 나타내는 선이 표시됩니다.  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a>8. 보고서 제목 추가  
  
#### <a name="to-add-a-report-title"></a>보고서 제목을 추가하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.  
  
3.  **Sales Chart**를 입력 하 고 enter 키를 누른 다음 **1 월부터 12 월 2009**을 입력 하면 다음과 같이 표시 됩니다.  
  
     **Sales Chart**  
  
     **January to December 2009**  
  
4.  **Sales Chart**를 선택 하 고 리본 메뉴의 **홈** 탭에 있는 **글꼴** 섹션에서 **굵게** 단추를 클릭 합니다.  
  
5.  **1 월 ~ 12 월 2009**을 선택 하 고 **홈** 탭의 **글꼴** 섹션에서 글꼴 크기를 **10**으로 설정 합니다.  
  
6.  필드 아래쪽 가장자리의 가운데를 클릭할 때 양방향 화살표를 끌어 두 줄의 텍스트를 포함 하기 위해 **제목** 입력란을 더 길게 만들어야 할 수도 있습니다.  
  
     이 제목은 보고서 맨 위에 나타납니다. 페이지 머리글이 정의되지 않았을 경우 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.  
  
7.  **실행** 을 클릭하여 보고서를 미리 봅니다.  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. 보고서 저장  
  
#### <a name="to-save-the-report"></a>보고서를 저장하려면  
  
1.  보고서 디자인 뷰로 전환합니다.  
  
2.  보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.  
  
3.  **이름**에 **Sales Order Column Chart**를 입력합니다.  
  
4.  **저장**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
 보고서에 세로 막대형 차트 추가 자습서를 성공적으로 완료했습니다. 차트에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 및 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md)   
 [SQL Server 2014의 보고서 작성기](report-builder/report-builder-in-sql-server-2016.md)  
  
  
