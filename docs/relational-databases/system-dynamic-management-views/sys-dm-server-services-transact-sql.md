---
title: sys.dm_server_services (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1c44b269f68b39d633a18f366615fd41b582938
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892957"
---
# <a name="sysdm_server_services-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações sobre os serviços do SQL Server, Texto Completo e do SQL Server Agent na instância atual do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use essa exibição de gerenciamento dinâmico para relatar informações de status sobre esses serviços.  
  
 
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Nome do serviço [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], de texto completo ou de SQL Server Agent. Não pode ser nulo.|  
|startup_type|**int**|Indica o modo inicial do serviço. A seguir estão os possíveis valores e suas descrições correspondentes.<br /><br /> 0: Outros<br />1: Outros<br />2: Automático<br />3: Manual<br />4: Desabilitado<br /><br /> Permite valor nulo.|  
|startup_type_desc|**nvarchar(256)**|Descreve o modo inicial do serviço. A seguir estão os possíveis valores e suas descrições correspondentes.<br /><br /> Outros Outro (inicialização inicial)<br />Outros Outro (início do sistema)<br />Automático: Início automático<br />Manual: Início da demanda<br />Desabilitado: Desabilitado<br /><br /> Não pode ser nulo.|  
|status|**int**|Indica o status atual do serviço. A seguir estão os possíveis valores e suas descrições correspondentes.<br /><br /> 1: Stopped (parado)<br />2: Outro (início pendente)<br />3: Outro (parar pendente)<br />4: Executando<br />5: Outro (continuar pendente)<br />6: Outro (pausa pendente)<br />7: Em Pausa<br /><br /> Permite valor nulo.|  
|status_desc|**nvarchar(256)**|Descreve o status atual do serviço. A seguir estão os possíveis valores e suas descrições correspondentes.<br /><br /> Interrompido O serviço foi interrompido.<br />Outro (Iniciar operação pendente): O serviço está em processo de inicialização.<br />Outro (parar operação pendente): O serviço está em processo de interrupção.<br />Executado O serviço está sendo executado.<br />Outro (continuar as operações pendentes): O serviço está em um estado pendente.<br />Outro (pausa pendente): O serviço está em processo de pausar.<br />Em pausa O serviço foi pausado.<br /><br /> Não pode ser nulo.|  
|process_id|**int**|A ID do processo do serviço. Não pode ser nulo.|  
|last_startup_time|**datetimeoffset(7)**|A data e a hora em que o serviço foi iniciado pela última vez. Permite valor nulo.|  
|service_account|**nvarchar(256)**|A conta autorizada para controlar o serviço. Essa conta pode iniciar ou parar o serviço, ou modificar as propriedades do serviço. Não pode ser nulo.|  
|filename|**nvarchar(256)**|O caminho e o nome do arquivo do serviço executável. Não pode ser nulo.|  
|is_clustered|**nvarchar(1)**|Indica se o serviço é instalado como um recurso de um servidor clusterizado. Não pode ser nulo.|  
|cluster_nodename|**nvarchar(256)**|O nome do nó de cluster no qual o serviço está instalado. Permite valor nulo.|
|instant_file_initialization_enabled|**nvarchar(1)**|Especifica se a inicialização instantânea de arquivo está habilitada para o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] serviço.<br /><br />Y = a inicialização instantânea de arquivo está habilitada para o serviço.<br /><br />N = a inicialização instantânea de arquivo está desabilitada para o serviço.<br /><br /> Permite valor nulo.<br /><br /> **Observação:** Não se aplica a outros serviços, como o SQL Server Agent.<br /><br /> **Aplica-se a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](A partir [!INCLUDE[sssql11](../../includes/sssql11-md.md)] do SP4 e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] do SP1 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]até).|  

## <a name="security"></a>Segurança  
  
### <a name="permissions"></a>Permissões  
 Requer a permissão `VIEW SERVER STATE` no servidor.  
  
## <a name="see-also"></a>Consulte também  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
