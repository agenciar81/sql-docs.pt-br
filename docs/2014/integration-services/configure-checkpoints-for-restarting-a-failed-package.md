---
title: Configurar pontos de verificação para reinicializar um pacote com falha | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3c2ae5affa24087bbb0511bc29559bba88f86cdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36118482"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>Configurar pontos de verificação para reinicializar um pacote com falha
  Você pode configurar os pacotes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] para reiniciá-los a partir de um ponto de falha em vez de executar novamente todo o pacote, selecionando as propriedades que se aplicam aos pontos de verificação.  
  
### <a name="to-configure-a-package-to-restart"></a>Para configurar um pacote para reinicialização  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra o projeto do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que contém o pacote que você deseja configurar.  
  
2.  No **Gerenciador de Soluções**, clique duas vezes no pacote para abri-lo.  
  
3.  Clique na guia **Fluxo de Controle** .  
  
4.  Clique com o botão direito do mouse em qualquer lugar da tela de fundo da superfície de design do fluxo de controle e clique em **Propriedades**.  
  
5.  Defina a propriedade SaveCheckpoints como `True`.  
  
6.  Digite o nome do arquivo de ponto de verificação na propriedade CheckpointFileName.  
  
7.  Defina a propriedade CheckpointUsage como um dos dois valores:  
  
    -   Selecione `Always` para reiniciar o pacote partindo sempre de um ponto de verificação.  
  
        > [!IMPORTANT]  
        >  Um erro ocorrerá se o arquivo do ponto de verificação não estiver disponível.  
  
    -   Selecione `IfExists` para reiniciar o pacote apenas se o arquivo de ponto de verificação está disponível.  
  
8.  Configure as tarefas e os contêineres a partir dos quais o pacote pode ser reiniciado.  
  
    -   Clique com o botão direito do mouse em uma tarefa ou contêiner e clique em **Propriedades**.  
  
    -   Defina a propriedade FailPackageOnFailure como `True` para cada tarefa e contêiner selecionados.  
  
## <a name="see-also"></a>Consulte também  
 [Reiniciar pacotes por meio de pontos de verificação](packages/restart-packages-by-using-checkpoints.md)  
  
  