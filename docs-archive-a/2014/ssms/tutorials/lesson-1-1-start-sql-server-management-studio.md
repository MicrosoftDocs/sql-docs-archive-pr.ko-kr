---
title: SQL Server Management Studio 시작 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8fc9de4884da9a4c372eecdeb6fde12cf3c507e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727836"
---
# <a name="start-sql-server-management-studio"></a>SQL Server Management Studio 시작
  이 자습서를 시작하기 전에 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 간단히 살펴봅니다.  
  
## <a name="opening-sql-server-management-studio"></a>SQL Server Management Studio 열기  
  
#### <a name="to-open-sql-server-management-studio"></a>SQL Server Management Studio를 열려면  
  
1.  **시작** 메뉴에서 **모든 프로그램**,을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] 다음 **SQL Server Management Studio**을 클릭 합니다.  
  
    > [!NOTE]  
    >  기본적으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]는 설치되지 않습니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용할 수 없으면 설치 프로그램을 실행하여 설치합니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]는 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서 사용할 수 없습니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Express는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=14630)에서 무료로 다운로드할 수 있지만이 자습서에 설명 된 것과 다른 사용자 인터페이스가 있습니다.  
  
2.  **서버에 연결** 대화 상자에서 기본 설정을 확인한 다음 **연결**을 클릭합니다. 연결 하려면 **서버 이름** 상자에가 설치 된 컴퓨터의 이름을 포함 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssDE](../../includes/ssde-md.md)]이 명명 된 인스턴스인 경우 **서버 이름** 상자에는 \<*computer_name*> \\ <> *instance_name* 형식으로 인스턴스 이름도 포함 되어야 합니다.  
  
## <a name="management-studio-components"></a>Management Studio 구성 요소  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 는 유형에 따른 전용 창에 정보를 나타냅니다. 데이터베이스 정보는 개체 탐색기 및 문서 창에 표시됩니다.  
  
-   개체 탐색기는 서버에 있는 모든 데이터베이스 개체의 트리 뷰로, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]데이터베이스를 포함할 수 있습니다. 개체 탐색기에는 연결된 모든 서버에 대한 정보가 포함되어 있습니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 열면 마지막으로 사용된 설정에 개체 탐색기를 연결하라는 메시지가 표시됩니다. 등록된 서버 구성 요소에서 서버를 두 번 클릭하여 연결할 수 있지만 연결할 서버를 등록하지 않아도 됩니다.  
  
-   문서 창은 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 가장 큰 부분으로, 쿼리 편집기와 브라우저 창을 포함할 수 있습니다. 기본적으로 현재 컴퓨터의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결된 요약 페이지가 표시됩니다.  
  
## <a name="showing-additional-windows"></a>추가 창 표시  
  
#### <a name="to-show-the-registered-servers-window"></a>등록된 서버 창을 표시하려면  
  
1.  **보기** 메뉴에서 **등록된 서버**를 클릭합니다.  
  
     등록된 서버 창은 개체 탐색기 위에 나타납니다. 예약된 서버에는 사용자가 자주 관리하는 서버가 나열됩니다. 이 목록에서 서버를 추가하거나 제거할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행 중인 컴퓨터의 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]인스턴스만 나열됩니다.  
  
2.  서버가 나타나지 않으면 등록 된 서버에서 **데이터베이스 엔진**를 마우스 오른쪽 단추로 클릭 한 다음 **로컬 서버 등록 업데이트**를 클릭 합니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [등록된 서버 및 개체 탐색기와 연결](../object/object-explorer.md)  
  
  
