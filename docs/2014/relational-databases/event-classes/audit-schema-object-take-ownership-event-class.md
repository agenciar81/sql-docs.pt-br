---
title: Classe de evento Audit Schema Object Take Ownership | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Audit Schema Object Take Ownership event class
ms.assetid: 66f39d9b-9ec2-48a7-8a9e-1b42931299c9
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1038af637f3e91d2e2c431ec241d11a5564bd060
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36120366"
---
# <a name="audit-schema-object-take-ownership-event-class"></a>Classe de evento Audit Schema Object Take Ownership
  A classe de evento **Audit Schema Object Take Ownership** ocorre quando as permissões para alterar o proprietário do objeto de esquema (como uma tabela, um procedimento ou funções) são verificadas. Isso acontece quando a instrução ALTER AUTHORIZATION é usada para atribuir um proprietário a um objeto.  
  
## <a name="audit-schema-object-take-ownership-event-class-data-columns"></a>Colunas de dados da classe de evento Audit Schema Object Take Ownership  
  
|Nome da coluna de dados|Tipo de dados|Description|ID da coluna|Filtrável|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome do aplicativo cliente que criou a conexão para uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essa coluna é populada com os valores passados pelo aplicativo e não com o nome exibido do programa.|10|Sim|  
|**DatabaseID**|**int**|ID do banco de dados especificado pela instrução USE de *database* ou o banco de dados padrão se nenhuma instrução USE de *database* tiver sido emitida para uma determinada instância. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] exibirá o nome do banco de dados se a coluna de dados **ServerName** for capturada no rastreamento e o servidor estiver disponível. Determine o valor para um banco de dados usando a função DB_ID.|3|Sim|  
|**DatabaseName**|**nvarchar**|Nome do banco de dados no qual a instrução do usuário está sendo executada.|35|Sim|  
|**DBUserName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do cliente.|40|Sim|  
|**EventSequence**|**int**|Sequência de um determinado evento na solicitação.|51|não|  
|**HostName**|**nvarchar**|Nome do computador no qual o cliente está sendo executado. Essa coluna de dados será populada se o cliente fornecer o nome do host. Para determinar o nome do host, use a função HOST_NAME.|8|Sim|  
|**IsSystem**|**int**|Indica se o evento ocorreu em um processo do sistema ou do usuário. 1 = sistema, 0 = usuário.|60|Sim|  
|**LoginName**|**nvarchar**|Nome do logon do usuário (logon de segurança do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou as credenciais de logon do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows no formato DOMÍNIO\nomedeusuário).|11|Sim|  
|**LoginSid**|**image**|Número SID (identificação de segurança) do usuário que fez logon. Você pode encontrar essas informações na exibição de catálogo **sys.server_principals** . Cada SID é exclusivo para cada logon no servidor.|41|Sim|  
|**NTDomainName**|**nvarchar**|O domínio do Windows ao qual o usuário pertence.|7|Sim|  
|**NTUserName**|**nvarchar**|Nome do usuário do Windows.|6|Sim|  
|**ObjectName**|**nvarchar**|Nome do objeto que está sendo referenciado.|34|Sim|  
|**ObjectType**|**int**|Valor que representa o tipo do objeto envolvido no evento. O valor retornado para essa coluna é uma combinação do valor correspondente na coluna **tipo** da exibição de catálogo **sys.objects** e dos valores listados em [Coluna de evento de rastreamento ObjectType](objecttype-trace-event-column.md).|28|Sim|  
|**OwnerName**|**nvarchar**|Nome de usuário de banco de dados do proprietário do objeto.|37|Sim|  
|**ParentName**|**nvarchar**|Nome do esquema que contém o objeto.|59|Sim|  
|**RequestID**|**int**|ID da solicitação que contém a instrução.|49|Sim|  
|**ServerName**|**nvarchar**|Nome da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que está sendo rastreada.|26|não|  
|**SessionLoginName**|**nvarchar**|Nome de logon do usuário que originou a sessão. Por exemplo, para se conectar ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando o Logon1 e executar uma instrução como Logon2, o **SessionLoginName** mostrará o Logon1 e o **LoginName** mostrará o Logon2. Essa coluna exibe logons do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e do Windows.|64|Sim|  
|**SPID**|**int**|Identificação da sessão em que ocorreu o evento.|12|Sim|  
|**StartTime**|**datetime**|Hora de início do evento, se disponível.|14|Sim|  
|**Êxito**|**int**|1 = êxito. 0 = falha. Por exemplo, o valor 1 indica êxito em uma verificação de permissões e o valor 0 indica falha nessa verificação.|23|Sim|  
|**TargetUserName**|**nvarchar**|Para ações direcionadas a um usuário do banco de dados (por exemplo, concessão de permissão a um usuário), o nome desse usuário.|39|Sim|  
|**TextData**|**ntext**|Valor do texto dependente da classe de evento capturada no rastreamento.|1|Sim|  
|**TransactionID**|**bigint**|ID da transação atribuída pelo sistema.|4|Sim|  
|**XactSequence**|**bigint**|Token usado para descrever a transação atual.|50|Sim|  
  
## <a name="see-also"></a>Consulte também  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  