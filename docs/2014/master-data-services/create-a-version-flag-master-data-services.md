---
title: Criar um sinalizador de versão (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cea2d431b213d6b62106fff5c0c15c588e1b115d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36130595"
---
# <a name="create-a-version-flag-master-data-services"></a>Criar um sinalizador de versão (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], crie um sinalizador de versão a ser atribuído a uma versão. O sinalizador pode indicar a versão que os usuários ou sistemas de assinatura devem usar.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Gerenciamento de Versões** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Para criar um sinalizador de versão  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Gerenciamento de Versões**.  
  
2.  Na página **Gerenciar Versões** , na barra de menus, aponte para **Gerenciar** e clique em **Sinalizadores**.  
  
3.  Na página **Gerenciar Sinalizadores de Versão** , no campo **Modelo** , selecione o modelo para o qual você deseja criar um sinalizador.  
  
4.  Clique em **Adicionar**.  
  
5.  Na caixa **Nome** , digite um nome.  
  
6.  Na caixa **Descrição** , digite uma descrição.  
  
7.  No campo **Somente Versões Confirmadas** , selecione **True** para indicar que o sinalizador pode ser atribuído a versões apenas com um status de **Confirmado** . Selecione **False** para indicar que o sinalizador pode ser atribuído a versões com qualquer status.  
  
8.  Clique em **Salvar**.  
  
## <a name="next-steps"></a>Próximas etapas  
  
-   [Atribuir um sinalizador a uma versão &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Consulte também  
 [Versões &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Alterar o nome de um sinalizador de versão &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  