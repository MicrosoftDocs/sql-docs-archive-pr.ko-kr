---
title: 데이터 피드 라이브러리를 사용 하 여 데이터 피드 공유 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feeds [Analysis Services with SharePoint]
ms.assetid: 4ec98dec-0cd2-4727-bb79-5bf6f8a865d6
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb24a0ae66cdb0b0623aaa217be778280bdb14ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651309"
---
# <a name="share-data-feeds-using-a-data-feed-library-powerpivot-for-sharepoint"></a>데이터 피드 라이브러리를 사용하여 데이터 피드 공유(SharePoint용 PowerPivot)
  데이터 피드는 Atom 연결 형식으로 데이터를 노출하는 서비스 또는 애플리케이션에서 생성되는 XML 데이터 스트림입니다. 데이터 피드는 애플리케이션 간에 데이터를 전송하고 클라이언트측 뷰어에게 데이터를 전송하는 데 점점 더 많이 사용되고 있습니다. SharePoint용 PowerPivot 배포에서는 데이터 피드를 사용 하 여 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 원본을 Atom 인식 응용 프로그램 또는 서비스의 데이터로 채웁니다.  
  
 이미 Atom 인식 애플리케이션 조합을 사용하고 있는 경우 애플리케이션 간의 데이터 전송이 완벽하게 수행되므로 피드가 어떻게 생성되고 사용되는지를 알 필요가 없습니다. 그러나 사용자 지정 솔루션을 사용하여 Atom 피드를 게시하는 조직에서는 정보 근로자가 피드를 사용할 수 있도록 해야 합니다. 이렇게 하는 한 가지 방법은 피드를 생성하는 온라인 원본에 대한 연결을 제공하는 데이터 서비스 문서(.atomsvc) 파일을 만들어 공유하는 것입니다. 데이터 피드 라이브러리라는 특수 용도의 라이브러리는 SharePoint 웹 애플리케이션에서 데이터 서비스 문서 만들기와 공유를 지원합니다.  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
 [필수 구성 요소](#prereq)  
  
 [데이터 서비스 문서 만들기](#createdsdoc)  
  
 [데이터 서비스 문서 보안](#securedsdoc)  
  
 [데이터 서비스 문서 수정](#modifydsdoc)  
  
 [다음 단계: 데이터 서비스 문서 사용](#usedsdoc)  
  
> [!NOTE]  
>  데이터 피드는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 에서 만든 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]데이터 원본에 웹 데이터를 추가하는 데 사용되지만 Atom 피드를 읽을 수 있는 모든 클라이언트 애플리케이션에서 데이터 서비스 문서를 처리할 수 있습니다.  
  
##  <a name="prerequisites"></a><a name="prereq"></a> 필수 조건  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]SharePoint 팜에 쿼리 처리를 추가 하는 SharePoint용 PowerPivot 배포가 있어야 합니다 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . 데이터 피드 지원은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 솔루션 패키지를 통해 배포됩니다.  
  
 데이터 서비스 문서 콘텐츠 형식을 지원하는 SharePoint 라이브러리가 있어야 합니다. 이 경우 기본 데이터 피드 라이브러리를 사용하는 것이 좋지만, 콘텐츠 형식을 라이브러리에 수동으로 추가할 수 있습니다. 자세한 내용은 [데이터 피드 라이브러리 만들기 또는 사용자 지정 &#40;SharePoint용 PowerPivot&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md)를 참조 하세요.  
  
 Atom 1.0 형식으로 XML 테이블 형식 데이터를 제공하는 데이터 서비스나 온라인 데이터 원본이 있어야 합니다.  
  
 SharePoint 라이브러리에서 데이터 서비스 문서를 만들거나 관리하려면 SharePoint 사이트에 대한 참가 권한이 있어야 합니다.  
  
##  <a name="create-a-data-service-document"></a><a name="createdsdoc"></a> 데이터 서비스 문서 만들기  
 데이터 서비스 문서는 데이터를 피드 형식으로 제공하는 온라인 데이터 원본 또는 애플리케이션의 요청에 따라 데이터를 스트리밍하라는 요청입니다. 데이터 서비스 문서를 만들 때 Atom 배포 형식으로 XML 테이블 형식을 제공하는 하나 이상의 URL 주소 지정 가능 데이터 서비스에 대한 포인터를 지정합니다.  
  
 단일 문서에서 여러 데이터 피드를 지정할 수 있습니다. 이 기능은 하나의 가져오기 작업에서 동일한 서비스나 다른 서비스의 데이터 페이로드 집합을 검색하려는 경우에 유용합니다.  
  
1.  SharePoint 사이트에서 데이터 피드 라이브러리나 데이터 서비스 콘텐츠 형식을 추가하고 구성한 다른 문서 라이브러리를 엽니다. 이전에 만든 데이터 피드 라이브러리를 찾으려면 빠른 실행에서 **모두 보기** 를 클릭합니다.  
  
2.  페이지 맨 위에 있는 리본의 문서 도구에서 **문서**를 클릭합니다.  
  
3.  **새 문서** 를 클릭한 다음 **데이터 서비스 문서**를 선택합니다.  
  
4.  새 데이터 서비스 문서 페이지에 다음 정보를 입력합니다.  
  
    1.  데이터 서비스 문서에 대한 이름 및 설명을 입력합니다. 사용자가 피드를 사용할지 여부를 결정할 수 있도록 충분한 정보를 제공해야 합니다.  
  
    2.  데이터 피드에서 Atom 1.0 형식으로 데이터를 제공하는 데이터 서비스 또는 웹 애플리케이션에 대한 URL을 입력합니다.  
  
         URL은 행과 열에 구조화된 데이터나 반구조화된 데이터를 반환하는 서비스로 확인되어야 합니다. 서비스는 현재 사용자의 보안 자격 증명을 사용하거나 익명으로 데이터를 반환해야 합니다.  
  
         URL은 Windows 인증, 기본 인증 또는 익명 액세스를 지원하는 서비스로 확인되어야 합니다. 피드를 가져오는 사용자가 사용할 체계를 지정합니다. 기본적으로 통합 보안이 선택됩니다.  
  
         데이터 피드 URL에는 매개 변수가 포함될 수 있습니다. 사용할 데이터를 정확하게 선택할 수 있는 고급 URL 주소 지정 체계를 지원하는 다양한 유형의 데이터 서비스 기술이 있습니다. 예를 들어 ADO.NET Data Service는 기본 데이터에서 엔터티, 연결 및 탐색 경로를 지정하는 URL 매개 변수를 제공합니다. 복잡한 URL을 데이터 피드 원본으로 지정하여 사용할 데이터 세트를 정확하게 지정할 수 있습니다.  
  
    3.  동일한 데이터 피드에 대해 클라이언트 애플리케이션의 데이터 세트를 식별하는 테이블 이름을 입력합니다. [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]에서 가져오는 각 데이터 피드는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 원본의 자체 테이블 컨트롤에 배치됩니다. 데이터 피드를 설정할 때 가져온 데이터를 수신하는 테이블의 이름을 지정해야 합니다.  
  
5.  동일한 서비스 또는 다른 서비스에서 추가 피드를 지정하려면 "다른 데이터 피드 추가"를 클릭하여 이전 단계를 반복합니다.  
  
     각 데이터 서비스 문서는 하나의 작업으로 처리됩니다. 문서의 모든 데이터 피드는 비동기적으로 생성되며 동일한 작업에서 클라이언트 애플리케이션에 반환됩니다. 따라서 함께 사용하려는 데이터 피드에 대한 URL 테이블 쌍만 지정합니다.  
  
     인증 체계는 데이터 서비스 문서 수준에서 설정되기 때문에 각 추가 데이터 피드는 첫 번째 피드와 동일한 인증 체계를 지원하는 서비스 또는 애플리케이션에서 생성되어야 합니다. 동일한 데이터 서비스 문서 내의 모든 피드는 런타임에서 동일한 방법으로 인증됩니다.  
  
6.  문서를 저장합니다. 데이터 서비스 문서는 이 콘텐츠 형식에 대해 구성된 콘텐츠 라이브러리에 물리적 파일(.atomsvc)로 저장됩니다.  
  
 데이터 서비스 문서를 사용하려면 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 에서 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 통합 문서를 열고 데이터 가져오기 마법사에서 **데이터 피드** 옵션을 선택할 수 있습니다. 메시지가 표시되면 데이터 가져오기 작업을 시작할 데이터 서비스 문서의 SharePoint URL을 지정합니다. 자세한 내용은 [데이터 피드 사용 &#40;SharePoint용 PowerPivot&#41;](use-data-feeds-power-pivot-for-sharepoint.md)를 참조 하세요.  
  
##  <a name="secure-a-data-service-document"></a><a name="securedsdoc"></a>데이터 서비스 문서 보안  
 데이터 서비스 문서는 해당 문서가 속해 있는 라이브러리의 권한을 상속합니다. 항목에 대해 설정한 권한에 따라 사용자가 데이터 서비스 문서를 열거나 수정하거나 삭제할 수 있는지 여부가 결정됩니다.  
  
 PowerPivot 클라이언트 애플리케이션에서 데이터 피드를 가져올 때 데이터 서비스 문서를 사용하려면 문서에 대한 보기 권한만 있으면 됩니다. 보기 권한만 있으면 가져오기 마법사에서 URL을 확인할 수 있습니다.  
  
 데이터 피드 가져오기 작업을 시작할 때만 데이터 서비스 문서에 대한 보기 권한이 확인됩니다. 가져오기를 수행한 이후에는 문서에 대한 권한이 계속 확인되지 않으므로, PowerPivot 데이터 원본에 추가된 피드는 원래의 연결 정보를 제공하는 데이터 서비스 문서에 연결되지 않은 상태의 정적 데이터로 존재합니다.  
  
 마찬가지로 이후에 예약하는 모든 데이터 새로 고침 작업에서도 데이터 서비스 문서가 제외됩니다. 가져오기를 수행하는 시점의 각 피드에 대한 연결 정보가 새로 고침을 위해 PowerPivot 데이터 원본에 복사됩니다. 따라서 문서가 새로 고침 작업에서 참조되지 않기 때문에 데이터 서비스 문서에 대한 권한은 데이터 새로 고침에서 확인되지 않습니다.  
  
|Task|SharePoint 사용 권한 요구 사항|  
|----------|----------------------------------------|  
|PowerPivot 사용 통합 문서로 데이터 피드를 가져옵니다.|라이브러리의 데이터 서비스 문서에 대한 보기 권한이 필요합니다.|  
|PowerPivot 클라이언트 애플리케이션에서 피드를 통해 이전에 검색된 데이터를 새로 고칩니다.|해당 사항 없음. PowerPivot 클라이언트 애플리케이션에서는 포함된 HTTP 연결 정보를 사용하여 피드를 제공하는 데이터 서비스 및 애플리케이션에 직접 연결합니다. PowerPivot 클라이언트 애플리케이션에서 데이터 서비스 문서를 사용하지 않습니다.|  
|SharePoint 팜에서 사용자의 입력을 요구하지 않고 데이터를 예약된 태스크로 새로 고칩니다.|해당 사항 없음. PowerPivot 서비스에서는 포함된 HTTP 연결 정보를 사용하여 피드를 제공하는 데이터 서비스 및 애플리케이션에 직접 연결합니다. PowerPivot 서비스에서 데이터 서비스 문서를 사용하지 않습니다.|  
|라이브러리에서 데이터 서비스 문서를 삭제합니다.|라이브러리에 대한 참가 권한이 필요합니다.|  
  
##  <a name="modify-a-data-service-document"></a><a name="modifydsdoc"></a> 데이터 서비스 문서 수정  
 데이터 서비스 문서에서 개별 URL 테이블 항목을 추가, 편집 또는 제거할 수 있습니다. 변경 내용을 저장한 후 사용자가 새 가져오기 작업에서 서비스 문서를 선택하면 지정된 데이터 피드가 수신됩니다.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서는 변경에 따른 영향을 받지 않습니다. 데이터 서비스 문서는 처음 가져오기 작업 중에 한 번만 읽기 때문입니다. 가져오기를 수행하는 동안 서비스 URL과 테이블 이름이 통합 문서에 복사되어 내부적으로 저장됩니다. 이후의 새로 고침 작업에서는 이 내부 값을 사용하여 업데이트된 데이터를 가져옵니다.  
  
 SharePoint 사이트의 데이터 서비스 문서와 가져온 피드를 포함하는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서 사이의 영구 링크가 없기 때문에 데이터 서비스 문서의 일부를 수정해도 기존 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에는 영향을 주지 않습니다.  
  
> [!IMPORTANT]  
>  데이터 서비스 문서를 한 번만 읽지만 실제 데이터를 제공하는 데이터 서비스를 정기적으로 액세스하여 새 피드를 가져올 수 있습니다. 데이터를 새로 고치는 방법에 대 한 자세한 내용은 [PowerPivot 데이터 새로 고침](power-pivot-data-refresh.md)을 참조 하세요.  
  
##  <a name="next-step-use-a-data-service-document"></a><a name="usedsdoc"></a> 다음 단계: 데이터 서비스 문서 사용  
 SharePoint 라이브러리에서 만든 데이터 서비스 문서를 사용 하려면 PowerPivot 데이터 원본에서 **데이터 피드** 가져오기 옵션을 사용 합니다. 지침은 [데이터 피드 사용 &#40;SharePoint용 PowerPivot&#41;](use-data-feeds-power-pivot-for-sharepoint.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [PowerPivot 데이터 피드](power-pivot-data-feeds.md)  
  
  
