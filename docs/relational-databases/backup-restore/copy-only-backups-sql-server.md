---
title: Backups somente cópia | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2018
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: eac98b2d0b5e7ac8c0cd8f765d172333f5ba0a30
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71341862"
---
# <a name="copy-only-backups"></a>Backups somente cópia
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Um *backup somente cópia* é um backup do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que não depende da sequência de backups convencionais do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Geralmente, um backup altera o banco de dados e afeta a forma de restauração dos backups posteriores. Contudo, ocasionalmente, é útil fazer um backup para uma finalidade especial sem afetar o backup global e os procedimentos de restauração do banco de dados. Backups de cópia servem para essa finalidade.  
  
 Os tipos de backups somente cópia são:  
  
- Backups completos somente cópia (todos os modelos de recuperação)  
  
     Um backup somente cópia não pode servir como base diferencial ou backup diferencial e não afeta a base diferencial.  
  
     Restaurar um backup completo somente cópia é o mesmo que restaurar qualquer outro backup completo.  
  
- Backups de log somente cópia (só modelo de recuperação completa e modelo de recuperação bulk-logged)  

     Um backup de log somente cópia preserva o ponto de arquivo de log existente e, portanto, não afeta a sequência de backups de log regulares. Backups de log somente cópia em geral são desnecessários. Em vez disso, você pode criar um novo backup de log de rotina (usando WITH NORECOVERY) e usar esse backup com qualquer backup de log anterior necessário para a sequência de restauração. No entanto, um backup de log somente cópia pode ser útil às vezes para executar uma restauração online. Para um exemplo disso, consulte [Exemplo: Restauração online de um arquivo de leitura/gravação #40;Modelo de recuperação completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md).  

     O log de transações nunca é truncado após um backup somente cópia.  
  
 Backups somente cópia são registrados na coluna **is_copy_only** da tabela [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) .  
  
## <a name="to-create-a-copy-only-backup"></a>Para criar um backup somente cópia  
 Você pode criar um backup somente cópia usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]ou PowerShell.  

### <a name="examples"></a>Exemplos  
###  <a name="SSMSProcedure"></a> A. Usando o SQL Server Management Studio  
Neste exemplo, será feito backup somente cópia do banco de dados `Sales` em disco no local de backup padrão.

[!INCLUDE[Freshness](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

1. No **Pesquisador de Objetos**, conecte-se a uma instância do Mecanismo de Banco de Dados do SQL Server e expanda-a.

1. Expanda **Banco de Dados**, clique com o botão direito do mouse em `Sales`, aponte para **Tarefas**e clique em **Fazer Backup...** .

1. Na página **Geral** , na seção **Origem** , marque a caixa de seleção **Backup somente cópia** .

1. Clique em **OK**.

###  <a name="TsqlProcedure"></a>B. Usando Transact-SQL  
Este exemplo cria um backup somente cópia para o banco de dados `Sales` com o parâmetro COPY_ONLY.  Também é feito um backup somente cópia do log de transações.

```sql
BACKUP DATABASE Sales
TO DISK = 'E:\BAK\Sales_Copy.bak'
WITH COPY_ONLY;

BACKUP LOG Sales
TO DISK = 'E:\BAK\Sales_LogCopy.trn'
WITH COPY_ONLY;
```
  
> [!NOTE]  
> COPY_ONLY não tem nenhum efeito quando é especificado com a opção DIFFERENTIAL.  

  
###  <a name="PowerShellProcedure"></a>C. Usando o PowerShell  
Este exemplo cria um backup somente cópia para o banco de dados `Sales` com o parâmetro -CopyOnly.  
```powershell
Backup-SqlDatabase -ServerInstance 'SalesServer' -Database 'Sales' -BackupFile 'E:\BAK\Sales_Copy.bak' -CopyOnly
```  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
 **Para criar um backup completo ou de log**  
  
- [Criar um backup completo de banco de dados &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
- [Fazer backup de um log de transações &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  

 **Para exibir backups somente cópia**  
  
- [conjunto de backup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
 **Para configurar e usar o provedor do SQL Server PowerShell**  
  
- [Provedor do SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell-provider.md)  

## <a name="see-also"></a>Confira também  
 [Visão geral do backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Modelos de recuperação &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Copiar bancos de dados com backup e restauração](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Visão geral de restauração e recuperação &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[Backup-SqlDatabase](/powershell/module/sqlserver/backup-sqldatabase)

  
