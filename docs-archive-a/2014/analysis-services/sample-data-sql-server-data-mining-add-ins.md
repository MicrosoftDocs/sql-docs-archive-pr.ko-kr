---
title: 샘플 데이터 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17da9a42f4d76f5c271d5b225cf897a8ac2e97ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647924"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a>데이터 샘플링(SQL Server 데이터 마이닝 추가 기능)
  ![데이터 마이닝 리본의 데이터 분할 마법사](media/dmc-partition.gif "데이터 마이닝 리본의 데이터 분할 마법사")  
  
 **데이터 샘플링** 마법사를 사용 하면 모델을 작성 (학습) 하 고 모델을 테스트 하기 위한 두 개의 집합으로 원본 데이터를 쉽게 나눌 수 있습니다. 이 마법사에서는 대상을 더욱 잘 나타내는 새 데이터 집합을 작성할 수 있도록 데이터를 다시 샘플링하는 옵션도 제공합니다.  
  
 모델을 학습하고 테스트하기 위해 적합한 종류의 데이터를 만드는 것은 데이터 마이닝에서 중요한 부분이지만 적합한 도구 없이는 힘든 작업입니다. 마법사는 층별 샘플링을 수행하여 학습 및 테스트 집합의 균형이 잘 잡히도록 합니다.  
  
## <a name="random-sampling-and-oversampling"></a>무작위 샘플링 및 과다 샘플링  
 . 무작위 샘플링은 모델을 테스트하는 데 사용하는 데이터가 모델을 만드는 데 사용하는 데이터를 잘 나타내는지 확인할 수 있는 가장 좋은 방법입니다. Excel 또는 외부 데이터 원본에 저장된 데이터를 무작위로 샘플링할 수 있습니다.  
  
 무작위 샘플링 옵션을 사용 하면 **데이터 샘플링** 마법사에서 자동으로 학습 및 테스트 데이터 집합을 만들고 나중에 참조할 수 있도록 개별 Excel 워크시트로 출력 합니다.  
  
 데이터가 외부 데이터 원본이 아닌 Excel 통합 문서에 저장 되어 있는 경우 *과다 샘플링*를 사용할 수도 있습니다. 이 옵션을 사용할 때 데이터에서 부족할 수 있는 대상 값을 지정합니다. 이렇게 하면 마법사는 대상 값이 더 포함된 균형이 잡힌 집합을 수집합니다. 마법사에 목표 백분율을 달성하거나 특정 개수의 행을 만들도록 지시할 수 있습니다.  
  
 과다 샘플링 옵션을 사용 하는 경우 **데이터 샘플링** 마법사는 새로 균형이 조정 된 예제 데이터를 포함 하는 새 워크시트를 만듭니다.  
  
## <a name="using-the-sample-data-wizard"></a>데이터 샘플링 마법사 사용  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a>데이터를 학습 집합 및 테스트 집합으로 나누려면  
  
1.  **데이터 마이닝** 리본에서 **샘플 데이터**를 클릭 합니다.  
  
2.  **원본 데이터 선택** 페이지에서 분할할 **데이터가** Excel 범위 또는 테이블에 있는지 아니면 외부 데이터 원본에 있는지를 지정 합니다.  
  
3.  **샘플링 유형 선택** 페이지에서 무작위 샘플링을 통해 학습 및 테스트 데이터 집합을 만들지 아니면 과다 샘플링로 새 데이터 집합을 만들지를 지정 합니다.  
  
    > [!NOTE]  
    >  외부 데이터 원본을 사용할 경우 무작위 샘플링 옵션만 사용할 수 있습니다. 외부 데이터로 과다 샘플링을 사용하려면 Excel 데이터 연결을 사용하여 Excel 워크시트로 데이터를 가져온 다음 데이터 샘플링 마법사를 사용하십시오.  
  
4.  선택한 샘플링 방법에 따라 옵션을 설정합니다.  
  
    -   무작위 샘플링의 경우 테스트에 사용할 원래 데이터의 비율 또는 테스트 데이터 집합에 사용할 총 행 개수를 지정합니다.  
  
    -   과다 샘플링의 경우 강조할 열과 값을 선택합니다. 그런 다음 새 데이터 집합의 총 행 개수와 대상 값에 포함해야 할 새 데이터 집합의 행 비율을 지정합니다.  
  
         과다 샘플링의 대상 값은 불연속 값이어야 합니다. 연속 숫자 데이터는 과다 샘플링할 수 없습니다.  
  
5.  **마침 페이지**에서 새 데이터 집합의 기본 이름을 그대로 적용 하거나 새 이름을 입력 합니다.  
  
     마법사에서 각 데이터 집합에 대한 새 워크시트를 만듭니다.  
  
 Excel용 데이터 마이닝 클라이언트에서 제공되는 대부분의 마법사에는 데이터를 무작위로 학습 집합과 테스트 집합으로 구분하는 옵션도 있습니다. 그러나 마법사를 사용하는 경우 데이터가 같은 워크시트나 다른 데이터 원본에 유지되며 특정 행이 테스트 사례인지 또는 학습 사례인지에 대한 정보는 내부적으로 저장됩니다. 이와 대조적으로 **데이터 샘플링** 마법사를 사용 하면 쉽게 참조할 수 있도록 테스트 및 학습 데이터가 개별 워크시트로 출력 됩니다.  
  
## <a name="related-options"></a>관련 옵션  
 마법사를 진행하면서 다음과 같은 옵션을 사용할 수 있습니다.  
  
|옵션|주석|  
|-------------|--------------|  
|원본 데이터 선택 대화 상자(Excel용 데이터 마이닝 클라이언트)|데이터를 포함하는 Excel 범위 또는 테이블을 선택합니다. 외부 데이터를 사용하려는 경우 데이터는 관계형일 수 있지만 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본에 포함되어야 합니다. T|  
|샘플링 유형 선택 페이지(Excel용 데이터 마이닝 클라이언트)|외부 데이터 원본을 사용할 경우 무작위 샘플링 옵션만 사용할 수 있습니다. 또한 **행 개수** 옵션을 사용 하 여 최종 데이터 집합에 만들 행 수를 지정 해야 합니다. 원본 데이터의 비율은 지정할 수 없습니다.|  
|임의 샘플링 페이지(Excel용 데이터 마이닝 클라이언트)|원본 또는 특정 수의 행에서 특정 비율의 행을 복사할 수 있습니다.|  
|과다 샘플링 페이지(Excel용 데이터 마이닝 클라이언트)|**대상 상태**<br /><br /> 원래 데이터 집합에서 실제보다 과소 표시된 목록의 값을 선택합니다. 과다 샘플링하면 이 상태를 포함하는 데이터 행의 비율이 늘어납니다.<br /><br /> **샘플 크기**<br /><br /> 추출할 행의 총 수를 선택합니다. 이 값은 최종 데이터 집합의 크기를 나타냅니다.|  
  
## <a name="other-sampling-options"></a>기타 샘플링 옵션  
 이 마법사의 샘플링 옵션이 필요에 맞지 않지 않으면 SSIS(SQL Server Integration Services)의 샘플링 변환을 사용하여 여러 데이터 원본의 행을 샘플링할 수 있습니다.  
  
 자세한 내용은 [행 샘플링 변환](../integration-services/data-flow/transformations/row-sampling-transformation.md) 및 [백분율 샘플링 변환](../integration-services/data-flow/transformations/percentage-sampling-transformation.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 마이닝 준비 검사 목록](checklist-of-preparation-for-data-mining.md)  
  
  
