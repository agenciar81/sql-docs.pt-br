---
title: Configurar o Gerenciador de relatórios para transmitir Cookies de autenticação personalizados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 65524c714361a7a43531a778121231a8ff2013a8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36006521"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>Configurar o Gerenciador de Relatórios para transmitir cookies de autenticação personalizados
  Se você estiver usando uma extensão de autenticação personalizada, configure o Gerenciador de Relatórios para transmitir cookies de autenticação personalizados. Caso contrário, o Gerenciador de Relatórios transmitirá cookies somente por solicitações HTTP específicas do servidor de relatório. Se desejar transmitir cookies adicionais, modifique o arquivo RSReportServer.Config.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>Modificando o arquivo RSReportServer.Config  
 Você pode habilitar o Gerenciador de relatórios para transmitir cookies adicionais pelo servidor de relatório adicionando um <`PassThroughCookies`> elemento para as definições de configuração do Gerenciador de relatórios no arquivo rsreportserver. config. A transmissão de cookies adicionais é útil em uma solução de autenticação de logon único que requer não só cookies de autenticação do servidor de relatório, mas também cookies de um sistema de autenticação de terceiros.  
  
 Para permitir que cookies adicionais sejam transmitidos através de solicitações HTTP ao usar o Gerenciador de Relatórios, defina os seguintes elementos no arquivo RSReportServer.config:  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Autenticação com o servidor de relatório](authentication-with-the-report-server.md)   
 [Arquivo de configuração RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Visão geral de extensões de segurança](../extensions/security-extension/security-extensions-overview.md)   
 [Configurar e administrar um servidor de relatório &#40;modo nativo do SSRS&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  