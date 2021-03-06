---
title: 보고서 데이터 창 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c87ee4411f5c1ec4c07e0fc9f0357f6fb33e3c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639353"
---
# <a name="report-data-pane-report-builder"></a>보고서 데이터 창(보고서 작성기)
  **보고서 데이터** 창을 사용하여 보고서의 현재 정의된 매개 변수, 데이터 원본, 데이터 세트, 필드 컬렉션 및 이미지를 볼 수 있습니다. 보고서 데이터는 보고서의 데이터를 나타내는 항목의 계층 뷰를 표시합니다. 최상위 노드는 기본 제공 필드, 매개 변수, 이미지 및 데이터 원본 참조를 나타냅니다. 각 노드를 확장하여 데이터 항목을 볼 수 있습니다. 예를 들어 데이터 원본 노드를 확장하면 해당 데이터 원본에 대해 정의된 데이터 세트가 표시됩니다. 데이터 세트를 확장하면 필드 컬렉션이 표시됩니다. 항목을 보고서 디자인 화면이나 그룹화 창으로 끌어 데이터를 보고서 페이지의 선택된 보고서 항목에 연결합니다. 자세한 내용은 [보고서 디자인 뷰&#40;보고서 작성기&#41;](report-builder/report-design-view-report-builder.md)를 참조하세요.

## <a name="options"></a>옵션
 **기본 제공 필드** 보고서 이름이 나 페이지 번호와 같이 보고서에서 일반적으로 사용 되는 필드를 나타냅니다. 자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.

 **매개 변수** 각각 단일 값 또는 다중값 일 수 있는 보고서 매개 변수의 컬렉션을 나타냅니다. 자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.

 **이미지** 보고서에 사용되는 이미지 집합을 나타냅니다. 자세한 내용은 [이미지&#40;보고서 작성기 및 SSRS&#41;](report-design/images-report-builder-and-ssrs.md)를 참조하세요.

 **데이터 원본** 포함 된 데이터 원본 또는 공유 데이터 원본에 대 한 참조를 나타냅니다. 데이터 원본은 보고서의 데이터 원본을 나타냅니다. 데이터 원본은 이를 사용하는 데이터 세트 컬렉션의 부모 노드입니다. 자세한 내용은 보고서 작성기의 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-datasets-ssrs.md) 및 [데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조 하세요.

 **데이터 집합** [!INCLUDE[tsql](../includes/tsql-md.md)]데이터베이스에서 데이터를 검색 하는 쿼리와 같은 명령 하나를 실행 하 여 데이터 원본에서 검색 되는 데이터를 나타냅니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . 데이터 세트은 쿼리로 지정되는 필드 컬렉션의 부모 노드이며 계산된 필드를 포함합니다. 보고서 작성기에서는 쿼리를 지정하는 데 유용한 쿼리 디자이너를 지원합니다. 자세한 내용은 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-datasets-ssrs.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
 [데이터 집합 필드 컬렉션 &#40;보고서 작성기 및 ssrs 보고서 작성기&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) [대화 상자, 창 및 마법사](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) [그룹화 창 &#40;](report-design/grouping-pane-report-builder.md) 보고서 작성기&#41;&#40;[및 ssrs 보고서를 찾고 보고 관리](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) 보고서 작성기


