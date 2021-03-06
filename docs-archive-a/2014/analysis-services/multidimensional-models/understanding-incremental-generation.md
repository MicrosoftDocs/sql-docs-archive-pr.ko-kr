---
title: 증분 생성 이해 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- incremental generation [Analysis Services]
- Schema Generation Wizard, incremental generation
- relational schema [Analysis Services], incremental generation
ms.assetid: 3ca0aa63-3eb5-4fe9-934f-8e96dee84eaa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a3bfef76d45d1d015e6f8a258b8df8b2ae639e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652398"
---
# <a name="understanding-incremental-generation"></a>증분 생성 이해
  처음 스키마를 생성한 후 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 큐브 및 차원 정의를 변경하고 스키마 생성 마법사를 다시 실행할 수 있습니다. 마법사는 주제 영역 데이터베이스 및 연결된 데이터 원본 뷰에서 스키마를 업데이트하여 변경 내용을 반영하고 다시 생성될 테이블의 현재 데이터를 가능한 범위까지 보존합니다. 처음 스키마를 생성한 후 테이블을 변경하면 스키마 생성 마법사가 다음 규칙에 따라 가능한 경우 해당 변경 내용을 유지합니다.  
  
-   마법사가 이전에 생성한 테이블을 덮어씁니다. 데이터 원본 뷰에서 테이블에 대한 `AllowChangesDuringGeneration` 속성을 `false`로 변경하여 마법사가 생성한 테이블을 덮어쓰지 못하게 할 수 있습니다. 테이블에 대한 제어 권한이 있는 경우 테이블은 다른 사용자 정의 테이블과 동일하게 처리되며 다시 생성 시 영향을 받지 않습니다. 생성되지 않도록 테이블을 제거한 후 나중에 데이터 원본 뷰에서 테이블에 대한 `AllowChangesDuringGeneration` 속성을 `true`로 변경할 수 있습니다. 또한 마법사가 변경할 수 있도록 테이블을 다시 열 수 있습니다. 자세한 내용은 [데이터 원본 뷰에서 속성 변경&#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md)을 참조하세요.  
  
-   마법사 이외의 방법으로 데이터 원본 뷰나 기본 데이터베이스에 테이블이 추가된 경우에는 테이블을 덮어쓰지 않습니다.  
  
 주제 영역 데이터베이스에서 이전에 생성된 테이블을 스키마 생성 마법사가 다시 생성할 때 이러한 테이블의 기존 데이터가 유지되도록 선택할 수 있습니다.  
  
## <a name="supporting-data-preservation"></a>데이터 유지 지원  
 일반적으로 스키마 생성 마법사는 이전에 생성한 테이블에 저장되는 데이터를 유지합니다. 또한 마법사가 생성한 테이블에 열을 추가하면 해당 데이터도 유지됩니다. 이러한 기능을 사용하여 차원 및 큐브를 추가하거나 수정하고 기본 테이블에 저장된 데이터를 다시 로드할 필요 없이 원본 개체를 다시 생성할 수 있습니다.  
  
> [!NOTE]  
>  구분된 텍스트 파일로부터 데이터를 로드하는 경우에는 다시 생성 시 스키마 생성 마법사가 이러한 파일과 해당 데이터를 덮어쓸지 여부도 선택할 수 있습니다. 마법사는 텍스트 파일을 완전히 덮어쓰거나 아예 덮어쓰지 않습니다. 스키마 생성 마법사는 이러한 파일을 부분적으로 덮어쓰지는 않습니다. 기본적으로 스키마 생성 마법사는 이러한 파일을 덮어쓰지 않습니다.  
  
### <a name="partial-preservation"></a>부분 유지  
 스키마 생성 마법사가 기존 데이터를 유지할 수 없는 경우가 있습니다. 다음 표에서는 다시 생성 시 마법사가 기본 테이블의 모든 기존 데이터를 유지할 수 없는 상황의 예를 보여 줍니다.  
  
|데이터 변경 유형|처리 방법|  
|-------------------------|---------------|  
|호환되지 않는 데이터 형식 변경|스키마 생성 마법사는 가능한 한 표준 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 변환을 사용하여 기존 데이터의 데이터 형식을 변환합니다. 그러나 특성의 데이터 형식을 기존 데이터와 호환되지 않는 형식으로 변경하면 영향을 받는 열의 데이터가 삭제됩니다.|  
|참조 무결성 오류|데이터가 있는 차원이나 큐브를 변경하는 경우 이로 인해 다시 생성 시 참조 무결성 오류가 발생하면 스키마 생성 마법사는 외래 키 테이블의 모든 데이터를 삭제합니다. 삭제되는 데이터가 FOREIGN KEY 제약 조건을 위반한 열 또는 참조 무결성 오류가 있는 행으로 제한되지는 않습니다. 예를 들어 차원 키를 비고유 또는 Null 데이터가 있는 특성으로 변경하면 외래 키 테이블의 기존 데이터가 모두 삭제됩니다. 또한 한 테이블의 모든 데이터를 삭제하면 연쇄적인 효과가 나타나며 다른 참조 무결성 위반이 발생할 수 있습니다.|  
|삭제된 특성 또는 차원|차원에서 특성을 삭제하는 경우 스키마 생성 마법사는 해당 특성에 매핑되는 열을 삭제합니다. 차원을 삭제하면 해당 차원에 매핑되는 테이블도 삭제됩니다. 이러한 경우 삭제된 열이나 테이블에 포함된 데이터가 삭제됩니다.|  
  
 스키마 생성 마법사는 데이터를 삭제하기 전에 데이터 손실 없이 마법사를 취소할 수 있도록 경고를 표시합니다. 그러나 스키마 생성 마법사가 예상되는 데이터 손실과 예상치 못한 데이터 손실을 구별하지는 못합니다. 마법사를 실행할 때 삭제될 데이터가 있는 테이블과 열이 대화 상자에 나열됩니다. 마법사가 계속하여 데이터를 삭제하도록 하거나 마법사를 취소하고 테이블과 열의 변경 내용을 수정할 수 있습니다.  
  
## <a name="supporting-cube-and-dimension-changes"></a>큐브 및 차원 변경 지원  
 차원과 큐브의 속성을 변경할 때 스키마 생성 마법사는 다음과 같이 관련 데이터 원본 뷰와 기본 주제 영역 데이터베이스에 적절한 개체를 다시 생성합니다.  
  
 차원, 큐브 또는 특성 등의 개체 삭제  
 스키마 생성 마법사는 삭제된 개체가 매핑되는 원본 개체를 삭제합니다. 마법사가 생성한 테이블에 열을 추가하더라도 해당 테이블은 삭제됩니다. 개체를 삭제하면 원본 개체에 저장된 데이터가 삭제되며 참조 무결성 오류가 발생할 경우 다른 데이터도 삭제될 수 있습니다.  
  
 차원, 큐브 또는 특성 등의 개체 이름 바꾸기  
 스키마 생성 마법사는 이름을 바꾼 개체가 매핑되는 원본 개체의 이름을 바꿉니다. 또한 마법사는 기본 키와 같이 영향을 받는 모든 개체의 이름도 바꿉니다. 원본 개체에 저장된 기존 데이터는 유지됩니다.  
  
 데이터 형식 변경 등의 개체 수정  
 스키마 생성 마법사는 변경된 개체가 매핑되는 원본 개체를 수정합니다. 새 데이터 형식이 기존 데이터와 호환되면 데이터베이스의 원본 개체에 저장된 기존 데이터가 유지됩니다.  
  
 차원, 큐브 또는 특성 등의 새 개체 추가  
 스키마 생성 마법사는 새 개체가 매핑되는 원본 개체를 추가합니다.  
  
 주제 영역 데이터베이스에 사용자 개체가 있어 데이터베이스 엔진이 오류를 반환하기 때문에 스키마 생성 마법사가 필요한 변경 작업을 수행할 수 없는 경우 스키마 생성 마법사는 실패하고 데이터베이스 엔진에서 반환한 오류가 표시됩니다. 예를 들어 마법사가 테이블을 생성 한 후 테이블에 primary key 제약 조건이 나 비클러스터형 인덱스를 만들 경우 스키마 생성 마법사는 제약 조건이 나 인덱스를 만들지 않았기 때문에 해당 테이블을 삭제 하지 않습니다.  
  
## <a name="supporting-schema-changes"></a>스키마 변경 지원  
 주제 영역 데이터베이스 또는 연결된 데이터 원본 뷰에서 테이블이나 열의 속성을 변경하면 스키마 생성 마법사는 다음과 같이 변경 내용을 처리합니다.  
  
 스키마 생성 마법사가 생성한 테이블이나 열 삭제  
 스키마 생성 마법사가 생성한 테이블이나 열을 삭제하면 해당 테이블이 다시 생성됩니다. 삭제된 테이블이나 열이 다시 생성된다는 경고는 표시되지 않습니다.  
  
 스키마 생성 마법사가 생성한 테이블이나 열의 속성 변경  
 스키마 생성 마법사가 생성한 테이블이나 열의 속성을 수정하면 변경 내용 없이 해당 테이블이 다시 생성됩니다. 예를 들어 열의 데이터 형식 또는 Null 허용 여부를 변경하거나 스키마 생성 마법사가 생성한 테이블의 파일 그룹을 변경할 경우 다시 생성 시 변경 내용이 유지되지 않습니다. 변경 내용 없이 해당 개체가 다시 생성된다는 경고는 표시되지 않습니다.  
  
 스키마 생성 마법사가 생성한 테이블에 열 추가 또는 주제 영역 데이터베이스나 준비 영역 데이터베이스에 테이블 추가  
 스키마 생성 마법사가 생성한 테이블에 열을 추가할 경우 다시 생성 시 해당 열이 유지됩니다. 이때 추가 열에 저장된 데이터도 모두 유지됩니다. 그러나 주제 영역 데이터베이스나 준비 영역 데이터베이스에 테이블을 추가하면 해당 테이블은 포함되지 않습니다. 추가된 열 또는 테이블은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스, DTS 패키지, 데이터 원본 뷰 또는 생성되는 스키마의 다른 위치에 반영되지 않습니다.  
  
## <a name="supporting-data-source-and-data-source-view-changes"></a>데이터 원본 및 데이터 원본 뷰 변경 지원  
 스키마 생성 마법사는 다시 실행될 때 원래 생성에 사용한 것과 동일한 데이터 원본 및 데이터 원본 뷰를 다시 사용합니다. 사용자가 추가하는 데이터 원본이나 데이터 원본 뷰는 사용되지 않습니다. 처음 생성 후 원래 데이터 원본이나 데이터 원본 뷰를 삭제하는 경우에는 마법사를 처음부터 실행해야 합니다. 마법사의 이전 설정도 모두 삭제됩니다. 삭제된 데이터 원본이나 데이터 원본 뷰에 바인딩된 기본 데이터베이스의 기존 개체는 다음에 스키마 생성 마법사를 실행할 때 사용자가 만든 개체로 처리됩니다.  
  
 생성 시 데이터 원본 뷰에 기본 데이터베이스의 실제 상태가 반영되지 않으면 스키마 생성 마법사가 주제 영역 데이터베이스와 준비 영역 데이터베이스에 대한 스키마를 생성할 때 오류가 발생할 수 있습니다. 예를 들어 데이터 원본 뷰에서 열에 대한 데이터 형식이 `int`로 설정되도록 지정하지만 열에 대한 데이터 형식이 실제로는 `string`으로 설정되어 있는 경우 스키마 생성 마법사는 데이터 원본 뷰에 따라 외래 키에 대한 데이터 형식을 `int`로 설정합니다. 실제 데이터 형식은 `string`이기 때문에 스키마 생성 마법사가 관계를 만들 때 오류가 발생합니다.  
  
 반면, 데이터 원본 연결 문자열을 이전 생성에서 다른 데이터베이스로 변경하는 경우에는 오류가 발생하지 않습니다. 새 데이터베이스가 사용되고 이전 데이터베이스는 변경되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 원본 뷰 및 데이터 원본에 대 한 변경 내용 관리](manage-changes-to-data-source-views-and-data-sources.md)   
 [스키마 생성 마법사&#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md)  
  
  
