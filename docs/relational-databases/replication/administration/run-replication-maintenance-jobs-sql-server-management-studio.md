---
title: Executar trabalhos de manutenção de replicação (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: e7d5764e3cfdaf88ebfa23cedd61884f3c4f347e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768766"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Executar trabalhos de manutenção de replicação (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  A replicação usa os seguintes trabalhos de manutenção:  
  
-   **Reinicializar assinaturas com falha na validação de dados**  
  
-   **Limpeza de histórico de agente: distribuição**  
  
-   **Atualizador de monitoramento de replicação para distribuição.**  
  
-   **Verificação de agentes de replicação**  
  
-   **Limpeza de distribuição: distribuição**  
  
-   **Limpeza de assinaturas expiradas**  
  
 Inicie e pare esse trabalhos na pasta **Trabalhos** em [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e na guia **Agentes** no Replication Monitor. Para obter informações sobre como iniciar o Replication Monitor, consulte [Start the Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md) (Iniciar o Replication Monitor). Exiba e modifique propriedades de cada trabalho na caixa de diálogo **Propriedades do trabalho – \<Trabalho>** , que está disponível na mesma pasta e guia.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Para iniciar ou parar um trabalho de manutenção de replicação no Management Studio  
  
1.  Conecte-se ao Distribuidor no [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e, em seguida, expanda o nó de servidor.  
  
2.  Expanda a pasta **SQL Server Agent** e, em seguida, a pasta **Trabalhos** .  
  
3.  Clique com o botão direito do mouse em um trabalho e então clique em **Iniciar Trabalho** ou **Parar Trabalho**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>Para iniciar ou parar um trabalho de manutenção de replicação no Replication Monitor  
  
1.  Expanda um Grupo do publicador no Replication Monitor e, então, selecione um Publicador.  
  
2.  Clique na guia **Agentes** .  
  
3.  Clique com o botão direito do mouse em um trabalho na grade e então clique em **Iniciar Trabalho** ou **Parar Trabalho**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Para exibir e modificar propriedades de um trabalho de manutenção de replicação no Management Studio  
  
1.  Conecte-se ao Distribuidor no [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e, em seguida, expanda o nó de servidor.  
  
2.  Expanda a pasta **SQL Server Agent** e, em seguida, a pasta **Trabalhos** .  
  
3.  Clique com o botão direito do mouse em um trabalho e clique em **Propriedades**.  
  
4.  Na caixa de diálogo **Propriedades do Trabalho – \<Trabalho>** , altere as propriedades se necessário e então clique em **OK**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>Para exibir e modificar propriedades de um trabalho de manutenção de replicação no Replication Monitor  
  
1.  Expanda um Grupo do publicador no Replication Monitor e, então, selecione um Publicador.  
  
2.  Clique na guia **Agentes** .  
  
3.  Clique com o botão direito do mouse em um trabalho na grade e então clique em **Propriedades**.  
  
4.  Na caixa de diálogo **Propriedades do Trabalho – \<Trabalho>** , altere as propriedades se necessário e então clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar e interromper um agente de replicação &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Exibir informações e executar tarefas para um Publicador &#40;Replication Monitor&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Administração do agente de replicação](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
