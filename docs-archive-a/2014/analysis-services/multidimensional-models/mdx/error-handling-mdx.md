---
title: 오류 처리 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653614"
---
# <a name="error-handling-mdx"></a>오류 처리(MDX)
  MDX 스크립트의 오류가 처리되는 방법을 각 큐브에서 제어할 수 있습니다. 오류 처리는 `ScriptErrorHandlingMode` 열거자를 통해 수행됩니다. 이 열거자에 사용할 수 있는 값은 다음과 같습니다.  
  
 `IgnoreNone`  
 가 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] MDX 스크립트에서 오류를 발견 하면 서버에서 오류를 발생 시킵니다.  
  
 `IgnoreAll`  
 구문 오류, 이름 확인 오류 등을 포함하는 MDX 스크립트 내의 모든 명령을 서버가 무시하도록 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
