---
title: 데이터 처리 확장 프로그램 구현 준비 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- data processing extensions [Reporting Services], implementing
ms.assetid: 698817e4-33da-4eb5-9407-4103e1c35247
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3588aea825233631cb4ad7752919ad88bb4dbf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741583"
---
# <a name="preparing-to-implement-a-data-processing-extension"></a><span data-ttu-id="ab3b5-102">데이터 처리 확장 프로그램 구현 준비</span><span class="sxs-lookup"><span data-stu-id="ab3b5-102">Preparing to Implement a Data Processing Extension</span></span>
  <span data-ttu-id="ab3b5-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 구현하기 전에 먼저 구현할 인터페이스를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-103">Before you implement your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="ab3b5-104">전체 인터페이스 집합의 확장 프로그램별 구현을 제공해야 할 수도 있습니다. 또는 클라이언트가 **DataReader** 개체 형태인 결과 집합과 주로 상호 작용하고 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 데이터 처리 확장 프로그램을 결과 집합과 데이터 원본 사이의 연결 고리로 사용하는 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 및 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 인터페이스와 같은 하위 집합에 대한 구현에 초점을 맞추어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-104">You may want to provide extension-specific implementations of the entire set of interfaces, or you may simply want to focus your implementation on a subset, such as the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> interfaces in which clients would interact primarily with a result set as a **DataReader** object and would use your [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extension as a bridge between the result set and your data source.</span></span>  
  
 <span data-ttu-id="ab3b5-105">다음 두 가지 방법 중 하나로 데이터 처리 확장 프로그램을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-105">You can implement data processing extensions in one of two ways:</span></span>  
  
-   <span data-ttu-id="ab3b5-106">데이터 처리 확장 프로그램 클래스는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자 인터페이스 및 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 제공하는 확장된 데이터 처리 확장 프로그램 인터페이스(선택 사항)를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-106">Your data processing extension classes can implement the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces and optionally the extended data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ab3b5-107">데이터 처리 확장 프로그램 클래스는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 제공하는 데이터 처리 확장 프로그램 인터페이스 및 확장된 데이터 처리 확장 프로그램 인터페이스(선택 사항)를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-107">Your data processing extension classes can implement the data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and optionally the extended data processing extension interfaces.</span></span>  
  
 <span data-ttu-id="ab3b5-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에서 특정 속성 또는 메서드를 지원하지 않을 경우 속성 또는 메서드를 작업 없음으로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-108">If your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension will not support a particular property or method, implement the property or method as no-operation.</span></span> <span data-ttu-id="ab3b5-109">클라이언트에서 특정 동작이 필요한 경우 **NotSupportedException** 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-109">If a client expects a particular behavior, throw a **NotSupportedException** exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab3b5-110">속성 또는 메서드에 대한 작업 없음 구현은 구현 대상으로 선택한 인터페이스의 속성 및 메서드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-110">A no-operation implementation of a property or method only applies to the properties and methods of those interfaces that you choose to implement.</span></span> <span data-ttu-id="ab3b5-111">구현하지 않도록 선택한 인터페이스는 데이터 처리 확장 프로그램 어셈블리에 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-111">Optional interfaces that you choose not to implement should be left out of your data processing extension assembly.</span></span> <span data-ttu-id="ab3b5-112">인터페이스가 필수인지 아니면 선택적인지에 대한 자세한 내용은 이 섹션의 후반에 나오는 표를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-112">For more information about whether an interface is required or optional, see the table later in this section.</span></span>  
  
## <a name="required-extension-functionality"></a><span data-ttu-id="ab3b5-113">필수 확장 프로그램 기능</span><span class="sxs-lookup"><span data-stu-id="ab3b5-113">Required Extension Functionality</span></span>  
 <span data-ttu-id="ab3b5-114">각 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램은 다음 기능을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-114">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="ab3b5-115">데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-115">Open a connection to a data source.</span></span>  
  
-   <span data-ttu-id="ab3b5-116">쿼리를 분석하고 결과 집합에 대한 필드 이름 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-116">Analyze a query and return a list of field names for the result set.</span></span>  
  
-   <span data-ttu-id="ab3b5-117">데이터 원본에 대한 쿼리를 실행하고 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-117">Execute a query against the data source and return a row set.</span></span>  
  
-   <span data-ttu-id="ab3b5-118">단일 값 매개 변수를 쿼리에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-118">Pass single-valued parameters to the query.</span></span>  
  
-   <span data-ttu-id="ab3b5-119">행 집합의 행을 반복 처리하고 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-119">Iterate through rows in the row set and retrieve data.</span></span>  
  
 <span data-ttu-id="ab3b5-120">각 데이터 처리 확장 프로그램은 다음 기능을 포함하도록 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-120">Each data processing extension can be extended to include the following functionality:</span></span>  
  
