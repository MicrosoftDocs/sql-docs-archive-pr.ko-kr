---
title: ICommand::Execute를 사용하여 행 집합 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: rothja
ms.author: jroth
ms.openlocfilehash: f4403ba79fada44d9eca47b533a718fe7167689d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739802"
---
# <a name="creating-rowsets-with-icommandexecute"></a><span data-ttu-id="f7827-102">ICommand::Execute를 사용하여 행 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="f7827-102">Creating Rowsets with ICommand::Execute</span></span>
  <span data-ttu-id="f7827-103">**ICommand::Execute** 메서드를 사용하여 행 집합을 만들 경우 결과 행 집합의 속성에 의해 명령 텍스트가 제한될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-103">For rowsets created by using the **ICommand::Execute** method, the properties that you want in the resulting rowset can constrain the text of the command.</span></span> <span data-ttu-id="f7827-104">이는 동적 명령 텍스트를 지원하는 고객에게 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-104">This is especially critical for consumers that support dynamic command text.</span></span>  
  
 <span data-ttu-id="f7827-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서를 사용 하 여 여러 명령으로 생성 된 다중 행 집합 결과를 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider cannot use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the multiple-rowset results generated by many commands.</span></span> <span data-ttu-id="f7827-106">고객이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서 지원을 필요로 하는 행 집합을 요청할 경우 명령 텍스트가 둘 이상의 행 집합을 해당 결과로 생성하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-106">If a consumer requests a rowset requiring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursor support, an error occurs if the command text generates more than a single rowset as its result.</span></span> <span data-ttu-id="f7827-107">자세한 내용은 [여러 행 집합 결과를 생성하는 명령](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7827-107">For more information, see [Commands Generating Multiple-Rowset Results](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).</span></span>  
  
 <span data-ttu-id="f7827-108">스크롤할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 수 있는 Native Client OLE DB 공급자 행 집합은 커서에서 지원 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7827-108">Scrollable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets are supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="f7827-109">에서는 데이터베이스의 다른 사용자가 변경한 내용의 영향을 받는 커서에 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-109">imposes limitations on cursors that are sensitive to changes made by other users of the database.</span></span> <span data-ttu-id="f7827-110">특히 일부 커서의 행을 정렬할 수 없기 때문에 SQL ORDER BY 절이 포함된 명령을 사용하여 행 집합을 만들려고 하면 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7827-110">Specifically, the rows in some cursors cannot be ordered, and trying to create a rowset by using a command that contains an SQL ORDER BY clause can fail.</span></span> <span data-ttu-id="f7827-111">자세한 내용은 [행 집합 및 SQL Server 커서](rowsets-and-sql-server-cursors.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7827-111">For more information, see [Rowsets and SQL Server Cursors](rowsets-and-sql-server-cursors.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7827-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7827-112">See Also</span></span>  
 [<span data-ttu-id="f7827-113">행 집합</span><span class="sxs-lookup"><span data-stu-id="f7827-113">Rowsets</span></span>](rowsets.md)  
  
  