---
title: '3 단원: 열 이름 바꾸기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639007"
---
# <a name="lesson-3-rename-columns"></a>3단원: 열 이름 바꾸기
  이 단원에서는 가져온 각 테이블에 있는 여러 열의 이름을 바꿉니다. 열 이름을 바꾸면 모델 디자이너에서 열을 명확하게 식별하고 탐색할 수 있을 뿐 아니라 사용자는 클라이언트 애플리케이션에서 필드를 손쉽게 선택할 수 있습니다. 자세한 내용은 [테이블 또는 열 이름 바꾸기&#40;SSAS 테이블 형식&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md)를 참조하세요.  
  
> [!IMPORTANT]  
>  이 자습서를 완료하기 위해 열 이름을 바꿀 필요는 없습니다. 그러나 관계 만들기, DAX 수식을 사용해 계산 열 및 측정값 만들기에 대해 소개하는 단원을 비롯한 나머지 단원에서는 이 단원에 설명된 알아보기 쉬운 열 이름을 참조합니다. 열 이름을 바꾸지 않으려는 경우 이 단원에 제공된 원래 원본 열 이름을 사용하도록 5, 6, 7단원에서 DAX 수식을 편집해야 합니다.  
  
 이 단원을 완료하기 위한 예상 시간: **20분**  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다. 이 단원의 태스크를 수행하려면 이전 단원인 [2단원: 데이터 추가](lesson-2-add-data.md)를 완료해야 합니다.  
  
## <a name="rename-columns"></a>열 이름 바꾸기  
  
#### <a name="to-rename-columns"></a>열 이름을 바꾸려면  
  
1.  모델 디자이너에서 **Customer** 테이블(탭)을 클릭합니다.  
  
     탭을 클릭하면 해당 테이블이 모델 디자이너 창에서 활성화됩니다.  
  
2.  **Customerkey** 열 이름을 두 번 클릭 하 고를 입력 한 `Customer  Id` 다음 enter 키를 누릅니다.  
  
    > [!TIP]  
    >  열의 **속성** 창이 나 다이어그램 뷰에서 열 **이름** 속성의 열 이름을 바꿀 수도 있습니다.  
  
3.  **Customer** 테이블의 나머지 열과 나머지 테이블에 있는 열의 이름을 바꿔 원본 이름을 알아보기 쉬운 이름으로 변경합니다.  
  
     **Customer 테이블**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |CustomerAlternateKey|Customer Alternate Id|  
    |FirstName|이름|  
    |MiddleName|Middle Name|  
    |LastName|성|  
    |NameStyle|Name Style|  
    |BirthDate|Birth Date|  
    |MaritalStatus|Marital Status|  
    |EmailAddress|메일 주소|  
    |YearlyIncome|Yearly Income|  
    |TotalChildren|Total Children|  
    |NumberChildrenAtHome|Number of Children At Home|  
    |EnglishEducation|Education|  
    |EnglishOccupation|Occupation|  
    |HouseOwnerFlag|Owns House|  
    |NumberCarsOwned|Number of Cars Owned|  
    |AddressLine1|Address Line 1|  
    |AddressLine2|Address Line 2|  
    |전화|전화 번호|  
    |DateFirstPurchase|Date of First Purchase|  
    |CommuteDistance|Commute Distance|  
  
     **날짜**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |FullDateAlternateKey|Date|  
    |DayNumberOfWeek|Day Number of Week|  
    |EnglishDayNameOfWeek|Day Name|  
    |DayNumberOfMonth|월간 일자|  
    |DayNumberOfYear|연간 일자|  
    |WeekNumberOfYear|Week Number of Year|  
    |EnglishMonthName|월 이름|  
    |MonthNumberOfYear|월|  
    |CalendarQuarter|Calendar Quarter|  
    |CalendarYear|Calendar Year|  
    |CalendarSemester|Calendar Semester|  
    |FiscalQuarter|Fiscal Quarter|  
    |FiscalYear|Fiscal Year|  
    |FiscalSemester|Fiscal Semester|  
  
     **지리**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |StateProvinceCode|State Province Code|  
    |StateProvinceName|State Province Name|  
    |CountryRegionCode|Country Region Code|  
    |EnglishCountryRegionName|Country Region Name|  
    |우편 번호|우편 번호|  
    |SalesTerritoryKey|Sales Territory Id|  
  
     **Product**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |ProductAlternateKey|Product Alternate Id|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |WeightUnitMeasureCode|Weight Unit Code|  
    |SizeUnitMeasureCode|Size Unit Code|  
    |EnglishProductName|제품 이름|  
    |StandardCost|Standard Cost|  
    |FinishedGoodsFlag|Is Finished Product|  
    |SafetyStockLevel|Safety Stock Level|  
    |ReorderPoint|Reorder Point|  
    |ListPrice|List Price|  
    |SizeRange|Size Range|  
    |DaysToManufacture|Days to Manufacture|  
    |ProductLine|Product Line|  
    |Dealer Price|Dealer Price|  
    |ModelName|모델 이름|  
    |LargePhoto|Large Photo|  
    |EnglishDescription|Description|  
    |StartDate|Product Start Date|  
    |EndDate|Product End Date|  
    |상태|Product Status|  
  
     **제품 범주**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |ProductCategoryKey|Product Category Id|  
    |ProductCategoryAlternateKey|Product Category Alternate Id|  
    |EnglishProductCategoryName|Product Category 이름|  
  
     **Product Subcategory**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |ProductSubcategoryAlternateKey|Product Subcategory Alternate Id|  
    |EnglishProductSubcategoryName|Product Subcategory Name|  
    |ProductCategoryKey|Product Category Id|  
  
     **Internet Sales**  
  
    |원본 이름|친숙한 이름|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |CustomerKey|Customer Id|  
    |PromotionKey|Promotion Id|  
    |CurrencyKey|Currency Id|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesOrderNumber|Sales Order Number|  
    |SalesOrderLineNumber|Sales Order Line Number|  
    |RevisionNumber|Revision Number|  
    |OrderQuantity|Order Quantity|  
    |UnitPrice|Unit Price|  
    |ExtendedAmount|Extended Amount|  
    |UnitPriceDiscountPct|Unit Price Discount Pct|  
    |DiscountAmount|Discount Amount|  
    |ProductStandardCost|Product Standard Cost|  
    |TotalProductCost|Total Product Cost|  
    |SalesAmount|Sales Amount|  
    |TaxAmt|Tax Amt|  
    |CarrierTrackingNumber|Carrier Tracking Number|  
    |CustomerPONumber|Customer PO Number|  
    |OrderDate|Order Date|  
    |DueDate|Due Date|  
    |ShipDate|Ship Date|  
  
## <a name="next-step"></a>다음 단계  
 이 자습서를 계속하려면 다음 단원인 [4단원: 날짜 테이블로 표시](lesson-3-mark-as-date-table.md)로 이동하세요.  
  
  
