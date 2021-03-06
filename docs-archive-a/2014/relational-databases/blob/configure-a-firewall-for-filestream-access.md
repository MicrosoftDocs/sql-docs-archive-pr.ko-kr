---
title: FILESTREAM 액세스를 위한 방화벽 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659491"
---
# <a name="configure-a-firewall-for-filestream-access"></a>FILESTREAM 액세스를 위한 방화벽 구성
  방화벽으로 보호되는 환경에서 FILESTREAM을 사용하려면 클라이언트와 서버에서 DNS 이름을 FILESTREAM 파일이 포함된 서버로 확인할 수 있어야 합니다. FILESTREAM을 사용하려면 Windows 파일 공유 포트 139 및 445가 열려 있어야 합니다.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Windows 7을 실행하는 컴퓨터에서 Windows 파일 공유 포트를 열려면  
  
1.  제어판에서 **Windows 방화벽**을 엽니다.  
  
2.  왼쪽 창에서 **고급 설정**을 클릭합니다. 관리자 암호를 입력하거나 확인하라는 메시지가 표시되면 암호를 입력하거나 확인을 제공합니다.  
  
3.  **고급 보안이 포함된 Windows 방화벽** 대화 상자의 왼쪽 창에서 **인바운드 규칙**을 클릭한 다음 오른쪽 창에서 **새 규칙**을 클릭합니다.  
  
4.  새 인바운드 규칙 마법사의 지시에 따라 TCP 포트 139를 추가합니다.  
  
5.  이전 단계를 반복하여 TCP 포트 445를 추가합니다.  
  
6.  **고급 보안이 포함된 Windows 방화벽** 대화 상자를 닫습니다.  
  
  
