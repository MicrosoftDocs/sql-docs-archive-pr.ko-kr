---
title: BackupEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- BackupEncryptionKey method
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d625401324e2117ee1e9677d840854fa7b63c6e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737768"
---
# <a name="backupencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7442d-102">BackupEncryptionKey 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7442d-102">BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7442d-103">지정된 보고서 서버 인스턴스에 대한 암호화 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-103">Backs up the encryption key for the specified report server instance.</span></span> <span data-ttu-id="7442d-104">암호화 키는 암호로 암호화되어 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-104">The encryption key is stored encrypted with a password.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7442d-105">구문</span><span class="sxs-lookup"><span data-stu-id="7442d-105">Syntax</span></span>  
  
```vb  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```csharp  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7442d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7442d-106">Parameters</span></span>  
 <span data-ttu-id="7442d-107">*암호*</span><span class="sxs-lookup"><span data-stu-id="7442d-107">*Password*</span></span>  
 <span data-ttu-id="7442d-108">암호화 키를 반환하기 전에 암호화하는 데 사용되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-108">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="7442d-109">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="7442d-109">*KeyFile[]*</span></span>  
 <span data-ttu-id="7442d-110">[out] 암호화된 암호화 키를 포함하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-110">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="7442d-111">*길이*</span><span class="sxs-lookup"><span data-stu-id="7442d-111">*Length*</span></span>  
 <span data-ttu-id="7442d-112">[out] 메서드에서 반환된 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-112">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="7442d-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7442d-113">*HRESULT*</span></span>  
 <span data-ttu-id="7442d-114">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-114">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="7442d-115">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="7442d-115">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="7442d-116">[out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-116">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7442d-117">Return Value</span><span class="sxs-lookup"><span data-stu-id="7442d-117">Return Value</span></span>  
 <span data-ttu-id="7442d-118">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7442d-119">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-119">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="7442d-120">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7442d-120">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7442d-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7442d-121">Requirements</span></span>  
 <span data-ttu-id="7442d-122">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7442d-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7442d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7442d-123">See Also</span></span>  
 [<span data-ttu-id="7442d-124">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="7442d-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  