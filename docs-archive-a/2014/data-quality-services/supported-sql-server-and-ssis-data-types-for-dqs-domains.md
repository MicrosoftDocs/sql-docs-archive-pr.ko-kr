---
title: DQS 도메인에 대해 지원되는 SQL Server 및 SSIS 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad79983f570beb4c789379b2b48682b358c34e1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742600"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a><span data-ttu-id="b3579-102">DQS 도메인에 대해 지원되는 SQL Server 및 SSIS 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-102">Supported SQL Server and SSIS Data Types for DQS Domains</span></span>
  <span data-ttu-id="b3579-103">SQL Server 및 SQL Server Integration Services(SSIS)에는 여러 가지 데이터 형식이 있지만 DQS 도메인에 대해서는 Date, Decimal, Integer 및 String으로 4개의 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-103">There are many data types in SQL Server and SQL Server Integration Services (SSIS), but only four data types for DQS domains: Date, Decimal, Integer, and String.</span></span> <span data-ttu-id="b3579-104">SQL Server 및 SSIS 데이터 형식이 DQS에서 모두 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-104">Not all SQL Server and SSIS data types are supported in DQS.</span></span> <span data-ttu-id="b3579-105">원본 데이터 형식이 DQS에서 지원되고 DQS 도메인 데이터 형식과 일치하는 경우에만 데이터 품질 활동을 수행하기 위해 DQS 도메인에 원본 데이터를 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-105">You can map your source data to a DQS domain for performing data-quality activities only if the source data type is supported in DQS, and matches with the DQS domain data type.</span></span> <span data-ttu-id="b3579-106">이 항목에서는 지원되는 SQL Server 및 SSIS 데이터 형식 및 DQS의 4가지 각 도메인 데이터 형식에 대해 매핑할 수 있는 데이터 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-106">This topic provides information about the SQL Server and SSIS data types that are supported, and available for mapping to each of the four domain data types in DQS.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3579-107">.xlsx 및 .xls 파일에서는 처음 8개 행에서 가장 많이 사용된 데이터 형식에 의해 원본 열의 데이터 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-107">In .xlsx and .xls files, the data type of the source column is determined by the most prevalent data type in the first eight rows.</span></span> <span data-ttu-id="b3579-108">데이터 형식을 따르지 않는 셀에는 null 값이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-108">If a cell does not conform to that data type, it will be given a null value.</span></span> <span data-ttu-id="b3579-109">마찬가지로 .csv 파일에서는 처음 8개 행에서 가장 많이 사용된 데이터 형식에 의해 원본 열의 데이터 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-109">Similarly, in .csv files, the data type of the source column is determined by the most prevalent data type in the first eight rows.</span></span>  
  
##  <a name="supported-sql-server-data-types"></a><a name="SQLServer"></a><span data-ttu-id="b3579-110">지원 되는 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-110">Supported SQL Server Data Types</span></span>  
 <span data-ttu-id="b3579-111">다음 표에서는 각 DQS 도메인 데이터 형식에 대해 지원되는 SQL Server 데이터 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-111">The following table provides information about the SQL Server data types supported for each DQS domain data type:</span></span>  
  
|<span data-ttu-id="b3579-112">DQS 도메인 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-112">DQS Domain Data Type</span></span>|<span data-ttu-id="b3579-113">지원되는 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-113">Supported SQL Server Data Type</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="b3579-114">날짜</span><span class="sxs-lookup"><span data-stu-id="b3579-114">Date</span></span>|<span data-ttu-id="b3579-115">날짜</span><span class="sxs-lookup"><span data-stu-id="b3579-115">date</span></span>|  
|<span data-ttu-id="b3579-116">Decimal</span><span class="sxs-lookup"><span data-stu-id="b3579-116">Decimal</span></span>|<span data-ttu-id="b3579-117">decimal</span><span class="sxs-lookup"><span data-stu-id="b3579-117">decimal</span></span><br /><br /> <span data-ttu-id="b3579-118">float</span><span class="sxs-lookup"><span data-stu-id="b3579-118">float</span></span><br /><br /> <span data-ttu-id="b3579-119">money</span><span class="sxs-lookup"><span data-stu-id="b3579-119">money</span></span><br /><br /> <span data-ttu-id="b3579-120">numeric</span><span class="sxs-lookup"><span data-stu-id="b3579-120">numeric</span></span><br /><br /> <span data-ttu-id="b3579-121">real</span><span class="sxs-lookup"><span data-stu-id="b3579-121">real</span></span><br /><br /> <span data-ttu-id="b3579-122">smallmoney</span><span class="sxs-lookup"><span data-stu-id="b3579-122">smallmoney</span></span>|  
|<span data-ttu-id="b3579-123">정수</span><span class="sxs-lookup"><span data-stu-id="b3579-123">Integer</span></span>|<span data-ttu-id="b3579-124">bigint</span><span class="sxs-lookup"><span data-stu-id="b3579-124">bigint</span></span><br /><br /> <span data-ttu-id="b3579-125">int</span><span class="sxs-lookup"><span data-stu-id="b3579-125">int</span></span><br /><br /> <span data-ttu-id="b3579-126">smallint</span><span class="sxs-lookup"><span data-stu-id="b3579-126">smallint</span></span><br /><br /> <span data-ttu-id="b3579-127">tinyint</span><span class="sxs-lookup"><span data-stu-id="b3579-127">tinyint</span></span>|  
|<span data-ttu-id="b3579-128">String</span><span class="sxs-lookup"><span data-stu-id="b3579-128">String</span></span>|<span data-ttu-id="b3579-129">char</span><span class="sxs-lookup"><span data-stu-id="b3579-129">char</span></span><br /><br /> <span data-ttu-id="b3579-130">nchar</span><span class="sxs-lookup"><span data-stu-id="b3579-130">nchar</span></span><br /><br /> <span data-ttu-id="b3579-131">nvarchar</span><span class="sxs-lookup"><span data-stu-id="b3579-131">nvarchar</span></span><br /><br /> <span data-ttu-id="b3579-132">varchar</span><span class="sxs-lookup"><span data-stu-id="b3579-132">varchar</span></span>|  
  
 <span data-ttu-id="b3579-133">다른 SQL Server 데이터 형식은 DQS에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-133">Rest of the SQL Server data types are not supported in DQS.</span></span> <span data-ttu-id="b3579-134">모든 SQL Server 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3579-134">For information about all the SQL Server data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
