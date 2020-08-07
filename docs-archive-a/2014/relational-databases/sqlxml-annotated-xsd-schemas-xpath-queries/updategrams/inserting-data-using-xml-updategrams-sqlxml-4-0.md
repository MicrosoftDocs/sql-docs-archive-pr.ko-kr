---
title: XML Updategrams을 사용 하 여 데이터 삽입 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: rothja
ms.author: jroth
ms.openlocfilehash: a80f2cb157e59f30ebcbff5c14abba1003de9e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732448"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="28168-102">XML Updategram을 사용하여 데이터 삽입(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="28168-102">Inserting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="28168-103">Updategram는 레코드 인스턴스가 블록에 나타나지만 **\<after>** 해당 블록에는 없는 경우 삽입 작업을 나타냅니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="28168-103">An updategram indicates an insert operation when a record instance appears in the **\<after>** block but not in the corresponding **\<before>** block.</span></span> <span data-ttu-id="28168-104">이 경우 updategram은 블록의 레코드를 **\<after>** 데이터베이스에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-104">In this case, the updategram inserts the record in the **\<after>** block into the database.</span></span>  
  
 <span data-ttu-id="28168-105">삽입 작업에 대한 Updategram 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-105">This is the updategram format for an insert operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a><span data-ttu-id="28168-106">\<before>거부</span><span class="sxs-lookup"><span data-stu-id="28168-106">\<before> Block</span></span>  
 <span data-ttu-id="28168-107">**\<before>** 삽입 작업에 대해 블록을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-107">The **\<before>** block can be omitted for an insert operation.</span></span> <span data-ttu-id="28168-108">선택적 특성을 `mapping-schema` 지정 하지 않으면 **\<ElementName>** updategram에 지정 된가 데이터베이스 테이블에 매핑되고 자식 요소 또는 특성은 테이블의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-108">If the optional `mapping-schema` attribute is not specified, the **\<ElementName>** that is specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
## <a name="after-block"></a><span data-ttu-id="28168-109">\<after>거부</span><span class="sxs-lookup"><span data-stu-id="28168-109">\<after> Block</span></span>  
 <span data-ttu-id="28168-110">블록에서 하나 이상의 레코드를 지정할 수 있습니다 **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="28168-110">You can specify one or more records in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="28168-111">**\<after>** 블록이 특정 열에 대 한 값을 제공 하지 않으면 updategram는 주석이 지정 된 스키마 (스키마가 지정 된 경우)에 지정 된 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-111">If the **\<after>** block does not supply a value for a particular column, the updategram uses the default value that is specified in the annotated schema (if a schema has been specified).</span></span> <span data-ttu-id="28168-112">스키마가 열의 기본값을 지정 하지 않는 경우 updategram는이 열에 명시적 값을 지정 하지 않고 대신 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본값 (지정 된 경우)을이 열에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-112">If the schema does not specify a default value for the column, the updategram does not specify any explicit value to this column and, instead, assigns the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value (if specified) to this column.</span></span> <span data-ttu-id="28168-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본값이 없고 열에서 NULL 값을 허용하는 경우 Updategram에서 열 값을 NULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-113">If there is no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value and the column accepts a NULL value, the updategram sets the column value to NULL.</span></span> <span data-ttu-id="28168-114">열에 기본값이 없고 NULL 값을 허용하지도 않는 경우 명령이 실패하고 Updategram에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-114">If the column neither has a default value nor accepts a NULL value, the command fails and the updategram returns an error.</span></span> <span data-ttu-id="28168-115">선택적 `updg:returnid` 특성은 IDENTITY 유형 열이 있는 테이블에 레코드가 추가될 때 시스템에서 생성하는 ID 값을 반환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-115">The optional `updg:returnid` attribute is used to return the identity value that is generated by the system when a record is added in a table with an IDENTITY-type column.</span></span>  
  
