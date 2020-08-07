---
title: Invoke-Sqlcmd cmdlet | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b1572b03b5772f35ac68a6b85aeedde43d150c07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730876"
---
# <a name="invoke-sqlcmd-cmdlet"></a><span data-ttu-id="2273d-102">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="2273d-102">Invoke-Sqlcmd cmdlet</span></span>
  <span data-ttu-id="2273d-103">**Invoke-Sqlcmd**는 [!INCLUDE[tsql](../includes/tsql-md.md)] 및 XQuery 언어로 된 문과 **sqlcmd** 유틸리티에서 지원되는 명령이 포함된 스크립트를 실행하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-103">**Invoke-Sqlcmd** is a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet that runs scripts that contain statements from the languages ([!INCLUDE[tsql](../includes/tsql-md.md)] and XQuery) and commands that are supported by the **sqlcmd** utility.</span></span>  
  
## <a name="using-invoke-sqlcmd"></a><span data-ttu-id="2273d-104">Invoke-Sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="2273d-104">Using Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="2273d-105">**Invoke-Sqlcmd** cmdlet을 사용하여 **sqlcmd** 스크립트 파일을 Windows PowerShell 환경에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-105">The **Invoke-Sqlcmd** cmdlet lets you run your **sqlcmd** script files in a Windows PowerShell environment.</span></span> <span data-ttu-id="2273d-106">**sqlcmd** 를 사용하여 수행할 수 있는 대부분의 작업은 **Invoke-Sqlcmd**로도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-106">Much of what you can do with **sqlcmd** can also be done using **Invoke-Sqlcmd**.</span></span>  
  
 <span data-ttu-id="2273d-107">다음은 Invoke-Sqlcmd를 호출하여 간단한 쿼리를 실행하는 예제입니다. 이 예제는 **sqlcmd** 에 **-Q** 및 **-S** 옵션을 지정하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-107">This is an example of calling Invoke-Sqlcmd to execute a simple query, similar to specifying **sqlcmd** with the **-Q** and **-S** options:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 <span data-ttu-id="2273d-108">다음은 **Invoke-Sqlcmd**를 호출하고 입력 파일을 지정한 후 출력을 파일로 파이핑하는 예제입니다. 이 예제는 **sqlcmd** 에 **-i** 및 **-o** 옵션을 지정하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-108">This is an example of calling **Invoke-Sqlcmd**, specifying an input file and piping the output to a file This is similar to specifying **sqlcmd** with the **-i** and **-o** options:</span></span>  
  
```powershell
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -FilePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 <span data-ttu-id="2273d-109">다음은 Windows PowerShell 배열을 사용하여 여러 **sqlcmd** 스크립팅 변수를 **Invoke-Sqlcmd**로 전달하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-109">This is an example of using a Windows PowerShell array to pass multiple **sqlcmd** scripting variables to **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="2273d-110">SELECT 문에서 **sqlcmd** 스크립팅 변수를 식별하는 "$" 문자는 PowerShell 역따옴표(\`) 이스케이프 문자를 사용하여 이스케이프 처리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-110">The "$" characters identifying the **sqlcmd** scripting variables in the SELECT statement have been escaped by using the PowerShell back-tick "\`" escape character:</span></span>  
  
```powershell
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 <span data-ttu-id="2273d-111">다음은 Windows PowerShell의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자를 사용하여 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스로 이동한 다음 Windows PowerShell **Get-Item** cmdlet을 사용하여 해당 인스턴스에 대한 SMO Server 개체를 가져와 **Invoke-Sqlcmd**로 전달하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-111">This is an example of using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell to navigate to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], and then using the Windows PowerShell **Get-Item** cmdlet to retrieve the SMO Server object for the instance and passing it to **Invoke-Sqlcmd**:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 <span data-ttu-id="2273d-112">-Query 매개 변수는 위치 매개 변수이며 이름을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-112">The -Query parameter is positional and does not have to be named.</span></span> <span data-ttu-id="2273d-113">**Invoke-Sqlcmd**에 전달된 첫 번째 문자열은 명명되지 않은 경우 -Query 매개 변수로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-113">If the first string that is passed to **Invoke-Sqlcmd**: is unnamed, it is treated as the -Query parameter.</span></span>  
  
