---
title: 오류 인터페이스의 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: e9859ccbd804ba15685d84b98cbe74d4b096d98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653840"
---
# <a name="information-in-error-interfaces"></a>오류 인터페이스의 정보
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 OLE DB 정의 오류 인터페이스 **IErrorInfo**, **Ierrorrecords**및 **ISQLErrorInfo**에 일부 오류 및 상태 정보를 보고 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 **IErrorInfo** 멤버 함수를 지원 합니다.  
  
|멤버 함수|Description|  
|---------------------|-----------------|  
|**GetDescription**|설명적인 오류 메시지 문자열입니다.|  
|**GetGUID**|오류를 정의한 인터페이스의 GUID입니다.|  
|**GetHelpContext**|지원되지 않습니다. 항상 0을 반환합니다.|  
|**GetHelpFile**|지원되지 않습니다. 항상 NULL을 반환합니다.|  
|**GetSource**|"Microsoft SQL Server Native Client" 문자열입니다.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 소비자가 사용할 수 있는 **Ierrorrecords** 멤버 함수를 지원 합니다.  
  
|멤버 함수|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|ERRORINFO 구조에 오류에 대한 기본 정보를 채웁니다. ERRORINFO 구조에는 오류에 대한 HRESULT 반환 값을 식별하는 멤버와 오류가 적용되는 공급자 및 인터페이스가 포함됩니다.|  
|**GetCustomErrorObject**|**ISQLErrorInfo** 및 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스에 대한 참조를 반환합니다.|  
|**GetErrorInfo**|**IErrorInfo** 인터페이스에 대한 참조를 반환합니다.|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 **geterrorparameters**를 통해 소비자에 게 매개 변수를 반환 하지 않습니다.|  
|**GetRecordCount**|사용할 수 있는 오류 레코드 수입니다.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 다음과 같이 **ISQLErrorInfo:: GetSQLInfo** 매개 변수를 지원 합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|오류의 SQLSTATE 값을 반환합니다. SQLSTATE 값은 SQL-92, ODBC 및 ISO SQL, API 사양에서 정의됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 구현 별 SQLSTATE 값을 정의 하지 않습니다.|  
|*plNativeError*|사용 가능한 경우 **master.dbo.sysmessages**의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 번호를 반환합니다. Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB 공급자 데이터 원본을 성공적으로 초기화 한 후 네이티브 오류를 사용할 수 있습니다. 시도 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 항상 0을 반환 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Errors](errors.md)  
  
  
