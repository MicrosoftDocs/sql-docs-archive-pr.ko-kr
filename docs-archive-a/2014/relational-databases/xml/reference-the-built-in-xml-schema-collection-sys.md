---
title: 기본 제공 XML 스키마 컬렉션 참조(sys) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- sys XML schema collections [SQL Server]
- schema collections [SQL Server], predefined
- predefined XML schema collections [SQL Server]
- XML schema collections [SQL Server], predefined
- built-in XML schema collections [SQL Server]
ms.assetid: 1e118303-5df0-4ee4-bd8d-14ced7544144
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fa30107e1746b33e3f9b8eb1cfa53d1f4d25fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730243"
---
# <a name="reference-the-built-in-xml-schema-collection-sys"></a><span data-ttu-id="7ee88-102">기본 제공 XML 스키마 컬렉션 참조(sys)</span><span class="sxs-lookup"><span data-stu-id="7ee88-102">Reference the Built-in XML Schema Collection (sys)</span></span>
  <span data-ttu-id="7ee88-103">사용자가 만드는 모든 데이터베이스의 **sys** 관계형 스키마에는 미리 정의된 **sys** XML 스키마 컬렉션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-103">Every database you create has a predefined **sys** XML schema collection in the **sys** relational schema.</span></span> <span data-ttu-id="7ee88-104">이 스키마 컬렉션에는 이러한 미리 정의된 스키마가 포함되며 사용자가 만든 다른 XML 스키마 컬렉션으로부터 이러한 스키마를 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-104">It reserves these predefined schemas, and they can be accessed from any other user-created XML schema collection.</span></span> <span data-ttu-id="7ee88-105">이러한 미리 정의된 스키마에 사용되는 접두사는 XQuery에서 의미를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-105">The prefixes used in these predefined schemas are meaningful in XQuery.</span></span> <span data-ttu-id="7ee88-106">예약된 접두사는 **xml** 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-106">Only **xml** is a reserved prefix.</span></span>  
  
```  
xml = http://www.w3.org/XML/1998/namespace  
xs = http://www.w3.org/2001/XMLSchema  
xsi = http://www.w3.org/2001/XMLSchema-instance  
fn = http://www.w3.org/2004/07/xpath-functions  
sqltypes = https://schemas.microsoft.com/sqlserver/2004/sqltypes  
xdt = http://www.w3.org/2004/07/xpath-datatypes  
(no prefix) = urn:schemas-microsoft-com:xml-sql  
(no prefix) = https://schemas.microsoft.com/sqlserver/2004/SOAP  
```  
  
 <span data-ttu-id="7ee88-107">**sqltypes** 네임스페이스에는 사용자가 만든 모든 XML 스키마 컬렉션에서 참조할 수 있는 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-107">Note that the **sqltypes** namespace contains components that can be referenced from any user-created XML schema collection.</span></span> <span data-ttu-id="7ee88-108">**Microsoft 웹 사이트** 에서 [sqltypes](https://go.microsoft.com/fwlink/?linkid=31850)스키마를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-108">You can download the **sqltypes** schema from this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=31850).</span></span> <span data-ttu-id="7ee88-109">기본 제공되는 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-109">The built-in components include the following:</span></span>  
  
-   <span data-ttu-id="7ee88-110">XSD 유형</span><span class="sxs-lookup"><span data-stu-id="7ee88-110">XSD types</span></span>  
  
-   <span data-ttu-id="7ee88-111">**lang**, **base**및 **space**XML 특성</span><span class="sxs-lookup"><span data-stu-id="7ee88-111">XML attributes **lang**, **base**, and **space**</span></span>  
  
-   <span data-ttu-id="7ee88-112">**sqltypes** 네임스페이스의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7ee88-112">Components of the **sqltypes** namespace</span></span>  
  
 <span data-ttu-id="7ee88-113">다음 쿼리는 사용자가 만든 XML 스키마 컬렉션에서 참조할 수 있는 기본 제공 구성 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-113">The following query returns built-in components that can be referenced from a user-created XML schema collection:</span></span>  
  
