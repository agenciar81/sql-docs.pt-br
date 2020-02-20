---
title: Autenticação do serviço Web | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3ea255c03803f6191d3161d3ef2fa149ef157f56
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "63069883"
---
# <a name="web-service-authentication"></a>Autenticação de serviço Web
  Você pode usar a Autenticação de Windows ou a autenticação Básica para autenticar as chamadas feitas ao serviço Web Servidor de Relatório. Qualquer cliente que faz solicitações SOAP ao servidor de relatório deve implementar a parte cliente de um dos protocolos de autenticação suportados. Se estiver usando o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], você poderá usar as classes HTTP de código gerenciado para implementar a autenticação. O uso dessas APIs facilita o envio de informações de autenticação junto comas solicitações SOAP.  
  
 Se você não tiver as credenciais apropriados antes de fazer uma chamada ao serviço Web Servidor de Relatório, a chamada falhará. Em tempo de execução, passe as credenciais para o serviço Web definindo a propriedade **Credentials** do objeto do lado do cliente que representa o serviço Web antes de chamar seus métodos.  
  
 As seções a seguir contêm código de exemplo que envia credenciais usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Autenticação do Windows  
 O código a seguir transmite credenciais do Windows ao serviço Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Autenticação Básica  
 O código a seguir transmite credenciais Básicas ao serviço Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 As credenciais devem ser definidas antes de você chamar qualquer um dos métodos do serviço Web Servidor de Relatório. Se você não definir as credenciais, receberá o código de erro HTTP 401 Erro: Acesso negado. Autentique o serviço antes de usá-lo, mas depois de definir as credenciais; não será preciso defini-las novamente, desde que você continue usando a mesma variável de serviço (como *rs*).  
  
## <a name="custom-authentication"></a>Autenticação personalizada  
 O [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclui uma API de programação que oferece aos desenvolvedores a oportunidade de criar e de desenvolver extensões de autenticação personalizadas, conhecido como extensões de segurança. Para obter mais informações, consulte [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Criando aplicativos usando o serviço Web e o .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Serviço Web do Servidor de Relatório](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
