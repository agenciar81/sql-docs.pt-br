---
title: SQL Server, objeto Métodos de Acesso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Access Methods object
- SQLServer:Access Methods
ms.assetid: 27558585-e780-48bb-a042-30d664662ebc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96229c151957cd0b0bf91c248b4d96a294864181
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63251106"
---
# <a name="sql-server-access-methods-object"></a>SQL Server, Objeto Métodos de Acesso
  O objeto de **métodos** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] acesso no fornece contadores para monitorar como os dados lógicos são acessados no banco de dado. O acesso físico às páginas do banco de dados no disco é monitorado usando os contadores do **Gerenciador de Buffer** . Monitorar os métodos usados para acessar os dados armazenados no banco de dados pode ajudá-lo a determinar se o desempenho da consulta pode ser melhorado, adicionando ou modificando índices, adicionando ou movendo partições, adicionando arquivos ou grupos de arquivo, desfragmentando índices ou regravando consultas. Os contadores dos **Métodos de Acesso** também podem ser usados para monitorar a quantidade de dados, índices e espaço livre dentro do banco de dados, indicando assim o volume e a fragmentação de dados para cada instância do servidor. A fragmentação excessiva do índice pode prejudicar o desempenho.  
  
 Para obter informações mais detalhadas sobre volume, fragmentação e uso de dados, use as seguintes exibições de gerenciamento dinâmico:  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)  
  
-   [sys. dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql)  
  
-   [sys. dm_db_index_usage_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql)  
  
 Para consumo de espaço em **tempdb** no arquivo, tarefa e nível de sessão, use essas exibições de gerenciamento dinâmico:  
  
-   [sys. dm_db_file_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql)  
  
-   [sys. dm_db_task_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql)  
  
-   [sys. dm_db_session_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql)  
  
 Esta tabela descreve os contadores dos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Access Methods** .  
  
