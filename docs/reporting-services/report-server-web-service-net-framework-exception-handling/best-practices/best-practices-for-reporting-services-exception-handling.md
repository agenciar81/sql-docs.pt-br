---
title: Melhores práticas para tratamento de exceção do Reporting Services | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c6e59ea3edb968182091b1b6496d47e9adb4d4be
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "63151113"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Práticas recomendadas para a manipulação de exceção do Reporting Services
  Durante o desenvolvimento de aplicativos do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], existem várias metodologias que você pode usar para eliminar ou reduzir a ocorrência de exceções. Quando houver exceções, forneça mensagens de erro claras e concisas ao usuário e adicione manipulação de exceção adequada para impedir que seus aplicativos sejam encerrados de forma inesperada.  
  
 Um aplicativo que envia solicitações ao serviço Web Servidor de Relatório deve fazer o seguinte:  
  
-   Evitar as exceções impedindo quantas solicitações inválidas for possível.  
  
-   Capturar exceções e fornecer código de manipulação de erro específico sempre que possível.  
  
-   Lidar com casos de erro que não lançam exceções.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|DESCRIÇÃO|  
|-----------|-----------------|  
|[Impedir solicitações inválidas](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Descreve técnicas para impedir que solicitações que não são válidas sejam enviadas ao servidor de relatório.|  
|[Usar blocos try e catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Descreve como aprimorar ainda mais a confiabilidade de seu aplicativo com blocos try/catch.|  
|[Manipular avisos e casos que não causam exceções](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Explica como manipular erros que não resultam em uma exceção é lançada pelo [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Usar a propriedade Detail para manipular erros específicos](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Explica como tratar erros específicos de forma programática usando a propriedade **Detail** do objeto **SoapException**.|  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedade Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introdução ao tratamento de exceção no Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException do Reporting Services +](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
