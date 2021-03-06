---
title: 보고서 인쇄(SharePoint 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- printing reports, SharePoint Web application
- printing reports
ms.assetid: 026784f7-8cb4-4351-93ee-230b2ab0f8f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5beb9301d21d59d166e1f3725e19b27e994c0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648819"
---
# <a name="print-a-report-reporting-services-in-sharepoint-mode"></a>보고서 인쇄(SharePoint 모드의 Reporting Services)
  SharePoint 모드에서 실행되는 보고서 서버의 경우 다음 세 가지 방법으로 SharePoint 웹 애플리케이션에서 보고서를 인쇄할 수 있습니다.  
  
-   **SharePoint 사이트** 보고서를 열 때 보고서 도구 모음에 나타나는 **동작** 메뉴에서 **인쇄** 를 선택합니다. 그러면 프린터 선택, 페이지 및 여백 지정, 보고서 미리 보기에 사용되는 표준 **인쇄** 대화 상자가 포함된 Reporting Services 인쇄 기능이 제공됩니다. 브라우저의 파일 메뉴에 있는 인쇄 명령 대신 이 인쇄 기능을 사용할 수 있습니다. 이러한 방식으로 보고서를 인쇄하면 웹 페이지 인쇄 결과물에 나타나는 추가 요소 없이 보고서가 디자인된 그대로 인쇄됩니다.  
  
-   **브라우저** 브라우저의 인쇄 기능은 단일 페이지에 맞는 HTML 보고서에 대해 가장 잘 작동합니다. 일반적으로 브라우저에서 인쇄하는 페이지에는 웹 페이지의 모든 시각적 요소뿐만 아니라 페이지나 웹 사이트를 식별하는 머리글 및 바닥글 정보가 포함됩니다. 브라우저에서 인쇄하면 현재 창의 내용만 인쇄됩니다. 보고서가 길 경우 브라우저에서는 보고서의 일부(일반적으로 첫 페이지)만 인쇄합니다.  
  
-   **대상 애플리케이션** 보고서를 내보내 Microsoft Office Excel 또는 Adobe Acrobat Reader와 같은 대상 애플리케이션의 인쇄 기능을 사용할 수 있습니다. 여러 페이지로 구성된 보고서를 인쇄할 경우 TIFF 또는 PDF와 같은 일부 애플리케이션 형식이 적합합니다. 보고서를 데스크톱 애플리케이션으로 내보낼 경우 해당 애플리케이션이 제공하는 모든 특수 인쇄 기능을 사용할 수 있습니다. 보고서를 내보내려면 보고서를 열 때 보고서 도구 모음에 나타나는 **동작** 메뉴에서 **내보내기** 를 선택합니다.  
  
> [!NOTE]  
>  보고서를 인쇄하려면 보고서를 볼 권한이 있어야 합니다.  
  
 웹 페이지에서 보고서를 인쇄할 때 최상의 결과를 얻으려면 **동작** 메뉴의 **인쇄** 를 사용하는 것이 좋습니다. **인쇄** 동작은 보고서 서버에서 다운로드되는 클라이언트 인쇄 컨트롤에 연결되어 있습니다. 다운로드는 처음 **인쇄**를 선택할 때 한 번 수행됩니다.  
  
 보고서 작성자는 인쇄 결과물이나 특정 애플리케이션 형식에 맞게 특별히 보고서를 디자인할 수 있습니다. 여러 애플리케이션 형식에 대해 페이지 매김이 구현되는 방식으로 인해 일부 내보내기 형식의 보고서에서는 최적의 인쇄 결과물을 얻지 못할 수 있습니다. 인쇄 결과물에 맞게 디자인되는 보고서와 달리 화면에 나타나는 보고서 페이지는 데이터 양의 변화에 따라 크기가 적절하게 조정되도록 디자인됩니다. 예를 들어 행렬을 포함하는 보고서의 경우 행과 열을 확장하는 방식에 따라 페이지가 가로와 세로 방향으로 모두 늘어날 수 있습니다. 가변 크기 보고서를 인쇄하는 경우 행렬을 확장하지 않는 사용자에게는 행렬을 확장하는 사용자와는 다른 인쇄 결과가 나타납니다. 내보낸 보고서 인쇄물에는 대부분 사용자가 컴퓨터 모니터에서 볼 때 보고서에 표시되는 항목이 모두 포함됩니다.  
  
### <a name="how-to-print-reports-from-the-actions-menu"></a>동작 메뉴에서 보고서를 인쇄하는 방법  
  
1.  보고서를 엽니다.  
  
2.  **동작** 메뉴에서 **인쇄**를 클릭합니다. **동작** 메뉴가 표시되지 않으면 보고서 도구 모음이 숨겨져 해당 기능을 사용할 수 없는 것입니다. **동작** 메뉴가 표시되지만 **인쇄** 가 없으면 보고서 서버에서 인쇄 기능이 해제되어 이 기능을 사용할 수 없는 것입니다.  
  
3.  **인쇄** 대화 상자에서 사용할 프린터와 설정을 선택하고 **확인**을 클릭합니다.  
  
     기본 설정을 수정하려면 **속성** 단추를 클릭합니다. 페이지 크기는 보고서 정의에 지정된 보고서 페이지 크기의 기본 높이와 너비에 따라 결정됩니다. 페이지 크기를 변경할 수 있는 범위는 사용하는 프린터의 기능에 따라 달라집니다.  
  
     인쇄하기 전에 보고서를 보려면 **미리 보기** 단추를 클릭합니다. 이렇게 하면 보고서의 첫 페이지가 별도의 미리 보기 창에서 열립니다. 보고서 서버에서 보고서가 렌더링됨에 따라 추가 페이지도 표시됩니다. 미리 보는 보고서는 EMF 형식으로 렌더링됩니다. 이전 페이지나 다음 페이지로 이동할 수 있으며 마지막 페이지에서는 **다음** 단추가 비활성화됩니다. 미리 보기 페이지에서 인쇄 여백을 수정하려면 **여백** 단추를 클릭합니다. 그러면 **여백** 대화 상자가 표시됩니다. 위쪽, 아래쪽, 오른쪽 및 왼쪽 여백을 구성하고 **확인**을 클릭합니다. 대화 상자가 닫히고 미리 보기 및 인쇄 렌더링 설정이 저장됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services에 대한 클라이언트 쪽 인쇄 기능 설정 및 해제](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
  
