---
title: 이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739027"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 시작 시간을 기준으로 추적 이벤트를 필터링하는 방법에 대해 설명합니다.  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>이벤트 시작 시간을 기준으로 이벤트를 필터링하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.  
  
     **추적 속성**대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  **추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **템플릿 사용**이름 목록에서 추적 템플릿을 선택합니다.  
  
4.  필요에 따라 추적 결과의 저장 대상을 지정합니다.  
  
5.  **이벤트 선택**탭에서 **StartTime** 열 머리글을 클릭합니다. 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 필터 편집** 을 클릭하여 **필터 편집** 대화 상자를 시작할 수도 있습니다.  
  
6.  보다 **큼** 또는 **보다 작음**을 확장 한 다음 `datetime` 비교 연산자 아래에 나타나는 필드에 값을 입력 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
