---
title: SetProtocolsOrder 메서드 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aaa1d43c8a2f7f210f61761b28313a93ac6c7a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660957"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a>SetProtocolsOrder 메서드(ClientNetworkProtocol 클래스)
  프로토콜 목록의 순서를 변경합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a>부분  
 *object*  
 클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](clientnetworkprotocol-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|Description|  
|---------------|-----------------|  
|*ProtocolOrderList*|클라이언트 네트워크 프로토콜을 새로운 순서로 나열하는 string[] 형식의 배열입니다.|  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 `uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx)   
 [클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
