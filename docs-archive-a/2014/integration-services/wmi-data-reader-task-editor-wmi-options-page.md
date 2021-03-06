---
title: WMI 데이터 판독기 태스크 편집기 (WMI 옵션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660018"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>WMI 데이터 판독기 태스크 편집기(WMI 옵션 페이지)
  **WMI 데이터 판독기 태스크 편집기** 대화 상자의 **WMI 옵션** 페이지를 사용하여 WQL(WMI Query Language) 쿼리의 원본 및 쿼리 결과의 대상을 지정할 수 있습니다.  
  
 이 태스크에 대한 자세한 내용은 [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)를 참조하십시오. WQL(WMI Query Language)에 대한 자세한 내용은 MSDN 라이브러리의 WMI(Windows Management Instrumentation) 항목인 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(WQL을 사용하여 쿼리)을 참조하세요.  
  
## <a name="static-options"></a>정적 옵션  
 **WMIConnectionName**  
 목록에서 WMI 연결 관리자를 선택하거나 \<**New WMI Connection...**>을 클릭하여 새 연결 관리자를 만듭니다.  
  
 **관련 항목:** [WMI 연결 관리자](connection-manager/wmi-connection-manager.md), [WMI 연결 관리자 편집기](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 태스크에서 실행하는 WQL 쿼리의 원본 유형을 선택합니다. 이 속성의 옵션은 다음 표에 나열되어 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**직접 입력**|WQL 쿼리에 대한 원본을 설정합니다. 이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.|  
|**파일 연결**|WQL 쿼리가 포함된 파일을 선택합니다. 이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.|  
|**변수**|원본을 WQL 쿼리를 정의하는 변수로 설정합니다. 이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.|  
  
 **OutputType**  
 출력 유형을 데이터 테이블, 속성 값 또는 속성 이름 및 값으로 지정합니다.  
  
 **OverwriteDestination**  
 대상 파일 또는 변수의 원본 데이터에 대한 유지, 덮어쓰기 또는 추가 여부를 지정합니다.  
  
 **DestinationType**  
 태스크에서 실행하는 WQL 쿼리의 대상 유형을 선택합니다. 이 속성의 옵션은 다음 표에 나열되어 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**파일 연결**|WQL 쿼리 결과를 저장할 파일을 선택합니다. 이 값을 선택하면 동적 옵션인 **DestinationType**이 표시됩니다.|  
|**변수**|WQL 쿼리 결과를 저장할 변수를 설정합니다. 이 값을 선택하면 동적 옵션인 **DestinationType**이 표시됩니다.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>WQLQuerySourceType 동적 옵션  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = 직접 입력  
 **WQLQuerySource**  
 쿼리를 제공하거나, 줄임표(...)를 클릭하고 **WQL 쿼리** 대화 상자를 사용하여 쿼리를 입력합니다.  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = 파일 연결  
 **WQLQuerySource**  
 목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.  
  
 **관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = 변수  
 **WQLQuerySource**  
 목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.  
  
 **관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>DestinationType 동적 옵션  
  
### <a name="destinationtype--file-connection"></a>DestinationType = 파일 연결  
 **대상**  
 목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.  
  
 **관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = 변수  
 **대상**  
 목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.  
  
 **관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>참고 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [WMI 데이터 판독기 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md)   
 [식 페이지](expressions/expressions-page.md)   
 [WMI 이벤트 감시자 태스크](control-flow/wmi-event-watcher-task.md)  
  
  
