---
title: For 루프 컨테이너 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cb33ea5b7f3f59baad3c94f6bc845c281613ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647166"
---
# <a name="configure-a-for-loop-container"></a>For 루프 컨테이너 구성
  이 절차에서는 **For 루프 편집기** 대화 상자를 사용하여 For 루프 컨테이너를 구성하는 방법에 대해 설명합니다.  
  
### <a name="to-configure-the-for-loop-container"></a>For 루프 컨테이너를 구성하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 For 루프 컨테이너를 두 번 클릭하여 **For 루프 편집기**를 엽니다.  
  
2.  선택적으로 For 루프 컨테이너의 이름과 설명을 수정합니다.  
  
3.  선택적으로 **InitExpression** 입력란에 초기화 식을 입력합니다.  
  
4.  **EvalExpression** 입력란에 계산 식을 입력합니다.  
  
    > [!NOTE]  
    >  식은 부울로 계산되어야 합니다. 식 결과가 `false`이면 루프 실행이 중지됩니다.  
  
5.  선택적으로 **AssignExpression** 입력란에 대입 식을 입력합니다.  
  
6.  선택적으로 **식** 페이지에서 **Expressions** 를 클릭하고 For 루프 컨테이너의 속성에 대한 속성 식을 만듭니다. 자세한 내용은 [속성 식 추가 또는 변경](expressions/add-or-change-a-property-expression.md)을 참조하세요.  
  
7.  **확인** 을 클릭하여 **For 루프 편집기**를 닫습니다.  
  
## <a name="see-also"></a>참고 항목  
 [For 루프 컨테이너](control-flow/for-loop-container.md)   
 [Integration Services &#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)   
 [패키지에서 속성 식 사용](expressions/use-property-expressions-in-packages.md)  
  
  
