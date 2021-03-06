---
title: '2단원: 연결 정보 지정(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731427"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>2단원: 연결 정보 지정(Reporting Services)
  Tutorial 프로젝트에 보고서를 추가한 뒤에는 보고서에서 관계형 데이터베이스, 다차원 데이터베이스 또는 다른 리소스의 데이터에 액세스하기 위해 사용하는 연결 정보인 *데이터 원본*을 정의해야 합니다.  
  
 이 단원에서는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 예제 데이터베이스를 데이터 원본으로 사용합니다. 이 자습서에서는이 데이터베이스가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로컬 컴퓨터에 설치 된의 기본 인스턴스에 있다고 가정 [!INCLUDE[ssDE](../includes/ssde-md.md)] 합니다.  
  
### <a name="to-set-up-a-connection"></a>연결을 설정하려면  
  
1.  **보고서 데이터** 창에서 **새로 만들기** 를 클릭 한 다음 **데이터 원본 ...** 을 클릭 합니다.  
  
    > [!NOTE]  
    >  **보고서 데이터** 창이 표시되지 않는 경우 **보기** 메뉴에서 **보고서 데이터**를 클릭하십시오.  
  
2.  **이름**에서 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]을 입력합니다.  
  
3.  **포함된 연결** 이 선택되어 있는지 확인합니다.  
  
4.  **유형**에서 **Microsoft SQL Server**를 선택합니다.  
  
5.  **연결 문자열**에서 다음과 같이 입력합니다.  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     이 연결 문자열에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], 보고서 서버 및 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스가 모두 로컬 컴퓨터에 설치되어 있고 사용자에게 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에 로그온할 수 있는 권한이 있다고 가정합니다.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 또는 명명된 인스턴스를 사용하는 경우에는 연결 문자열에 인스턴스 정보가 포함되어야 합니다.  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  연결 문자열에 대 한 자세한 내용은 Reporting Services 및 [데이터 원본 속성 대화 상자, 일반](data-source-properties-dialog-box-general.md) [의 데이터 연결, 데이터 원본 및 연결 문자열](data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하세요.  
  
6.  왼쪽 창에서 **자격 증명** 을 클릭하고 **Windows 인증 사용(통합 보안)** 을 클릭합니다.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]데이터 원본이 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] **보고서 데이터** 창에 추가 됩니다.  
  
## <a name="next-task"></a>다음 태스크  
 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 샘플 데이터베이스에 대한 연결이 정의되었습니다. 다음 단원에서는 보고서를 만듭니다. [3단원: 테이블 보고서에 대한 데이터 세트 정의&#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 서비스의 데이터 연결, 데이터 원본 및 연결 문자열](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
