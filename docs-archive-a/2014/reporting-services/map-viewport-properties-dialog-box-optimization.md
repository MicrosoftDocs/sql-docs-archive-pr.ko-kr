---
title: 지도 뷰포트 속성 대화 상자, 최적화 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.optimization.f1
- "10522"
ms.assetid: 8c0310ba-eedd-4c9f-95bd-1f9e2a1a8ed3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1adbeccdedb8d80900047790d94ff35568460ff4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741551"
---
# <a name="map-viewport-properties-dialog-box-optimization"></a><span data-ttu-id="52312-102">지도 뷰포트 속성 대화 상자, 최적화</span><span class="sxs-lookup"><span data-stu-id="52312-102">Map Viewport Properties Dialog Box, Optimization</span></span>
  <span data-ttu-id="52312-103">**지도 뷰포트 속성** 대화 상자의 **최적화** 를 선택하여 보고서에서 지도를 보기 위한 해상도를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52312-103">Select **Optimization** for the **Map Viewport Properties** dialog box to help control the resolution for viewing a map in a report.</span></span>  
  
 <span data-ttu-id="52312-104">공간 데이터가 보고서에 포함된 경우 해상도가 높을수록 보고서에 저장된 데이터가 많아집니다.</span><span class="sxs-lookup"><span data-stu-id="52312-104">When spatial data is embedded in the report, higher resolution means more data is stored in the report.</span></span> <span data-ttu-id="52312-105">공간 데이터가 보고서에 포함되지 않은 경우에는 해상도가 높을수록 보고서 처리기가 지도 세부 항목을 만드는 데 시간이 더 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="52312-105">When spatial data is not embedded in the report, higher resolution means that the report processor spends more time creating the map details.</span></span> <span data-ttu-id="52312-106">해상도가 낮을수록 보고서 렌더링을 기다리는 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="52312-106">Lower resolution means less time waiting for the report to render.</span></span>  
  
 <span data-ttu-id="52312-107">옵션의 값을 설정하는 식을 편집하려면 **식** 단추(*fx*)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52312-107">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="52312-108">옵션</span><span class="sxs-lookup"><span data-stu-id="52312-108">Options</span></span>  
 <span data-ttu-id="52312-109">**성능**</span><span class="sxs-lookup"><span data-stu-id="52312-109">**Performance**</span></span>  
 <span data-ttu-id="52312-110">지도를 단순화하고 덜 자세하게 표시하려면 포인터를 **성능** 에 가깝게 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52312-110">Slide the pointer closer to **Performance** to simplify the map and display less detail.</span></span>  
  
 <span data-ttu-id="52312-111">**품질**</span><span class="sxs-lookup"><span data-stu-id="52312-111">**Quality**</span></span>  
 <span data-ttu-id="52312-112">지도를 더 자세하게 그리려면 포인터를 **품질** 에 가깝게 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52312-112">Slide the pointer closer to **Quality** to draw the map with greater detail.</span></span>  
  
 <span data-ttu-id="52312-113">**지도 해상도**</span><span class="sxs-lookup"><span data-stu-id="52312-113">**Map resolution**</span></span>  
 <span data-ttu-id="52312-114">지도 해상도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52312-114">Specify a map resolution.</span></span> <span data-ttu-id="52312-115">이 값은 렌더링된 지도에서 표시할 가장 작은 항목을 포인트 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52312-115">This value specifies the smallest detail that you want to see in the rendered map in points.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52312-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52312-116">See Also</span></span>  
 <span data-ttu-id="52312-117">[지도&#40;보고서 작성기 및 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52312-117">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="52312-118">보고서 문제 해결: 맵 보고서&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52312-118">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  