---
title: 추적 모니터링 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, traces
- XMLA, traces
- monitoring traces [XMLA]
- traces [Analysis Services]
ms.assetid: cdbfb984-18bd-4c4e-8fb7-d64ce298ed35
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2ca181b7c194fdd3909875f881d1030a77ae039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649758"
---
# <a name="monitoring-traces-xmla"></a>추적 모니터링(XMLA)
  XMLA (XML for Analysis)에서 [구독](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) 명령을 사용 하 여 인스턴스에 정의 된 기존 추적을 모니터링할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . `Subscribe` 명령에서는 추적 결과를 행 집합으로 반환합니다.  
  
## <a name="specifying-a-trace"></a>추적 지정  
 명령의 [개체](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 속성은 인스턴스에 `Subscribe` 대 한 개체 참조 또는 인스턴스에 대 한 추적을 포함 해야 합니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . `Object` 속성을 지정하지 않거나 `Object` 속성에 추적 식별자를 지정하지 않은 경우 `Subscribe` 명령에서는 명령의 SOAP 헤더에 지정된 명시적 세션에 대한 기본 세션 추적을 모니터링합니다.  
  
## <a name="returning-results"></a>결과 반환  
 `Subscribe` 명령에서는 지정된 추적에 의해 캡처된 추적 이벤트가 포함되어 있는 행 집합을 반환합니다. 명령은 `Subscribe` [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) 명령에 의해 명령이 취소 될 때까지 추적 결과를 반환 합니다.  
  
 행 집합에는 다음 표에 나열된 열이 들어 있습니다.  
  
|열|데이터 형식|Description|  
|------------|---------------|-----------------|  
|EventClass|정수|추적에 의해 수신된 이벤트의 이벤트 클래스입니다.|  
|EventSubclass|정수(Long)|추적에 의해 수신된 이벤트의 이벤트 하위 클래스입니다.|  
|CurrentTime|DateTime|이벤트가 시작된 시간입니다(사용 가능한 경우). 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|StartTime|DateTime|이벤트가 시작된 시간입니다(사용 가능한 경우). 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|EndTime|DateTime|이벤트가 종료된 시간입니다(사용 가능한 경우). 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.<br /><br /> 프로세스 또는 동작의 시작을 설명하는 이벤트 클래스의 경우 이 열은 채워지지 않습니다.|  
|기간|정수(Long)|이벤트에 소요된 경과 시간(밀리초)입니다.|  
|CPUTime|정수(Long)|이벤트에 소요된 프로세서 시간(밀리초)입니다.|  
|JobID|정수(Long)|프로세스에 대한 작업 식별자입니다.|  
|SessionID|String|이벤트가 발생한 세션의 식별자입니다.|  
|SessionType|String|이벤트가 발생한 세션의 유형입니다.|  
|ProgressTotal|정수(Long)|이벤트에 의해 보고된 총 진행률입니다.|  
|IntegerData|정수(Long)|이벤트와 연결된 정수 데이터입니다. 이 열의 내용은 이벤트의 이벤트 클래스 및 하위 클래스에 따라 달라집니다.|  
|ObjectID|String|이벤트가 발생한 개체의 식별자입니다.|  
|ObjectType|String|ObjectName에 지정된 개체의 형식입니다.|  
|ObjectName|String|이벤트가 발생한 개체의 이름입니다.|  
|ObjectPath|String|이벤트가 발생한 개체의 계층 구조 경로입니다. 이 경로는 ObjectName에 지정된 개체의 부모에 대한 개체 식별자로 구성된 쉼표로 구분된 문자열로 표시됩니다.|  
|ObjectReference|String|ObjectName에 지정된 개체에 대한 개체 참조의 XML 표현입니다.|  
|NestLevel|정수|이벤트가 발생한 트랜잭션의 수준입니다.|  
|NumSegments|정수(Long)|이벤트를 발생시킨 명령에서 영향을 받거나 액세스된 데이터 세그먼트의 수입니다.|  
|심각도|정수|이벤트에 대한 예외의 심각도 수준입니다. 이 열 값은 다음 중 하나일 수 있습니다.<br /><br /> 값: 0 = 성공<br /><br /> 값: 1 = 정보<br /><br /> 값: 2 = 경고<br /><br /> 값: 3 = 오류|  
|Success|부울|명령의 성공 여부를 나타냅니다.|  
|오류|정수(Long)|이벤트의 오류 번호입니다(해당되는 경우).|  
|ConnectionID|String|이벤트가 발생한 연결의 식별자입니다.|  
|DatabaseName|String|이벤트가 발생한 데이터베이스의 이름입니다.|  
|NTUserName|String|이벤트와 연결된 사용자의 Windows 사용자 이름입니다.|  
|NTDomainName|String|이벤트와 연결된 사용자의 Windows 도메인입니다.|  
|ClientHostName|String|클라이언트 애플리케이션을 실행 중인 컴퓨터의 이름입니다. 이 열은 클라이언트 애플리케이션에서 전달한 값으로 채워집니다.|  
|ClientProcessID|정수(Long)|클라이언트 애플리케이션의 프로세스 식별자입니다.|  
|ApplicationName|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결한 클라이언트 애플리케이션의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 클라이언트 애플리케이션에서 전달한 값으로 채워집니다.|  
|NTCanonicalUserName|String|이벤트와 연결된 사용자의 정식 Windows 사용자 이름입니다.|  
|SPID|String|이벤트가 발생한 세션의 SPID(서버 프로세스 ID)입니다. 이 열의 값은 이벤트가 발생한 XMLA 메시지의 SOAP 헤더에 지정된 세션 ID에 직접 해당합니다.|  
|TextData|String|이벤트와 연결된 텍스트 데이터입니다. 이 열의 내용은 이벤트의 이벤트 클래스 및 하위 클래스에 따라 달라집니다.|  
|ServerName|String|이벤트가 발생한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 이름입니다.|  
|RequestParameters|String|이벤트가 발생한 매개 변수가 있는 쿼리 또는 XMLA 명령의 매개 변수입니다.|  
|RequestProperties|String|이벤트가 발생한 XMLA 메서드의 속성입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Analysis Services에서 XMLA를 사용하여 개발](developing-with-xmla-in-analysis-services.md)  
  
  
