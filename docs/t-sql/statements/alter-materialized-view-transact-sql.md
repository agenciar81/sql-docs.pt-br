---
title: ALTER MATERIALIZED VIEW (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: data-warehouse
ms.topic: language-reference
f1_keywords:
- ALTER_VIEW_TSQL
- ALTER VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], modifying
- views [SQL Server], modifying
- modifying views
- ALTER VIEW statement
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: b03515cb8fa6780f43927327b4afec21b3933acb
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68809742"
---
# <a name="alter-materialized-view-transact-sql-preview"></a>ALTER MATERIALIZED VIEW (Transact-SQL) (versão prévia)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifica uma exibição materializada criada anteriormente. ALTER VIEW não afeta disparadores ou procedimentos armazenados dependentes e não altera permissões.  
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```
ALTER MATERIALIZED VIEW [ schema_name . ] view_name
{
      REBUILD | DISABLE
}
[;]
```  
  
## <a name="arguments"></a>Argumentos

 *schema_name*     
 É o nome do esquema ao qual a exibição pertence.  
  
 *view_name*     
 É o nome da exibição materializada a alterar.  
  
*REBUILD*   
Retoma a exibição materializada.

*DISABLE*   
Suspende a manutenção da exibição materializada, mantendo os metadados e as permissões.  Resolve todas as consultas em relação à exibição materializada em um estado desabilitado em relação às tabelas subjacentes.
  
## <a name="permissions"></a>Permissões

Requer a permissão ALTER na tabela ou exibição.
  
## <a name="examples"></a>Exemplos

Este exemplo desabilita uma exibição materializada e a coloca no modo suspenso.
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View DISABLE;  
```  
  
Este exemplo retoma a exibição materializada ao recompilá-la.  
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View REBUILD;  
```  
  
## <a name="see-also"></a>Confira também

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[Exibições de Catálogo do SQL Data Warehouse e Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Exibições do sistema com suporte no SQL Data Warehouse do Azure](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instruções T-SQL com suporte no SQL Data Warehouse do Azure](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
