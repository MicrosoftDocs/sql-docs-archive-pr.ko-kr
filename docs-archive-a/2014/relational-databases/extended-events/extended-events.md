---
title: 확장 이벤트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server]
- xe
ms.assetid: bf3b98a6-51ed-4f2d-9c26-92f07f1fa947
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ef183a218c2930199696aa1e0144714006e12ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661105"
---
# <a name="extended-events"></a>확장 이벤트
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트는 확장성이 높고 다양하게 구성 가능한 인프라를 갖추고 있으므로 사용자는 이를 통해 문제를 해결하거나 성능 문제를 파악하는 데 필요한 만큼의 정보만 수집할 수 있습니다.  
  
 확장 이벤트에 대한 자세한 내용은 [SQL Server 확장 이벤트](https://blogs.msdn.com/b/extended_events/)에서 찾을 수 있습니다.  
  
## <a name="benefits-of-ssnoversion-extended-events"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트의 이점  
 확장 이벤트는 성능 리소스를 적게 사용하는 간단한 성능 모니터링 시스템입니다. 확장 이벤트에서는**새 세션 마법사** 와 **새 세션**이라는 두 가지 그래픽 사용자 인터페이스가 제공되므로 세션 데이터를 작성, 수정, 표시 및 분석할 수 있습니다.  
  
## <a name="extended-events-concepts"></a>확장 이벤트 개념  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트(Extended Event)는 이벤트나 이벤트 소비자와 같은 기존 개념을 바탕으로 하고 Windows용 이벤트 추적의 개념을 사용하며 여기에 새로운 개념을 도입했습니다.  
  
 다음 표는 확장 이벤트의 개념에 대해 설명합니다.  
  
|항목|Description|  
|-----------|-----------------|  
|[SQL Server 확장 이벤트 패키지](sql-server-extended-events-packages.md)|확장 이벤트 세션이 실행 중일 때 데이터를 얻거나 처리하는 데 사용되는 개체가 포함된 확장 이벤트 패키지에 대해 설명합니다.|  
|[SQL Server 확장 이벤트 대상](../../database-engine/sql-server-extended-events-targets.md)|이벤트 세션이 지속되는 동안 데이터를 수신할 수 있는 이벤트 소비자에 대해 설명합니다.|  
|[SQL Server 확장 이벤트 엔진](sql-server-extended-events-engine.md)|확장 이벤트 세션을 구현 및 관리하는 엔진에 대해 설명합니다.|  
|[SQL Server 확장 이벤트 세션](sql-server-extended-events-sessions.md)|확장 이벤트 세션에 대해 설명합니다.|  
  
## <a name="extended-events-architecture"></a>확장 이벤트 아키텍처  
 확장 이벤트는 서버 시스템을 위한 일반적인 이벤트 처리 시스템입니다. 확장 이벤트 인프라는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]데이터와의 연계가 가능하고 특정 조건에서는 운영 체제 및 데이터베이스 애플리케이션 데이터와 연계해서 사용할 수 있는 기능도 지원합니다. 후자의 경우 운영 체제 또는 애플리케이션 이벤트 데이터와 이벤트 데이터의 상관 관계를 파악하려면 확장 이벤트 출력을 ETW(Windows용 이벤트 추적)로 전송해야 합니다.  
  
 모든 애플리케이션에는 애플리케이션 내부 및 외부 모두에서 유용한 실행 지점이 있습니다. 애플리케이션 내부에서는 태스크의 초기 실행 중에 수집된 정보를 사용하여 비동기 처리를 큐에 넣을 수 있습니다. 애플리케이션 외부의 경우 실행 지점은 모니터링되는 애플리케이션의 동작 및 성능 특성에 대한 정보를 모니터링 유틸리티에 제공합니다.  
  
 확장 이벤트는 프로세스 외부에서의 이벤트 데이터 사용을 지원하며 이러한 데이터는 일반적으로 다음에서 사용됩니다.  
  
-   SQL 추적 및 시스템 모니터와 같은 추적 도구  
  
-   Windows 이벤트 로그 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그 등의 로깅 도구  
  
-   제품을 관리하거나 제품의 애플리케이션을 개발하는 사용자  
  
 확장 이벤트는 다음과 같은 주요 요소를 고려하여 디자인되었습니다.  
  
-   확장 이벤트 엔진은 이벤트 중립적입니다. 즉, 이벤트 내용에 따른 제한이 없으므로 모든 이벤트를 모든 대상에 바인딩할 수 있습니다. 확장 이벤트 엔진에 대한 자세한 내용은 [SQL Server Extended Events Engine](sql-server-extended-events-engine.md)을 참조하십시오.  
  
-   이벤트는 확장 이벤트의 *대상* 이라고 하는 이벤트 소비자와 분리됩니다. 따라서 모든 대상이 모든 이벤트를 수신할 수 있습니다. 또한 발생한 모든 이벤트는 대상에서 자동으로 사용되므로 추가 이벤트 컨텍스트가 기록되거나 제공될 수 있습니다. 자세한 내용은 [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md)을 참조하세요.  
  
-   이벤트는 이벤트가 발생할 때 실행되는 동작과는 별개입니다. 따라서 모든 이벤트에 모든 동작을 연결할 수 있습니다.  
  
-   조건자를 사용하면 이벤트 데이터를 캡처해야 할 때를 동적으로 필터링할 수 있으므로 확장 이벤트 인프라의 유연성이 높아집니다. 자세한 내용은 [SQL Server Extended Events Packages](sql-server-extended-events-packages.md)을 참조하세요.  
  
 확장 이벤트는 이벤트 데이터를 동기적으로 생성하고 데이터를 비동기적으로 처리하여 유연한 이벤트 처리 솔루션을 제공합니다. 또한 확장 이벤트는 다음 기능도 지원합니다.  
  
