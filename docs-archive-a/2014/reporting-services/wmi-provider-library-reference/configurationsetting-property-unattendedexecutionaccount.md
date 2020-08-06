---
title: UnattendedExecutionAccount 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- UnattendedExecutionAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- UnattendedExecutionAccount property
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f032cd8a9e8d5305f4eef82f815b4f0e328756a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737606"
---
# <a name="unattendedexecutionaccount-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="04bda-102">UnattendedExecutionAccount 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="04bda-102">UnattendedExecutionAccount Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="04bda-103">보고서 서버가 무인 모드로 보고서를 실행할 때 가장하는 사용자 계정을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="04bda-103">Returns the user account that the report server impersonates when running reports unattended.</span></span> <span data-ttu-id="04bda-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="04bda-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bda-105">구문</span><span class="sxs-lookup"><span data-stu-id="04bda-105">Syntax</span></span>  
  
```vb  
Public Dim UnattendedExecutionAccount As String  
```  
  
```csharp  
public string UnattendedExecutionAccount;  
```  
  
## <a name="property-values"></a><span data-ttu-id="04bda-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="04bda-106">Property Values</span></span>  
 <span data-ttu-id="04bda-107">계정 이름을 나타내는 `String` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="04bda-107">A `String` object that represents the account name.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="04bda-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="04bda-108">Example Code</span></span>  
 [<span data-ttu-id="04bda-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="04bda-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="04bda-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="04bda-110">Requirements</span></span>  
 <span data-ttu-id="04bda-111">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04bda-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bda-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04bda-112">See Also</span></span>  
 [<span data-ttu-id="04bda-113">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="04bda-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
