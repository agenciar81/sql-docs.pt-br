---
title: Criar um instantâneo de banco de dados (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
ms.openlocfilehash: a0acec2dd2e4e7e9d08d979febf85cf98f883e77
ms.sourcegitcommit: 5a03dc2bba481c2e2f03d67f6ee9486fc9f8ba95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71066872"
---
# <a name="create-a-database-snapshot-transact-sql"></a>Criar um instantâneo do banco de dados (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  A única maneira de criar um instantâneo do banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é usando o [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] não dá suporte à criação de instantâneos de banco de dados.  
  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
 O banco de dados de origem, que pode usar qualquer modelo de recuperação, deve atender aos seguintes pré-requisitos:  
  
-   A instância de servidor deve estar sendo executada em uma edição do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que oferece suporte a instantâneos de banco de dados. Para obter mais informações sobre o suporte para instantâneos de banco de dados no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consulte [Recursos com suporte nas edições do SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
-   O banco de dados de origem precisa estar online, a menos que se trate de um banco de dados espelho dentro de uma sessão de espelhamento de banco de dados.  
  
-   Para criar um instantâneo do banco de dados em um banco de dados espelho, o banco de dados precisa estar no [estado de espelhamento](../../database-engine/database-mirroring/mirroring-states-sql-server.md)sincronizado.  
  
-   O banco de dados de origem não pode ser configurado como banco de dados compartilhado escalonável.  

- O banco de dados de origem não deve conter um grupo de arquivos MEMORY_OPTIMIZED_DATA. Para obter mais informações, consulte [Recursos do SQL Server sem suporte no OLTP in-memory](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md).

> [!IMPORTANT]
> Para obter informações sobre outras considerações significativas, consulte [Instantâneos de banco de dados &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="Recommendations"></a> Recomendações  
 Esta seção aborda as seguintes práticas recomendadas:  
  
-   [Melhor prática: Nomeando instantâneos do banco de dados](#Naming)  
  
-   [Melhor prática: Limitando o número de instantâneos do banco de dados](#Limiting_Number)  
  
-   [Melhor prática: Conexões de cliente com um instantâneo do banco de dados](#Client_Connections)  
  
####  <a name="Naming"></a> Melhor prática: Nomeando instantâneos de banco de dados  
 Antes de criar instantâneos, é importante considerar como serão nomeados. Cada instantâneo de banco de dados requer um nome exclusivo de banco de dados. Para facilidade administrativa, o nome de um instantâneo pode inserir informações que identifiquem o banco de dados, como:  
  
-   O nome do banco de dados de origem.  
  
-   Uma indicação de que o nome novo destina-se a um instantâneo.  
  
-   A data de criação e o horário do instantâneo, um número de sequência ou alguma outra informação, como hora do dia, para distinguir instantâneos sequenciais em um determinado banco de dados.  
  
 Por exemplo, considere uma série de instantâneos para o banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Três instantâneos diários são criados em intervalos de 6 horas entre 6h e 18h, com base em um relógio de 24 horas. Cada instantâneo diário é mantido durante 24 horas antes de ser descartado e substituído por um instantâneo novo de mesmo nome. Note que cada nome de instantâneo indica a hora, mas não o dia:  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 Como alternativa, se a hora de criação desses instantâneos diários variar de um dia para o outro, uma convenção de nomenclatura menos precisa poderia ser preferível, como por exemplo:  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
#### <a name="Limiting_Number"></a> Melhor prática: Limitando o número de instantâneos de banco de dados  
 Criar uma série de instantâneos do longo do tempo captura instantâneos sequenciais do banco de dados de origem. Cada instantâneo persiste até que seja explicitamente descartado. Como cada instantâneo continuará crescendo à medida que as páginas originais forem atualizadas, você pode preferir conservar espaço de disco excluindo um instantâneo mais antigo depois de criar um instantâneo novo.  
  

**Observação!** Para reverter a um instantâneo de banco de dados, você precisa excluir qualquer outro instantâneo desse banco de dados.  
  
####  <a name="Client_Connections"></a> Melhor prática: Conexões do cliente a um instantâneo de banco de dados  
 Para usar um instantâneo de banco de dados, os clientes precisam saber onde encontrá-lo. Os usuários podem ler de um instantâneo de banco de dados enquanto outro está sendo criado ou excluído. Porém, quando você substituir um instantâneo novo por um já existente, será necessário redirecionar os clientes ao novo instantâneo. Os usuários podem se conectar manualmente a um instantâneo de banco de dados por meio do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. No entanto, para dar suporte a um ambiente de produção, você deverá criar uma solução programática que direcione de maneira transparente os clientes de gravação de relatório ao último instantâneo de banco de dados do banco de dados.  
  

  
####  <a name="Permissions"></a> Permissões  
 Qualquer usuário que possa criar um banco de dados pode criar um instantâneo de banco de dados, entretanto, para criar um instantâneo de um banco de dados espelho, você deve ser um membro da função de servidor fixa **sysadmin** .  
  
##  <a name="TsqlProcedure"></a> Como criar um instantâneo de banco de dados (usando o Transact-SQL)  
 **Para criar um instantâneo do banco de dados**  
  
>  Para obter um exemplo deste procedimento, consulte [Exemplos (Transact-SQL)](#TsqlExample), posteriormente nesta seção.  
  
1.  Com base no tamanho atual do banco de dados de origem, verifique se você tem espaço em disco suficiente para suportar o instantâneo do banco de dados. O tamanho máximo de um instantâneo do banco de dados é o tamanho do banco de dados de origem no momento da criação do instantâneo. Para obter mais informações, consulte [Exibir o tamanho do arquivo esparso de um instantâneo de banco de dados &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).  
  
2.  Emita uma instrução CREATE DATABASE nos arquivos usando a cláusula AS SNAPSHOT OF. Criar um instantâneo requer especificar o nome lógico de cada arquivo de banco de dados do banco de dados de origem. A sintaxe é a seguinte:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     CREATE DATABASE *database_snapshot_name*  
  
     ON  
  
     (  
  
     NAME =*logical_file_name*,  
  
     FILENAME ='*os_file_name*'  
  
     ) [ ,...*n* ]  
  
     AS SNAPSHOT OF *source_database_name*  
  
     [;]  
  
     Where *source_**database_name* is the source database, *logical_file_name i*s the logical name used in SQL Server when referencing the file, *os_file_name* is the path and file name used by the operating system when you create the file, and *database_snapshot_name* is the name of the snapshot to which you want to revert the database. For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
    > [!NOTE]  
    >  When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.  
  
###  <a name="TsqlExample"></a> Exemplos (Transact-SQL)  
  
> [!NOTE]  
>  A extensão `.ss` usada nos exemplos é arbitrária.  
  
 Esta seção contém os seguintes exemplos:  
  
-   A. [Criando um instantâneo no banco de dados AdventureWorks](#Creating_on_AW)  
  
-   B. [Criando um instantâneo no banco de dados Vendas](#Creating_on_Sales)
  
####  <a name="Creating_on_AW"></a> A. Criando um instantâneo no banco de dados AdventureWorks  
 Este exemplo cria um instantâneo de banco de dados no banco de dados `AdventureWorks` . O nome do instantâneo, `AdventureWorks_dbss_1800`e o nome do arquivo de seu respectivo arquivo esparso, `AdventureWorks_data_1800.ss`, indicam a hora da criação, 18h00.  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="Creating_on_Sales"></a> B. Criando um instantâneo no banco de dados Vendas  
 Este exemplo cria um instantâneo do banco de dados, `sales_snapshot1200`, no banco de dados `Sales` . Este banco de dados foi criado no exemplo “Criando um banco de dados que tem grupos de arquivos” em [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
  
-   [Exibir um instantâneo de banco de dados &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [Reverter um banco de dados para um instantâneo do banco de dados](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [Remover um instantâneo do banco de dados &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>Consulte Também  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Instantâneos de banco de dados &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  

