---
title: MultiIpConfigurationSupport 속성 (ServerNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638579"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>MultiIpConfigurationSupport 속성(ServerNetworkProtocol 클래스)
  서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하는지 여부를 지정하는 부울 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 인스턴스에서 사용 하는 네트워크 프로토콜을 나타내는 [Protocolname 속성 (ServerNetworkProtocol 클래스)](servernetworkprotocol-class.md) 개체입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하는지 여부를 지정하는 부울 값입니다. `true`는 서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원함을 나타내고 `false`는 서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하지 않음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
