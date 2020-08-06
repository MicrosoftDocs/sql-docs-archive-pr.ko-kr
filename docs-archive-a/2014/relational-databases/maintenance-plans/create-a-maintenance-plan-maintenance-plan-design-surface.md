---
title: 유지 관리 계획 만들기(유지 관리 계획 디자인 화면) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77e347720824198ba7d6abaddedd7a581ace98a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653356"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a>유지 관리 계획 만들기(유지 관리 계획 디자인 화면)
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 유지 관리 디자인 화면을 사용하여 단일 서버 또는 다중 서버 유지 관리 계획을 만드는 방법에 대해 설명합니다. 기본 유지 관리 계획을 만들 때는 **유지 관리 계획 마법사** 가 적합한 반면 디자인 화면을 사용하여 계획을 만들면 워크플로의 향상된 기능을 활용할 수 있습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   [유지 관리 계획 디자인 화면을 사용하여 유지 관리 계획 만들기](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   다중 서버 유지 관리 계획을 만들려면 하나의 마스터 서버 및 하나 이상의 대상 서버가 있는 다중 서버 환경을 구성해야 합니다. 다중 서버 유지 관리 계획은 마스터 서버에서 만들고 유지 관리해야 합니다. 이러한 계획을 대상 서버에서 볼 수 있지만 유지 관리할 수는 없습니다.  
  
-   **db_ssisadmin** 및 **dc_admin** 역할의 멤버는 해당 권한을 **sysadmin**으로 승격할 수 있습니다. 이러한 권한 승격이 발생할 수 있는 것은 이러한 역할이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 수정할 수 있고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **에이전트의** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 컨텍스트를 사용하여 이러한 패키지를 실행할 수 있기 때문입니다. 유지 관리 계획, 데이터 컬렉션 집합 및 기타 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 때 이러한 권한 상승이 발생하지 않도록 하려면 패키지를 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 제한된 권한을 갖는 프록시 계정을 사용하도록 구성하거나 **db_ssisadmin** 및 **dc_admin** 역할에 **sysadmin** 멤버만 추가합니다.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 유지 관리 계획을 만들거나 관리하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다. 개체 탐색기에 **sysadmin** 고정 서버 역할의 멤버인 사용자에 대한 **유지 관리 계획** 노드만 표시됩니다.  
  
##  <a name="using-maintenance-plan-design-surface"></a><a name="SSMSProcedure"></a> 유지 관리 계획 디자인 화면 사용  
  
#### <a name="to-create-a-maintenance-plan"></a>유지 관리 계획을 만들려면  
  
1.  개체 탐색기에서 더하기 기호를 클릭하여 유지 관리 계획을 만들 서버를 확장합니다.  
  
2.  더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.  
  
3.  **유지 관리 계획** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 유지 관리 계획**을 선택합니다.  
  
4.  **새 유지 관리 계획** 대화 상자의 **이름** 상자에 계획의 이름을 입력하고 **확인**을 클릭합니다. 이렇게 하면 주 그리드에서 만든 **Subplan_1** 하위 계획이 있는 _maintenance_plan_name_ **[Design]** 화면과 도구 상자가 열립니다.  
  
     다음 옵션은 디자인 화면의 헤더에서 사용할 수 있습니다.  
  
     **하위 계획 추가**  
     구성할 수 있는 하위 계획을 추가합니다.  
  
     **하위 계획 속성**  
     주 표에서 선택한 하위 계획에 대해 **하위 계획 속성** 대화 상자를 표시합니다. 또는 표에서 하위 계획을 두 번 클릭하여 **하위 계획 속성** 대화 상자를 표시합니다. 이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.  
  
     **선택한 하위 계획 삭제**  
     선택한 하위 계획을 삭제합니다.  
  
     **하위 계획 일정**  
     선택한 하위 계획에 대해 **새 작업 일정** 대화 상자를 표시합니다.  
  
     **일정 제거**  
     선택한 하위 계획에서 일정을 제거합니다.  
  
     **연결 관리**  
     **연결 관리** 대화 상자를 표시합니다. 유지 관리 계획에 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 연결을 추가하는 데 사용됩니다. 이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.  
  
     **보고 및 로깅**  
     **보고 및 로깅** 대화 상자를 표시합니다. 이 대화 상자에 대한 자세한 내용은 아래를 참조하세요.  
  
     **서버**  
     하위 계획 태스크를 실행할 서버를 선택하는 데 사용되는 **서버** 대화 상자를 표시합니다. 이 옵션은 다중 서버 환경의 마스터 서버에서만 사용할 수 있습니다. 자세한 내용은 [다중 서버 환경 만들기](../../ssms/agent/create-a-multiserver-environment.md) 및 [유지 관리 계획&#40;Servers&#41;](maintenance-plan-servers.md)을 참조하세요.  
  
     **이름**  
     유지 관리 계획 이름을 표시합니다. 새 유지 관리 계획의 경우 유지 관리 계획 디자이너가 열리기 전에 나타나는 대화 상자에서 이름을 지정합니다. 유지 관리 계획의 이름을 바꾸려면 개체 탐색기에서 해당 계획을 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.  
  
     **설명**  
     유지 관리 계획에 대한 설명을 확인하거나 지정합니다. 설명의 최대 길이는 512자입니다.  
  
     **디자이너 화면**  
     유지 관리 계획을 디자인 및 유지 관리합니다. 디자이너 화면을 사용하여 계획에 유지 관리 태스크를 추가하거나 제거하고, 작업 간의 선행 링크를 지정하며 작업 분기와 병렬 처리를 나타낼 수 있습니다.  
  
     두 태스크 간의 선행 링크는 작업 간의 관계를 설정합니다. 두 번째 태스크( *종속 태스크*)는 첫 번째 태스크( *선행 태스크*)의 실행 결과가 지정한 조건과 일치하는 경우에만 실행됩니다. 대개 지정되는 실행 결과는 **성공**, **실패**또는 **완료**입니다. 자세한 내용은 아래의 **8** 단계를 참조하세요.  
  
5.  디자인 화면의 헤더에서 **Subplan_1** 을 두 번 클릭하고 **하위 계획 속성** 대화 상자에 하위 계획의 이름 및 설명을 입력합니다.  
  
     다음 옵션은 **하위 계획 속성** 대화 상자에서 사용할 수 있습니다.  
  
     **이름**  
     하위 계획의 이름입니다.  
  
     **설명**  
     하위 계획에 대한 간단한 설명입니다.  
  
     **일정**  
     하위 계획이 어떤 일정에 따라 실행될지 나타냅니다. **하위 계획 일정** 을 클릭하여 **새 작업 일정** 대화 상자를 엽니다. **일정 제거** 를 클릭하여 하위 계획에서 일정을 삭제합니다.  
  
     **다음 계정으로 실행** 목록  
     이 하위 태스크를 실행하는 데 사용할 계정을 선택합니다.  
  
6.  **하위 계획 일정** 을 클릭하여 **새 작업 일정** 대화 상자에 일정 정보를 입력합니다.  
  
7.  하위 계획을 작성하려면 **도구 상자** 에서 계획 디자인 화면으로 태스크 흐름 요소를 끌어다 놓습니다. 태스크를 두 번 클릭하여 대화 상자를 연 후 작업 옵션을 구성합니다.  
  
     다음 유지 관리 계획 태스크는 **도구 상자**에서 사용할 수 있습니다.  
  
    -   **데이터베이스 백업 태스크**  
  
    -   **데이터베이스 무결성 검사 태스크**  
  
    -   **SQL Server 에이전트 작업 실행 태스크**  
  
    -   **T-SQL 문 실행 태스크**  
  
    -   **기록 정리 태스크**  
  
    -   **유지 관리 정리 태스크**  
  
    -   **운영자에게 알림 태스크**  
  
    -   **인덱스 다시 작성 태스크**  
  
    -   **인덱스 다시 구성 태스크**  
  
    -   **데이터베이스 축소 태스크**  
  
    -   **통계 업데이트 태스크**  
  
     **도구 상자**에 태스크를 추가하려면  
  
    1.  **도구** 메뉴에서 **도구 상자 항목 선택**을 클릭합니다.  
  
    2.  **도구 상자**에 표시할 도구를 선택한 다음 **확인**을 클릭합니다.  
  
     **도구 상자** 에 유지 관리 계획 태스크를 추가하면 이 태스크를 **유지 관리 계획 마법사**에서도 사용할 수 있습니다. 위의 개별 태스크에 대한 자세한 내용은 [유지 관리 계획 마법사 시작](use-the-maintenance-plan-wizard.md#SSMSProcedure) 에서 **유지 관리 계획 마법사 사용**을 참조하세요.  
  
8.  태스크 간의 워크플로를 정의하려면:  
  
    1.  선행 태스크를 마우스 오른쪽 단추로 클릭하고 **선행 제약 조건 추가**를 선택합니다.  
  
    2.  **제어 흐름** 대화 상자의 **대상** 목록에서 종속 태스크를 선택하고 **확인**을 클릭합니다.  
  
    3.  두 태스크 사이의 커넥터를 두 번 클릭하여 **선행 제약 조건 편집기** 대화 상자를 엽니다.  
  
         다음 옵션은 **선행 제약 조건 편집기** 대화 상자에서 사용할 수 있습니다.  
  
         **제약 조건 옵션**  
         두 태스크 사이에서 제약 조건이 작동하는 방식을 정의합니다.  
  
         **평가 작업**  목록  
         선행 제약 조건에서 사용하는 평가 작업을 지정합니다. 사용할 수 있는 작업에는 **제약 조건**, **식**, **식 및 제약 조건**, **식 또는 제약 조건**이 있습니다.  
  
         **값** 목록  
         제약 조건 값을 지정합니다. **성공**, **실패** 또는 **완료**와 같은 값을 사용할 수 있습니다. 기본값은**성공** 입니다.  
  
        > [!NOTE]  
        >  선행 제약 조건 줄은 **성공**인 경우 녹색, **실패**인 경우 빨간색, **완료**인 경우 파란색으로 표시됩니다.  
  
         **식**  
         **식**, **식 및 제약 조건**또는 **식 또는 제약 조건**작업을 사용하는 경우 식을 입력합니다. 식은 부울로 계산되어야 합니다.  
  
         **Test**  
         식의 유효성을 검사합니다.  
  
         **여러 제약 조건**  
         여러 제약 조건이 제한된 태스크의 실행을 제어하기 위해 어떤 방식으로 상호 운영되는지 정의합니다.  
  
         **논리적 AND**  
         동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다. 모든 제약 조건이 True여야 합니다. 이 옵션이 기본값입니다.  
  
        > [!NOTE]  
        >  이 유형의 선행 제약 조건은 녹색, 빨간색 또는 파란색 실선으로 나타납니다.  
  
         **논리적 OR**  
         동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다. 적어도 하나의 제약 조건이 True여야 합니다.  
  
        > [!NOTE]  
        >  이 유형의 선행 제약 조건은 녹색, 빨간색 또는 파란색 점선으로 나타납니다.  
  
9. 다른 일정에서 실행되는 태스크를 포함하는 다른 하위 계획을 추가하려면 도구 모음에서 **하위 계획 추가** 를 클릭하여 **하위 계획 속성** 대화 상자를 엽니다.  
  
10. 다른 서버에 연결을 추가하려면:  
  
    1.  디자인 화면의 도구 모음에서 **연결 관리**를 클릭합니다.  
  
    2.  **연결 관리** 대화 상자에서 **추가**를 클릭합니다.  
  
    3.  **연결 속성** 대화 상자의 **연결 이름** 상자에 만들려는 연결의 이름을 입력합니다.  
  
    4.  **SQL Server 데이터에 연결하려면 다음을 지정하세요.** 의 **서버 이름 선택 또는 입력** 상자에 사용하려는 SQL Server의 이름을 입력하거나 줄임표 **(...)** 를 클릭하여 **SQL Server** 대화 상자에서 서버를 선택합니다. **SQL Server** 대화 상자에서 서버를 선택하는 경우 **확인**을 클릭합니다.  
  
    5.  **서버 로그온 정보 입력**에서 **Windows NT 통합 보안 사용** 또는 **특정 사용자 이름 및 암호 사용**을 선택합니다. 특정 사용자 이름 및 암호를 사용하도록 선택한 경우 **사용자 이름** 및 **암호** 상자에 각각 해당 정보를 입력합니다.  
  
    6.  **연결 속성** 대화 상자에서 **확인**을 클릭합니다.  
  
    7.  **연결 관리** 대화 상자에서 **닫기**를 클릭합니다.  
  
11. 보고 옵션을 지정하려면:  
  
    1.  디자인 화면의 도구 모음에서 **보고 및 로깅**을 클릭합니다.  
  
    2.  **보고 및 로깅** 대화 상자의 **보고**에서 **텍스트 파일 보고서 생성** 또는 **전자 메일 받는 사람에게 보고서 보내기** 중 하나를 선택하거나 둘 다 선택합니다.  
  
        1.  **텍스트 파일 보고서 생성**을 선택하는 경우 **새 파일 만들기** 또는 **파일에 추가**를 선택합니다.  
  
        2.  위에서 선택한 내용에 따라 **폴더** 또는 **파일 이름** 상자에 정보를 입력하여 새 파일이나 추가할 파일의 이름과 전체 경로를 입력합니다. 또는 줄임표 **(...)** 를 클릭 하 고 **폴더 찾기-**_server_name_ 또는 **데이터베이스 파일 찾기-**_server_name_ 대화 상자에서 폴더나 파일 이름의 경로를 선택 합니다.  
  
        3.  **전자 메일 받는 사람에게 보고서 보내기**를 선택하는 경우 **에이전트 운영자** 목록에서 전자 메일로 보낼 보고서의 받는 사람을 선택합니다.  
  
            > [!NOTE]  
            >  SQL Server 에이전트에서 메일을 보내려면 데이터베이스 메일을 사용하도록 구성해야 합니다. 자세한 내용은 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)를 참조하세요.  
  
    3.  보다 자세한 정보를 저장하려면 **로깅**에서 **확장 정보 기록**을 선택합니다.  
  
    4.  유지 관리 계획 결과 정보를 다른 서버에 쓰려면 **원격 서버에 기록** 을 선택하고 **연결** 목록에서 서버 연결을 선택하거나 **새로 만들기** 를 클릭하고 **연결 속성** 대화 상자에 연결 정보를 입력합니다.  
  
    5.  **보고 및 로깅** 대화 상자에서 **확인**을 클릭합니다.  
  
12. 로그 파일 뷰어에서 이 결과를 보려면 **개체 탐색기**에서 **유지 관리 계획** 폴더 또는 특정 유지 관리 계획을 마우스 오른쪽 단추로 클릭하고 **기록 보기**를 선택합니다.  
  
     **로그 파일 뷰어-**_server_name_ 대화 상자에서 다음 옵션을 사용할 수 있습니다.  
  
     **로그 로드**  
     로드할 로그 파일을 지정할 수 있는 대화 상자를 엽니다.  
  
     **내보내기**  
     **로그 파일 요약** 표에 표시된 정보를 텍스트 파일로 내보낼 수 있는 대화 상자를 엽니다.  
  
     **새로 고침**  
     선택한 로그의 뷰를 새로 고칩니다. **새로 고침** 단추를 누르면 필터 설정을 적용하는 동안 대상 서버에서 선택한 로그를 다시 읽습니다.  
  
     **Filter**  
     **연결**, **날짜**또는 기타 **일반** 필터 조건과 같이 로그 파일 필터링에 사용되는 설정을 지정할 수 있는 대화 상자를 엽니다.  
  
     **검색**  
     로그 파일에서 특정 텍스트를 검색합니다. 와일드카드 문자를 사용한 검색은 지원되지 않습니다.  
  
     **중지**  
     로그 파일 항목의 로드를 중지합니다. 예를 들어 원격 또는 오프라인 로그 파일을 로드하는 데 시간이 오래 걸리며 최근 항목만 보려는 경우 이 옵션을 사용할 수 있습니다.  
  
     **로그 파일 요약**  
     이 정보 창에는 로그 파일 필터링에 대한 요약이 표시됩니다. 파일을 필터링하지 않은 경우 **적용된 필터 없음**이 표시됩니다. 로그에 필터를 적용한 경우에는 **로그 항목 필터링 조건:** \<filter criteria>라는 텍스트가 표시됩니다.  
  
     **Date**  
     이벤트의 날짜를 표시합니다.  
  
     **원본**  
     서비스의 이름(예: MSSQLSERVER)과 같이 이벤트가 생성된 원본 기능을 표시합니다. 이 열은 일부 로그 유형의 경우에만 나타납니다.  
  
     **메시지**  
     이벤트와 관련된 메시지를 표시합니다.  
  
     **로그 유형**  
     이벤트가 속한 로그의 유형을 표시합니다. 선택한 모든 로그가 로그 파일 요약 창에 나타납니다.  
  
     **로그 원본**  
     이벤트가 캡처되는 원본 로그에 대한 설명을 표시합니다.  
  
     **선택한 행 정보**  
     선택한 이벤트 행에 대한 추가 정보를 페이지 아래쪽에 표시하려면 해당 행을 선택합니다. 열을 표의 새 위치로 끌어서 다시 정렬할 수 있습니다. 표 머리글의 열 구분선을 왼쪽이나 오른쪽으로 끌어 열의 크기를 조정할 수도 있습니다. 열 내용에 맞게 열 너비를 자동 조정하려면 표 머리글의 열 구분선을 두 번 클릭합니다.  
  
     **인스턴스**  
     이벤트가 발생한 인스턴스의 이름입니다. 이 이름은 *컴퓨터 이름*\\*인스턴스 이름*으로 표시됩니다.  
  
  