---
title: 파티션 병합 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649759"
---
# <a name="merging-partitions-xmla"></a>파티션 병합(XMLA)
  파티션의 집계 디자인 및 구조가 동일한 경우 XML for Analysis (XMLA)에서 [Mergepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) 명령을 사용 하 여 파티션을 병합할 수 있습니다. 파티션 병합은 파티션을 관리할 때 수행하는 중요한 동작으로, 특히 날짜별로 파티션된 기록 데이터가 들어 있는 파티션을 관리하는 데 유용합니다.  
  
 예를 들어, 재무 큐브에서 다음과 같은 파티션 2개를 사용할 수 있습니다.  
  
-   한 파티션은 올해의 재무 데이터를 나타내며 성능을 위해 실시간 ROLAP(관계형 OLAP) 스토리지 설정을 사용합니다.  
  
-   다른 파티션은 작년의 재무 데이터를 나타내며 저장을 위해 MOLAP(다차원 OLAP) 스토리지 설정을 사용합니다.  
  
 두 파티션에 사용된 스토리지 설정은 서로 다르지만 집계 디자인은 같습니다. 연말에 기록 데이터를 연도별로 처리하는 방식으로 큐브를 처리하는 대신 `MergePartitions` 명령을 사용하여 올해의 파티션을 작년의 파티션에 병합할 수 있습니다. 이렇게 하면 많은 시간이 소요될 수 있는 전체 큐브 처리 작업을 수행하지 않고도 집계 데이터를 유지할 수 있습니다.  
  
## <a name="specifying-partitions-to-merge"></a>병합할 파티션 지정  
 `MergePartitions`명령이 실행 되 면 [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) 속성에 지정 된 원본 파티션에 저장 된 집계 데이터가 [대상](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) 속성에 지정 된 대상 파티션에 추가 됩니다.  
  
> [!NOTE]  
>  `Source` 속성은 둘 이상의 파티션 개체 참조를 가질 수 있지만 `Target` 속성은 그럴 수 없습니다.  
  
 `Source` 및 `Target`에 모두 지정된 파티션을 성공적으로 병합하려면 두 속성이 같은 측정값 그룹에 포함되어야 하고 같은 집계 디자인을 사용해야 합니다. 그렇지 않으면 오류가 발생합니다.  
  
 `Source`에 지정된 파티션은 `MergePartitions` 명령이 완료된 후 삭제됩니다.  
  
## <a name="examples"></a>예  
  
### <a name="description"></a>Description  
 다음 예에서는 **놀이 works DW** 예제 데이터베이스에 있는 **어드벤처 works** 큐브의 **Customer 개수** 측정값 그룹에 있는 모든 파티션을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Customers_2004** 파티션에 병합 합니다.  
  
### <a name="code"></a>코드  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Analysis Services에서 XMLA를 사용하여 개발](developing-with-xmla-in-analysis-services.md)  
  
  
