---
title: sys. spatial_index_tessellations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4f2f4b8ea0184d063a6423f27fdf2cf9c450a05
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078656"
---
# <a name="sysspatial_index_tessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 Representa as informações sobre o esquema de mosaico e os parâmetros de cada um dos índices espaciais.  
  
> [!NOTE]  
>  Para obter informações sobre mosaico, veja [visão geral de índices espaciais](../../relational-databases/spatial/spatial-indexes-overview.md).  
  

|Nome da coluna|Tipo de dados|DESCRIÇÃO|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID do objeto no qual o índice é definido. Cada par (object_id, index_id) tem uma entrada correspondente em [Sys. spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md).|  
|index_id|**int**|ID do índice espacial no qual a coluna indexada é definida.|  
|tessellation_scheme|**sysname**|Nome do esquema de mosaico, um dos: GEOMETRY_GRID, GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|Coordenada X do canto inferior esquerdo da caixa delimitadora: NULL = não aplicável para um determinado esquema de mosaico (como GEOGRAPHY_GRID) *n* = Se tessellation_scheme for GEOMETRY_GRID, o valor da coordenada x-min.                     **Observação:** As coordenadas definidas pelos parâmetros da caixa delimitadora são interpretadas para cada objeto de acordo com seu [SRID (identificador de referência espacial)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).|  
|bounding_box_ymin|**float(53)**|Coordenada Y do canto inferior esquerdo da caixa delimitadora: NULL = não aplicável para um determinado esquema de mosaico (como GEOGRAPHY_GRID) *n* = Se tessellation_scheme for GEOMETRY_GRID, o valor da coordenada y-min|  
|bounding_box_xmax|**float(53)**|Coordenada X do canto superior direito da caixa delimitadora: NULL = não aplicável para um determinado esquema de mosaico (como GEOGRAPHY_GRID) *n* = Se tessellation_scheme for GEOMETRY_GRID, o valor de coordenada x-Max|  
|bounding_box_ymax|**float(53)**|Coordenada Y do canto superior direito da caixa delimitadora: NULL = não aplicável para um determinado esquema de mosaico (como GEOGRAPHY_GRID) *n* = Se tessellation_scheme for GEOMETRY_GRID, o valor de coordenada y-Max|  
|level_1_grid|**smallint**|Densidade de grade para a grade de nível superior. Se tessellation_scheme for GEOMETRY_GRID ou GEOGRAPHY_GRID, uma das: 16 = 4 por 4 grade (baixa) 64 = 8 por 8 grade (média) 256 = 16 por 16 grade (alta) NULL = não aplicável para determinado tipo de índice espacial ou esquema de mosaico.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_1_grid_desc|**nvarchar (60)**|Densidade da grade para a grade de nível superior, uma das: baixa média alta NULL = não aplicável para o tipo de índice espacial ou o esquema de mosaico fornecido.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_2_grid|**smallint**|Densidade de grade para a grade de 2º nível. Se tessellation_scheme for GEOMETRY_GRID ou GEOGRAPHY_GRID, uma das: 16 = 4 por 4 grade (baixa) 64 = 8 por 8 grade (média) 256 = 16 por 16 grade (alta) NULL = não aplicável para determinado tipo de índice espacial ou esquema de mosaico.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_2_grid_desc|**nvarchar (60)**|Densidade de grade para a grade de 2º nível, uma das: baixa média alta NULL = não aplicável para o tipo de índice espacial ou o esquema de mosaico fornecido.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_3_grid|**smallint**|Densidade de grade para grade de 3º nível.   Se tessellation_scheme for GEOMETRY_GRID ou GEOGRAPHY_GRID, uma das: 16 = 4 por 4 grade (baixa) 64 = 8 por 8 grade (média) 256 = 16 por 16 grade (alta) NULL = não aplicável para determinado tipo de índice espacial ou esquema de mosaico.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_3_grid_desc|**nvarchar (60)**|Densidade de grade para a grade de terceiro nível, uma das: baixa média alta NULL = não aplicável para o tipo de índice espacial ou o esquema de mosaico fornecido.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_4_grid|**smallint**|Densidade de grade para grade de 4º nível. Se tessellation_scheme for GEOMETRY_GRID ou GEOGRAPHY_GRID, uma das: 16 = 4 por 4 grade (baixa) 64 = 8 por 8 grade (média) 256 = 16 por 16 grade (alta) NULL = não aplicável para determinado tipo de índice espacial ou esquema de mosaico.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|level_4_grid_desc|**nvarchar (60)**|Densidade de grade para a grade de 4º nível, uma das: < baixa média alta NULL = não aplicável para o tipo de índice espacial ou o esquema de mosaico fornecido.  NULL é retornado quando o novo mosaico do SQL Server 11 é usado.|  
|cells_per_object|**int**|Número de células por objeto espacial, uma das: If tessellation_scheme é GEOMETRY_GRID ou GEOGRAPHY_GRID, *n* = número de células por objeto NULL = não aplicável a um determinado tipo de índice espacial ou esquema de mosaico|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições de catálogo de objeto&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Visão geral de índices espaciais](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys. Indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
