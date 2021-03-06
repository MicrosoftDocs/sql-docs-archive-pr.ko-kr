---
title: 실패 한 패키지를 다시 시작 하기 위한 검사점 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a85354377453e0b24692ab8c2b567cc8998b6b05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736663"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>실패한 패키지를 다시 시작하는 검사점 구성
  검사점에 적용되는 속성을 설정하여 전체 패키지를 다시 실행하는 대신 장애 지점에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 다시 시작하도록 구성합니다.  
  
### <a name="to-configure-a-package-to-restart"></a>패키지를 다시 시작하도록 구성하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 구성할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  **솔루션 탐색기**에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **제어 흐름** 탭을 클릭합니다.  
  
4.  제어 흐름 디자인 화면 배경의 아무 위치나 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.  
  
5.  SaveCheckpoints 속성을로 설정 `True` 합니다.  
  
6.  CheckpointFileName 속성에 검사점 파일의 이름을 입력합니다.  
  
7.  CheckpointUsage 속성을 다음 두 값 중 하나로 설정합니다.  
  
    -   패키지를 항상 검사점에서 다시 시작하려면 `Always`를 선택합니다.  
  
        > [!IMPORTANT]  
        >  검사점 파일을 사용할 수 없으면 오류가 발생합니다.  
  
    -   검사점 파일이 있는 경우에만 패키지를 검사점에서 다시 시작하려면 `IfExists`를 선택합니다.  
  
8.  패키지가 다시 시작될 수 있는 태스크 및 컨테이너를 구성합니다.  
  
    -   태스크 또는 컨테이너를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
    -   `True`선택한 각 태스크 및 컨테이너에 대해 FailPackageOnFailure 속성을로 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [검사점을 사용하여 패키지 다시 시작](packages/restart-packages-by-using-checkpoints.md)  
  
  
