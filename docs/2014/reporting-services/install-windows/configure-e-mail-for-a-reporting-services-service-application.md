---
title: Configurar o email para um relatório dos serviços de aplicativo de serviço (SharePoint 2010 e SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 0e12d4d1c630dcc1e46492cf93582ab5b882e3af
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36009303"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a>Configurar o email para um serviço de aplicativo do Reporting Services (SharePoint 2010 e SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] O alerta de dados envia alertas de dados em mensagens de email. Para enviar um email, talvez seja necessário configurar o aplicativo de serviço do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e modificar a extensão de entrega de email do aplicativo de serviço. As configurações de email também serão necessárias se você estiver planejando usar a extensão de entrega de email do recurso de assinatura do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modo do SharePoint &#124; do SharePoint 2010 e SharePoint 2013.|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>Para configurar o email para o serviço compartilhado  
  
1.  Na Administração Central do SharePoint, clique em **Gerenciamento de Aplicativos**.  
  
2.  No grupo **Aplicativos de Serviço** , clique em **Gerenciar aplicativos de serviço**.  
  
3.  Na lista **Nome** , clique no nome do seu aplicativo de serviço do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Clique em **Configurações de Email** na página **Gerenciar Aplicativo Reporting Services** .  
  
5.  Selecione **Usar servidor SMTP**.  
  
6.  Na caixa **Servidor SMTP de saída** , digite o nome de um servidor SMTP.  
  
7.  Na caixa **Endereço de origem** , digite um endereço de email.  
  
     Esse endereço corresponde ao remetente de mensagens de email de alerta.  
  
     A conta de usuário especificada no **Endereço de origem** deve ser uma conta gerenciada que você especificou quando configurou o pool de aplicativos para o aplicativo de serviço do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Se tiver permissão, você poderá exibir uma lista das contas gerenciadas existentes na página Contas de Serviço na Administração Central do SharePoint.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>Autenticação NTLM  
  
1.  Se o seu ambiente de email exigir a autenticação NTLM e não permitir acesso anônimo, será necessário modificar a configuração de extensão de entrega de email para aplicativos de serviço do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Altere **SMTPAuthenticate** para usar um valor de “2”. Esse valor não pode ser alterado na interface do usuário. O exemplo de script PowerShell a seguir atualiza a configuração completa da extensão de entrega de email do servidor de relatório para o aplicativo de serviço denominado “SSRS_TESTAPPLICATION”. Observe que alguns dos nós listados no script também podem ser definidos na interface do usuário, por exemplo, o endereço de origem.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  Se for necessário verificar o nome do seu aplicativo de serviço, execute o **cmdlet Get-SPRSServiceApplication**.  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  O exemplo a seguir retornará os valores atuais da extensão de email para o aplicativo de serviço denominado “SSRS_TESTAPPLICATION”.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  O exemplo a seguir criará um novo arquivo denominado “emailconfig.txt” com os valores atuais da extensão de email para o aplicativo de serviço chamado “SSRS_TESTAPPLICATION”  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  