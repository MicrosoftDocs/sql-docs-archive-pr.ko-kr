---
title: 가장 정보 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9226fdbe8656aecf0f9173976c67ee386040d6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728924"
---
# <a name="impersonation-information"></a>가장 정보
  **가장 정보** 페이지를 사용하여 Analysis Services에서 데이터 원본에 연결하는 데 사용할 자격 증명을 지정할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **특정 Windows 사용자 이름 및 암호 사용**  
 지정된 Windows 사용자 계정의 보안 자격 증명을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 사용하려면 이 옵션을 선택합니다. 지정한 자격 증명은 처리, ROLAP 쿼리, 아웃오브 라인 바인딩, 로컬 큐브, 마이닝 모델, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 사용됩니다. 그러나 DMX(Data Mining Extensions) OPENQUERY 문의 경우 이 옵션이 무시되고 현재 사용자의 자격 증명이 사용됩니다.  
  
 **사용자 이름**  
 선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 사용할 사용자 계정의 도메인과 이름을 입력합니다. 이때 다음 형식을 사용합니다.  
  
 *\<Domain name>* **\\** *\<User account name>*  
  
 이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.  
  
 **암호**  
 선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 사용할 사용자 계정의 암호를 입력합니다.  
  
 이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.  
  
 **서비스 계정 사용**  
 개체를 관리하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서비스와 연결된 보안 자격 증명을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 사용하려면 이 옵션을 선택합니다. 서비스 계정 자격 증명은 처리, ROLAP 쿼리, 원격 파티션, 연결된 개체, 대상과 원본 간의 동기화 등에 사용됩니다. 그러나 DMX(Data Mining Extensions) OPENQUERY 문, 로컬 큐브 및 마이닝 모델의 경우 현재 사용자의 자격 증명이 사용됩니다. 아웃오브 라인 바인딩에 대해서는 이 옵션이 지원되지 않습니다.  
  
 **현재 사용자의 자격 증명 사용**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에서 아웃오브 라인 바인딩, DMX OPENQUERY, 로컬 큐브 및 마이닝 모델에 대해 현재 사용자의 보안 자격 증명을 사용하려면 이 옵션을 선택합니다. 처리, ROLAP 쿼리, 원격 파티션, 연결된 개체 및 대상과 원본 간의 동기화에 대해서는 이 옵션이 지원되지 않습니다.  
  
 **계승**  
 데이터베이스 수준에서 정의된 가장 동작을 사용하려면 이 옵션을 선택합니다. 가장 동작은 서버 관리자가 `DataSourceImpersonation` 데이터베이스 속성을 사용하여 설정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델의 데이터 원본](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [SSAS 다차원&#41;&#40;지원 되는 데이터 원본](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
