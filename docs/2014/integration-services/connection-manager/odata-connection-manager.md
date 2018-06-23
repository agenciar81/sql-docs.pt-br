---
title: Gerenciador de Conexões OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4c0c38e2aa12991ead24a0ba162462504d28e60d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36115495"
---
# <a name="odata-connection-manager"></a>Gerenciador de conexões do OData
  Um gerenciador de conexões OData habilita um pacote a conectar-se a uma fonte OData. Um componente de origem OData se conecta a uma origem OData usando um gerenciador de conexões OData e consome dados do serviço. Consulte a seção [OData Source](../data-flow/odata-source.md)para obter informações detalhadas, inclusive as instruções de instalação desses componentes.  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a>Adicionando o gerenciador de conexões a um pacote SSIS  
 Você pode adicionar um novo Gerenciador de Conexões OData a um pacote SSIS de três maneiras:  
  
-   Clique no botão **Novo...** em **Editor de origem OData**  
  
-   Clique com o botão direito na pasta **Gerenciadores de Conexões** no **Gerenciador de Soluções** e clique em **Novo Gerenciador de Conexões**. Selecione **ODATA** para o **Tipo de gerenciador de conexões**.  
  
-   Clique com o botão direito do mouse no painel de **Gerenciadores de Conexões** na parte inferior do designer de pacote, e selecione **Nova Conexão...**. Selecione **ODATA** para o **Tipo de gerenciador de conexões**.  
  
## <a name="connection-manager-authentication"></a>Autenticação do gerenciador de conexões  
 O gerenciador de conexões do OData oferece suporte a dois modos de autenticação.  
  
-   Autenticação do Windows  
  
-   Autenticação básica (nome de usuário e senha)  
  
 Para o acesso anônimo, selecione a opção de Autenticação do Windows  
  
### <a name="specifying-and-securing-credentials"></a>Especificando e protegendo credenciais  
 Se seu serviço OData exigir autenticação básica, você pode especificar um nome de usuário e uma senha no [OData Connection Manager Editor](../odata-connection-manager-editor.md). Os valores que você insere no publicador são persistidos no pacote. O valor de senha é criptografado de acordo com o nível de proteção do pacote.  
  
 Há várias maneiras de exteriorizar/parametrizar os valores de nome de usuário e senha. As duas principais maneiras de fazer isso no [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] são usando parâmetros, ou definindo as propriedades do gerenciador de conexões diretamente quando você executa o pacote usando o SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Propriedades do gerenciador de conexões do OData  
 A lista a seguir descreve algumas das propriedades do gerenciador de conexões do OData que talvez você queira alterar.  
  
|||  
|-|-|  
|Propriedade|Description|  
|Url|URL do documento de serviço.|  
|UserName|Nome de usuário para ser usado na autenticação básica.|  
|Senha|Senha a ser usada na autenticação básica.|  
|ConnectionString|Reflete outras propriedades do gerenciador de conexões.|  
  
## <a name="see-also"></a>Consulte também  
 [OData Connection Manager Editor](../odata-connection-manager-editor.md)  
  
  