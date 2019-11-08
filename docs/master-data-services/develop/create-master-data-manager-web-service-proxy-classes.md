---
title: Criar classes proxy do serviço Web do Master Data Manager
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1096da19a45e15ab2216cea2f4a4a38ecb05233e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729313"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Criar classes proxy do serviço Web do Master Data Manager

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  O serviço Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] permite a você fazer uso programático dos recursos do [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] de qualquer computador que possa acessar seu site do [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Antes de começar a gravar código para acessar o serviço Web, você deve gerar classes proxy. A classe proxy principal que você usa para executar operações de serviço Web é a classe <xref:Microsoft.MasterDataServices.ServiceClient>, que implementa a interface <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Habilitar a publicação de metadados de serviço Web  
 Antes de gerar classes proxy, você deve habilitar a publicação de metadados de serviço Web. Siga estas etapas para fazer isso:  
  
1.  Abra o arquivo Web.config do [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] em um editor de texto. Esse arquivo está na pasta WebApplication, no caminho de instalação do [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Localize a seção **mdsWsHttpBehavior** em **\<serviceBehaviors>** . Para o elemento **\<serviceMetadata>** , defina **httpGetEnabled** como **true**.  
  
    > [!NOTE]  
    >  Se quiser habilitar serviços Web sobre o protocolo SSL, defina **httpsGetEnabled** como **true** na seção **mdsWsHttpBehavior** do arquivo web.config. Você também precisa alterar o **mdsWsHTTPBinding** para que ele seja configurado para SSL também e faça um comentário da seção não SSL.  
  
3.  Salve as alterações no arquivo.  
  
4.  Teste a publicação de metadados navegando para a URL do serviço, por exemplo: `https://yourserver/MDS/service/service.svc`. Se a publicação de metadados estiver habilitada, será exibida uma página que começa com   
    "Você criou um serviço."  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Criando classes proxy usando o Visual Studio  
 Se você tiver o Visual Studio 2010 instalado, o modo mais simples de gerar classes proxy será adicionar uma **Referência de Serviço** ao seu projeto. O endereço da referência do serviço é a URL do aplicativo Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], com /service/service.svc. Por exemplo: `https://yourserver/MDS/service/service.svc`. Para obter mais informações, consulte [Como adicionar, atualizar ou remover uma referência de serviço](https://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Criando classes proxy usando Svcutil.exe  
 Você deve ter o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou o SDK do Windows do [!INCLUDE[msCoName](../../includes/msconame-md.md)] instalado para ter o Svcutil.exe em seu computador. Se você usar o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], deverá usar o prompt de comando do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para executar o comando. Para obter mais informações, consulte [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) [Gerando um cliente WCF de metadados do serviço](https://go.microsoft.com/fwlink/?LinkId=164821).  
  
 Para criar um conjunto de classes proxy C# usando Svcutil.exe, utilize um comando como o seguinte:  
  
```  
svcutil.exe https://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Onde:  
  
-   *server_name*:*port* são o número da porta e o nome do computador que hospeda o [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *virtual_path* é o caminho virtual do [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] no IIS (Serviços de Informações da Internet).  
  
-   *proxy_name* é o nome do arquivo proxy gerado.  
  
## <a name="see-also"></a>Consulte também  
 [Operações de serviço Web categorizadas &#40;Master Data Services&#41;](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
