---
title: 텍스트 및 이미지 데이터 대량 복사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: rothja
ms.author: jroth
ms.openlocfilehash: 9240fd0eb8c32ed39613824ea5a07764e277160c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661091"
---
# <a name="bulk-copying-text-and-image-data"></a>텍스트 및 이미지 데이터 대량 복사
  대용량 **text**, **ntext**및 **image** 값은 [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 함수를 사용 하 여 대량 복사 됩니다. *.Pdata* 포인터가 NULL로 설정 **된 text**, **ntext**또는 **image** 열에 대 한 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) 코드를 사용 하 여 데이터가 **bcp_moretext**에 제공 됨을 나타냅니다. 대량 복사 된 각 행에서 각 **text**, **ntext**또는 **image** 열에 대해 제공 되는 정확한 데이터 길이를 지정 하는 것이 중요 합니다. 열에 대 한 데이터 길이가 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)에 지정 된 열 길이와 다른 경우 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) 를 사용 하 여 길이를 적절 한 값으로 설정 합니다. [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) 은 텍스트가 아닌 모든**텍스트**,**ntext**및**이미지가** 아닌 데이터를 모두 보냅니다. 그런 다음 **bcp_moretext** 를 호출 하 여 **text**, **ntext**또는 **image** 데이터를 별도의 단위로 보냅니다. 대량 복사 함수는 **bcp_moretext** 를 통해 전송 된 데이터의 길이가 최신 **bcp_collen** 나 **bcp_bind**에 지정 된 길이와 일치 하는 경우 현재 **text**, **ntext**또는 **image** 열에 대해 모든 데이터가 전송 되었음을 결정 합니다.  
  
 **bcp_moretext** 에는 열을 식별 하는 매개 변수가 없습니다. 한 행에 **text**, **ntext**또는 **image** 열이 여러 개 있는 경우 **bcp_moretext** 는 가장 낮은 서 수 번호가 있는 열로 시작 하는 **text**, **ntext**또는 **image** 열에 대해 작동 하며 서 수 번호가 가장 높은 열로 진행 됩니다. 전송 된 데이터의 길이가 최신 **bcp_collen** **bcp_bind** 또는 현재 열에 대해 지정 된 길이와 같으면 한 열에서 다음 열로 이동 **bcp_moretext** .  
  
## <a name="see-also"></a>참고 항목  
 [ODBC&#41;&#40;대량 복사 작업 수행](performing-bulk-copy-operations-odbc.md)  
  
  
