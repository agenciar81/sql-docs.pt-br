---
title: Especificar o local de um servidor de destino | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 99c67c3d0e3afbda0c05e3feb3ed1e0d6951f870
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69552472"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a>Especificar o local de um servidor de destino (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico descreve como especificar o local de um servidor de destino em uma configuração de administração multisservidor no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Restrictions"></a>Limitações e restrições  
Executar essa ação edita o registro. A edição manual do registro não é recomendada, pois alterações incorretas ou não apropriadas podem causar sérios problemas de configuração para o sistema. Portanto, apenas usuários experientes deveriam usar o programa Editor do Registro para editar o registro. Para obter mais informações, consulte a documentação do Microsoft Windows.  
  
### <a name="Security"></a>Segurança  
  
#### <a name="Permissions"></a>Permissões  
Exige associação à função de servidor fixa **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-specify-a-target-servers-location"></a>Para especificar o local de um servidor de destino  
  
1.  No **Pesquisador de Objetos,** clique no sinal de adição para expandir o servidor mestre no qual você deseja especificar o local de um servidor de destino.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent**, aponte para **Administração Multisservidor**e selecione **Gerenciar Servidores de Destino**.  
  
3.  Clique com o botão direito do mouse em um servidor de destino e selecione **Propriedades**.  
  
4.  Na caixa **Local** , insira um local para o servidor e clique em **OK**.  
  
## <a name="TsqlProcedure"></a>Usando Transact-SQL  
  
#### <a name="to-specify-a-target-servers-location"></a>Para especificar o local de um servidor de destino  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
Para obter mais informações, veja [sp_msx_enlist (Transact-SQL)](https://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
