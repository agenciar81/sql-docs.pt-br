---
title: Iniciar, parar ou pausar o serviço
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5b01447d2d7975ea2e6075677a3bf3b01c1c1605
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75257920"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico descreve como iniciar, parar reiniciar o Serviço SQL Server Agent no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
É possível configurar o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent para que se inicie automaticamente quando o sistema operacional for iniciado, mas você também poderá iniciá-lo manualmente quando precisar concluir trabalhos. Você pode interromper ou pausar o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent para suspender trabalhos, notificações de operador e alertas.  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Restrictions"></a>Limitações e restrições  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] O Agent deve estar em execução como um serviço para automatizar tarefas administrativas. Para obter mais informações, consulte [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
-   O Pesquisador de Objetos só exibirá o nó [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se você tiver permissão para usá-lo.  
  
### <a name="Security"></a>Segurança  
  
#### <a name="Permissions"></a>Permissões  
Para executar suas funções, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent deve ser configurado de modo a usar as credenciais de uma conta que seja membro da função de servidor fixa **sysadmin** no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A conta deve ter as seguintes permissões do Windows:  
  
-   Fazer logon como um serviço (SeServiceLogonRight)  
  
-   Substituir um token de nível de processo (SeAssignPrimaryTokenPrivilege)  
  
-   Ignorar verificação completa (SeChangeNotifyPrivilege)  
  
-   Ajustar cotas de memória para um processo (SeIncreaseQuotaPrivilege)  
  
Para obter mais informações sobre as permissões do Windows necessárias para a conta de serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consulte [Selecionar uma conta para o serviço do SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) e [Setting Up Windows Service Accounts (Configurando as contas de serviço do Windows)](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="SSMSProcedure"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Para iniciar, parar ou reiniciar o Serviço SQL Server Agent  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor no qual você deseja gerenciar o Serviço SQL Server Agent.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent**e selecione **Iniciar**, **Parar**ou **Reiniciar**.  
  
3.  Na caixa de diálogo **Controle de Conta de Usuário** , clique em **Sim**.  
  
4.  Quando solicitado a indicar se você deseja executar a ação, clique em **Sim**.  
  
Para obter mais informações, consulte:  
  
-   [Iniciar, parar, pausar, retomar, reiniciar o mecanismo de banco de dados, o SQL Server Agent ou o serviço SQL Server Browser](https://msdn.microsoft.com/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Iniciar automaticamente o SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  