## <a name="updgid-attribute"></a><span data-ttu-id="28168-116">updg:id 특성</span><span class="sxs-lookup"><span data-stu-id="28168-116">updg:id Attribute</span></span>  
 <span data-ttu-id="28168-117">Updategram에서 레코드만 삽입하는 경우에는 `updg:id` 특성이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-117">If the updategram is inserting only records, the updategram does not require the `updg:id` attribute.</span></span> <span data-ttu-id="28168-118">에 대 한 자세한 내용은 `updg:id` [XML Updategrams을 사용 하 여 데이터 업데이트 &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-118">For more information about `updg:id`, see [Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="updgat-identity-attribute"></a><span data-ttu-id="28168-119">updg:at-identity 특성</span><span class="sxs-lookup"><span data-stu-id="28168-119">updg:at-identity Attribute</span></span>  
 <span data-ttu-id="28168-120">Updategram은 IDENTITY 유형 열이 있는 테이블에 레코드를 삽입할 때 선택적 `updg:at-identity` 특성을 사용하여 시스템에서 할당된 값을 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-120">When an updategram inserts a record in a table that has an IDENTITY-type column, the updategram can capture the system assigned value by using the optional `updg:at-identity` attribute.</span></span> <span data-ttu-id="28168-121">Updategram은 이 값을 이후 작업에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-121">The updategram can then use this value in subsequent operations.</span></span> <span data-ttu-id="28168-122">Updategram을 실행할 때 `updg:returnid` 특성을 지정하여 생성된 ID 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-122">Upon execution of the updategram, you can return the identity value that is generated by specifying the `updg:returnid` attribute.</span></span>  
  
## <a name="updgguid-attribute"></a><span data-ttu-id="28168-123">updg:guid 특성</span><span class="sxs-lookup"><span data-stu-id="28168-123">updg:guid Attribute</span></span>  
 <span data-ttu-id="28168-124">`updg:guid` 특성은 GUID(Globally Unique Identifier)를 생성하는 선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-124">The `updg:guid` attribute is an optional attribute that generates a globally unique identifier.</span></span> <span data-ttu-id="28168-125">이 값은 지정 된 전체 블록의 범위 내에 유지 됩니다 **\<sync>** .</span><span class="sxs-lookup"><span data-stu-id="28168-125">This value remains in scope for the entire **\<sync>** block in which it is specified.</span></span> <span data-ttu-id="28168-126">블록의 아무 곳에서 나이 값을 사용할 수 있습니다 **\<sync>** .</span><span class="sxs-lookup"><span data-stu-id="28168-126">You can use this value anywhere in the **\<sync>** block.</span></span> <span data-ttu-id="28168-127">특성은 함수를 호출 `NEWGUID()` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 하 여 고유 식별자를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-127">The attribute calls the `NEWGUID()`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] function to generate the unique identifier.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="28168-128">예제</span><span class="sxs-lookup"><span data-stu-id="28168-128">Examples</span></span>  
 <span data-ttu-id="28168-129">다음 예제를 사용 하 여 작업 예제를 만들려면 [SQLXML 예를 실행 하기 위한 요구 사항](../../sqlxml/requirements-for-running-sqlxml-examples.md)에 지정 된 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-129">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="28168-130">Updategram 예를 사용하기 전에 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="28168-130">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="28168-131">대부분의 예에서는 기본 매핑을 사용합니다. 즉, Updategram에 매핑 스키마가 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-131">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="28168-132">매핑 스키마를 사용 하는 updategram의 추가 예제는 [Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정 ](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-132">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="28168-133">대부분의 예에서는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-133">Most of the examples use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="28168-134">모든 업데이트는 이 데이터베이스의 테이블에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-134">All the updates are applied to the tables in this database.</span></span>  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a><span data-ttu-id="28168-135">A.</span><span class="sxs-lookup"><span data-stu-id="28168-135">A.</span></span> <span data-ttu-id="28168-136">Updategram을 사용하여 단일 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="28168-136">Inserting a record by using an updategram</span></span>  
 <span data-ttu-id="28168-137">이 특성 중심 Updategram은 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스의 HumanResources.Employee 테이블에 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-137">This attribute-centric updategram inserts a record in the HumanResources.Employee table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="28168-138">이 예에서 Updategram은 매핑 스키마를 지정하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="28168-138">In this example, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="28168-139">요소 이름은 테이블 이름에 매핑되고 특성 또는 자식 요소는 해당 테이블의 열에 매핑되는 기본 매핑을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-139">Therefore, the updategram uses default mapping, in which the element name maps to a table name and the attributes or child elements map to columns in that table.</span></span>  
  
 <span data-ttu-id="28168-140">HumanResources.Department 테이블에 대한 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 스키마는 모든 열에 'not null' 제한을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-140">The [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] schema for the HumanResources.Department table imposes a 'not null' restriction on all columns.</span></span> <span data-ttu-id="28168-141">따라서 Updategram은 모든 열에 대해 지정된 값을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-141">Therefore, the updategram must include values specified for all columns.</span></span> <span data-ttu-id="28168-142">DepartmentID는 IDENTITY 유형 열입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-142">The DepartmentID is an IDENTITY-type column.</span></span> <span data-ttu-id="28168-143">따라서 해당 값이 지정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-143">Therefore, no values are specified for it.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="28168-144">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="28168-145">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-145">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-146">파일을 MyUpdategram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-146">Save the file as MyUpdategram.xml.</span></span>  
  
2.  <span data-ttu-id="28168-147">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-147">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="28168-148">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-148">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="28168-149">요소 중심 매핑에서 Updategram은 다음과 같이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="28168-149">In an element-centric mapping, the updategram looks like this:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-150">혼합 모드(요소 중심 및 특성 중심) Updategram에서 요소는 다음 Updategram과 같이 특성과 하위 요소를 모두 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-150">In a mixed-mode (element-centric and attribute-centric) updategram, an element can have both attributes and subelements, as shown in this updategram:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a><span data-ttu-id="28168-151">B.</span><span class="sxs-lookup"><span data-stu-id="28168-151">B.</span></span> <span data-ttu-id="28168-152">Updategram을 사용하여 여러 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="28168-152">Inserting multiple records by using an updategram</span></span>  
 <span data-ttu-id="28168-153">이 Updategram은 HumanResources.Shift 테이블에 새 근무조 레코드 두 개를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-153">This updategram adds two new shift records to the HumanResources.Shift table.</span></span> <span data-ttu-id="28168-154">Updategram는 선택적 블록을 지정 하지 않습니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="28168-154">The updategram does not specify the optional **\<before>** block.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="28168-155">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-155">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="28168-156">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-156">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-157">파일을 Updategram-AddShifts.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-157">Save the file as Updategram-AddShifts.xml.</span></span>  
  
2.  <span data-ttu-id="28168-158">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="28168-159">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="28168-160">이 예제의 또 다른 버전은 **\<after>** 두 개의 직원을 삽입 하는 한 블록 대신 별도의 두 블록을 사용 하는 updategram입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-160">Another version of this example is an updategram that uses two separate **\<after>** blocks instead of one block to insert the two employees.</span></span> <span data-ttu-id="28168-161">이 작업은 유효하며 다음과 같이 인코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-161">This is valid and can be encoded as follows:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a><span data-ttu-id="28168-162">C.</span><span class="sxs-lookup"><span data-stu-id="28168-162">C.</span></span> <span data-ttu-id="28168-163">유효한 XML이 아닌 유효한 SQL Server 문자 작업</span><span class="sxs-lookup"><span data-stu-id="28168-163">Working with valid SQL Server characters that are not valid in XML</span></span>  
 <span data-ttu-id="28168-164">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 테이블 이름은 Northwind 데이터베이스의 Order Details 테이블과 같이 공백을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-164">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space, such as the Order Details table in the Northwind database.</span></span> <span data-ttu-id="28168-165">그러나 잘못 된 식별자 인 XML 문자는 유효 하지 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 않지만 잘못 된 xml 식별자는 ' __xHHHH '를 인코딩 값으로 사용 하 여 인코딩할 수 있습니다 \_ \_ . 여기서 HHHH는 가장 중요 한 비트 우선 순서로 문자에 대 한 4 자리 16 진수 UCS-2 코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28168-165">However, this is not valid in XML characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but not valid XML identifiers can be encoded using '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28168-166">이 예에서는 Northwind 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-166">This example uses the Northwind database.</span></span> <span data-ttu-id="28168-167">이 [Microsoft 웹 사이트](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)에서 다운로드할 수 있는 SQL 스크립트를 사용 하 여 Northwind 데이터베이스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-167">You can install the Northwind database by using an SQL script available for download from this [Microsoft Web site](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="28168-168">또한 요소 이름을 대괄호([ ])로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-168">Also, the element name must be enclosed within brackets ([ ]).</span></span> <span data-ttu-id="28168-169">XML에서 [및] 문자는 유효 하지 않으므로 각각 _x005B 및 _x005D로 인코딩해야 합니다 \_ \_ .</span><span class="sxs-lookup"><span data-stu-id="28168-169">Because the characters [and] are not valid in XML, you must encode them as _x005B\_ and _x005D\_, respectively.</span></span> <span data-ttu-id="28168-170">매핑 스키마를 사용하는 경우 공백과 같은 유효하지 않은 문자가 포함된 요소 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-170">(If you use a mapping schema, you can provide element names that do not contain characters that are not valid, such as white spaces.</span></span> <span data-ttu-id="28168-171">매핑 스키마에서 필요한 매핑을 수행하므로 이러한 문자를 인코딩할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-171">The mapping schema does the necessary mapping; therefore, you do not need to encode for these characters).</span></span>  
  
 <span data-ttu-id="28168-172">이 Updategram은 Northwind 데이터베이스의 Order Details 테이블에 레코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-172">This updategram adds a record to the Order Details table in the Northwind database:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-173">Order Details 테이블의 UnitPrice 열은 `money` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-173">The UnitPrice column in the Order Details table is of the `money` type.</span></span> <span data-ttu-id="28168-174">적절한 형식 변환(`string` 형식에서 `money` 형식으로 변환)을 적용하려면 값의 일부로 달러 기호 문자($)를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-174">To apply the appropriate type conversion (from a `string` type to a `money` type), the dollar sign character ($) must be added as part of the value.</span></span> <span data-ttu-id="28168-175">Updategram에서 매핑 스키마를 지정하지 않는 경우 `string` 값의 첫 문자가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-175">If the updategram does not specify a mapping schema, the first character of the `string` value is evaluated.</span></span> <span data-ttu-id="28168-176">첫 문자가 달러 기호($)이면 해당 변환이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-176">If the first character is a dollar sign ($), the appropriate conversion is applied.</span></span>  
  
 <span data-ttu-id="28168-177">열이 `dt:type="fixed.14.4"` 또는 `sql:datatype="money"`로 적절하게 표시된 매핑 스키마에 대해 Updategram을 지정하면 달러 기호($)가 필요하지 않으며 매핑에 의해 변환이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-177">If the updategram is specified against a mapping schema where the column is appropriately marked as either `dt:type="fixed.14.4"` or `sql:datatype="money"`, the dollar sign ($) is not required and the conversion is handled by the mapping.</span></span> <span data-ttu-id="28168-178">적절한 형식 변환을 수행하려는 이 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-178">This is the recommended way to ensure that the appropriate type conversion occurs.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="28168-179">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="28168-180">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-180">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-181">파일을 UpdategramSpacesInTableName.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-181">Save the file as UpdategramSpacesInTableName.xml.</span></span>  
  
2.  <span data-ttu-id="28168-182">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-182">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="28168-183">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-183">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a><span data-ttu-id="28168-184">D.</span><span class="sxs-lookup"><span data-stu-id="28168-184">D.</span></span> <span data-ttu-id="28168-185">at-identity 특성을 사용하여 IDENTITY 유형 열에 삽입된 값 검색</span><span class="sxs-lookup"><span data-stu-id="28168-185">Using the at-identity attribute to retrieve the value that has been inserted in the IDENTITY-type column</span></span>  
 <span data-ttu-id="28168-186">다음 Updategram은 두 개의 레코드를 삽입합니다. 하나는 Sales.SalesOrderHeader 테이블에 삽입하고 다른 하나는 Sales.SalesOrderDetail 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-186">The following updategram inserts two records: one in the Sales.SalesOrderHeader table and another in the Sales.SalesOrderDetail table.</span></span>  
  
 <span data-ttu-id="28168-187">먼저 Updategram은 Sales.SalesOrderHeader 테이블에 레코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-187">First, the updategram adds a record to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="28168-188">이 테이블에서 SalesOrderID 열은 IDENTITY 유형 열입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-188">In this table, the SalesOrderID column is an IDENTITY-type column.</span></span> <span data-ttu-id="28168-189">따라서 이 레코드를 테이블에 추가할 때 Updategram은 `at-identity` 특성을 사용하여 할당된 SalesOrderID 값을 "x"(자리 표시자 값)로 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-189">Therefore, when you add this record to the table, the updategram uses the `at-identity` attribute to capture the assigned SalesOrderID value as "x" (a placeholder value).</span></span> <span data-ttu-id="28168-190">그런 다음 updategam은이 `at-identity` 변수를 요소에 있는 SalesOrderID 특성의 값으로 지정 합니다 \<Sales.SalesOrderDetail> .</span><span class="sxs-lookup"><span data-stu-id="28168-190">The updategam then specifies this `at-identity` variable as the value of SalesOrderID attribute in the \<Sales.SalesOrderDetail> element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-191">`updg:at-identity` 특성에서 생성된 ID 값을 반환하려는 경우 `updg:returnid` 특성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-191">If you want to return the identity value that is generated by the `updg:at-identity` attribute, you can use the `updg:returnid` attribute.</span></span> <span data-ttu-id="28168-192">다음은 이 ID 값을 반환하는 수정된 Updategram입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-192">The following is a revised updategram that returns this identity value.</span></span> <span data-ttu-id="28168-193">이 Updategram은 예를 좀더 복잡하게 만들기 위해 주문 레코드 두 개와 주문 정보 레코드 두 개를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-193">(This updategram adds two order records and two order detail records, just to make the example a little more complex.)</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-194">Updategram을 실행하면 생성된 ID 값(테이블 ID에 사용되는 ShiftID 열의 생성된 값)이 포함된 다음과 유사한 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-194">When the updategram is executed, it returns results similar to the following, which includes the identity value (the generated value of the ShiftID column used for table identity) that was generated:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="28168-195">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="28168-196">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-196">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-197">파일을 Updategram-returnId.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-197">Save the file as Updategram-returnId.xml.</span></span>  
  
2.  <span data-ttu-id="28168-198">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-198">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="28168-199">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-199">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a><span data-ttu-id="28168-200">E.</span><span class="sxs-lookup"><span data-stu-id="28168-200">E.</span></span> <span data-ttu-id="28168-201">updg:guid 특성을 사용하여 고유한 값 생성</span><span class="sxs-lookup"><span data-stu-id="28168-201">Using the updg:guid attribute to generate a unique value</span></span>  
 <span data-ttu-id="28168-202">이 예에서 Updategram은 Cust 및 CustOrder 테이블에 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-202">In this example, the updategram inserts a record in the Cust and CustOrder tables.</span></span> <span data-ttu-id="28168-203">또한 Updategram은 `updg:guid` 특성을 사용하여 CustomerID 특성의 고유한 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-203">Also, the updategram generates a unique value for the CustomerID attribute by using the `updg:guid` attribute.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-204">Updategram은 `returnid` 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-204">The updategram specifies the `returnid` attribute.</span></span> <span data-ttu-id="28168-205">따라서 생성된 GUID가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-205">As a result, the GUID that is generated is returned:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="28168-206">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="28168-207">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-207">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-208">파일을 Updategram-GenerateGuid.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-208">Save the file as Updategram-GenerateGuid.xml.</span></span>  
  
2.  <span data-ttu-id="28168-209">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28168-209">Create these tables:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  <span data-ttu-id="28168-210">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-210">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="28168-211">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-211">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a><span data-ttu-id="28168-212">F.</span><span class="sxs-lookup"><span data-stu-id="28168-212">F.</span></span> <span data-ttu-id="28168-213">Updategram에 스키마 지정</span><span class="sxs-lookup"><span data-stu-id="28168-213">Specifying a schema in an updategram</span></span>  
 <span data-ttu-id="28168-214">이 예의 Updategram은 다음 테이블에 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-214">The updategram in this example inserts a record into the following table:</span></span>  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 <span data-ttu-id="28168-215">이 Updategram에는 XSD 스키마가 지정됩니다. 즉, Updategram 요소 및 특성의 기본 매핑이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-215">An XSD schema is specified in this updategram (that is, there is no default mapping of updategram elements and attributes).</span></span> <span data-ttu-id="28168-216">스키마는 데이터베이스 테이블과 열에 필요한 요소 및 특성의 매핑을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-216">The schema provides the necessary mapping of the elements and attributes to the database tables and columns.</span></span>  
  
 <span data-ttu-id="28168-217">다음 스키마 (CustOrderSchema.xml)는 **\<CustOrder>** **OrderID** 및 **EmployeeID** 특성으로 구성 된 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-217">The following schema (CustOrderSchema.xml) describes a **\<CustOrder>** element that consists of the **OrderID** and **EmployeeID** attributes.</span></span> <span data-ttu-id="28168-218">스키마를 더 흥미롭게 만들려면 **EmployeeID** 특성에 기본값이 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-218">To make the schema more interesting, a default value is assigned to the **EmployeeID** attribute.</span></span> <span data-ttu-id="28168-219">Updategram은 삽입 작업에 대해서만 및 Updategram에서 해당 특성을 지정하지 않는 경우에만 특성의 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-219">An updategram uses an attribute's default value only for insert operations, and then only if the updategram does not specify that attribute.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="28168-220">이 Updategram은 CustOrder 테이블에 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-220">This updategram inserts a record into the CustOrder table.</span></span> <span data-ttu-id="28168-221">Updategram은 OrderID 및 EmployeeID 특성 값만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-221">The updategram specifies only the OrderID and EmployeeID attribute values.</span></span> <span data-ttu-id="28168-222">OrderType 특성 값은 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-222">It does not specify the OrderType attribute value.</span></span> <span data-ttu-id="28168-223">따라서 Updategram은 앞의 스키마에 지정된 EmployeeID 특성의 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-223">Therefore, the updategram uses the default value of the EmployeeID attribute that is specified in the preceding schema.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-224">매핑 스키마를 지정 하는 updategram의 추가 예는 [Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정 ](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-224">For more examples of updategrams that specify a mapping schema, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="28168-225">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-225">To test the updategram</span></span>  
  
1.  <span data-ttu-id="28168-226">**Tempdb** 데이터베이스에이 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28168-226">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  <span data-ttu-id="28168-227">위 스키마를 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-227">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="28168-228">파일을 CustOrderSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-228">Save the file as CustOrderSchema.xml.</span></span>  
  
3.  <span data-ttu-id="28168-229">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-229">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-230">이전 단계에 사용된 폴더와 같은 폴더에 CustOrderUpdategram.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-230">Save the file as CustOrderUpdategram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="28168-231">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-231">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="28168-232">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-232">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="28168-233">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="28168-233">This is the equivalent XDR schema:</span></span>  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a><span data-ttu-id="28168-234">G.</span><span class="sxs-lookup"><span data-stu-id="28168-234">G.</span></span> <span data-ttu-id="28168-235">xsi:nil 특성을 사용하여 열에 Null 값 삽입</span><span class="sxs-lookup"><span data-stu-id="28168-235">Using the xsi:nil attribute to insert null values in a column</span></span>  
 <span data-ttu-id="28168-236">테이블의 해당 열에 Null 값을 삽입하려는 경우 Updategram의 요소에 `xsi:nil` 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-236">If you want to insert a null value in the corresponding column in the table, you can specify the `xsi:nil` attribute on an element in an updategram.</span></span> <span data-ttu-id="28168-237">해당 XSD 스키마에 XSD `nillable` 특성도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-237">In the corresponding XSD schema, the XSD `nillable` attribute also must be specified.</span></span>  
  
 <span data-ttu-id="28168-238">예를 들어 다음 XSD 스키마를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28168-238">For example, consider this XSD schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="28168-239">XSD 스키마는 요소에 대해 **nillable = "true"** 를 지정 합니다 **\<fname>** .</span><span class="sxs-lookup"><span data-stu-id="28168-239">The XSD schema specifies **nillable="true"** for the **\<fname>** element.</span></span> <span data-ttu-id="28168-240">다음 Updategram은 이 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-240">The following updategram uses this schema:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 <span data-ttu-id="28168-241">Updategram는 `xsi:nil` 블록의 요소에 대해를 지정 합니다 **\<fname>** **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="28168-241">The updategram specifies `xsi:nil` for the **\<fname>** element in the **\<after>** block.</span></span> <span data-ttu-id="28168-242">따라서 이 Updategram을 실행하면 테이블의 first_name 열에 대해 NULL 값이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-242">Therefore, when this updategram is executed, a value of NULL is inserted for the first_name column in the table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="28168-243">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-243">To test the updategram</span></span>  
  
1.  <span data-ttu-id="28168-244">**Tempdb** 데이터베이스에 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28168-244">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  <span data-ttu-id="28168-245">위 스키마를 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-245">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="28168-246">파일을 StudentSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-246">Save the file as StudentSchema.xml.</span></span>  
  
3.  <span data-ttu-id="28168-247">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-247">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-248">이전 단계에서 StudentSchema.xml을 저장한 폴더와 같은 폴더에 StudentUpdategram.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-248">Save the file as StudentUpdategram.xml in the same folder used in previous step to save StudentSchema.xml.</span></span>  
  
4.  <span data-ttu-id="28168-249">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-249">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="28168-250">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-250">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a><span data-ttu-id="28168-251">H.</span><span class="sxs-lookup"><span data-stu-id="28168-251">H.</span></span> <span data-ttu-id="28168-252">Updategram에 네임스페이스 지정</span><span class="sxs-lookup"><span data-stu-id="28168-252">Specifying namespaces in an updategram</span></span>  
 <span data-ttu-id="28168-253">Updategram에는 Updategram의 동일한 요소에서 선언된 네임스페이스에 속하는 요소가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-253">In an updategram you can have elements that belong to a namespace declared in the same element in the updategram.</span></span> <span data-ttu-id="28168-254">이 경우 해당 스키마에서도 동일한 네임스페이스를 선언해야 하며 요소가 대상 네임스페이스에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-254">In this case, the corresponding schema must also declare the same namespace and the element must belong to that target namespace.</span></span>  
  
 <span data-ttu-id="28168-255">예를 들어 다음 updategram (UpdateGram-ElementHavingNamespace.xml)에서 **\<Order>** 요소는 요소에 선언 된 네임 스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-255">For example, in the following updategram (UpdateGram-ElementHavingNamespace.xml), the **\<Order>** element belongs to a namespace declared in the element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-256">이 경우 스키마에서도 이 스키마와 같이 해당 네임스페이스를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-256">In this case, the schema must also declare the namespace as shown in this schema:</span></span>  
  
 <span data-ttu-id="28168-257">다음 스키마(XSD-ElementHavingNamespace.xml)에서는 해당 요소와 특성을 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28168-257">The following schema (XSD-ElementHavingNamespace.xml) shows how the corresponding element and attributes must be declared.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="28168-258">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-258">To test the updategram</span></span>  
  
1.  <span data-ttu-id="28168-259">위 스키마를 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-259">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="28168-260">파일을 XSD-ElementHavingNamespace.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-260">Save the file as XSD-ElementHavingNamespace.xml.</span></span>  
  
2.  <span data-ttu-id="28168-261">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-261">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-262">XSD-ElementHavingnamespace.xml을 저장한 폴더와 같은 폴더에 Updategram-ElementHavingNamespace.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-262">Save the file as Updategram-ElementHavingNamespace.xml in the same folder used to save XSD-ElementHavingnamespace.xml.</span></span>  
  
3.  <span data-ttu-id="28168-263">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-263">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="28168-264">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-264">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a><span data-ttu-id="28168-265">9\.</span><span class="sxs-lookup"><span data-stu-id="28168-265">I.</span></span> <span data-ttu-id="28168-266">XML 데이터 형식 열에 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="28168-266">Inserting data into an XML data type column</span></span>  
 <span data-ttu-id="28168-267">`xml` 데이터 형식은 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-267">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="28168-268">Updategram을 사용하여 다음 프로비전과 함께 `xml` 데이터 형식 열에 저장된 데이터를 삽입 및 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-268">You can use updategrams to insert and update data stored in `xml` data type columns with the following provisions:</span></span>  
  
-   <span data-ttu-id="28168-269">`xml` 열은 기존 행을 식별하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-269">The `xml` column cannot be used for identifying an existing row.</span></span> <span data-ttu-id="28168-270">따라서 Updategram의 `updg:before` 섹션에 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-270">Therefore, it cannot be included in the `updg:before` section of an updategram.</span></span>  
  
-   <span data-ttu-id="28168-271">`xml` 열에 삽입된 XML 조각의 범위에 있는 네임스페이스가 유지되고 해당 네임스페이스 선언이 삽입된 조각의 최상위 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="28168-271">Namespaces that are in scope of the XML fragment inserted into the `xml` column will be preserved and their namespace declarations are added to the top element of the inserted fragment.</span></span>  
  
 <span data-ttu-id="28168-272">예를 들어 다음 updategram (SampleUpdateGram.xml)에서 **\<Desc>** 요소는 샘플 데이터베이스의 Production>제품 모델 테이블에서 제품 설명 열을 업데이트 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-272">For example, in the following updategram (SampleUpdateGram.xml), the **\<Desc>** element updates the ProductDescription column in the Production>productModel table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="28168-273">이 updategram의 결과는 제품 설명 열의 XML 콘텐츠가 요소의 XML 내용으로 업데이트 된다는 것입니다 **\<Desc>** .</span><span class="sxs-lookup"><span data-stu-id="28168-273">The result of this updategram is that the XML contents of the ProductDescription column are update with the XML contents of the **\<Desc>** element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="28168-274">Updategram은 주석이 추가된 다음 XSD 스키마(SampleSchema.xml)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-274">The updategram refers to the following annotated XSD schema (SampleSchema.xml).</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="28168-275">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="28168-275">To test the updategram</span></span>  
  
1.  <span data-ttu-id="28168-276">위 스키마를 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-276">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="28168-277">파일을 XSD-SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-277">Save the file as XSD-SampleSchema.xml.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="28168-278">Updategram은 기본 매핑을 지원하므로 `xml` 데이터 형식의 시작 부분과 끝 부분을 식별할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-278">Because updategrams support default mapping, there is no way to identify the beginning and ending of the `xml` data type.</span></span> <span data-ttu-id="28168-279">즉, `xml` 데이터 형식 열을 사용하여 테이블을 삽입하거나 업데이트할 때 매핑 스키마가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-279">This effectively means that a mapping schema is required when inserting or updating tables with `xml` data type columns.</span></span> <span data-ttu-id="28168-280">스키마를 제공하지 않으면 SQLXML에서 열 중 하나가 테이블에 없음을 나타내는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-280">When a schema is not provided, SQLXML returns an error indicating that one of the columns is missing from the table.</span></span>  
  
2.  <span data-ttu-id="28168-281">위 Updategram을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28168-281">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="28168-282">SampleSchema.xml을 저장하는 데 사용된 폴더와 같은 폴더에 SampleUpdategram.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-282">Save the file as SampleUpdategram.xml in the same folder used to save SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="28168-283">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28168-283">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="28168-284">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28168-284">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28168-285">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28168-285">See Also</span></span>  
 [<span data-ttu-id="28168-286">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="28168-286">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  