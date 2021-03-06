---
title: InitializeReportServer 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649913"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a>InitializeReportServer 메서드(WMI MSReportServer_ConfigurationSetting)
  지정된 보고서 서비스 인스턴스를 초기화합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>매개 변수  
 *InstallationID*  
 암호화 키를 반환하기 전에 암호화하는 데 사용되는 문자열입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
 *ExtendedErrors[]*  
 [out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.  
  
## <a name="return-value"></a>Return Value  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
 이 메서드를 호출하면 보고서 서버 데이터베이스 보안 정보에 액세스하는 암호화 키가 *InstallationID*에 의해 식별되는 보고서 서버의 공개 키를 사용하여 암호화됩니다.  
  
 지정된 보고서 서버의 공개 키는 이전에 보고서 서버 데이터베이스에 기록되어 있어야 합니다.  
  
 *InitializeReportServer* 메서드는 암호화 키를 해독할 수 있도록 이미 보안 정보에 대한 액세스 권한이 있는 보고서 서버에 대해 호출되어야 합니다. 그런 다음 암호화된 결과 암호화 키가 보고서 서버 데이터베이스에 저장됩니다.  
  
 Inreypservermethod가 호출 될 때 보고서 서버의 [Isinitialized](configurationsetting-property-isinitialized.md) 속성이로 설정 된 경우 `true` 메서드는 암호화 키를 암호화 하지 않고 success를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
