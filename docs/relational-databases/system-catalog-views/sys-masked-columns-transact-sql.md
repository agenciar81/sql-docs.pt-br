---
title: sys. masked_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e059265dc5f5e0d2e4bc4a3b1396d2401386d7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102371"
---
# <a name="sysmasked_columns-transact-sql"></a>sys. masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Use a exibição **Sys. masked_columns** para consultar colunas de tabela que têm uma função de máscara de dados dinâmicos aplicada a elas. Essa exibição herda valores da exibição **sys.columns** . Ela retorna todas as colunas na exibição **sys.columns** , mais as colunas **is_masked** e **masking_function** , indicando se a coluna é mascarada e, em caso positivo, qual função de mascaramento foi definida. Essa exibição só mostra colunas com uma função de máscara aplicada.  
  
|Nome da coluna|Tipo de dados|DESCRIÇÃO|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID do objeto ao qual esta coluna pertence.|  
|name|**sysname**|Nome da coluna. É exclusiva no objeto.|  
|column_id|**int**|ID da coluna. É exclusiva no objeto.<br /><br /> Os IDs de coluna podem não ser sequenciais.|  
|**Sys. masked_columns** retorna muito mais colunas herdadas de **Sys. Columns**.|vários|Consulte [Sys. columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) para obter mais definições de coluna.|  
|is_masked|**bit**|Indica se a coluna está mascarada. 1 indica mascarado.|  
|masking_function|**nvarchar(4000)**|A função de mascaramento para a coluna.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="permissions"></a>Permissões  
 Essa exibição retorna informações sobre tabelas em que o usuário tem algum tipo de permissão na tabela ou se o usuário tem a permissão VIEW ANY DEFINITION.  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir une **Sys. masked_columns** a **Sys. Tables** para retornar informações sobre todas as colunas mascaradas.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Máscara de Dados Dinâmicos](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
