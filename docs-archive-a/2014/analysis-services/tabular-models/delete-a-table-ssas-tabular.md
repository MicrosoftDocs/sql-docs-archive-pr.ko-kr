---
title: 테이블 삭제 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
ms.openlocfilehash: c72fa90426440c1be84318a15cf0d761ef16aca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653513"
---
# <a name="delete-a-table-ssas-tabular"></a>테이블 삭제(SSAS 테이블 형식)
  모델 디자이너의 모델 작업 영역 데이터베이스에서 더 이상 필요하지 않은 테이블을 삭제할 수 있습니다. 테이블을 삭제하면 원래 원본 데이터는 영향을 받지 않고 가져와서 작업하고 있는 데이터만 삭제됩니다. 테이블의 삭제는 실행 취소할 수 없습니다.  
  
### <a name="to-delete-a-table"></a>테이블 삭제  
  
-   삭제하려는 테이블에 대해 모델 디자이너 아래쪽의 탭을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.  
  
## <a name="considerations-when-deleting-tables"></a>테이블 삭제 시 고려 사항  
  
-   테이블을 삭제하면 테이블이 있던 전체 탭이 삭제됩니다.  
  
-   해당 테이블과 연결된 측정값의 정의도 삭제됩니다.  
  
-   해당 테이블을 사용하여 계산 열을 만든 경우 해당 테이블의 열도 삭제됩니다. 다른 테이블에서 삭제된 테이블의 열을 사용하는 계산 열에서는 오류가 표시됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [테이블 및 열&#40;SSAS 테이블 형식&#41;](tables-and-columns-ssas-tabular.md)  
  
  
