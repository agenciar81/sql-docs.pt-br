---
title: Modificar um Proxy do SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 028f92bc953f1baecae1a68bcdc822a0aa84e8fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36115346"
---
# <a name="modify-a-sql-server-agent-proxy"></a>Modificar um proxy do SQL Server Agent
  Este tópico descreve como modificar um proxy do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   **Para modificar um proxy do SQL Server Agent usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
  
-   Os proxies do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usam credenciais para armazenar informações sobre as contas de usuário do Windows. O usuário especificado na credencial deve ter a permissão "Fazer logon como trabalho em lotes" no computador que executa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verifica o acesso a subsistemas de um proxy e fornece acesso ao proxy sempre que a etapa de trabalho é executada. Se o proxy já não tiver acesso ao subsistema, a etapa de trabalho falhará. Caso contrário, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent representará o usuário especificado no proxy e executará a etapa de trabalho.  
  
-   Se o logon do usuário tiver acesso ao proxy ou se o usuário pertencer a alguma função com acesso ao proxy, ele poderá utilizá-lo em uma etapa de trabalho.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Somente membros da função de servidor fixa **sysadmin** podem criar, modificar ou excluir contas proxy.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversion-mdmd-agent-proxy"></a>Para modificar um proxy do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor que contém a conta proxy do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent que você deseja modificar.  
  
2.  Clique no sinal de adição para expandir o **SQL Server Agent**.  
  
3.  Clique no sinal de adição para expandir a pasta **Proxies** .  
  
4.  Clique no sinal de adição para expandir o nó do subsistema do proxy (por exemplo, **Script do ActiveX**).  
  
5.  Clique com o botão direito do mouse na conta proxy cujas propriedades serão modificadas e selecione **Propriedades**.  
  
6.  Na caixa de diálogo *proxy_name***Propriedades da Conta Proxy*, faça alterações na conta proxy conforme necessário. Para obter mais informações sobre as opções dessa caixa de diálogo, consulte [Criar um proxy do SQL Server Agent](create-a-sql-server-agent-proxy.md).  
  
7.  Quando terminar, clique em **OK**.  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversion-mdmd-agent-proxy"></a>Para modificar um proxy do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 Para obter mais informações, consulte [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).  
  
  