---
title: Atribuir um trabalho a uma categoria de trabalho | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ff6fa55f2c4accc16a89758d0687519d76b51f6c
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69553369"
---
# <a name="assign-a-job-to-a-job-category"></a>Atribuir um trabalho a uma categoria de trabalho

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico descreve como atribuir trabalhos do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a categorias de trabalho no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] ou o SQL Server Management Objects.  
  
As categorias de trabalho ajudam a organizar os trabalhos de modo a facilitar sua filtragem e agrupamento. Por exemplo, você pode organizar todos os seus trabalhos de backup de banco de dados na categoria Manutenção de Banco de Dados. É possível atribuir trabalhos a categorias de trabalho internas ou criar uma categoria de trabalho definida pelo usuário e atribuir trabalhos a ela.  

## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Security"></a>Segurança  
Para obter informações detalhadas, consulte [Implementar a segurança do SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Para atribuir um trabalho a uma categoria de trabalho  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor no qual você deseja atribuir um trabalho a uma categoria de trabalho.  
  
2.  Clique no sinal de adição para expandir o **SQL Server Agent**.  
  
3.  Clique no sinal de adição para expandir a pasta **Trabalhos** .  
  
4.  Clique com o botão direito do mouse no trabalho que deseja editar e selecione **Propriedades**.  
  
5.  Na caixa de diálogo **Propriedades do Trabalho –** _job\_name_, na lista **Categoria**, selecione a categoria de trabalho à qual você deseja atribuí-lo.  
  
6.  Clique em **OK**.  
  
## <a name="TSQL"></a>Usando Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Para atribuir um trabalho a uma categoria de trabalho  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Para obter mais informações, veja [sp_update_job (Transact-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="SMO"></a>Usando o SQL Server Management Objects  
**Para atribuir um trabalho a uma categoria de trabalho**  
  
Use a classe **JobCategory** com uma linguagem de programação à sua escolha, como Visual Basic, Visual C# ou PowerShell.  
  