-   <span data-ttu-id="ab3b5-121">쿼리를 분석하고 쿼리에 사용된 매개 변수 이름 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-121">Analyze a query and return a list of parameter names used in the query.</span></span>  
  
-   <span data-ttu-id="ab3b5-122">쿼리를 분석하고 쿼리 그룹화 기준이 되는 필드 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-122">Analyze a query and return the list of fields by which the query is grouped.</span></span>  
  
-   <span data-ttu-id="ab3b5-123">쿼리를 분석하고 쿼리 정렬 기준이 되는 필드 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-123">Analyze a query and return the list of fields by which the query is sorted.</span></span>  
  
-   <span data-ttu-id="ab3b5-124">연결 문자열에 독립적인 데이터 원본에 연결하기 위한 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-124">Provide a user name and password to connect to the data source that is independent of the connection string.</span></span>  
  
-   <span data-ttu-id="ab3b5-125">행 집합의 행을 반복 처리하고 데이터 값에 대한 보조 메타데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-125">Iterate through rows in the row set and retrieve auxiliary metadata about the data values.</span></span>  
  
-   <span data-ttu-id="ab3b5-126">서버에서 데이터를 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-126">Aggregate data at the server.</span></span>  
  
## <a name="available-extension-interfaces"></a><span data-ttu-id="ab3b5-127">사용 가능한 확장 프로그램 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ab3b5-127">Available Extension Interfaces</span></span>  
 <span data-ttu-id="ab3b5-128">다음 표에서는 사용 가능한 인터페이스를 보여 주고 구현이 필수인지 선택적인지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-128">The following table describes the available interfaces and whether implementation is required or optional.</span></span>  
  