```  
SELECT C.name, N.name, C.symbol_space_desc from sys.xml_schema_components C join sys.xml_schema_namespaces N  
on ((C.xml_namespace_id = N.xml_namespace_id) AND (C.xml_collection_id = N.xml_collection_id))  
join sys.xml_schema_collections SC  
on SC.xml_collection_id = C.xml_collection_id  
where ((C.xml_collection_id = 1) AND (C.name is not null) AND (C.scoping_xml_component_id is null)   
AND (SC.schema_id = 4))  
GO  
```  
  
 <span data-ttu-id="7ee88-114">다음 예에서는 사용자 스키마에서 이러한 구성 요소를 참조하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-114">The following example shows how these components are referenced in a user schema.</span></span> <span data-ttu-id="7ee88-115">`CREATE XML SCHEMA COLLECTION` 은 `varchar` 네임스페이스에 정의된 `sqltypes` 유형을 참조하는 XML 스키마 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-115">`CREATE XML SCHEMA COLLECTION` creates an XML schema collection that references the `varchar` type defined in the `sqltypes` namespace.</span></span> <span data-ttu-id="7ee88-116">또한 `lang` 네임스페이스에 정의된 `xml` 특성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-116">The example also references the `lang` attribute that is defined in the `xml` namespace.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema   
   xmlns="http://www.w3.org/2001/XMLSchema"   
   targetNamespace="myNS"  
   xmlns:ns="myNS"  
   xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
   <import namespace="http://www.w3.org/XML/1998/namespace"/>  
   <import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
   <element name="root">  
      <complexType>  
          <sequence>  
             <element name="a" type="string"/>  
             <element name="b" type="string"/>  
             <!-- varchar type is defined in the sys.sys collection and   
                  can be referenced in any user-defined schema -->  
             <element name="c" type="s:varchar"/>  
          </sequence>  
          <attribute name="att" type="int"/>  
          <!-- xml:lang attribute is defined in the sys.sys collection   
               and can be referenced in any user-defined schema -->  
          <attribute ref="xml:lang"/>  
      </complexType>  
    </element>  
 </schema>'  
GO  
 -- Cleanup  
DROP xml schema collection SC   
GO  
```  
  
 <span data-ttu-id="7ee88-117">다음 사항에 유념하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ee88-117">You should note the following:</span></span>  
  
-   <span data-ttu-id="7ee88-118">사용자 정의 XML 스키마 컬렉션에 있는 이러한 네임스페이스의 XML 스키마는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-118">You cannot modify XML schemas with these namespaces in any user-defined XML schema collection.</span></span> <span data-ttu-id="7ee88-119">예를 들어 다음 XML 스키마 컬렉션은 보호되는 `sqltypes` 네임스페이스에 구성 요소를 추가하기 때문에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-119">For example, the following XML schema collection fails, because it is adding a component to the `sqltypes` protected namespace:</span></span>  
  
    ```  
    CREATE XML SCHEMA COLLECTION SC AS '  
    <schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace    
        ="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
          <element name="root" type="string"/>  
    </schema>'  
    GO  
    ```  
  
-   <span data-ttu-id="7ee88-120">`sys` XML 스키마 컬렉션을 사용하여 `xml` 열, 변수 또는 매개 변수를 형식화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-120">You cannot use the `sys` XML schema collection to type `xml` columns, variables, or parameters.</span></span> <span data-ttu-id="7ee88-121">예를 들어 다음 코드는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-121">For example, the following code returns an error:</span></span>  
  
    ```  
    DECLARE @x xml (sys.sys)  
    ```  
  
-   <span data-ttu-id="7ee88-122">이러한 기본 제공 스키마의 직렬화는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-122">Serialization of these built-in schemas is not supported.</span></span> <span data-ttu-id="7ee88-123">예를 들어 다음 코드는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-123">For example, the following code returns an error:</span></span>  
  
    ```  
    SELECT XML_SCHEMA_NAMESPACE(N'sys',N'sys')  
    GO  
    ```  
  
 <span data-ttu-id="7ee88-124">다음 코드는 `varchar` 네임스페이스에 정의된 `sqltypes` 유형을 사용하는 XML 스키마 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-124">The following code is another example in which you create an XML schema collection that uses the `varchar` type defined in the `sqltypes` namespace:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="myNS" xmlns:ns="myNS"  
        xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes">  
   <import     
     namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
            <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
go  
```  
  
 <span data-ttu-id="7ee88-125">다음과 같이 형식화된 `XML` 변수를 만들고, 여기에 XML 인스턴스를 지정한 다음 <`root`> 요소 유형의 값이 `varchar` 유형인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-125">As shown in the following, you can create a typed `XML` variable, assign an XML instance to it, and verify that the value of the <`root`> element type is a `varchar` type.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
GO  
```  
  
 <span data-ttu-id="7ee88-126">`instance of sqltypes:varchar?` 식은 <`root`> 요소 값이 `@var` 변수와 연결된 스키마에 따라 **varchar**로부터 파생된 유형이기 때문에 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ee88-126">The `instance of sqltypes:varchar?` expression returns TRUE, because the <`root`> element value is of a type derived from **varchar** according to the schema that is associated with the `@var` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee88-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ee88-127">See Also</span></span>  
 [<span data-ttu-id="7ee88-128">XML 스키마 컬렉션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7ee88-128">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  