---
title: sys. TRACES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 147c080df688ff02d133e725b1ac310439a68eb8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68126682"
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  A exibição do catálogo **Sys. TRACES** contém os rastreamentos em execução atuais no sistema. Essa exibição é destinada como uma substituição para a função **fn_trace_getinfo** .  
  
 Para obter uma lista completa de eventos de rastreamento com suporte, consulte [SQL Server referência de classe de evento](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use exibições do catálogo de Eventos Estendidos.  
  
|Nome da coluna|Tipo de dados|DESCRIÇÃO|  
|-----------------|---------------|-----------------|  
|**sessão**|**int**|ID do rastreamento.|  
|**Estado**|**int**|Status do rastreamento:<br /><br /> 0 = parado<br /><br /> 1 = em execução|  
|**Multi-Path**|**nvarchar(260)**|Caminho do arquivo de rastreamento. Este valor será nulo quando o rastreamento for referente a um conjunto de linhas.|  
|**max_size**|**bigint**|Limite máximo do tamanho do arquivo de rastreamento em megabytes (MB). Este valor será nulo quando o rastreamento for referente a um conjunto de linhas.|  
|**stop_time**|**datetime**|Hora em que o rastreamento em execução será parado.|  
|**max_files**|**int**|Número máximo de arquivos de substituição. Este valor será nulo se o número máximo não for definido.|  
|**is_rowset**|**bit**|1 = rastreamento de conjunto de linhas.|  
|**is_rollover**|**bit**|1 = a opção de substituição está habilitada.|  
|**is_shutdown**|**bit**|1 = a opção de desligamento está habilitada.|  
|**is_default**|**bit**|1 = rastreamento padrão.|  
|**buffer_count**|**int**|Número de buffers em memória usados pelo rastreamento.|  
|**buffer_size**|**int**|Tamanho de cada buffer (KB).|  
|**file_position**|**bigint**|Última posição do arquivo de rastreamento. Este valor será nulo quando o rastreamento for referente a um conjunto de linhas.|  
|**reader_spid**|**int**|ID da sessão do leitor do rastreamento de conjunto de linhas. Esse valor será nulo quando o rastreamento for referente a um arquivo.|  
|**start_time**|**datetime**|Hora de início do rastreamento.|  
|**last_event_time**|**datetime**|Hora em que o último evento foi acionado.|  
|**event_count**|**bigint**|Número total de eventos ocorridos.|  
|**dropped_event_count**|**int**|Número total de eventos descartados.|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Para obter mais informações, consulte [configuração de visibilidade de metadados](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições de catálogo de objeto&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