|<span data-ttu-id="ab3b5-129">인터페이스</span><span class="sxs-lookup"><span data-stu-id="ab3b5-129">Interface</span></span>|<span data-ttu-id="ab3b5-130">Description</span><span class="sxs-lookup"><span data-stu-id="ab3b5-130">Description</span></span>|<span data-ttu-id="ab3b5-131">구현</span><span class="sxs-lookup"><span data-stu-id="ab3b5-131">Implementation</span></span>|  
|---------------|-----------------|--------------------|  
|<span data-ttu-id="ab3b5-132">IDbConnection</span><span class="sxs-lookup"><span data-stu-id="ab3b5-132">IDbConnection</span></span>|<span data-ttu-id="ab3b5-133">데이터 원본의 고유 세션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-133">Represents a unique session with a data source.</span></span> <span data-ttu-id="ab3b5-134">클라이언트/서버 데이터베이스 시스템의 경우에는 세션이 서버에 대한 네트워크 연결과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-134">In the case of a client/server database system, the session may be equivalent to a network connection to the server.</span></span>|<span data-ttu-id="ab3b5-135">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-135">Required</span></span>|  
|<span data-ttu-id="ab3b5-136">IDbConnectionExtension</span><span class="sxs-lookup"><span data-stu-id="ab3b5-136">IDbConnectionExtension</span></span>|<span data-ttu-id="ab3b5-137">보안 및 인증과 관련하여 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 데이터 처리 확장 프로그램으로 구현할 수 있는 추가 연결 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-137">Represents additional connection properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions regarding security and authentication.</span></span>|<span data-ttu-id="ab3b5-138">옵션</span><span class="sxs-lookup"><span data-stu-id="ab3b5-138">Optional</span></span>|  
|<span data-ttu-id="ab3b5-139">IDbTransaction</span><span class="sxs-lookup"><span data-stu-id="ab3b5-139">IDbTransaction</span></span>|<span data-ttu-id="ab3b5-140">로컬 트랜잭션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-140">Represents a local transaction.</span></span>|<span data-ttu-id="ab3b5-141">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-141">Required</span></span>|  
|<span data-ttu-id="ab3b5-142">IDbTransactionExtension</span><span class="sxs-lookup"><span data-stu-id="ab3b5-142">IDbTransactionExtension</span></span>|<span data-ttu-id="ab3b5-143">[!INCLUDE[ssRS](../../../includes/ssrs.md)] 데이터 처리 확장 프로그램으로 구현할 수 있는 추가 트랜잭션 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-143">Represents additional transaction properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions.</span></span>|<span data-ttu-id="ab3b5-144">옵션</span><span class="sxs-lookup"><span data-stu-id="ab3b5-144">Optional</span></span>|  
|<span data-ttu-id="ab3b5-145">IDbCommand</span><span class="sxs-lookup"><span data-stu-id="ab3b5-145">IDbCommand</span></span>|<span data-ttu-id="ab3b5-146">데이터 원본에 연결되었을 때 사용되는 쿼리 또는 명령을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-146">Represents a query or command that is used when connected to a data source.</span></span>|<span data-ttu-id="ab3b5-147">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-147">Required</span></span>|  
|<span data-ttu-id="ab3b5-148">IDbCommandAnalysis</span><span class="sxs-lookup"><span data-stu-id="ab3b5-148">IDbCommandAnalysis</span></span>|<span data-ttu-id="ab3b5-149">쿼리를 분석하고 쿼리에서 사용된 매개 변수 이름 목록을 반환하기 위한 추가 명령 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-149">Represents additional command information for analyzing a query and returning a list of parameter names used in the query.</span></span>|<span data-ttu-id="ab3b5-150">옵션</span><span class="sxs-lookup"><span data-stu-id="ab3b5-150">Optional</span></span>|  
|<span data-ttu-id="ab3b5-151">IDataParameter</span><span class="sxs-lookup"><span data-stu-id="ab3b5-151">IDataParameter</span></span>|<span data-ttu-id="ab3b5-152">명령 또는 쿼리에 전달된 매개 변수 또는 이름/값 쌍을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-152">Represents a parameter or name/value pair that is passed to a command or query.</span></span>|<span data-ttu-id="ab3b5-153">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-153">Required</span></span>|  
|<span data-ttu-id="ab3b5-154">IDataParameterCollection</span><span class="sxs-lookup"><span data-stu-id="ab3b5-154">IDataParameterCollection</span></span>|<span data-ttu-id="ab3b5-155">명령 또는 쿼리와 관련된 모든 매개 변수의 모음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-155">Represents a collection of all parameters relevant to a command or query.</span></span>|<span data-ttu-id="ab3b5-156">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-156">Required</span></span>|  
|<span data-ttu-id="ab3b5-157">IDataReader</span><span class="sxs-lookup"><span data-stu-id="ab3b5-157">IDataReader</span></span>|<span data-ttu-id="ab3b5-158">데이터 원본에서 데이터의 정방향 전용, 읽기 전용 스트림을 읽는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-158">Provides a method of reading a forward-only, read-only stream of data from your data source.</span></span>|<span data-ttu-id="ab3b5-159">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-159">Required</span></span>|  
|<span data-ttu-id="ab3b5-160">IDataReaderExtension</span><span class="sxs-lookup"><span data-stu-id="ab3b5-160">IDataReaderExtension</span></span>|<span data-ttu-id="ab3b5-161">데이터 원본에서 명령을 실행하여 얻은 정방향 전용 결과 집합 스트림을 하나 이상 읽는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-161">Provides a method of reading one or more forward-only streams of result sets, obtained by executing a command at a data source.</span></span> <span data-ttu-id="ab3b5-162">이 인터페이스는 필드 집계에 대한 추가 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-162">This interface provides additional support for field aggregates.</span></span>|<span data-ttu-id="ab3b5-163">옵션</span><span class="sxs-lookup"><span data-stu-id="ab3b5-163">Optional</span></span>|  
|<span data-ttu-id="ab3b5-164">IExtension</span><span class="sxs-lookup"><span data-stu-id="ab3b5-164">IExtension</span></span>|<span data-ttu-id="ab3b5-165">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에 대한 기본 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-165">Provides the base class for a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="ab3b5-166">또한 구현 전문가는 이 인터페이스를 사용하여 확장 프로그램에 대한 지역화된 이름을 포함시키고 구성 파일에서 확장 프로그램으로 구성 설정을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-166">Also enables an implementer to include a localized name for the extension and to pass configuration settings from the configuration file to the extension.</span></span>|<span data-ttu-id="ab3b5-167">필수</span><span class="sxs-lookup"><span data-stu-id="ab3b5-167">Required</span></span>|  
  
 <span data-ttu-id="ab3b5-168">데이터 처리 확장 프로그램 인터페이스는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자 인터페이스, 메서드 및 속성의 하위 집합과 동일합니다(가능한 경우 항상).</span><span class="sxs-lookup"><span data-stu-id="ab3b5-168">The data processing extension interfaces are identical to a subset of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces, methods, and properties whenever possible.</span></span> <span data-ttu-id="ab3b5-169">전체 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자를 구현하는 방법은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK(소프트웨어 개발 키트) 설명서의 ".NET Framework 데이터 공급자 구현(Implementing a .NET Framework Data Provider)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab3b5-169">For more information about implementing a full [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider, see "Implementing a .NET Framework Data Provider" in your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3b5-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab3b5-170">See Also</span></span>  
 <span data-ttu-id="ab3b5-171">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="ab3b5-171">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="ab3b5-172">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ab3b5-172">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="ab3b5-173">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="ab3b5-173">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  