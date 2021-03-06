---
title: Visio 용 데이터 마이닝 셰이프 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a12d7d5f3ad021105f06043f47dcdfe5c3e5c2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653069"
---
# <a name="data-mining-shapes-for-visio"></a>Visio용 데이터 마이닝 셰이프
  Visio용 데이터 마이닝 셰이프는 데이터 마이닝 모델을 표시하기 위해 사용자 지정된 템플릿을 제공합니다. 이러한 템플릿을 사용하여, 사용자가 만든 모델에 연결할 수 있으며 데이터 마이닝의 결과를 보여 주기 위한 대화형 프레젠테이션을 만들 수 있습니다.  
  
 템플릿은 정적 그래프와 화면 캡처에 비해 많은 이점을 제공 합니다. 기본 데이터 마이닝 모델과 상호 작용 하며 Analysis Services 인스턴스에 저장 되며 마이닝 모델의 패턴이 표시 되는 방식을 사용자 지정할 수 있습니다. 트리 모델을 축소 및 확장하고 데이터 노드 또는 특성별로 필터링하며 확률 및 계수와 같은 모델 통계를 표시할 수 있습니다.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Visio 템플릿에는 다음과 같은 마법사가 포함되어 있습니다.  
  
-   **종속성 네트워크 다이어그램:** 이 마법사를 사용 하 여 의사 결정 트리 및 신경망에 대 한 그래프를 만들 수 있습니다.  
  
-   **의사 결정 트리 다이어그램:** 이 마법사를 사용 하 여 의사 결정 트리 모델과 연결 된 의사 결정 지점과 수식을 보여 주는 다이어그램을 만들 수 있습니다. 이 다이어그램은 회귀 모델에서도 사용할 수 있습니다.  
  
-   **클러스터 다이어그램:** 이 마법사를 사용 하 여 조각화 모델에 대 한 다채로운 그래프를 만들 수 있습니다. 특성 판별, 클러스터 프로필 및 종속성과 같은 뷰 사이를 전환하고 클러스터의 모양을 사용자 지정할 수 있습니다.  
  
## <a name="installation"></a>설치  
 Visio 용 데이터 마이닝 템플릿을 설치 하는 경우 기본적으로 다음 파일은 \<drive> Files\Microsoft SQL Server 2012 Dm 추가 기능 (또는 \<drive> \ 또는 Program files (x86) \Microsoft SQL SERVER 2012 Dm 추가 기능)에 설치 됩니다.  
  
-   **Microsoft 데이터 마이닝. v m s** 이 템플릿에는 데이터 마이닝 셰이프를 사용 하는 데 도움이 되는 미리 디자인 된 서식 지정, 레이아웃 및 마법사가 포함 되어 있습니다.  
  
-   **Microsoft 데이터 마이닝 셰이프 스튜디오. v** m 이 스텐실 파일에는 템플릿과 연결 된 셰이프가 포함 되어 있습니다.  
  
## <a name="how-to-use-the-templates"></a>템플릿 사용 방법  
 템플릿을 열려면 셰이프 파일을 두 번 클릭하거나 Visio를 연 다음 셰이프 템플릿을 엽니다.  
  
1.  스텐실에서 Visio 데이터 마이닝 셰이프 중 하나를 새 페이지에 끌어서 놓습니다.  
  
2.  마법사가 시작되면 표시하려는 데이터 마이닝 모델이 있는 서버에 연결합니다.  
  
3.  시각화 유형과 모델 유형이 일치하는 데이터 마이닝 모델을 선택합니다.  
  
4.  데이터를 표시하고 포맷하는 방법에 대한 옵션을 설정합니다.  
  
5.  **데이터 마이닝 셰이프 마법사**를 완료 한 후 Visio의 기능을 사용 하 여 수정 하 고 향상 시킬 수 있는 다이어그램이 있습니다.  
  
 Visio 모델 다이어그램을 사용 하 고 기능을 개선 하는 방법에 대 한 자세한 내용은 [visio에서 데이터 마이닝 모델 보기 &#40;데이터 마이닝 추가 기능](viewing-data-mining-models-in-visio-data-mining-add-ins.md) 을 참조 하세요&#41;  
  
## <a name="requirements"></a>요구 사항  
  
-   템플릿을 사용하려면 먼저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결해야 합니다.  
  
     마법사는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버를 선택하고 마이닝 모델이 포함된 데이터베이스를 지정하라는 메시지를 표시합니다.  
  
     연결을 만드는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.  
  
-   테이블 분석 도구를 사용하는 경우 모델을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 저장해야 하며 임시 모델을 사용하지 않아야 합니다.  
  
-   지원 되는 알고리즘 (클러스터링, 의사 결정 트리, 신경망, Naive Bayes 또는 로지스틱 회귀) 중 하나를 사용 하 여 모델을 만들어야 합니다.  
  
  
