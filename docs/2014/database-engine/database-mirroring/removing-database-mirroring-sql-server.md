---
title: Removendo o espelhamento de banco de dados (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20f1ffabe6726c53c0d9d10f1e9641a25b0e09ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36122005"
---
# <a name="removing-database-mirroring-sql-server"></a>Removendo o espelhamento de banco de dados (SQL Server)
  O proprietário do banco de dados pode interromper manualmente uma sessão de espelhamento de banco de dados a qualquer momento, em qualquer parceiro.  
  
## <a name="impact-of-removing-mirroring"></a>Impacto da remoção do espelhamento  
 Quando o espelhamento é removido, acontece o seguinte:  
  
-   A relação entre os parceiros e entre cada parceiro e a testemunha se rompe permanentemente, caso exista alguma relação.  
  
     Se os parceiros estiverem se comunicando entre si quando a sessão for interrompida, sua relação será imediatamente rompida em ambos os computadores. Se os parceiros não estiverem se comunicando (o banco de dados estiver em um estado DISCONNECTED no momento da interrupção), a relação será imediatamente interrompida no parceiro em que o espelhamento é interrompido; quando o outro parceiro tenta se reconectar, descobre que a sessão de espelhamento de banco de dados foi concluída.  
  
-   As informações sobre a sessão de espelhamento são descartadas, diferentemente de quando uma sessão é pausada. O espelhamento é removido do banco de dados principal e do banco de dados espelho. No **sys.databases**, a coluna **mirroring_state** e todas as demais colunas de espelhamento são definidas como NULL. Para obter mais informações, veja [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).  
  
-   Cada instância de servidor parceiro é deixada com uma cópia separada do banco de dados.  
  
-   O banco de dados espelho é deixado em estado RESTORING (consulte a coluna **estado** do **sys.databases**), porque o banco de dados espelho foi criado usando RESTORE WITH NORECOVERY. Nesse momento, você pode descartar o banco de dados espelho anterior ou restaurá-lo usando WITH RECOVERY. Ao ser recuperado, o banco de dados diverge do banco de dados principal anterior porque a recuperação inicia uma nova bifurcação da recuperação.  
  
> [!NOTE]  
>  Para continuar o espelhamento depois de interromper uma sessão, é preciso estabelecer uma nova sessão de espelhamento de banco de dados. Se você criar um backup de log depois de ter interrompido um espelhamento, deverá registrá-lo no banco de dados espelho antes reiniciar o espelhamento.  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
 **Para remover o espelhamento de banco de dados**  
  
-   [Remover o espelhamento de banco de dados &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
 **Para inicializar o espelhamento de banco de dados**  
  
-   [Estabelecer uma sessão de espelhamento de banco de dados usando a Autenticação do Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Estabelecer uma sessão de espelhamento de banco de dados com a Autenticação do Windows &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a>Consulte também  
 [Espelhamento de banco de dados ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Espelhamento de banco de dados &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Pausando e retomando o espelhamento de banco de dados &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  