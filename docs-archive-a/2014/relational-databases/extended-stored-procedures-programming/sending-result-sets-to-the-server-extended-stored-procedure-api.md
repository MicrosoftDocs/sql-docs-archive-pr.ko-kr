---
title: 서버에 결과 집합 보내기 (확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638782"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>서버로 결과 집합 보내기(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하십시오.  
  
 로 결과 집합을 보낼 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 저장 프로시저는 다음과 같이 적절 한 API를 호출 해야 합니다.  
  
-   **Srv_sendmsg** 함수는 **srv_sendrow**를 사용 하 여 모든 행 (있는 경우)이 전송 되기 전이나 후에 순서에 관계 없이 호출 될 수 있습니다. **Srv_senddone**를 사용 하 여 완료 상태를 보내기 전에 모든 메시지를 클라이언트로 보내야 합니다.  
  
-   클라이언트로 보내는 각 행에 대해 한 번씩 **srv_sendrow** 함수를 호출합니다. 메시지, 상태 값 또는 완료 상태가 **srv_sendmsg**, **srv_pfield**의 **srv_status** 인수 또는 **srv_senddone**를 전송 하기 전에 모든 행을 클라이언트로 보내야 합니다.  
  
-   **Srv_describe** 를 사용 하 여 정의 된 모든 열이 없는 행을 보내면 응용 프로그램에서 정보 오류 메시지를 발생 시키고 클라이언트에 FAIL을 반환 합니다. 이 경우 행이 전송되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [확장 저장 프로시저 만들기](creating-extended-stored-procedures.md)  
  
  
