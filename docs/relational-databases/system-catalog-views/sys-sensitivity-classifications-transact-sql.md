---
title: sys.sensitivity_classifications (Transact-SQL) | Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a9d14cd93b08c0094ad984a6469b433e0b266479
ms.sourcegitcommit: 77293fb1f303ccfd236db9c9041d2fb2f64bce42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929775"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retorna uma linha para cada item classificado no banco de dados.

|Nome da coluna|Tipo de dados|Descrição|
|-----------------|---------------|-----------------|  
|**class**|**int**|Identifica a classe do item no qual a classificação existe|  
|**class_desc**|**varchar(16)**|Uma descrição da classe do item no qual a classificação existe|  
|**major_id**|**int**|ID do item no qual a classificação existe. < br \>< br \>se a classe for 0, major_id será sempre 0.<br>Se a classe for 1, 2 ou 7, major_id será object_id.|  
|**minor_id**|**int**|ID secundária do item no qual a classificação existe, interpretada de acordo com sua classe.<br><br>Se Class = 1, minor_id for o column_id (if Column), Else 0 (if Object).<br>Se class = 2, minor_id será parameter_id.<br>Se Class = 7, minor_id for o index_id. |  
|**label**|**sysname**|O rótulo (legível por humanos) atribuído para a classificação de sensibilidade|  
|**label_id**|**sysname**|Uma ID associada ao rótulo, que pode ser usada por um sistema de proteção de informações, como a proteção de informações do Azure (AIP)|  
|**information_type**|**sysname**|O tipo de informação (legível humana) atribuído para a classificação de sensibilidade|  
|**information_type_id**|**sysname**|Uma ID associada ao tipo de informação, que pode ser usada por um sistema de proteção de informações, como a proteção de informações do Azure (AIP)|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Comentários  

- Essa exibição fornece visibilidade do estado de classificação do banco de dados. Ele pode ser usado para gerenciar as classificações de banco de dados, bem como para gerar relatórios.
- Atualmente, há suporte apenas para a classificação de colunas de banco de dados. Consequente
    - **classe** -sempre terá o valor 1 (representando uma coluna)
    - **class_desc** -sempre terá o valor *OBJECT_OR_COLUMN*
    - **major_id** -representa a ID da tabela que contém a coluna classificada, correspondente a sys. All _objects. object_id
    - **minor_id** -representa a ID da coluna na qual a classificação existe, correspondendo a sys. All _columns. column_id

## <a name="examples"></a>Exemplos

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Listando todas as colunas classificadas e sua classificação correspondente

O exemplo a seguir retorna uma tabela que lista o nome da tabela, o nome da coluna, o rótulo, a ID do rótulo, o tipo de informação, a ID do tipo de informação para cada coluna classificada no banco de dados.

> [!NOTE]
> O rótulo é uma palavra-chave para SQL Data Warehouse do Azure.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>Consulte também  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Introdução à Proteção de Informações do SQL](https://aka.ms/sqlip)
