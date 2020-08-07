---
title: OLE DB 속성 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4eb80ab9c0ab90da11d8580e9a2983455b676bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730628"
---
# <a name="about-ole-db-properties"></a><span data-ttu-id="126ad-102">OLE DB 속성 정보</span><span class="sxs-lookup"><span data-stu-id="126ad-102">About OLE DB Properties</span></span>
  <span data-ttu-id="126ad-103">소비자는 속성 값을 설정하여 특정 개체 동작을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-103">Consumers set property values to request specific object behavior.</span></span> <span data-ttu-id="126ad-104">예를 들어 소비자는 속성을 사용하여 행 집합에서 노출할 인터페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-104">For example, consumers use properties to specify the interfaces to be exposed by a rowset.</span></span> <span data-ttu-id="126ad-105">소비자는 속성 값을 가져와서 행 집합, 세션 또는 데이터 원본 개체와 같은 개체의 기능을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-105">Consumers get the property values to determine the capabilities of an object, such as a rowset, a session, or a data source object.</span></span>  
  
 <span data-ttu-id="126ad-106">각 속성에는 값, 유형, 설명 및 읽기/쓰기 특성이 있고 행 집합 속성의 경우 열 단위로 지정할 수 있는지 여부는 나타내는 표시도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-106">Each property has a value, type, description, and read/write attribute, and for rowset properties, an indicator of whether it can be applied on a column-by-column basis.</span></span>  
  
 <span data-ttu-id="126ad-107">속성은 GUID와 속성 ID를 나타내는 정수로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-107">A property is identified by a GUID and an integer representing the property ID.</span></span> <span data-ttu-id="126ad-108">속성 집합은 동일한 GUID를 공유하는 모든 속성의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-108">A property set is a set of all properties that share the same GUID.</span></span> <span data-ttu-id="126ad-109">Native Client OLE DB 공급자는 미리 정의 된 OLE DB 속성 집합 외에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공급자별 속성 집합과 속성을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-109">In addition to the predefined OLE DB property sets, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements provider-specific property sets and properties in them.</span></span> <span data-ttu-id="126ad-110">각 속성은 하나 이상의 속성 그룹에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-110">Each property belongs to one or more property groups.</span></span> <span data-ttu-id="126ad-111">속성 그룹은 특정 개체에 적용되는 모든 속성의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-111">A property group is the group of all properties that apply to a particular object.</span></span> <span data-ttu-id="126ad-112">예를 들어 초기화 속성 그룹, 데이터 원본 속성 그룹, 세션 속성 그룹, 행 집합 속성 그룹, 테이블 속성 그룹, 열 속성 그룹 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-112">Some property groups include the initialization property group, data source property group, session property group, rowset property group, table property group, and column property group.</span></span> <span data-ttu-id="126ad-113">이러한 각 속성 그룹에는 속성들이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-113">There are properties in each of these property groups.</span></span>  
  
 <span data-ttu-id="126ad-114">속성 값을 설정하는 과정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-114">Setting property values involves:</span></span>  
  
1.  <span data-ttu-id="126ad-115">값을 설정할 속성을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-115">Determining the properties for which to set values.</span></span>  
  
2.  <span data-ttu-id="126ad-116">식별된 속성을 포함하는 속성 집합을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-116">Determining the property sets that contain the identified properties.</span></span>  
  
3.  <span data-ttu-id="126ad-117">식별한 각 속성 집합에 대해 하나씩 DBPROPSET 구조 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-117">Allocating an array of DBPROPSET structures, one for each identified property set.</span></span>  
  
4.  <span data-ttu-id="126ad-118">각 속성 집합에 대해 DBPROP 구조 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-118">Allocating an array of DBPROP structures for each property set.</span></span> <span data-ttu-id="126ad-119">각 배열의 요소 수는 1단계에서 식별한 해당 속성 집합에 속한 속성의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-119">The number of elements in each array is the number of properties (identified in Step 1) that belong to that property set.</span></span>  
  
5.  <span data-ttu-id="126ad-120">각 속성의 DBPROP 구조를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-120">Filling in the DBPROP structure for each property.</span></span>  
  
6.  <span data-ttu-id="126ad-121">각 속성 집합의 DBPROPSET 구조에 정보(속성 집합 GUID, 요소 수 및 해당 DBPROP 배열에 대한 포인터)를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-121">Filling in information (property set GUID, count of number of elements, and a pointer to the corresponding DBPROP array) in the DBPROPSET structure for each property set.</span></span>  
  
7.  <span data-ttu-id="126ad-122">속성을 설정할 메서드를 호출하고 DBPROPSET 구조의 수 및 배열을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="126ad-122">Calling a method to set properties and passing the count and the array of DBPROPSET structures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126ad-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="126ad-123">See Also</span></span>  
 <span data-ttu-id="126ad-124">[SQL Server Native Client OLE DB 공급자 응용 프로그램 만들기](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="126ad-124">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="126ad-125">속성(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="126ad-125">Properties (OLE DB)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  