|Contadores dos Métodos de Acesso do SQL Server|DESCRIÇÃO|  
|----------------------------------------|-----------------|  
|**Lotes de limpeza de AU/s**|O número de lotes por segundo concluídos com êxito pela tarefa em segundo plano responsável pela limpeza de unidades de alocação canceladas e adiadas.|  
|**Limpezas de AU/s**|O número de unidades de alocação por segundo descartadas com sucesso pela tarefa em segundo plano responsável pela limpeza das unidades de alocação canceladas e adiadas. Cada descarte de unidade de alocação requer vários lotes.|  
|**Contagem de criação de LOB por referência**|Contagem de valores de LOB (objeto grande) que foram transmitidos por referência. LOBs por referência são usados em determinadas operações em massa para evitar o custo de transmiti-los por valor.|  
|**Contagem de uso de LOB por referência**|Contagem de valores de LOB por referência que foram usados. LOBs por referência são usados em determinadas operações em massa para evitar o custo de transmiti-los por valor.|  
|**Contar leitura antecipada de LOB**|Contagem de páginas de LOB com emissão de leitura antecipada.|  
|**Contar pull na linha**|Contagem de valores da coluna que foram puxadas para dentro da linha.|  
|**Contar push para fora da linha**|Contagem de valores da coluna que foram empurrados para fora da linha.|  
|**Adiada ignorada aus**|O número de unidades de alocação aguardando para serem descartadas pela tarefa em segundo plano responsável pela limpeza das unidades de alocação canceladas e adiadas.|  
|**Conjuntos de linhas adiados ignorados**|O número de conjuntos de linhas criados como resultado de operações anuladas de compilação de índices online, que estão aguardando para serem descartados pela tarefa em segundo plano responsável pela limpeza dos conjuntos de linhas adiado ignorado.|  
|**Limpezas de conjunto de linhas descartadas/s**|O número de conjuntos de linhas, por segundo criados como resultado de operações anuladas de compilação de índices online, que foram cancelados com êxito pela tarefa em segundo plano responsável pela limpeza de conjuntos de linhas cancelados e adiados.|  
|**Conjuntos de linhas ignorados/s**|O número de conjuntos de linhas por segundo, criados como resultado de operações anuladas de compilação de índices online, que foram ignorados pela tarefa em segundo plano responsável pela limpeza de conjuntos de linhas cancelados e adiados criados.|  
|**Desalocações de extensão/s**|Número de extensões desalocadas por segundo em todos os bancos de dados nesta instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Extensões alocadas/s**|Número de extensões alocadas por segundo em todos os bancos de dados nesta instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Falha em lotes de limpeza de AU/s**|O número de lotes por segundo que apresentaram falhas e precisaram ser repetidos pela tarefa em segundo plano responsável pela limpeza das unidades de alocação canceladas e adiadas. As falhas podem estar relacionadas à falta de memória ou de espaço no disco, a uma falha de hardware ou outros motivos.|  
|**Falha no cookie da página de folha**|O número de vezes em que não foi possível usar um cookie na página de folha durante uma pesquisa de índice, devido a alterações que ocorreram nessa página de folha. O cookie é usado para acelerar a pesquisa de índice.|  
|**Falha no cookie na página de árvore**|O número de vezes em que não foi possível usar um cookie na página de árvore durante uma pesquisa de índice, devido a alterações que ocorreram nas páginas pai dessas páginas de árvore. O cookie é usado para acelerar a pesquisa de índice.|  
|**Registros encaminhados/s**|Número de registros por segundo encontrados por ponteiros de registros encaminhados.|  
|**Buscas de página de espaço livre/s**|Número de páginas encontradas por segundo por exames de espaço livre. Esses exames pesquisam o espaço livre em páginas já alocadas a uma unidade de alocação para atender a solicitações ou para inserir ou modificar fragmentos de registro.|  
|**Exames de espaço livre/s**|Número de exames por segundo que foram iniciados para pesquisar espaço livre em páginas já alocadas a uma unidade de alocação para inserir ou modificar fragmento de registro. Cada exame pode localizar várias páginas.|  
|**Exames totais/s**|Número de exames totais irrestritos por segundo. Eles podem ser exames da tabela base ou do índice total.|  
|**Pesquisas de índice/s**|Número de pesquisas de índice por segundo. Eles são usados para iniciar exames de intervalo, reposicionar um exame de intervalo, revalidar um ponto de exame, buscar um registro de índice único e procurar o índice para localizar onde inserir uma nova linha.|  
|**Contagem de criação de LobHandle**|Contagem de LOBs temporários criados.|  
|**Contagem de destruição de LobHandle**|Contagem de LOBs temporários destruídos.|  
|**Contagem de criação de Provedor LobSS**|Contagem de SSPs (Provedores de Serviço de Armazenamento) de LOB criados. Uma tabela de trabalho criada por SSP de LOB.|  
|**Contagem de destruição de Provedor LobSS**|Contagem de SSP de LOB destruído.|  
|**Contagem de truncamento do Provedor LobSS**|Contagem de SSP de LOB truncado.|  
|**Alocações de página mistas/s**|Número de páginas alocadas por segundo a partir de extensões mistas. Essas páginas podem ser usadas para armazenar as páginas IAM e as primeiras oito páginas alocadas a uma unidade de alocação.|  
|**Tentativas de compactação de página/s**|Número de páginas avaliadas para a compactação do nível de página. Inclui as páginas que não foram compactadas porque poderia haver economias significativas. Inclui todos os objetos na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter informações sobre objetos específicos, veja [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).|  
|**Desalocações de página/s**|Número de páginas desalocadas por segundo em todos os bancos de dados nesta instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Páginas de extensões mistas e de extensões uniformes estão incluídas.|  
|**Divisões de página/s**|Número de divisões de página por segundo que ocorrem em decorrência do estouro de páginas de índice.|  
|**Páginas alocadas/s**|Número de páginas alocadas por segundo em todos os bancos de dados nesta instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elas incluem alocações de páginas a partir de extensões mistas e de extensões uniformes.|  
|**Páginas compactadas/s**|Número de páginas de dados compactadas usando compactação de PÁGINA. Inclui todos os objetos na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter informações sobre objetos específicos, veja [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).|  
|**Exames de investigação/s**|Número de exames de sondagem por segundo usados para localizar no máximo uma linha qualificada em um índice ou em uma tabela base diretamente.|  
|**Exames de intervalo/s**|Número de exames de intervalo qualificados em índices por segundo.|  
|**Revalidações de ponto de exame/s**|Número de vezes por segundo que o ponto de exame teve que ser revalidado para continuar o exame.|  
|**Registros fantasmas ignorados/s**|Número de registros fantasmas por segundo ignorados durante exames.|  
|**Escalonamentos de bloqueios de tabela/s**|Número de vezes que bloqueios em uma tabela foram escalados para a granularidade TABELA ou HoBT.|  
|**Cookie usado na página de folha**|Número de vezes que um cookie na página de folha foi usado com êxito durante uma pesquisa de índice, pois nenhuma alteração ocorreu nesta página de folha. O cookie é usado para acelerar a pesquisa de índice.|  
|**Cookie usado na página de árvore**|Número de vezes que um cookie na página de árvore foi usado com êxito durante uma pesquisa de índice, pois nenhuma alteração ocorreu na página pai dessa página de árvore. O cookie é usado para acelerar a pesquisa de índice.|  
|**Arquivos de criação/s**|Número de arquivos de trabalho criados por segundo. Por exemplo, os arquivos de trabalho podem ser usados para armazenar os resultados temporários de junções de hash e de agregações de hash.|  
|**Tabelas de criação/s**|Número de tabelas de trabalho criadas por segundo. Por exemplo, tabelas de trabalho podem ser usadas para armazenar os resultados temporários de spool de consultas, variáveis LOB, variáveis XML e cursores.|  
|**Tabelas da taxa de cache**|Porcentagem de tabelas de trabalho criadas em que as duas páginas iniciais de uma determinada tabela não estavam alocadas, mas estavam imediatamente disponíveis no cache de tabelas de trabalho. (Quando uma tabela de trabalho é descartada, duas páginas podem permanecer alocadas e são retornadas ao cache de tabelas de trabalho. Isto aumenta o desempenho.)|  
  
## <a name="see-also"></a>Consulte Também  
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  
