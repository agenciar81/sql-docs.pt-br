---
title: SET RESULT_SET_CACHING (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d2368cfe612831685da141f99069676ebf33cbb3
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729841"
---
# <a name="set-result-set-caching-transact-sql"></a>SET RESULT SET CACHING (Transact-SQL) 

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Controla o comportamento de cache do conjunto de resultados da sessão do cliente atual.  

Aplica-se a ao SQL Data Warehouse do Azure (versão prévia)
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  

Execute este comando quando estiver conectado ao banco de dados do usuário para o qual você deseja definir a configuração result_set_caching.

**Ligado**   
Habilita o armazenamento em cache do conjunto de resultados da sessão do cliente atual.  O armazenamento em cache do conjunto de resultados não poderá ser ATIVADO para uma sessão se estiver DESATIVADO no nível do banco de dados.

**Desligado**   
Desabilita o armazenamento em cache do conjunto de resultados da sessão do cliente atual.

## <a name="examples"></a>Exemplos

Consulte a coluna result_cache_hit em [sys.dm_pdw_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql) com o request_id de uma consulta para ver se essa consulta foi executada com um acerto ou erro do cache de resultados.

```sql
SELECT result_cache_hit
FROM sys.dm_pdw_exec_requests
WHERE request_id = 'QID58286'
```

## <a name="permissions"></a>Permissões

Requer associação à função pública

## <a name="see-also"></a>Confira também
[Ajuste de desempenho com armazenamento em cache do conjunto de resultados](/azure/sql-data-warehouse/performance-tuning-result-set-caching)</br>
[Opções ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-showresultcachespaceused-transact-sql)</br>
[DBCC DROPRESULTSETCACHE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)