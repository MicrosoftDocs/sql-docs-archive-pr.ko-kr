---
title: SetServiceState 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b4a29b3379fc1d312af42a1f5b1296ee35dcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737702"
---
# <a name="setservicestate-method-wmi-msreportserver_configurationsetting"></a>SetServiceState 메서드(WMI MSReportServer_ConfigurationSetting)
  보고서 서버 Windows 및 웹 서비스를 설정하거나 해제합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *EnableWindowsService*  
 Windows 서비스의 상태를 나타내는 `Boolean` 값입니다. `true` 값은 보고서 서버 Windows 서비스를 시작하고 `false` 값은 Windows 서비스를 중지합니다.  
  
 *EnableWebService*  
 `Boolean`웹 서비스의 상태를 나타내는 값 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 입니다. `true` 값은 보고서 서버 웹 서비스를 시작하고 `false` 값은 웹 서비스를 중지합니다.  
  
 *EnableReportManager*  
 보고서 관리자의 필요한 상태를 나타내는 `Boolean` 값입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="return-value"></a>Return Value  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
