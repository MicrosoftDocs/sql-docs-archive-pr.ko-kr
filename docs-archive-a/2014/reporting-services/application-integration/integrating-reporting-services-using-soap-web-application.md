---
title: 웹 애플리케이션에서 SOAP API 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729148"
---
# <a name="using-the-soap-api-in-a-web-application"></a>웹 애플리케이션에서 SOAP API 사용
  Reporting Services SOAP API를 통해 보고서 서버의 전체 기능에 액세스할 수 있습니다. SOAP API는 웹 서비스이므로 쉽게 액세스하여 사용자 지정 비즈니스 애플리케이션에 엔터프라이즈 보고 기능을 제공할 수 있습니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션에서 SOAP API에 액세스하는 것과 동일한 방법으로 웹 애플리케이션에서 보고서 서버 웹 서비스에 액세스합니다. 를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 보고서 서버 웹 서비스의 속성 및 메서드를 표시 하는 프록시 클래스를 생성할 수 있으며 친숙 한 인프라와 도구를 사용 하 여 기술에서 비즈니스 응용 프로그램을 빌드할 수 있습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 관리 기능은 Windows 애플리케이션에서 액세스하는 것과 마찬가지로 웹 애플리케이션에서도 쉽게 액세스할 수 있습니다. 웹 애플리케이션에서는 보고서 서버 데이터베이스에서 항목 추가 및 제거, 항목 보안 설정, 보고서 서버 데이터베이스 항목 수정, 일정 예약 및 배달 관리 등을 수행할 수 있습니다.  
  
## <a name="enabling-impersonation"></a>가장 사용  
 웹 애플리케이션 구성의 첫 단계는 웹 서비스 클라이언트에서 가장을 사용하도록 하는 것입니다. 가장을 사용하면 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션은 대신 작업할 다른 클라이언트의 ID로 실행할 수 있습니다. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS(인터넷 정보 서비스)에 의존하여 사용자를 인증하고 인증된 토큰을 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션에 전달하거나 사용자를 인증할 수 없는 경우 인증되지 않은 토큰을 전달합니다. 가장을 사용한다면 두 경우 모두 어떤 토큰이 수신되든지 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션은 이 토큰을 가장합니다. 클라이언트 애플리케이션의 Web.config 파일을 다음과 같이 수정하여 클라이언트에서 가장을 사용하도록 설정할 수 있습니다.  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  가장은 기본적으로 사용 안 함으로 설정되어 있습니다.  
  
 가장에 대 한 자세한 내용은 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조 하세요.  
  
## <a name="managing-the-report-server-using-soap-api"></a>SOAP API를 사용하여 보고서 서버 관리  
 웹 애플리케이션을 사용하여 보고서 서버 및 콘텐츠를 관리할 수도 있습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 포함된 보고서 관리자는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 및 Reporting Services SOAP API를 사용하여 작성된 웹 애플리케이션의 예입니다. 보고서 관리자의 보고서 관리 기능을 사용자 지정 웹 애플리케이션에 추가할 수 있습니다. 예를 들어 보고서 서버 데이터베이스에서 사용 가능한 보고서 목록을 반환 하 고 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 사용자가 선택할 수 있도록 컨트롤에 표시 하는 것이 좋습니다 `Listbox` . 다음 코드는 보고서 서버 데이터베이스에 연결하고 보고서 서버 데이터베이스의 항목 목록을 반환합니다. 그러면 사용 가능한 보고서가 Listbox 컨트롤에 추가되고 각 보고서의 경로가 표시됩니다.  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md)   
 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)   
 [Windows 애플리케이션에서 SOAP API 사용](integrating-reporting-services-using-soap-windows-application.md)  
  
  
