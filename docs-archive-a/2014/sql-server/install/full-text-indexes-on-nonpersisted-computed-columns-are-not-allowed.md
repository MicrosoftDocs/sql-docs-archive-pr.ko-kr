---
title: 비지속형 계산 열에서 전체 텍스트 인덱스는 허용 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661509"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>비지속형 계산 열에 전체 텍스트 인덱스를 사용할 수 없습니다.
  비결정적이고 정확하지 않은 계산 열에서는 전체 텍스트 인덱스를 만들 수 없습니다. 이러한 열은 유형 열 또는 전체 텍스트 키 열로 사용할 수 없습니다.  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 비결정적이고 정확하지 않은 계산 열을 유형 열이나 전체 텍스트 키 열로 사용하여 전체 텍스트 인덱스를 만들 수 있었지만 이제는 이 기능이 지원되지 않습니다. 업그레이드하면 오래되고 호환되지 않으며 지원되지 않는 전체 텍스트 인덱스가 비활성화됩니다.  
  
## <a name="corrective-action"></a>수정 동작  
 전체 텍스트 인덱스를 활성화하려면 열 정의를 수정하여 열을 결정적이고 정확하게 만듭니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