-   사용자가 문제 해결을 위해 특정 이벤트를 격리할 수 있도록 허용하면서 서버 시스템 전체에서 일관된 이벤트 처리 방식  
  
-   기존 ETW 도구 통합 및 지원  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)]을 기반으로 하는 완전히 구성 가능한 이벤트 처리 메커니즘  
  
-   활성 프로세스에 거의 영향을 주지 않고 동적으로 이를 모니터링할 수 있는 기능  
  
-   성능에 크게 영향을 주지 않고 실행되는 기본 시스템 상태 세션. 이 세션은 성능 문제를 해결하는 데 사용할 수 있는 시스템 데이터를 수집합니다. 자세한 내용은 [system_health 세션 사용](use-the-ssms-xe-profiler.md)을 참조하세요.  
  
## <a name="extended-events-tasks"></a>확장 이벤트 태스크  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL(데이터 정의 언어) 문, 동적 관리 뷰와 함수 또는 카탈로그 뷰를 실행하면 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경에 맞는 간단하거나 복잡한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트 문제 해결 솔루션을 만들 수 있습니다.  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|**개체 탐색기** 를 사용하여 이벤트 세션을 관리합니다.|[개체 탐색기에서 이벤트 세션 관리](../../ssms/object/object-explorer.md)|  
|확장 이벤트 세션을 만드는 방법에 대해 설명합니다.|[확장 이벤트 세션 만들기](../../database-engine/create-an-extended-events-session.md)|  
|대상 데이터를 보고 새로 고치는 방법에 대해 설명합니다.|[이벤트 세션 데이터 보기](../../database-engine/view-event-session-data.md)|  
|확장 이벤트 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트 세션을 만들고 관리하는 방법에 대해 설명합니다.|[확장 이벤트 도구](extended-events-tools.md)|  
|확장 이벤트 세션을 변경하는 방법에 대해 설명합니다.|[확장 이벤트 세션 변경](alter-an-extended-events-session.md)|  
|대상 데이터를 복사하거나 내보내는 방법에 대해 설명합니다.|[대상 데이터 복사 또는 내보내기](../../database-engine/copy-or-export-target-data.md)|  
|추적 결과 뷰를 수정하여 데이터를 분석할 방법을 사용자 지정하는 방법에 대해 설명합니다.|[추적 결과 보기 수정](../../database-engine/modify-the-trace-results-view.md)|  
|이벤트와 관련된 필드에 대한 정보를 가져오는 방법에 대해 설명합니다.|[모든 이벤트에 대한 필드 가져오기](../../database-engine/get-the-fields-for-all-events.md)|  
|등록된 패키지에서 사용할 수 있는 이벤트를 확인하는 방법에 대해 설명합니다.|[등록된 패키지에 대한 이벤트 보기](../../database-engine/view-the-events-for-registered-packages.md)|  
|등록된 패키지에서 사용할 수 있는 확장 이벤트 대상을 확인하는 방법에 대해 설명합니다.|[등록된 패키지의 확장 이벤트 대상 보기](../../database-engine/view-the-extended-events-targets-for-registered-packages.md)|  
|각 SQL 추적 이벤트 및 관련 열에 해당하는 확장 이벤트의 이벤트 및 동작을 확인하는 방법에 대해 설명합니다.|[SQL 추적 이벤트 클래스에 해당하는 확장 이벤트 항목 확인](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)|  
|CREATE EVENT SESSION 또는 ALTER EVENT SESSION에 ADD TARGET 인수를 사용할 경우에 설정할 수 있는 매개 변수를 확인하는 방법에 대해 설명합니다.|[ADD TARGET 인수에 대한 구성 가능한 매개 변수 가져오기](../../database-engine/get-the-configurable-parameters-for-the-add-target-argument.md)|  
|기존 SQL 추적 스크립트를 확장 이벤트 세션으로 변환하는 방법에 대해 설명합니다.|[기존 SQL 추적 스크립트를 확장 이벤트 세션으로 변환](convert-an-existing-sql-trace-script-to-an-extended-events-session.md)|  
|잠금을 보유 중인 쿼리, 쿼리 계획 및 잠긴 시점의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스택을 확인하는 방법에 대해 설명합니다.|[잠금을 보유한 쿼리 파악](determine-which-queries-are-holding-locks.md)|  
|데이터베이스 성능을 저하시키는 잠금의 원인을 파악하는 방법에 대해 설명합니다.|[가장 많은 잠금이 발생한 개체 찾기](find-the-objects-that-have-the-most-locks-taken-on-them.md)|  
|확장 이벤트를 Windows용 이벤트 추적과 함께 사용하여 시스템 작업을 모니터링하는 방법에 대해 설명합니다.|[확장 이벤트를 사용하여 시스템 작업 모니터링](monitor-system-activity-using-extended-events.md)|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 계층 애플리케이션](../data-tier-applications/data-tier-applications.md)   
 [SQL Server 개체 및 버전에 대 한 DAC 지원](../data-tier-applications/dac-support-for-sql-server-objects-and-versions.md)   
 [데이터 계층 응용 프로그램 배포](../data-tier-applications/deploy-a-data-tier-application.md)   
 [데이터 계층 응용 프로그램 모니터링](../data-tier-applications/monitor-data-tier-applications.md)   
 [확장 이벤트 동적 관리 뷰](../views/views.md)   
 [확장 이벤트 카탈로그 뷰 &#40;Transact-sql&#41;] (~/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql  
  
  
