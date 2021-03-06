---
title: Alterar a conta proxy para o conjunto de coleta do utilitário em um Instância Gerenciada de SQL Server (Utilitário do SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: efa4af0c12379abaab2d810fd39ce6d7a3b0afef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62806320"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a>Alterar a conta proxy para o conjunto de coleta do utilitário em uma instância gerenciada do SQL Server (Utilitário do SQL Server)
  Este tópico descreve como alterar a conta proxy para o Conjunto de Coleta do Utilitário em uma instância gerenciada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>Para alterar a conta proxy do conjunto de coleta do utilitário em uma instância gerenciada do SQL Server  
  
1.  Remova a instância gerenciada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.  
  
    -   No **Gerenciador do Utilitário** no SSMS, clique no nó **Instâncias Gerenciadas** .  
  
    -   Na exibição de lista do **Gerenciador do Utilitário**, clique com o botão direito do mouse no nome da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e selecione **Remover Instância Gerenciada...** . Para obter mais informações, veja [Remover uma instância do SQL Server do Utilitário do SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Inscreva a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] novamente.  
  
    -   No **Gerenciador do Utilitário** no SSMS, clique com o botão direito do mouse no nó **Instâncias Gerenciadas** e selecione **Adicionar Instância Gerenciada...** .  
  
    -   Siga os prompts para concluir o assistente, especificando a nova conta proxy.  
  
## <a name="see-also"></a>Consulte Também  
 [Recursos e tarefas do Utilitário do SQL Server](sql-server-utility-features-and-tasks.md)   
 [Solucionar problemas do Utilitário do SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