```powershell
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a><span data-ttu-id="2273d-114">Invoke-Sqlcmd의 경로 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="2273d-114">Path Context in Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="2273d-115">-Database 매개 변수를 사용하지 않는 경우 Invoke-Sqlcmd에 대한 데이터베이스 컨텍스트는 cmdlet을 호출할 때 활성화된 경로에 의해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-115">If you do not use the -Database parameter, the database context for Invoke-Sqlcmd is set by the path that is active when the cmdlet is called.</span></span>  
  
|<span data-ttu-id="2273d-116">경로</span><span class="sxs-lookup"><span data-stu-id="2273d-116">Path</span></span>|<span data-ttu-id="2273d-117">데이터베이스 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="2273d-117">Database Context</span></span>|  
|----------|----------------------|  
|<span data-ttu-id="2273d-118">SQLSERVER: 이외의 드라이브로 시작</span><span class="sxs-lookup"><span data-stu-id="2273d-118">Starts with a drive other than SQLSERVER:</span></span>|<span data-ttu-id="2273d-119">로컬 컴퓨터에 있는 기본 인스턴스의 로그인 ID에 대한 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-119">The default database for the login ID in the default instance on the local computer.</span></span>|  
|<span data-ttu-id="2273d-120">SQLSERVER:\SQL</span><span class="sxs-lookup"><span data-stu-id="2273d-120">SQLSERVER:\SQL</span></span>|<span data-ttu-id="2273d-121">로컬 컴퓨터에 있는 기본 인스턴스의 로그인 ID에 대한 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-121">The default database for the login ID in the default instance on the local computer.</span></span>|  
|<span data-ttu-id="2273d-122">SQLSERVER:\SQL\ComputerName</span><span class="sxs-lookup"><span data-stu-id="2273d-122">SQLSERVER:\SQL\ComputerName</span></span>|<span data-ttu-id="2273d-123">지정된 컴퓨터에 있는 기본 인스턴스의 로그인 ID에 대한 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-123">The default database for the login ID in the default instance on the specified computer.</span></span>|  
|<span data-ttu-id="2273d-124">SQLSERVER:\SQL\ComputerName\InstanceName</span><span class="sxs-lookup"><span data-stu-id="2273d-124">SQLSERVER:\SQL\ComputerName\InstanceName</span></span>|<span data-ttu-id="2273d-125">지정된 컴퓨터에 있는 지정된 인스턴스의 로그인 ID에 대한 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-125">The default database for the login ID in the specified instance on the specified computer.</span></span>|  
|<span data-ttu-id="2273d-126">SQLSERVER:\SQL\ComputerName\InstanceName\Databases</span><span class="sxs-lookup"><span data-stu-id="2273d-126">SQLSERVER:\SQL\ComputerName\InstanceName\Databases</span></span>|<span data-ttu-id="2273d-127">지정된 컴퓨터에 있는 지정된 인스턴스의 로그인 ID에 대한 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-127">The default database for the login ID in the specified instance on the specified computer.</span></span>|  
|<span data-ttu-id="2273d-128">SQLSERVER:\SQL\ComputerName\InstanceName\Databases\DatabaseName</span><span class="sxs-lookup"><span data-stu-id="2273d-128">SQLSERVER:\SQL\ComputerName\InstanceName\Databases\DatabaseName</span></span>|<span data-ttu-id="2273d-129">지정된 컴퓨터에 있는 지정된 인스턴스의 지정된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-129">The specified database in the specified instance on the specified computer.</span></span> <span data-ttu-id="2273d-130">이는 또한 데이터베이스 내의 테이블 및 열 노드를 지정하는 경로와 같은 보다 긴 경로에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-130">This also applies to longer paths, such as a path that specifies the Tables and Columns node within a database.</span></span>|  
  
 <span data-ttu-id="2273d-131">예를 들어 로컬 컴퓨터의 기본 인스턴스에 있는 Windows 계정에 대한 기본 데이터베이스가 master라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-131">For example, assume that the default database for your Windows account in the default instance of the local computer is master.</span></span> <span data-ttu-id="2273d-132">이 경우 다음 명령에서 master를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-132">Then, the following commands would return master:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 <span data-ttu-id="2273d-133">다음 명령에서 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-133">The following commands would return [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 <span data-ttu-id="2273d-134">Invoke-Sqlcmd에서 경로 데이터베이스 컨텍스트를 사용하는 경우 경고를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-134">Invoke-Sqlcmd provides a warning when it uses the path database context.</span></span> <span data-ttu-id="2273d-135">-SuppressProviderContextWarning 매개 변수를 사용하여 경고 메시지를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-135">You can use the -SuppressProviderContextWarning parameter to turn off the warning message.</span></span> <span data-ttu-id="2273d-136">-IgnoreProviderContext 매개 변수를 사용하여 Invoke-Sqlcmd에서 로그인에 대한 기본 데이터베이스를 항상 사용하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-136">You can use the -IgnoreProviderContext parameter to tell Invoke-Sqlcmd to always use the default database for the login.</span></span>  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a><span data-ttu-id="2273d-137">Invoke-Sqlcmd와 sqlcmd 유틸리티 비교</span><span class="sxs-lookup"><span data-stu-id="2273d-137">Comparing Invoke-Sqlcmd and the sqlcmd Utility</span></span>  
 <span data-ttu-id="2273d-138">**Invoke-Sqlcmd** 를 사용하면 **sqlcmd** 유틸리티로 실행할 수 있는 대부분의 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-138">**Invoke-Sqlcmd** can be used to run many of the scripts that can be run using the **sqlcmd** utility.</span></span> <span data-ttu-id="2273d-139">하지만 **Invoke-Sqlcmd** 는 **sqlcmd** 가 실행되는 명령 프롬프트 환경과는 다른 Windows PowerShell 환경에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-139">However, **Invoke-Sqlcmd** runs in a Windows PowerShell environment which is different than the command prompt environment that **sqlcmd** is run in.</span></span> <span data-ttu-id="2273d-140">**Invoke-Sqlcmd** 의 동작은 Windows PowerShell 환경에서 작동하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-140">The behavior of **Invoke-Sqlcmd** has been modified to work in a Windows PowerShell environment.</span></span>  
  
 <span data-ttu-id="2273d-141">모든 **sqlcmd** 명령이 **Invoke-Sqlcmd**에서 구현되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-141">Not all of the **sqlcmd** commands are implemented in **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="2273d-142">구현되지 않는 명령으로는 **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**, **:serverlist**등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-142">Commands that are not implemented include the following: **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**, and **:serverlist**.</span></span>  
  
 <span data-ttu-id="2273d-143">**Invoke-Sqlcmd** 는 **sqlcmd** 환경 변수 또는 스크립팅 변수(예: SQLCMDDBNAME, SQLCMDWORKSTATION)를 초기화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-143">**Invoke-Sqlcmd** does not initialize the **sqlcmd** environment or scripting variables such as SQLCMDDBNAME or SQLCMDWORKSTATION.</span></span>  
  
 <span data-ttu-id="2273d-144">**Invoke-Sqlcmd** 는 Windows PowerShell **-Verbose** 공통 매개 변수를 지정해야 PRINT 문 출력과 같은 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-144">**Invoke-Sqlcmd** does not display messages, such as the output of PRINT statements, unless you specify the Windows PowerShell **-Verbose** common parameter.</span></span> <span data-ttu-id="2273d-145">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="2273d-145">For example:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 <span data-ttu-id="2273d-146">모든 **sqlcmd** 매개 변수가 PowerShell 환경에서 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-146">Not all of the **sqlcmd** parameters are needed in a PowerShell environment.</span></span> <span data-ttu-id="2273d-147">예를 들어 Windows PowerShell은 cmdlet의 모든 출력 서식을 지정하므로 서식 옵션을 지정하는 **sqlcmd** 매개 변수는 **Invoke-Sqlcmd**에서 구현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-147">For example, Windows PowerShell formats all output from cmdlets, so the **sqlcmd** parameters specifying formatting options are not implemented in **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="2273d-148">다음 표에서는 호출 하는 **sqlcmd** 매개 변수 및 **sqlcmd** 옵션 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2273d-148">The following table shows the relationship between the **Invoke-Sqlcmd** parameters and **sqlcmd** options:</span></span>  
  
|<span data-ttu-id="2273d-149">설명</span><span class="sxs-lookup"><span data-stu-id="2273d-149">Description</span></span>|<span data-ttu-id="2273d-150">sqlcmd 옵션</span><span class="sxs-lookup"><span data-stu-id="2273d-150">sqlcmd option</span></span>|<span data-ttu-id="2273d-151">Invoke-Sqlcmd 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2273d-151">Invoke-Sqlcmd parameter</span></span>|  
|-----------------|-------------------|------------------------------|  
|<span data-ttu-id="2273d-152">서버 및 인스턴스 이름</span><span class="sxs-lookup"><span data-stu-id="2273d-152">Server and instance name.</span></span>|<span data-ttu-id="2273d-153">-S</span><span class="sxs-lookup"><span data-stu-id="2273d-153">-S</span></span>|<span data-ttu-id="2273d-154">-ServerInstance</span><span class="sxs-lookup"><span data-stu-id="2273d-154">-ServerInstance</span></span>|  
|<span data-ttu-id="2273d-155">사용할 초기 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="2273d-155">The initial database to use.</span></span>|<span data-ttu-id="2273d-156">-d</span><span class="sxs-lookup"><span data-stu-id="2273d-156">-d</span></span>|<span data-ttu-id="2273d-157">-Database</span><span class="sxs-lookup"><span data-stu-id="2273d-157">-Database</span></span>|  
|<span data-ttu-id="2273d-158">지정된 쿼리 실행 후 종료</span><span class="sxs-lookup"><span data-stu-id="2273d-158">Run the specified query and exit.</span></span>|<span data-ttu-id="2273d-159">-Q</span><span class="sxs-lookup"><span data-stu-id="2273d-159">-Q</span></span>|<span data-ttu-id="2273d-160">-Query</span><span class="sxs-lookup"><span data-stu-id="2273d-160">-Query</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="2273d-161">인증 로그인 ID</span><span class="sxs-lookup"><span data-stu-id="2273d-161">Authentication login ID.</span></span>|<span data-ttu-id="2273d-162">-U</span><span class="sxs-lookup"><span data-stu-id="2273d-162">-U</span></span>|<span data-ttu-id="2273d-163">-Username</span><span class="sxs-lookup"><span data-stu-id="2273d-163">-Username</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="2273d-164">인증 암호</span><span class="sxs-lookup"><span data-stu-id="2273d-164">Authentication password.</span></span>|<span data-ttu-id="2273d-165">-P</span><span class="sxs-lookup"><span data-stu-id="2273d-165">-P</span></span>|<span data-ttu-id="2273d-166">-Password</span><span class="sxs-lookup"><span data-stu-id="2273d-166">-Password</span></span>|  
|<span data-ttu-id="2273d-167">변수 정의</span><span class="sxs-lookup"><span data-stu-id="2273d-167">Variable definition.</span></span>|<span data-ttu-id="2273d-168">-v</span><span class="sxs-lookup"><span data-stu-id="2273d-168">-v</span></span>|<span data-ttu-id="2273d-169">-Variable</span><span class="sxs-lookup"><span data-stu-id="2273d-169">-Variable</span></span>|  
|<span data-ttu-id="2273d-170">쿼리 제한 시간 간격</span><span class="sxs-lookup"><span data-stu-id="2273d-170">Query timeout interval.</span></span>|<span data-ttu-id="2273d-171">-t</span><span class="sxs-lookup"><span data-stu-id="2273d-171">-t</span></span>|<span data-ttu-id="2273d-172">-QueryTimeout</span><span class="sxs-lookup"><span data-stu-id="2273d-172">-QueryTimeout</span></span>|  
|<span data-ttu-id="2273d-173">오류 발생 시 실행 중지</span><span class="sxs-lookup"><span data-stu-id="2273d-173">Stop running on an error</span></span>|<span data-ttu-id="2273d-174">-b</span><span class="sxs-lookup"><span data-stu-id="2273d-174">-b</span></span>|<span data-ttu-id="2273d-175">-AbortOnError</span><span class="sxs-lookup"><span data-stu-id="2273d-175">-AbortOnError</span></span>|  
|<span data-ttu-id="2273d-176">관리자 전용 연결</span><span class="sxs-lookup"><span data-stu-id="2273d-176">Dedicated Administrator Connection.</span></span>|<span data-ttu-id="2273d-177">-A</span><span class="sxs-lookup"><span data-stu-id="2273d-177">-A</span></span>|<span data-ttu-id="2273d-178">-DedicatedAdministratorConnection</span><span class="sxs-lookup"><span data-stu-id="2273d-178">-DedicatedAdministratorConnection</span></span>|  
|<span data-ttu-id="2273d-179">대화형 명령, 시작 스크립트 및 환경 변수를 사용하지 않음</span><span class="sxs-lookup"><span data-stu-id="2273d-179">Disable interactive commands, startup script, and environment variables.</span></span>|<span data-ttu-id="2273d-180">-X</span><span class="sxs-lookup"><span data-stu-id="2273d-180">-X</span></span>|<span data-ttu-id="2273d-181">-DisableCommands</span><span class="sxs-lookup"><span data-stu-id="2273d-181">-DisableCommands</span></span>|  
|<span data-ttu-id="2273d-182">변수 대체를 사용하지 않음</span><span class="sxs-lookup"><span data-stu-id="2273d-182">Disable variable substitution.</span></span>|<span data-ttu-id="2273d-183">-X</span><span class="sxs-lookup"><span data-stu-id="2273d-183">-x</span></span>|<span data-ttu-id="2273d-184">-DisableVariables</span><span class="sxs-lookup"><span data-stu-id="2273d-184">-DisableVariables</span></span>|  
|<span data-ttu-id="2273d-185">보고할 최소 심각도 수준</span><span class="sxs-lookup"><span data-stu-id="2273d-185">Minimum severity level to report.</span></span>|<span data-ttu-id="2273d-186">-v</span><span class="sxs-lookup"><span data-stu-id="2273d-186">-V</span></span>|<span data-ttu-id="2273d-187">-SeverityLevel</span><span class="sxs-lookup"><span data-stu-id="2273d-187">-SeverityLevel</span></span>|  
|<span data-ttu-id="2273d-188">보고할 최소 오류 수준</span><span class="sxs-lookup"><span data-stu-id="2273d-188">Minimum error level to report.</span></span>|<span data-ttu-id="2273d-189">-M</span><span class="sxs-lookup"><span data-stu-id="2273d-189">-m</span></span>|<span data-ttu-id="2273d-190">-ErrorLevel</span><span class="sxs-lookup"><span data-stu-id="2273d-190">-ErrorLevel</span></span>|  
|<span data-ttu-id="2273d-191">로그인 제한 시간 간격</span><span class="sxs-lookup"><span data-stu-id="2273d-191">Login timeout interval.</span></span>|<span data-ttu-id="2273d-192">-l</span><span class="sxs-lookup"><span data-stu-id="2273d-192">-l</span></span>|<span data-ttu-id="2273d-193">-ConnectionTimeout</span><span class="sxs-lookup"><span data-stu-id="2273d-193">-ConnectionTimeout</span></span>|  
|<span data-ttu-id="2273d-194">호스트 이름</span><span class="sxs-lookup"><span data-stu-id="2273d-194">Hostname.</span></span>|<span data-ttu-id="2273d-195">-H</span><span class="sxs-lookup"><span data-stu-id="2273d-195">-H</span></span>|<span data-ttu-id="2273d-196">-HostName</span><span class="sxs-lookup"><span data-stu-id="2273d-196">-HostName</span></span>|  
|<span data-ttu-id="2273d-197">암호 변경 후 종료</span><span class="sxs-lookup"><span data-stu-id="2273d-197">Change password and exit.</span></span>|<span data-ttu-id="2273d-198">-Z</span><span class="sxs-lookup"><span data-stu-id="2273d-198">-Z</span></span>|<span data-ttu-id="2273d-199">-NewPassword</span><span class="sxs-lookup"><span data-stu-id="2273d-199">-NewPassword</span></span>|  
|<span data-ttu-id="2273d-200">쿼리가 포함된 입력 파일</span><span class="sxs-lookup"><span data-stu-id="2273d-200">Input file containing a query</span></span>|<span data-ttu-id="2273d-201">-i</span><span class="sxs-lookup"><span data-stu-id="2273d-201">-i</span></span>|<span data-ttu-id="2273d-202">-InputFile</span><span class="sxs-lookup"><span data-stu-id="2273d-202">-InputFile</span></span>|  
|<span data-ttu-id="2273d-203">최대 문자 출력 길이</span><span class="sxs-lookup"><span data-stu-id="2273d-203">Maximum length of character output.</span></span>|<span data-ttu-id="2273d-204">-w</span><span class="sxs-lookup"><span data-stu-id="2273d-204">-w</span></span>|<span data-ttu-id="2273d-205">-MaxCharLength</span><span class="sxs-lookup"><span data-stu-id="2273d-205">-MaxCharLength</span></span>|  
|<span data-ttu-id="2273d-206">최대 이진 출력 길이</span><span class="sxs-lookup"><span data-stu-id="2273d-206">Maximum length of binary output.</span></span>|<span data-ttu-id="2273d-207">-w</span><span class="sxs-lookup"><span data-stu-id="2273d-207">-w</span></span>|<span data-ttu-id="2273d-208">-MaxBinaryLength</span><span class="sxs-lookup"><span data-stu-id="2273d-208">-MaxBinaryLength</span></span>|  
|<span data-ttu-id="2273d-209">SSL 암호화를 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="2273d-209">Connect using SSL encryption.</span></span>|<span data-ttu-id="2273d-210">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-210">No parameter</span></span>|<span data-ttu-id="2273d-211">-EncryptConnection</span><span class="sxs-lookup"><span data-stu-id="2273d-211">-EncryptConnection</span></span>|  
|<span data-ttu-id="2273d-212">오류 표시</span><span class="sxs-lookup"><span data-stu-id="2273d-212">Display errors</span></span>|<span data-ttu-id="2273d-213">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-213">No parameter</span></span>|<span data-ttu-id="2273d-214">-OutputSqlErrors</span><span class="sxs-lookup"><span data-stu-id="2273d-214">-OutputSqlErrors</span></span>|  
|<span data-ttu-id="2273d-215">메시지를 stderr로 출력</span><span class="sxs-lookup"><span data-stu-id="2273d-215">Output messages to stderr.</span></span>|<span data-ttu-id="2273d-216">-r</span><span class="sxs-lookup"><span data-stu-id="2273d-216">-r</span></span>|<span data-ttu-id="2273d-217">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-217">No parameter</span></span>|  
|<span data-ttu-id="2273d-218">클라이언트의 국가별 설정 사용</span><span class="sxs-lookup"><span data-stu-id="2273d-218">Use client's regional settings</span></span>|<span data-ttu-id="2273d-219">-R</span><span class="sxs-lookup"><span data-stu-id="2273d-219">-R</span></span>|<span data-ttu-id="2273d-220">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-220">No parameter</span></span>|  
|<span data-ttu-id="2273d-221">지정된 쿼리 실행 후 실행 중인 상태로 유지</span><span class="sxs-lookup"><span data-stu-id="2273d-221">Run the specified query and remain running.</span></span>|<span data-ttu-id="2273d-222">-Q</span><span class="sxs-lookup"><span data-stu-id="2273d-222">-q</span></span>|<span data-ttu-id="2273d-223">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-223">No parameter</span></span>|  
|<span data-ttu-id="2273d-224">출력 데이터에 사용할 코드 페이지</span><span class="sxs-lookup"><span data-stu-id="2273d-224">Code page to use for output data.</span></span>|<span data-ttu-id="2273d-225">-f</span><span class="sxs-lookup"><span data-stu-id="2273d-225">-f</span></span>|<span data-ttu-id="2273d-226">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-226">No parameter</span></span>|  
|<span data-ttu-id="2273d-227">암호 변경 후 실행 중인 상태로 유지</span><span class="sxs-lookup"><span data-stu-id="2273d-227">Change a password and remain running</span></span>|<span data-ttu-id="2273d-228">-Z</span><span class="sxs-lookup"><span data-stu-id="2273d-228">-z</span></span>|<span data-ttu-id="2273d-229">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-229">No parameter</span></span>|  
|<span data-ttu-id="2273d-230">패킷 크기</span><span class="sxs-lookup"><span data-stu-id="2273d-230">Packet size</span></span>|<span data-ttu-id="2273d-231">지정하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="2273d-231">-a</span></span>|<span data-ttu-id="2273d-232">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-232">No parameter</span></span>|  
|<span data-ttu-id="2273d-233">열 구분 기호</span><span class="sxs-lookup"><span data-stu-id="2273d-233">Column separator</span></span>|<span data-ttu-id="2273d-234">-S</span><span class="sxs-lookup"><span data-stu-id="2273d-234">-s</span></span>|<span data-ttu-id="2273d-235">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-235">No parameter</span></span>|  
|<span data-ttu-id="2273d-236">출력 헤더 제어</span><span class="sxs-lookup"><span data-stu-id="2273d-236">Control output headers</span></span>|<span data-ttu-id="2273d-237">-H</span><span class="sxs-lookup"><span data-stu-id="2273d-237">-h</span></span>|<span data-ttu-id="2273d-238">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-238">No parameter</span></span>|  
|<span data-ttu-id="2273d-239">제어 문자 지정</span><span class="sxs-lookup"><span data-stu-id="2273d-239">Specify control characters</span></span>|<span data-ttu-id="2273d-240">-k</span><span class="sxs-lookup"><span data-stu-id="2273d-240">-k</span></span>|<span data-ttu-id="2273d-241">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-241">No parameter</span></span>|  
|<span data-ttu-id="2273d-242">고정 길이 표시 너비</span><span class="sxs-lookup"><span data-stu-id="2273d-242">Fixed length display width</span></span>|<span data-ttu-id="2273d-243">-y</span><span class="sxs-lookup"><span data-stu-id="2273d-243">-Y</span></span>|<span data-ttu-id="2273d-244">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-244">No parameter</span></span>|  
|<span data-ttu-id="2273d-245">변수 길이 표시 너비</span><span class="sxs-lookup"><span data-stu-id="2273d-245">Variable length display width</span></span>|<span data-ttu-id="2273d-246">-y</span><span class="sxs-lookup"><span data-stu-id="2273d-246">-y</span></span>|<span data-ttu-id="2273d-247">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-247">No parameter</span></span>|  
|<span data-ttu-id="2273d-248">입력 에코</span><span class="sxs-lookup"><span data-stu-id="2273d-248">Echo input</span></span>|<span data-ttu-id="2273d-249">-E</span><span class="sxs-lookup"><span data-stu-id="2273d-249">-e</span></span>|<span data-ttu-id="2273d-250">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-250">No parameter</span></span>|  
|<span data-ttu-id="2273d-251">따옴표 붙은 식별자 사용</span><span class="sxs-lookup"><span data-stu-id="2273d-251">Enable quoted identifiers</span></span>|<span data-ttu-id="2273d-252">-I</span><span class="sxs-lookup"><span data-stu-id="2273d-252">-I</span></span>|<span data-ttu-id="2273d-253">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-253">No parameter</span></span>|  
|<span data-ttu-id="2273d-254">후행 공백 제거</span><span class="sxs-lookup"><span data-stu-id="2273d-254">Remove trailing spaces</span></span>|<span data-ttu-id="2273d-255">-w</span><span class="sxs-lookup"><span data-stu-id="2273d-255">-W</span></span>|<span data-ttu-id="2273d-256">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-256">No parameter</span></span>|  
|<span data-ttu-id="2273d-257">인스턴스 나열</span><span class="sxs-lookup"><span data-stu-id="2273d-257">List instances</span></span>|<span data-ttu-id="2273d-258">-l</span><span class="sxs-lookup"><span data-stu-id="2273d-258">-L</span></span>|<span data-ttu-id="2273d-259">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-259">No parameter</span></span>|  
|<span data-ttu-id="2273d-260">출력을 유니코드 형식으로 지정</span><span class="sxs-lookup"><span data-stu-id="2273d-260">Format output as Unicode</span></span>|<span data-ttu-id="2273d-261">-U</span><span class="sxs-lookup"><span data-stu-id="2273d-261">-u</span></span>|<span data-ttu-id="2273d-262">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-262">No parameter</span></span>|  
|<span data-ttu-id="2273d-263">통계 인쇄</span><span class="sxs-lookup"><span data-stu-id="2273d-263">Print statistics</span></span>|<span data-ttu-id="2273d-264">-p</span><span class="sxs-lookup"><span data-stu-id="2273d-264">-p</span></span>|<span data-ttu-id="2273d-265">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-265">No parameter</span></span>|  
|<span data-ttu-id="2273d-266">명령 종료</span><span class="sxs-lookup"><span data-stu-id="2273d-266">Command end</span></span>|<span data-ttu-id="2273d-267">-c</span><span class="sxs-lookup"><span data-stu-id="2273d-267">-c</span></span>|<span data-ttu-id="2273d-268">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-268">No parameter</span></span>|  
|<span data-ttu-id="2273d-269">Windows 인증을 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="2273d-269">Connect using Windows Authentication</span></span>|<span data-ttu-id="2273d-270">-E</span><span class="sxs-lookup"><span data-stu-id="2273d-270">-E</span></span>|<span data-ttu-id="2273d-271">매개 변수 없음</span><span class="sxs-lookup"><span data-stu-id="2273d-271">No parameter</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2273d-272">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2273d-272">See Also</span></span>  
 <span data-ttu-id="2273d-273">[데이터베이스 엔진 cmdlet 사용](../../2014/database-engine/use-the-database-engine-cmdlets.md) </span><span class="sxs-lookup"><span data-stu-id="2273d-273">[Use the Database Engine cmdlets](../../2014/database-engine/use-the-database-engine-cmdlets.md) </span></span>  
 <span data-ttu-id="2273d-274">[sqlcmd 유틸리티](../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2273d-274">[sqlcmd Utility](../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="2273d-275">sqlcmd 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="2273d-275">Use the sqlcmd Utility</span></span>](../relational-databases/scripting/sqlcmd-use-the-utility.md)  