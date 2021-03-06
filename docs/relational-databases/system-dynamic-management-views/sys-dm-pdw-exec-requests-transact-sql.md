---
title: sys. dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 15049436b0d1769361ae1cfc47b52bfb503ba763
ms.sourcegitcommit: 58c25f47cfd701c61022a0adfc012e6afb9ce6e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256870"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys. dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contém informações sobre todas as solicitações no momento ou recentemente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ativas no. Ele lista uma linha por solicitação/consulta.  
  
|Nome da coluna|Tipo de Dados|DESCRIÇÃO|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar (32)**|Chave para esta exibição. ID numérica exclusiva associada à solicitação.|Exclusivo em todas as solicitações no sistema.|  
|session_id|**nvarchar (32)**|ID numérica exclusiva associada à sessão na qual essa consulta foi executada. Consulte [Sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar (32)**|Status atual da solicitação.|' Running ', ' SUSPENDED ', ' Completed ', ' cancelado ', ' Failed '.|  
|submit_time|**datetime**|Hora em que a solicitação foi enviada para execução.|**DateTime** válido menor ou igual à hora e start_time atuais.|  
|start_time|**datetime**|Hora em que a execução da solicitação foi iniciada.|NULL para solicitações em fila; caso contrário, **DateTime** válido menor ou igual à hora atual.|  
|end_compile_time|**datetime**|Hora em que o mecanismo concluiu a compilação da solicitação.|NULO para solicitações que ainda não foram compiladas; caso contrário, um **DateTime** válido menor que start_time e menor ou igual à hora atual.|
|end_time|**datetime**|Hora em que a execução da solicitação foi concluída, falhou ou foi cancelada.|NULL para solicitações em fila ou ativas; caso contrário, um **DateTime** válido menor ou igual à hora atual.|  
|total_elapsed_time|**int**|Tempo decorrido na execução desde que a solicitação foi iniciada, em milissegundos.|Entre 0 e a diferença entre start_time e end_time.</br></br> Se total_elapsed_time exceder o valor máximo de um inteiro, total_elapsed_time continuará a ser o valor máximo. Essa condição irá gerar o aviso "o valor máximo foi excedido".</br></br> O valor máximo em milissegundos é o mesmo que 24,8 dias.|  
|label|**nvarchar (255)**|Cadeia de caracteres de rótulo opcional associada a algumas instruções de consulta SELECT.|Qualquer cadeia de caracteres contendo ' a-z ', ' A-Z ', ' 0-9 ', ' _ '.|  
|error_id|**nvarchar (36)**|ID exclusiva do erro associado à solicitação, se houver.|Consulte [Sys. dm_pdw_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); Defina como NULL se nenhum erro tiver ocorrido.|  
|database_id|**int**|Identificador do banco de dados usado pelo contexto explícito (por exemplo, USE DB_X).|Consulte a ID em [Sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Mantém o texto completo da solicitação como enviado pelo usuário.|Qualquer consulta ou texto de solicitação válido. Consultas com mais de 4000 bytes são truncadas.|  
|resource_class|**nvarchar (20)**|O grupo de cargas de trabalho usado para esta solicitação. |Classes de recurso estáticas</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Classes de recurso dinâmicas</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(128)**|A importância definindo a solicitação executada em.  Essa é a importância relativa de uma solicitação neste grupo de carga de trabalho e entre grupos de carga de trabalho para recursos compartilhados.  A importância especificada no classificador substitui a configuração de importância do grupo de carga de trabalho.</br>Aplica-se a: SQL Data Warehouse do Azure|NULO</br>baixa</br>below_normal</br>normal (padrão)</br>above_normal</br>alto|
|group_name|**sysname** |Para solicitações que utilizam recursos, group_name é o nome do grupo de carga de trabalho sob o qual a solicitação está sendo executada.  Se a solicitação não utilizar recursos, group_name será NULL.</br>Aplica-se a: SQL Data Warehouse do Azure|
|classifier_name|**sysname**|Para solicitações que utilizam recursos, o nome do classificador usado para atribuir recursos e importância.||
|resource_allocation_percentage|**decimal (5, 2)**|A quantidade percentual de recursos alocados para a solicitação.</br>Aplica-se a: SQL Data Warehouse do Azure|
|result_set_cache|**bit**|Detalha se uma consulta concluída usou o cache do conjunto de resultados.  </br>Aplica-se a: SQL Data Warehouse do Azure| 1 = impacto no cache do conjunto de resultados </br> 0 = erro de cache do conjunto de resultados </br> Valores negativos = motivos pelos quais o cache do conjunto de resultados não foi usado.  Consulte a seção comentários para obter detalhes.|
||||
  
## <a name="remarks"></a>Comentários 
 Para obter informações sobre o máximo de linhas retidas por essa exibição, consulte a seção de metadados no tópico [limites de capacidade](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .

 O result_set_cache é um bitmask do uso de uma consulta do cache do conjunto de resultados.  Esta coluna pode ser a [| (OR-bit)](../../t-sql/language-elements/bitwise-or-transact-sql.md) produto de um ou mais destes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|**1**|Impacto no cache do conjunto de resultados|  
|-**0x00**|Erro de cache do conjunto de resultados|  
|-**0x01**|O cache do conjunto de resultados está desabilitado no banco de dados.|  
|-**0x02**|O cache do conjunto de resultados está desabilitado na sessão. | 
|-**0x04**|O cache do conjunto de resultados está desabilitado devido a nenhuma fonte de dados para a consulta.|  
|-**0x08**|O cache do conjunto de resultados está desabilitado devido a predicados de segurança em nível de linha.|  
|-**0x10**|O cache do conjunto de resultados está desabilitado devido ao uso da tabela do sistema, da tabela temporária ou da tabela externa na consulta.|  
|-**0x20**|O cache do conjunto de resultados está desabilitado porque a consulta contém constantes de tempo de execução, funções definidas pelo usuário ou funções não determinísticas.|  
|-**0x40**|O cache do conjunto de resultados está desabilitado porque o tamanho do conjunto de resultados estimado é muito grande (> 1 milhão linhas).|  
|-**0x80**|O cache do conjunto de resultados está desabilitado porque o conjunto de resultados contém linhas com tamanho grande (>64 KB).|  
  
## <a name="permissions"></a>Permissões

 Requer a permissão VIEW SERVER STAT.  
  
## <a name="security"></a>Segurança

 sys. dm_pdw_exec_requests não filtra os resultados da consulta de acordo com as permissões específicas do banco de dados. Os logons com a permissão VIEW SERVER STATE podem obter resultados da consulta de resultados para todos os bancos de dados  
  
>[!WARNING]  
>Um invasor pode usar sys. dm_pdw_exec_requests para recuperar informações sobre objetos de banco de dados específicos, simplesmente tendo a permissão VIEW SERVER STATE e não tem permissão específica do banco de dados.  
  
## <a name="see-also"></a>Consulte Também

 [Exibições de gerenciamento dinâmico de SQL Data Warehouse e paralelo data warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
