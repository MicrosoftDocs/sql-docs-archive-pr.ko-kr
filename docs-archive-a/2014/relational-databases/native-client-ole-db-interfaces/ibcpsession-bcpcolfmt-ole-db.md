---
title: IBCPSession::BCPColFmt(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: rothja
ms.author: jroth
ms.openlocfilehash: d60fa5dc93473f477926719cdcc05d13e72d8fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739831"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a><span data-ttu-id="222cd-102">IBCPSession::BCPColFmt(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="222cd-102">IBCPSession::BCPColFmt (OLE DB)</span></span>
  <span data-ttu-id="222cd-103">프로그램 변수와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 간의 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-103">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222cd-104">구문</span><span class="sxs-lookup"><span data-stu-id="222cd-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a><span data-ttu-id="222cd-105">설명</span><span class="sxs-lookup"><span data-stu-id="222cd-105">Remarks</span></span>  
 <span data-ttu-id="222cd-106">**BCPColFmt** 메서드는 BCP 데이터 파일 필드와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 간의 바인딩을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-106">The **BCPColFmt** method is used to create a binding between BCP data file fields and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span> <span data-ttu-id="222cd-107">열의 길이, 유형, 종결자 및 접두사 길이를 매개 변수로 사용하고 개별 필드에 대해 이러한 각 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-107">It takes in the length, type, terminator, and prefix length of a column as parameters and sets each of these properties for individual fields.</span></span>  
  
 <span data-ttu-id="222cd-108">사용자가 대화형 모드를 선택하면 이 메서드가 두 번 호출됩니다. 서버 열의 유형을 기반으로 하는 기본값에 따라 열 형식을 설정하기 위해 한 번 호출되고, 대화형 모드에서 각 열에 대해 선택된 클라이언트의 열 유형에 따라 형식을 설정하기 위해 한 번 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-108">If the user chooses interactive mode, this method is called twice; once to set the column format according to the default values (which are according to the type of the server column), and once to set the format according to the column type of the choice of the client chosen during interactive mode, for each column.</span></span>  
  
 <span data-ttu-id="222cd-109">비대화형 모드에서는 열당 한 번만 호출되어 각 열의 유형을 문자 또는 네이티브 유형으로 설정하고 열과 행 종결자를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-109">In non-interactive modes, it is called only once per column to set the type of each column to character or native type, and to set the column and row terminators.</span></span>  
  
 <span data-ttu-id="222cd-110">**BCPColFmt** 메서드를 사용하여 대량 복사에 사용할 사용자 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-110">The **BCPColFmt** method allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="222cd-111">대량 복사의 경우 형식에는 다음과 같은 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-111">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="222cd-112">사용자 파일 필드에서 데이터베이스 열로의 매핑</span><span class="sxs-lookup"><span data-stu-id="222cd-112">A mapping from user-file fields to database columns.</span></span>  
  
-   <span data-ttu-id="222cd-113">각 사용자 파일 필드의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="222cd-113">The data type of each user-file field.</span></span>  
  
-   <span data-ttu-id="222cd-114">각 필드에 대한 표시기(옵션)의 길이</span><span class="sxs-lookup"><span data-stu-id="222cd-114">The length of the optional indicator for each field.</span></span>  
  
-   <span data-ttu-id="222cd-115">사용자 파일 필드당 최대 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="222cd-115">The maximum length of data per user-file field.</span></span>  
  
-   <span data-ttu-id="222cd-116">각 필드에 대한 종결 바이트 시퀀스(옵션)</span><span class="sxs-lookup"><span data-stu-id="222cd-116">The optional terminating byte sequence for each field.</span></span>  
  
-   <span data-ttu-id="222cd-117">선택 사항인 종결 바이트 시퀀스의 길이</span><span class="sxs-lookup"><span data-stu-id="222cd-117">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="222cd-118">**BCPColFmt** 에 대한 각 호출에서는 사용자 파일의 한 필드에 대한 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-118">Each call to **BCPColFmt** specifies the format for one user-file field.</span></span> <span data-ttu-id="222cd-119">예를 들어 다섯 개의 필드로 구성된 사용자 데이터 파일에서 세 필드의 기본 설정을 변경하려면 먼저 `BCPColumns(5)`를 호출한 다음 **BCPColFmt** 를 다섯 번 호출합니다. 이 중 세 번의 호출에서 사용자 지정 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-119">For example, to change the default settings for three fields in a five-field user data file, first call `BCPColumns(5)`, and then call **BCPColFmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="222cd-120">나머지 두 번의 호출에서는 *eUserDataType* 을 BCP_TYPE_DEFAULT로 설정하고 *cbIndicator*, *cbUserData*및 *cbUserDataTerm* 을 각각 0, BCP_VARIABLE_LENGTH 및 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-120">For the remaining two calls, set *eUserDataType* to BCP_TYPE_DEFAULT, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, BCP_VARIABLE_LENGTH, and 0 respectively.</span></span> <span data-ttu-id="222cd-121">이 프로시저는 다섯 개의 열을 모두 복사하는데 이 중 세 개는 사용자 지정된 형식으로, 두 개는 기본 형식으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-121">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="222cd-122">[BCPColFmt](ibcpsession-bcpcolumns-ole-db.md)가 호출되기 전에 **IBCPSession::BCPColumns** 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-122">The [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) method must be called before any calls to **BCPColFmt**.</span></span> <span data-ttu-id="222cd-123">사용자 파일에 있는 각 열에 대해 **BCPColFmt** 를 한 번씩 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-123">You must call **BCPColFmt** once for each column in the user file.</span></span> <span data-ttu-id="222cd-124">사용자 파일의 열에 대해 **BCPColFmt** 를 두 번 이상 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-124">Calling **BCPColFmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="222cd-125">사용자 파일의 모든 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 복사할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-125">You do not have to copy all of the data in a user file to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="222cd-126">열을 건너뛰려면 idxServerCol 매개 변수를 0으로 설정하여 해당 열의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-126">To skip a column, specify the format of the data for the column setting the idxServerCol parameter to 0.</span></span> <span data-ttu-id="222cd-127">필드를 건너뛰려는 경우에도 메서드가 제대로 작동하려면 모든 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-127">In order to skip a field, you still need all the information for the method to work correctly.</span></span>  
  
 <span data-ttu-id="222cd-128">**참고**[IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 함수를 사용하여 **BCPColFmt**를 통해 제공된 형식 지정을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-128">**Note** The [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) function can be used to persist the format specification provided through **BCPColFmt**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="222cd-129">인수</span><span class="sxs-lookup"><span data-stu-id="222cd-129">Arguments</span></span>  
 <span data-ttu-id="222cd-130">*idxUserDataCol*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-130">*idxUserDataCol*[in]</span></span>  
 <span data-ttu-id="222cd-131">사용자 데이터 파일에 포함된 필드의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-131">Index of field in the user's data file.</span></span>  
  
 <span data-ttu-id="222cd-132">*eUserDataType*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-132">*eUserDataType*[in]</span></span>  
 <span data-ttu-id="222cd-133">사용자 데이터 파일에 포함된 필드의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-133">The data type of field in the user's data file.</span></span> <span data-ttu-id="222cd-134">사용 가능한 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 헤더 파일(sqlncli.h)에 BCP_TYPE_XXX 형식으로 표시됩니다(예: BCP_TYPE_SQLINT4).</span><span class="sxs-lookup"><span data-stu-id="222cd-134">The data types available are listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h) with BCP_TYPE_XXX format, for example, BCP_TYPE_SQLINT4.</span></span> <span data-ttu-id="222cd-135">BCP_TYPE_DEFAULT 값을 지정하면 공급자는 테이블 또는 뷰 열 유형과 동일한 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-135">If the BCP_TYPE_DEFAULT value is specified, the provider tries to use the same type as the table or view column type.</span></span> <span data-ttu-id="222cd-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `eUserDataType` 인수를 BCP_TYPE_SQLDECIMAL 하거나 BCP_TYPE_SQLNUMERIC 때 파일에 대 한 대량 복사 작업의 경우:</span><span class="sxs-lookup"><span data-stu-id="222cd-136">For bulk copy operations out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and into a file when the `eUserDataType` argument is BCP_TYPE_SQLDECIMAL or BCP_TYPE_SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="222cd-137">원본 열이 decimal 또는 numeric이 아니면 기본 전체 자릿수 및 소수 자릿수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-137">If the source column is not decimal or numeric, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="222cd-138">원본 열이 decimal 또는 numeric이면 원본 열의 전체 자릿수 및 소수 자릿수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-138">If the source column is decimal or numeric, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="222cd-139">*cbIndicator*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-139">*cbIndicator*[in]</span></span>  
 <span data-ttu-id="222cd-140">필드의 접두사 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-140">Prefix length for the field.</span></span> <span data-ttu-id="222cd-141">기본값은 BCP_PREFIX_DEFAULT입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-141">The default is BCP_PREFIX_DEFAULT.</span></span> <span data-ttu-id="222cd-142">유효한 접두사 길이는 0, 1, 2, 4 및 8입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-142">The valid lengths for the prefix are 0, 1, 2, 4 and 8.</span></span> <span data-ttu-id="222cd-143">접두사 크기 8은 주로 필드가 청크되었음을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-143">A prefix size of 8 is most commonly used to indicate that the field is chunked.</span></span> <span data-ttu-id="222cd-144">이 값은 큰 값 형식 열을 효율적으로 대량 복사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-144">This is used for efficiently bulk copying large value type columns.</span></span>  
  
 <span data-ttu-id="222cd-145">*cbUserData*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-145">*cbUserData*[in]</span></span>  
 <span data-ttu-id="222cd-146">길이 표시기나 종결자의 길이를 제외한 사용자 파일에 있는 이 필드 데이터의 최대 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-146">The maximum length, in bytes, of this field's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="222cd-147">`cbUserData`BCP_LENGTH_NULL로 설정 하면 데이터 파일 필드의 모든 값이 이거나 NULL로 설정 되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-147">Setting `cbUserData` to BCP_LENGTH_NULL indicates that all values in the data file fields are, or should be set to NULL.</span></span> <span data-ttu-id="222cd-148">`cbUserData`BCP_LENGTH_VARIABLE로 설정 하면 시스템에서 각 필드에 대 한 데이터의 길이를 확인 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-148">Setting `cbUserData` to BCP_LENGTH_VARIABLE indicates that the system should determine the length of data for each field.</span></span> <span data-ttu-id="222cd-149">일부 필드의 경우 이 설정은 길이 또는 Null 표시기가 생성되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복사되는 복사본의 데이터 앞에 추가됨을 의미하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사되는 데이터에 표시기가 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-149">For some fields, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="222cd-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]문자 및 이진 데이터 형식의 경우은 `cbUserData` BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 또는 양수 값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-150">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, `cbUserData` can be BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0, or some positive value.</span></span> <span data-ttu-id="222cd-151">`cbUserData`가 BCP_LENGTH_VARIABLE 경우 시스템은 길이 표시기 (있는 경우) 또는 종결자 시퀀스를 사용 하 여 데이터 길이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-151">If `cbUserData` is BCP_LENGTH_VARIABLE, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="222cd-152">길이 표시기와 종결자 시퀀스를 모두 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-152">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="222cd-153">`cbUserData`이 BCP_LENGTH_VARIABLE 경우 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 또는 이진 형식이 고 길이 표시기 나 종결자 시퀀스를 모두 지정 하지 않으면 시스템에서 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-153">If `cbUserData` is BCP_LENGTH_VARIABLE, the data type is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and if neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="222cd-154">`cbUserData`가 0 또는 양수 값 이면 시스템은를 `cbUserData` 최대 데이터 길이로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-154">If `cbUserData` is 0 or a positive value, the system uses `cbUserData` as the maximum data length.</span></span> <span data-ttu-id="222cd-155">그러나 양수 `cbUserData` , 길이 표시자 또는 종결자 시퀀스가 제공 되는 경우 시스템은 복사할 데이터가 적은 방법을 사용 하 여 데이터 길이를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-155">However, if, in addition to a positive `cbUserData`, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="222cd-156">`cbUserData`데이터의 바이트 수를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-156">The `cbUserData` value represents the count of bytes of data.</span></span> <span data-ttu-id="222cd-157">문자 데이터가 유니코드 와이드 문자로 표현 되는 경우 양의 `cbUserData` 매개 변수 값은 문자 수와 각 문자의 크기 (바이트)를 곱한 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-157">If character data is represented by Unicode wide characters, then a positive `cbUserData` parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="222cd-158">*pbUserDataTerm*[size_is][in]</span><span class="sxs-lookup"><span data-stu-id="222cd-158">*pbUserDataTerm*[size_is][in]</span></span>  
 <span data-ttu-id="222cd-159">이 필드에 사용할 종결자 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-159">The terminator sequence to be used for the field.</span></span> <span data-ttu-id="222cd-160">이 매개 변수는 주로 문자 데이터 형식에 유용한데 그 이유는 다른 모든 형식은 길이가 고정되어 있거나 이진 데이터의 경우 현재 바이트 수를 정확하게 기록하기 위해 길이 표시기가 필요하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-160">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="222cd-161">추출한 데이터가 종결되지 않도록 하거나 사용자 파일의 데이터가 종결되지 않았음을 나타내려면 이 매개 변수를 NULL로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="222cd-161">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="222cd-162">종결자와 길이 표시기를 사용하거나 종결자와 최대 열 길이를 사용하는 등 두 가지 이상의 방법을 사용하여 사용자 파일 열 길이를 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-162">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="222cd-163">대량 복사 API는 필요한 경우 유니코드에서 MBCS로의 문자 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-163">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="222cd-164">종결자 바이트 문자열 및 바이트 문자열 길이가 모두 올바르게 설정되도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-164">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="222cd-165">*cbUserDataTerm*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-165">*cbUserDataTerm*[in]</span></span>  
 <span data-ttu-id="222cd-166">이 열에 사용할 종결자 시퀀스의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-166">The length, in bytes, of the terminator sequence to be used for the column.</span></span> <span data-ttu-id="222cd-167">종결자가 없거나 데이터에 필요하지 않은 경우 이 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-167">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="222cd-168">*idxServerCol*[in]</span><span class="sxs-lookup"><span data-stu-id="222cd-168">*idxServerCol*[in]</span></span>  
 <span data-ttu-id="222cd-169">데이터베이스 테이블에서 열의 서수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-169">The ordinal position of the column in the database table.</span></span> <span data-ttu-id="222cd-170">첫 번째 열 번호는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-170">The first column number is 1.</span></span> <span data-ttu-id="222cd-171">열의 서수 위치는 **IColumnsInfo::GetColumnInfo** 또는 이와 유사한 메서드를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-171">The ordinal position of a column is reported by **IColumnsInfo::GetColumnInfo** or similar methods.</span></span> <span data-ttu-id="222cd-172">이 값이 0이면 대량 복사에서 데이터 파일의 필드를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-172">If this value is 0, bulk copy ignores the field in the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="222cd-173">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="222cd-173">Return Code Values</span></span>  
 <span data-ttu-id="222cd-174">S_OK</span><span class="sxs-lookup"><span data-stu-id="222cd-174">S_OK</span></span>  
 <span data-ttu-id="222cd-175">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-175">The method succeeded.</span></span>  
  
 <span data-ttu-id="222cd-176">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="222cd-176">E_FAIL</span></span>  
 <span data-ttu-id="222cd-177">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="222cd-177">A provider specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="222cd-178">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="222cd-178">E_UNEXPECTED</span></span>  
 <span data-ttu-id="222cd-179">예기치 않은 메서드가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-179">The call to the method was unexpected.</span></span> <span data-ttu-id="222cd-180">예를 들어 이 메서드를 호출하기 전에 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 메서드를 호출하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-180">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
 <span data-ttu-id="222cd-181">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="222cd-181">E_INVALIDARG</span></span>  
 <span data-ttu-id="222cd-182">잘못된 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-182">The argument was invalid.</span></span>  
  
 <span data-ttu-id="222cd-183">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="222cd-183">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="222cd-184">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="222cd-184">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222cd-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="222cd-185">See Also</span></span>  
 <span data-ttu-id="222cd-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="222cd-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="222cd-187">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="222cd-187">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  