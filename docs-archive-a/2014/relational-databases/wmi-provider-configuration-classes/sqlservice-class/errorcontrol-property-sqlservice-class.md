---
title: ErrorControl 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738104"
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl 속성(SqlService 클래스)
  시스템을 시작할 때 서비스가 시작되지 않은 경우 오류의 심각도를 가져오거나 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 시스템을 시작할 때 서비스가 시작되지 않은 경우 보고된 오류 심각도를 지정하는 문자열 값입니다. 다음 표에서는 가능한 값을 보여 줍니다.  
  
 무시  
 사용자에게 오류를 알리지 않습니다.  
  
 보통  
 사용자에게 오류를 알립니다.  
  
 심각  
 마지막으로 성공한 올바른 구성으로 시스템을 다시 시작합니다.  
  
 위험  
 올바른 구성으로 시스템을 다시 시작합니다.  
  
 알 수 없음  
 심각도를 알 수 없습니다.  
  
## <a name="remarks"></a>설명  
 이 값은 오류가 발생할 때 시작 프로그램에서 수행하는 동작을 나타냅니다. 모든 오류는 컴퓨터 시스템에 기록됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