##  <a name="supported-ssis-data-types"></a><a name="SSIS"></a> <span data-ttu-id="b3579-135">지원되는 SSIS 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-135">Supported SSIS Data Types</span></span>  
 <span data-ttu-id="b3579-136">다음 표에서는 각 DQS 도메인 데이터 형식에 대해 지원되는 SSIS 데이터 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-136">The following table provides information about the SSIS data types supported for each DQS domain data type:</span></span>  
  
|<span data-ttu-id="b3579-137">DQS 도메인 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-137">DQS Domain Data Type</span></span>|<span data-ttu-id="b3579-138">지원되는 SSIS 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b3579-138">Supported SSIS Data Type</span></span>|  
|--------------------------|------------------------------|  
|<span data-ttu-id="b3579-139">Date</span><span class="sxs-lookup"><span data-stu-id="b3579-139">Date</span></span>|<span data-ttu-id="b3579-140">DT_DATE</span><span class="sxs-lookup"><span data-stu-id="b3579-140">DT_DATE</span></span>|  
|<span data-ttu-id="b3579-141">Decimal</span><span class="sxs-lookup"><span data-stu-id="b3579-141">Decimal</span></span>|<span data-ttu-id="b3579-142">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="b3579-142">DT_DECIMAL</span></span><br /><br /> <span data-ttu-id="b3579-143">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="b3579-143">DT_NUMERIC</span></span><br /><br /> <span data-ttu-id="b3579-144">DT_R4</span><span class="sxs-lookup"><span data-stu-id="b3579-144">DT_R4</span></span><br /><br /> <span data-ttu-id="b3579-145">DT_R8</span><span class="sxs-lookup"><span data-stu-id="b3579-145">DT_R8</span></span>|  
|<span data-ttu-id="b3579-146">정수</span><span class="sxs-lookup"><span data-stu-id="b3579-146">Integer</span></span>|<span data-ttu-id="b3579-147">DT_I1</span><span class="sxs-lookup"><span data-stu-id="b3579-147">DT_I1</span></span><br /><br /> <span data-ttu-id="b3579-148">DT_I2</span><span class="sxs-lookup"><span data-stu-id="b3579-148">DT_I2</span></span><br /><br /> <span data-ttu-id="b3579-149">DT_I4</span><span class="sxs-lookup"><span data-stu-id="b3579-149">DT_I4</span></span><br /><br /> <span data-ttu-id="b3579-150">DT_I8</span><span class="sxs-lookup"><span data-stu-id="b3579-150">DT_I8</span></span><br /><br /> <span data-ttu-id="b3579-151">DT_U1</span><span class="sxs-lookup"><span data-stu-id="b3579-151">DT_U1</span></span><br /><br /> <span data-ttu-id="b3579-152">DT_U2</span><span class="sxs-lookup"><span data-stu-id="b3579-152">DT_U2</span></span><br /><br /> <span data-ttu-id="b3579-153">DT_U4</span><span class="sxs-lookup"><span data-stu-id="b3579-153">DT_U4</span></span><br /><br /> <span data-ttu-id="b3579-154">DT_U8</span><span class="sxs-lookup"><span data-stu-id="b3579-154">DT_U8</span></span>|  
|<span data-ttu-id="b3579-155">String</span><span class="sxs-lookup"><span data-stu-id="b3579-155">String</span></span>|<span data-ttu-id="b3579-156">DT_STR</span><span class="sxs-lookup"><span data-stu-id="b3579-156">DT_STR</span></span><br /><br /> <span data-ttu-id="b3579-157">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="b3579-157">DT_WSTR</span></span>|  
  
 <span data-ttu-id="b3579-158">다른 SSIS 데이터 형식은 DQS에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3579-158">Rest of the SSIS data types are not supported in DQS.</span></span> <span data-ttu-id="b3579-159">모든 SSIS 데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3579-159">For information about all the SSIS data types, see [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3579-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3579-160">See Also</span></span>  
 [<span data-ttu-id="b3579-161">도메인 관리</span><span class="sxs-lookup"><span data-stu-id="b3579-161">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)  
  
  