---
title: 데이터 원본 이름 및 64 비트 운영 체제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648355"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>데이터 원본 이름 및 64비트 운영 체제
  애플리케이션을 64비트 운영 체제에서 32비트 애플리케이션으로 작성하여 실행하려는 경우 %windir%\SysWOW64\odbcad32.exe에서 ODBC 관리자를 사용하여 ODBC 데이터 원본을 만들어야 합니다.  
  
## <a name="remarks"></a>설명  
 64비트 Windows 운영 체제에는 odbcad32.exe 파일이 두 개 있습니다.  
  
-   %SystemRoot%\system32\odbcad32.exe는 64비트 애플리케이션의 데이터 원본 이름을 만들고 유지 관리하는 데 사용됩니다.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe는 64비트 운영 체제에서 실행되는 32비트 애플리케이션을 포함하여 32비트 애플리케이션의 데이터 원본 이름을 만들고 유지 관리하는 데 사용됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
