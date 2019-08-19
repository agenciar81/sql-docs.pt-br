---
title: Arquivo de anúncios do SQL Server 2019 CTP | Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9f881367442cfa2e24921300ba7595bdbf28ce27
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028874"
---
# <a name="sql-server-2019-ctp-announcement-archive"></a>Arquivo de anúncios do SQL Server 2019 CTP

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Este artigo fornece um arquivo de anúncios de recursos de versões do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (CTP). Ele é fornecido para fins de histórico, mas não se aplica à produção ou às versões de pré-lançamento atuais do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Este artigo será removido quando o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] for liberado para produção.

Para obter informações atuais, confira [Novidades no SQL Server 2019](what-s-new-in-sql-server-ver15.md).

## <a name="ctp-31-june-2019"></a>CTP 3.1 de junho de 2019

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:---|:---|
| Alterações de comando `mssqlctl` | Comandos `mssqlctl cluster` foram renomeados para `mssqlctl bdc`. Para obter mais informações, consulte a [referência do `mssqlctl`](../big-data-cluster/reference-azdata.md). |
|Novos comandos de status para `mssqlsctl`|`mssqlctl` adiciona novos comandos para complementar os comandos de monitoramento existentes. Eles substituem o portal de administração de cluster – que foi removido nesta versão.|
| Pools de computação do Spark | Crie nós adicionais para aumentar a potência de computação do Spark sem precisar escalar verticalmente o armazenamento. Além disso, você pode iniciar nós de pool de armazenamento que não são usados para o Spark. O Spark e o armazenamento são separados. Para obter mais informações, consulte [Configurar o armazenamento sem o Spark](../big-data-cluster/deployment-custom-configuration.md#sparkstorage). |
| Conector do Spark MSSQL | Suporte para leitura/gravação para tabelas externas do pool de dados. As versões anteriores eram compatíveis apenas com leitura/gravação para tabelas da instância MASTER. Para obter mais informações, consulte [Como ler e gravar para o SQL Server no Spark usando o Conector do Spark MSSQL](../big-data-cluster/spark-mssql-connector.md). |
| Machine Learning usando o MLeap | [Treine um modelo de machine learning do MLeap no Spark e pontue-o no SQL Server usando a extensão da linguagem Java](../big-data-cluster/spark-create-machine-learning-model.md). |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:---|:---|
|Indexar colunas criptografadas|Criar índices em colunas criptografadas usando criptografia aleatória e chaves habilitada para enclave, a fim de melhorar o desempenho de consultas avançadas (usando `LIKE` e operadores de comparação). Veja [Always Encrypted com enclaves seguros](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Definir os valores de memória do servidor `MIN` e `MAX` na instalação |Durante a instalação, você pode definir valores de memória do servidor. Use os valores padrão, os valores recomendados calculados ou especifique manualmente seus próprios valores depois de escolher a opção **Recomendado** em [Opções de Configuração de Memória do Servidor](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).
|Nova função do grafo – `SHORTEST_PATH` | Use `SHORTEST_PATH` dentro de `MATCH` para localizar o caminho mais curto entre quaisquer dois nós em um grafo ou para executar passagens de comprimento arbitrário.|
|Tabelas de partição e os índices para bancos de dados de grafo|Os dados de tabelas e índices particionados são divididos em unidades que podem ser difundidas por mais de um grupo de arquivos em um banco de dados de grafo. |
|Nova opção para índices – `OPTIMIZE_FOR_SEQUENTIAL_KEY`|Ativa uma otimização no mecanismo de banco de dados que ajuda a melhorar a taxa de transferência para inserções de alta simultaneidade em um índice. Essa opção destina-se a índices que estão sujeitos a contenção de inserção de última página, geralmente vista com os índices que têm uma chave sequencial, tal como uma coluna de identidade, uma sequência ou uma coluna de data/hora. Para obter mais informações, veja [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server no Linux

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
| Aprimoramentos do Tempdb | Por padrão, uma nova instalação do SQL Server em Linux cria vários arquivos de dados tempdb com base no número de núcleos lógicos (com até 8 arquivos de dados). Isso não é aplicável a upgrades de versões principais ou secundárias no local. Cada arquivo do tempdb tem 8 MB com um aumento automático de 64 MB. Esse comportamento é semelhante à instalação padrão do SQL Server no Windows. |
| &nbsp; | &nbsp; |

## <a name="ctp-30-may-2019"></a>CTP 3.0 de maio de 2019

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:---|:---|
| Atualizações de **mssqlctl** | Várias [atualizações de comando e parâmetro](../big-data-cluster/reference-mssqlctl.md) do **mssqlctl**. Isso inclui uma atualização do comando **mssqlctl login**, que agora direciona o nome de usuário do controlador e o ponto de extremidade. |
| Melhorias no armazenamento | Suporte para diferentes configurações de armazenamento para logs e dados. Além disso, o número de declarações de volume persistente para um cluster de Big Data foi reduzido. |
| Várias instâncias do pool de computação | Suporte para várias instâncias do pool de computação. |
| Novas funcionalidades e novo comportamento do pool | O pool de computação agora é usado por padrão em operações do pool de dados e do pool de armazenamento apenas em uma distribuição **ROUND_ROBIN**. Agora o pool de dados pode usar um novo tipo de distribuição **REPLICATED**, o que significa que os mesmos dados estão presentes em todas as instâncias do pool de dados. |
| Melhorias na tabela externa | As tabelas externas do tipo de fonte de dados HADOOP agora dão suporte à leitura de linhas com até 1 MB. As tabelas externas (ODBC, pool de armazenamento, pool de dados) agora dão suporte a linhas da mesma largura de uma tabela do SQL Server. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:---|:---|
|Extensões de Linguagem do SQL Server – [Extensão da linguagem Java](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|O [SDK de Extensibilidade da Microsoft para Java para Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) já é software livre e está [disponível no GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Registrar linguagens externas|A nova DDL, `CREATE EXTERNAL LANGUAGE`, registra linguagens externas, como Java, no SQL Server. Confira [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Mais tipos de dados compatíveis para Java|Confira [Tipos de dados Java](../language-extensions/how-to/java-to-sql-data-types.md).|
|Política de captura personalizada para o Repositório de Consultas|Quando habilitadas, as configurações adicionais do Repositório de Consultas ficam disponíveis em uma nova configuração da Política de Captura do Repositório de Consultas, a fim de ajustar a coleta de dados em um servidor específico. Para obter mais informações, veja [Opções ALTER DATABASE SET (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|O [banco de dados em memória](../relational-databases/in-memory-database.md) adiciona uma nova sintaxe DDL para controlar o pool de buffers híbrido. <sup>2</sup>|Com o [pool de buffers híbrido](../database-engine/configure-windows/hybrid-buffer-pool.md), as páginas de banco de dados que residem em arquivos de banco de dados colocados em um dispositivo PMEM (memória persistente) serão acessadas diretamente quando necessário.|
|Adição do novo recurso do banco de dados em memória, metadados do tempdb com otimização de memória.|Confira [Metadados do TempDB com otimização de memória](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata)|
|Os servidores vinculados dão suporte a codificação de caracteres UTF-8. |[Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md) |
|O nome da ordenação BIN2_UTF8 foi alterado para Latin1_General_100_BIN2_UTF8. |[Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md) |
|A instalação do SQL Server inclui recomendações do MaxDOP que seguem as diretrizes documentadas. |[Configurar a opção de configuração de servidor max degree of parallelism](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|`sys.dm_exec_query_plan_stats` retorna mais informações sobre o grau de paralelismo e as concessões de memória para planos de consulta. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| &nbsp; | &nbsp; |

><sup>1</sup> Esse é um recurso de aceitação e requer que o [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 esteja habilitado.
>
><sup>2</sup> Um sinalizador de rastreamento não é mais necessário para habilitar o pool de buffers híbrido.

### [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Novo recurso ou atualização | Detalhes |
|:---|:---|
|O [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] dá suporte a bancos de dados de instância gerenciada do Banco de Dados SQL do Azure.| Hospede [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] em uma instância gerenciada. Confira [Instalação e configuração do [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Novo recurso ou atualização | Detalhes |
|:---|:---|
|O suporte a consulta MDX para modelos de tabela com grupos de cálculo. |Esta versão remove uma limitação anterior dos [grupos de cálculo](#calc-ctp24). |
|Formatação dinâmica de medidas usando grupos de cálculo. |Esse recurso permite que você altere condicionalmente cadeias de caracteres de formato para medidas com [grupos de cálculo](#calc-ctp24). Por exemplo, com a conversão de moeda, uma medida pode ser exibida usando diferentes formatos de moeda estrangeira.|
| &nbsp; | &nbsp; |

## <a name="ctp-25-april-2019"></a>CTP 2.5 abril de 2019

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:---|:---|
| Perfis de implantação | Use os [arquivos JSON de configuração de implantação](../big-data-cluster/deployment-guidance.md#configfile) para padrão e personalizados para implantações de cluster de Big Data, em vez de variáveis de ambiente. |
| Implantações solicitadas | O `mssqlctl cluster create` agora solicitará qualquer configuração necessária para implantações padrão. |
| Alterações de nome de ponto de extremidade de serviço e de pod | Para obter mais informações, veja [notas sobre a versão do cluster de Big Data](../big-data-cluster/release-notes-big-data-cluster.md). |
| Melhorias a **mssqlctl** | Use **mssqlctl** para [listar pontos de extremidade externos](../big-data-cluster/deployment-guidance.md#endpoints) e verifique a versão do **mssqlctl** com o parâmetro `--version`. |
| Instalação offline | [Orientação para implantações de cluster de Big Data offline](../big-data-cluster/deploy-offline.md). |
| Melhorias em camadas do HDFS | Disposição em camadas do HDFS com relação ao armazenamento do Amazon S3. Suporte do OAuth para ADLS Gen2. Funcionalidade de cache para melhor desempenho. Para obter mais informações, veja [Disposição em camadas do HSDFS](../big-data-cluster/hdfs-tiering.md) |
| Conector do Spark para SQL Server | [Ler e gravar no SQL Server do Spark usando o Conector JDBC do MSSQL](../big-data-cluster/spark-mssql-connector.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:---|:---|
| PolyBase em Linux. | [Instalar o PolyBase](../relational-databases/polybase/polybase-linux-setup.md) no Linux para conectores não Hadoop.<br/><br/>[Mapeamento de tipo do PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Novo SDK de linguagem Java para SQL Server. | Simplifica o desenvolvimento de programas Java que podem ser executados do SQL Server. Veja [Novidades em Serviços do Machine Learning do SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
| Expandido o escopo dos planos disponíveis no DMF `sys.dm_exec_query_plan_stats`. |Veja [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| Nova configuração no escopo do banco de dados `LAST_QUERY_PLAN_STATS` para habilitar o `sys.dm_exec_query_plan_stats`. |Veja [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)|
| Novos SRIDs (Spatial Reference Identifiers). |[GDA2020 australiano](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) fornece uma referência mais robusta e precisa, que está alinhada mais estreitamente a sistemas de posicionamento global. Os novos SRIDs são:<br/><br/> – 7843 – 2D geográfico<br/> – 7844 – 3D geográfico <br/><br/>A exibição [spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) contém as definições de SRIDs novos. |
| &nbsp; | &nbsp; |

><sup>1</sup> Esse é um recurso de aceitação e exige que o [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 esteja habilitado ou que a definição de configuração no escopo do banco de dados `LAST_QUERY_PLAN_STATS` esteja definida como ON.

## <a name="ctp-24-march-2019"></a>CTP 2.4 março de 2019

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:---|:---|
| Diretrizes de suporte de GPU para execução de aprendizado profundo com o TensorFlow no Spark. | [Implantar um cluster de Big Data com suporte GPU e executar o TensorFlow](../big-data-cluster/spark-gpu-tensorflow.md). |
| As fontes de dados **SqlDataPool** e **SqlStoragePool** não são mais criadas por padrão. | Crie-os manualmente, se necessário. Veja os [problemas conhecidos](../big-data-cluster/release-notes-big-data-cluster.md#externaltablesctp24). |
| Suporte a `INSERT INTO SELECT` para o pool de dados. | Para um exemplo, veja [Tutorial: Ingerir dados em um pool de dados do SQL Server com Transact-SQL](../big-data-cluster/tutorial-data-pool-ingest-sql.md). |
| Opções `FORCE SCALEOUTEXECUTION` e `DISABLE SCALEOUTEXECUTION`. | Veja [Notas sobre a versão de clusters de Big Data](../big-data-cluster/release-notes-big-data-cluster.md#whats-new).|
| Recomendações atualizadas de implantação do AKS. | Ao avaliar a clusters de Big Data no AKS, agora recomendamos usar um único nó de tamanho **Standard_L8s**. |
| Atualização de tempo de execução do Spark para o Spark 2.4. | |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|A mensagem de erro de truncamento inclui por padrão nomes de tabela e coluna, bem como o valor truncado.|[VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)|
|O novo DMF `sys.dm_exec_query_plan_stats` retorna o equivalente do último plano de execução real conhecido para a maioria das consultas. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
|O novo evento estendido `query_post_execution_plan_profile` coleta o equivalente a um plano de execução real com base em criação de perfil leve, ao contrário de `query_post_execution_showplan`, que usa a criação de perfil padrão. |[Infraestrutura de criação de perfil de consulta](../relational-databases/performance/query-profiling-infrastructure.md)|
|Verificação de TDE (Transparent Data Encryption) – suspender e retomar.|[Verificação de TDE (Transparent Data Encryption) – suspender e retomar](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
| &nbsp; | &nbsp; |

><sup>1</sup> Esse é um recurso de aceitação e requer que o [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 esteja habilitado.

### <a name="sql-server-analysis-services-ssas"></a>SSAS (SQL Server Analysis Services)

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Relações muitos para muitos em modelos tabulares.|[Relações muitos para muitos em modelos tabulares](#many-to-many-ctp24)|
|Configurações de propriedade para governança de recursos.|[Configurações de propriedade para governança de recursos](#property-ctp24)|
| &nbsp; | &nbsp; |

## <a name="ctp-23-february-2019"></a>CTP 2.3 fevereiro de 2019

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
| :---------- | :------ |
| Enviar trabalhos do Spark em clusters de Big Data no IntelliJ. | [Enviar trabalhos do Spark em clusters de Big Data do SQL Server no IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) |
| CLI comum para gerenciamento de cluster e de implantação do aplicativo. | [Como implantar um aplicativo no cluster de Big Data do SQL Server 2019 (versão prévia)](../big-data-cluster/big-data-cluster-create-apps.md) |
| Extensão do VS Code para implantar aplicativos em um cluster de Big Data. | [Como usar o VS Code para implantar aplicativos em clusters de Big Data do SQL Server](../big-data-cluster/app-deployment-extension.md) |
| Muda para o uso de comando de ferramenta **mssqlctl**. | Para obter mais detalhes, veja o [problemas conhecidos de mssqlctl](../big-data-cluster/release-notes-big-data-cluster.md ). |
| Usar o Sparklyr em clusters de Big Data. | [Usar o Sparklyr em clusters de Big Data do SQL Server 2019](../big-data-cluster/sparklyr-from-RStudio.md) |
| Montar armazenamento compatível com HDFS externo no cluster de Big Data com a disposição em **camadas do HDFS**. | Veja [Camadas do HDFS](../big-data-cluster/hdfs-tiering.md). |
| Nova experiência de conexão unificada para a instância principal do SQL Server e o Gateway do HDFS/Spark. | Veja [Instância principal do SQL Server e o Gateway do HDFS/Spark](../big-data-cluster/connect-to-big-data-cluster.md). |
| Excluir um cluster com **mssqlctl cluster delete** agora exclui somente os objetos no namespace que faziam parte do cluster de big data. | O namespace não é excluído. No entanto, em versões anteriores, esse comando excluía todo o namespace. |
| Nomes de ponto de extremidade de _segurança_ foram alterados e consolidados. | **service-security-lb** e **service-security-nodeport** foram consolidados no ponto de extremidade **endpoint-security**. |
| Nomes de ponto de extremidade de _proxy_ foram alterados e consolidados. | **service-proxy-lb** e **service-proxy-nodeport** foram consolidados no ponto de extremidade **endpoint-service-proxy**. |
| Nomes de ponto de extremidade de _controlador_ foram alterados e consolidados. | **service-mssql-controller-lb** e **service-mssql-controller-nodeport** foram consolidados no ponto de extremidade **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Habilitar recuperação de banco de dados acelerada pode ser habilitada por banco de dados.| [Recuperação acelerada de banco de dados](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)|
|Suporte à imposição de plano de Repositório de Consultas para cursores fast forward e static.|[Planejar forçar suporte para cursores fast forward e static](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23) |
|Recompilações reduzidas para cargas de trabalho usando tabelas temporárias em vários escopos. |[Redução de recompilações para cargas de trabalho](../relational-databases/tables/tables.md#ctp23) |
|Escalabilidade de ponto de verificação indiretos aprimorada. |[Escalabilidade de ponto de verificação indireto aprimorada](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)|
|Adiciona suporte para usar codificação de caracteres UTF-8 com uma ordenação BIN2 (`UTF8_BIN2`). |[Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md) |
|Defina as ações de exclusão em cascata em uma restrição de borda em um banco de dados de grafo. |[Restrições de borda](../relational-databases/tables/graph-edge-constraints.md) |
|Habilite ou desabilite `LIGHTWEIGHT_QUERY_PROFILING` com a nova configuração no escopo do banco de dados. |[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Ferramentas

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|O Azure Data Studio dá suporte ao Azure Active Directory. |[Azure Data Studio](../azure-data-studio/what-is.md) |
|A interface do usuário da exibição do notebook foi movida para o núcleo do Azure Data Studio. |[Como gerenciar notebooks no Azure Data Studio](../big-data-cluster/notebooks-how-to-manage.md) |
|Um novo assistente foi adicionado para criar fontes de dados externas do HDFS (sistema de arquivos distribuído do Hadoop) para o cluster de Big Data do SQL Server. | [Ferramentas](#tools-ctp23)|
|Interface do visualizador do notebook aprimorada. | [Ferramentas](#tools-ctp23) |
|Novas APIs do notebook foram adicionadas.| [Ferramentas](#tools-ctp23) |
|Adicionado o comando "Reinstalar dependências do notebook" para ajudá-lo com as atualizações de pacote do Python. | [Ferramentas](#tools-ctp23) |
|Iniciar o Azure Data Studio do SSMS.| [Ferramentas](#tools-ctp23) |
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Grupos de cálculo em modelo tabular.| [Grupos de cálculo em modelo tabular](#calc-ctp24) |
| &nbsp; | &nbsp; |

## <a name="ctp-22-december-2018"></a>CTP 2.2 dezembro de 2018

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Usar o SparkR do Azure Data Studio em um cluster de Big Data. | |
|Implantar aplicativos Python e R.|[Implantar aplicativos usando mssqlctl](../big-data-cluster/big-data-cluster-create-apps.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Adiciona suporte para usar codificação de caracteres UTF-8 com replicação do SQL Server. |[Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
| &nbsp; | &nbsp; |


### <a name="sql-server-on-linux"></a>SQL Server no Linux

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Grupos de Disponibilidade Always On em contêineres do Docker com Kubernetes. |[Grupos de Disponibilidade Always On para contêineres](../linux/sql-server-ag-kubernetes.md) |
| &nbsp; | &nbsp; |

## <a name="ctp-21-november-2018"></a>CTP 2.1 novembro de 2018

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Adiciona suporte para selecionar a ordenação de UTF-8 como padrão durante a instalação do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
|Inlining do UDF escalar transforma automaticamente UDFs (funções definidas pelo usuário) escalares em expressões relacionais e as insere na consulta SQL chamada. |[Inlining de UDF escalar](../relational-databases/user-defined-functions/scalar-udf-inlining.md) |
|O modo de exibição de gerenciamento dinâmico `sys.dm_exec_requests` de coluna `command` mostra `SELECT (STATMAN)` se um `SELECT` está aguardando até que uma operação de atualização de estatísticas síncronas seja concluída antes de continuar a execução da consulta. | [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) |
|O novo tipo de espera `WAIT_ON_SYNC_STATISTICS_REFRESH` é exposto no modo de exibição de gerenciamento dinâmico `sys.dm_os_wait_stats`. Ele mostra o tempo de nível de instância acumulado gasto em operações de atualização de estatísticas síncronas.|[`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) |
|O pool de buffers híbrido é um novo recurso do mecanismo de banco de dados do SQL Server em que páginas de banco de dados em arquivos de banco de dados são colocadas em um dispositivo de PMEM (memória persistente) que será acessado diretamente quando necessário.|[Pool de buffers híbrido](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Usar aliases de exibição ou tabela derivada em consulta de correspondência de grafo |[Restrições de borda de grafo](../relational-databases/tables/graph-edge-constraints.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server no Linux

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Novo registro de contêiner para o SQL Server. |[Introdução a contêineres do SQL Server no Docker](../linux/quickstart-install-connect-docker.md) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Ferramentas

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|O [Azure Data Studio](../azure-data-studio/what-is.md) dá suporte a Conectar e gerenciar clusters de Big Data [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. | |
| &nbsp; | &nbsp; |

## <a name="ctp-20-october-2018"></a>CTP 2.0 outubro de 2018

### <a name="big-data-clusters"></a>Clusters de Big Data

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Implantar um cluster de Big Data com contêineres Spark Linux e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no Kubernetes. | |
|Acessar Big Data do HDFS. | |
|Executar análises avançadas e machine learning com o Spark. | |
|Usar o Spark para fazer streaming de dados para pools de dados SQL. | |
|Executar livros de consulta que fornecem uma experiência de notebook no **Azure Data Studio**.|[Engenharia de dados](../azure-data-studio/what-is.md#data-engineering)|
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Mecanismo de banco de dados

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|**COMPATIBILITY_LEVEL 150** do banco de dados adicionado. |[Nível de compatibilidade de ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) |
|Criação de Índice Online Retomável.|[CREATE INDEX (Transact-SQL)](../t-sql/statements/create-index-transact-sql.md#resumable-indexes) |
|Comentários de concessão de memória do modo de linha. |[Comentários de concessão de memória do modo de linha](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|`COUNT DISTINCT` aproximado.|[Processamento de consulta aproximada](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Modo de Lote em rowstore.|[Modo de Lote no Rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |
|Compilação adiada de variável da tabela.|[Compilação Adiada de Variável da Tabela](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Extensão da linguagem Java.|[Extensão da linguagem Java](../advanced-analytics/java/extension-java.md) |
|Mescle seus dados de gráfico atuais de tabelas de nó ou de borda com novos dados usando os predicados `MATCH` na instrução `MERGE`. | |
|Restrições de borda.|[Restrições de borda de grafo](../relational-databases/tables/graph-edge-constraints.md) |
|Configuração padrão com escopo de banco de dados para operações de DDL online e retomáveis.| |
|Grupos de disponibilidade dão suporte a até cinco réplicas secundárias síncronas.|[Grupos de disponibilidade](../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) |
|Redirecionamento de conexão de leitura/gravação de réplica secundária para primária|[Redirecionamento de conexão de leitura/gravação de réplica secundária para primária – Grupos de Disponibilidade Always On](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) |
|Descoberta e Classificação de Dados do SQL.| [Classificação e descoberta de dados SQL](../relational-databases/security/sql-data-discovery-and-classification.md) |
|Suporte estendido para dispositivos de memória persistentes.|[Pool de Buffers Híbrido](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Suporte para estatísticas de columnstore em `DBCC CLONEDATABASE`|[Blob de estatísticas para índices columnstore](../t-sql/database-console-commands/dbcc-clonedatabase-transact-sql.md#ctp23)|
|`sp_estimate_data_compression_savings` apresenta `COLUMNSTORE` e `COLUMNSTORE_ARCHIVE`.|[Considerações para Índices Columnstore](../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md#considerations-for-columnstore-indexes)|
|Serviços do Machine Learning com suporte no Cluster de Failover do Windows Server. |[Novidades – Serviços do Machine Learning do SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)|
|Suporte para Machine Learning para modelagem baseada em partição.|[Novidades – Serviços do Machine Learning do SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) |
|Infraestrutura de perfil de consulta leve habilitada por padrão |[Infraestrutura de criação de perfil de estatísticas de execução de consulta leve v3](../relational-databases/performance/query-profiling-infrastructure.md#lightweight-query-execution-statistics-profiling-infrastructure-v3) |
|Novos conectores de PolyBase para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata e MongoDB. |[O que é o PolyBase?](../relational-databases/polybase/polybase-guide.md) |
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` retorna informações sobre uma página em um banco de dados. |[sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)|
|Always Encrypted com enclaves seguros. |[Always Encrypted com enclaves seguros](../relational-databases/security/encryption/always-encrypted-enclaves.md) |
|Compilar e recompilar índices de columnstore em cluster online. |[Executar operações de índice online](../relational-databases/indexes/perform-index-operations-online.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server no Linux

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Suporte para replicação |[Objetos de replicação do SQL Server em Linux](../linux/sql-server-linux-replication.md)
|Suporte para MSDTC (Coordenador de Transações Distribuídas da Microsoft) |[Como configurar o MSDTC no Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Suporte para OpenLDAP para provedores de AD de terceiros |[Tutorial: Usar autenticação do Azure Active Directory com o SQL Server em Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine Learning no Linux |[Configurar o Machine Learning no Linux](../linux/sql-server-linux-setup-machine-learning.md) |
| &nbsp; | &nbsp; |

### <a name="master-data-services"></a>Master Data Services

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|O portal do MDS (Master Data Services) não depende mais do Silverlight.| Todos os componentes do Silverlight anteriores foram substituídos por controles HTML.|
| &nbsp; | &nbsp; |

### <a name="security"></a>Segurança

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|Gerenciamento de certificados no SQL Server Configuration Manager|[Gerenciamento de certificado (SQL Server Configuration Manager)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |

### <a name="tools"></a>Ferramentas

| Novo recurso ou atualização | Detalhes |
|:-----|:-----|
|O [Azure Data Studio](../azure-data-studio/what-is.md) dá suporte a Conectar e gerenciar clusters de Big Data [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[O que é o Azure Data Studio](../azure-data-studio/what-is.md)|
|Dá suporte a cenários que usam clusters de Big Data do SQL Server. |[Extensão do SQL Server 2019 (versão prévia)](../azure-data-studio/sql-server-2019-extension.md)|
|[**SSMS (SQL Server Management Studio) 18.0 (versão prévia)** ](../ssms/sql-server-management-studio-ssms.md): Dá suporte a [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].| |
|Suporte para Always Encrypted com enclaves seguros. |[Always Encrypted com enclaves seguros](../relational-databases/security/encryption/always-encrypted-enclaves.md)|
| &nbsp; | &nbsp; |


## <a name="other-services"></a>Outros serviços

No CTP 2.4, o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] não introduz novos recursos para os seguintes serviços:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="details"></a>Detalhes

### <a id="bigdatacluster"></a>Clusters de Big Data

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [Clusters de Big Data](../big-data-cluster/big-data-cluster-overview.md) permitem novos cenários, incluindo o seguinte:

- [Suporte de GPU para execução de aprendizado profundo com o TensorFlow no Spark](../big-data-cluster/spark-gpu-tensorflow.md). (CTP 2.4)
- Atualização de tempo de execução do Spark para o Spark 2.4. (CTP 2.4)
- Suporte do `INSERT INTO SELECT` para o pool de dados.)(CTP 2.4)
- Cláusula de opção `FORCE SCALEOUTEXECUTION` e `DISABLE SCALEOUTEXECUTION` para consultas de tabela externa. (CTP 2.4)
- [Enviar trabalhos do Spark em clusters de Big Data do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] no IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md). (CTP 2.3)
- [Experiência de gerenciamento e implantação de aplicativo](../big-data-cluster/big-data-cluster-create-apps.md) para uma variedade de aplicativos, dados relacionados, incluindo operacionalizar modelos de aprendizado de máquina usando R e Python, executar trabalhos do SSIS (SQL Server Integration Services) e muito mais. (CTP 2.3)
- [Usar o Sparklyr em [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] clusters de Big Data](../big-data-cluster/sparklyr-from-RStudio.md). (CTP 2.3)
- Montar armazenamento compatível com HDFS externo no cluster de Big Data com a disposição em [camadas do HDFS](../big-data-cluster/hdfs-tiering.md). (CTP 2.3)
- Usar o SparkR do Azure Data Studio em um cluster de Big Data. (CTP 2.2)
- [Implantar aplicativos Python e R](../big-data-cluster/big-data-cluster-create-apps.md). (CTP 2.2)
- Implantar um cluster de Big Data com contêineres Spark Linux e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no Kubernetes. (CTP 2.0)
- Acessar Big Data do HDFS. (CTP 2.0)
- Executar análises avançadas e machine learning com o Spark. (CTP 2.0)
- Usar o Spark para fazer streaming de dados para pools de dados SQL. (CTP 2.0)
- Executar livros de consulta que fornecem uma experiência de notebook no [**Azure Data Studio**](../sql-operations-studio/what-is.md). (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

### <a id="databaseengine"></a> Mecanismo de Banco de Dados

O [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduz ou aprimora os recursos novos a seguir para o [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].

#### <a name="new-query_post_execution_plan_profile-extended-event-ctp-24"></a>Novo evento estendido Query_post_execution_plan_profile (CTP 2.4)

O novo evento estendido `query_post_execution_plan_profile` coleta o equivalente a um plano de execução real com base em criação de perfil leve, ao contrário de `query_post_execution_showplan`, que usa a criação de perfil padrão. Para obter mais informações, confira [Infraestrutura de criação de perfil de consulta](../relational-databases/performance/query-profiling-infrastructure.md).

##### <a name="example-1---extended-event-session-using-standard-profiling"></a>Exemplo 1 – sessão de evento estendido usando a criação de perfil padrão

```sql
CREATE EVENT SESSION [QueryPlanOld] ON SERVER 
ADD EVENT sqlserver.query_post_execution_showplan(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename = N'C:\Temp\QueryPlanStd.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

##### <a name="example-2---extended-event-session-using-lightweight-profiling"></a>Exemplo 2 – sessão de evento estendido usando a criação de perfil leve

```sql
CREATE EVENT SESSION [QueryPlanLWP] ON SERVER 
ADD EVENT sqlserver.query_post_execution_plan_profile(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename=N'C:\Temp\QueryPlanLWP.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

#### <a name="new-dmf-sysdm_exec_query_plan_stats-ctp-24"></a>Novo DMF sys.dm_exec_query_plan_stats (CTP 2.4) 

O novo DMF `sys.dm_exec_query_plan_stats` retorna o equivalente do último plano de execução real conhecido para a maioria das consultas, com base na criação de perfil leve. Para obter mais informações, consulte [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) e [Infraestrutura de criação de perfil de consulta](../relational-databases/performance/query-profiling-infrastructure.md). Consulte o seguinte script como exemplo:

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

Esse é um recurso opcional e requer que o [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 esteja habilitado.

#### <a name="transparent-data-encryption-tde-scan---suspend-and-resume-ctp-24"></a>Verificação de TDE (Transparent Data Encryption) – suspender e retomar (CTP 2.4)

Para habilitar o [TDE (Transparent Data Encryption)](../relational-databases/security/encryption/transparent-data-encryption.md) em um banco de dados, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deve executar uma verificação de criptografia que lê cada página dos dados de arquivo no pool de buffers e, em seguida, grava as páginas criptografadas de volta no disco. Para fornecer ao usuário mais controle sobre a verificação de criptografia, [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduz a sintaxe de verificação de TDE – suspender e retomar, de modo que você possa pausar a verificação enquanto a carga de trabalho do sistema estiver pesada ou durante horários comercialmente críticos e continuar a verificação mais tarde.

Use a sintaxe a seguir para pausar a verificação de criptografia de TDE:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

De modo semelhante, a sintaxe a seguir retoma a verificação de criptografia de TDE:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

Para mostrar o estado atual do exame de criptografia, `encryption_scan_state` foi adicionado à exibição de gerenciamento dinâmico `sys.dm_database_encryption_keys`. Também há uma nova coluna chamada `encryption_scan_modify_date` que conterá a data e hora da última alteração de estado da verificação de criptografia. Observe também que, se a instância [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] for reiniciada enquanto a verificação de criptografia estiver em um estado suspenso, uma mensagem será registrada no log de erros na inicialização, indicando que há uma verificação existente em pausa.

#### <a name="accelerated-database-recovery-ctp-23"></a>Recuperação de banco de dados acelerada (CTP 2.3)

A [recuperação de banco de dados acelerada](/azure/sql-database/sql-database-accelerated-database-recovery/) melhora significativamente a disponibilidade do banco de dados, especialmente na presença de transações de execução prolongada, remodelando o processo de recuperação do mecanismo de banco de dados do SQL Server. A [recuperação de banco de dados](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started) é o processo que o SQL Server usa para cada banco de dados iniciar em um estado transacionalmente consistente – ou limpo. Um banco de dados, com a recuperação de banco de dados acelerada habilitada conclui a recuperação significativamente mais rápido após um failover ou outro desligamento não limpo. Do CTP 2.3 em diante, recuperação acelerada de banco de dados pode ser habilitada para cada banco de dados usando a seguinte sintaxe:

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

> [!NOTE]
> Essa sintaxe não é necessária para tirar proveito desse recurso no BD SQL do Azure, em que ele é [ativado por solicitação durante a versão prévia pública](/azure/sql-database/sql-database-accelerated-database-recovery). Após sua habilitação, o recurso estará ativado por padrão.

Se você tiver bancos de dados críticos que estão sujeitos a grandes quantidades de transações, faça experiências com esse recurso durante a versão prévia. Forneça comentários à [equipe do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](<https://aka.ms/sqlfeedback>).

#### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>Suporte à imposição de plano de Repositório de Consultas para cursores fast forward e static (CTP 2.3)

O Repositório de Consultas agora dá suporte à capacidade de impor os planos de execução de consulta para cursores fast forward e static de API e T-SQL. Agora há suporte para a imposição por meio de `sp_query_store_force_plan` ou por meio de relatórios do Repositório de Consultas do SQL Server Management Studio.

#### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>Recompilações reduzidas para cargas de trabalho usando tabelas temporárias em vários escopos (CTP 2.3)

Antes desse recurso, ao fazer referência a uma tabela temporária com uma instrução DML (linguagem de manipulação de dados) (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), se a tabela temporária tivesse sido criada por um lote de escopo externo, isso resultaria em uma recompilação da instrução DML cada vez que ela fosse executada. Com essa melhoria, o SQL Server executa verificações adicionais leves para evitar recompilações desnecessárias:

- Verifique se o módulo de escopo externo usado para criar a tabela temporária em tempo de compilação é a mesma usada para execuções consecutivas. 
- Controle quaisquer alterações de DDL (linguagem de definição de dados) feitas na compilação inicial e compare-as com as operações de DDL para execuções consecutivas. 

O resultado final é uma redução de recompilações desnecessárias e sobrecarga de CPU.

#### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>Escalabilidade de pontos de verificação indiretos aprimorada (CTP 2.3)

Nas versões anteriores do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], os usuários podem enfrentar erros de agendador sem resposta quando há um banco de dados que gera um grande número de páginas sujas, assim como tempdb. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] apresenta melhor escalabilidade para o ponto de verificação indireto, que deve ajudar a evitar esses erros em bancos de dados que têm uma carga de trabalho de UPDATE/INSERT pesada.

#### <a name="utf-8-support-ctp-23"></a>Suporte a UTF-8 (CTP 2.3)

Suporte completo para a amplamente utilizada codificação de caracteres UTF-8 como codificação de importação ou exportação, ou como ordenação em nível de banco de dados ou nível de coluna para dados de texto. A UTF-8 é permitida nos tipos de dados `CHAR` e `VARCHAR` e é habilitada quando você cria ou altera a ordenação de um objeto para uma ordenação com o sufixo `UTF8`. 

Por exemplo, `LATIN1_GENERAL_100_CI_AS_SC` para `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. A UTF-8 só está disponível para agrupamentos do Windows com suporte para caracteres suplementares, conforme introduzido no [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. `NCHAR` e `NVARCHAR` permitem somente a codificação UTF-16 e permanecem inalterados.

Esse recurso pode fornecer economia de armazenamento significativa dependendo do conjunto de caracteres utilizado. Por exemplo, a alteração de um tipo de dados de coluna existente com cadeias de caracteres ASCII (Latinas) de `NCHAR(10)` para `CHAR(10)` usando uma ordenação habilitada para UTF-8 resulta em 50% de redução nos requisitos de armazenamento. Essa redução ocorre porque `NCHAR(10)` exige 20 bytes para armazenamento, enquanto `CHAR(10)` requer 10 bytes para a mesma cadeia de caracteres Unicode.

Para obter mais informações, consulte [Suporte a ordenações e a Unicode](../relational-databases/collations/collation-and-unicode-support.md).

O **CTP 2.1** adiciona suporte para selecionar a ordenação de UTF-8 como padrão durante a instalação do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

O **CTP 2.2** adiciona suporte para usar codificação de caracteres UTF-8 com replicação do SQL Server.

O **CTP 2.3** adiciona suporte para usar codificação de caracteres UTF-8 com uma ordenação BIN2 (UTF8_BIN2).

#### <a name="scalar-udf-inlining-ctp-21"></a>Inlining do UDF escalar (CTP 2.1)

O inlining do UDF escalar transforma automaticamente funções definidas pelo usuário (UDF) escalares em expressões relacionais e as insere na consulta SQL de chamada, melhorando o desempenho de cargas de trabalho que aproveitam UDFs escalares. O inlining do UDF escalar possibilita a otimização baseada em custo de operações em UDFs e resulta em planos eficientes que são orientados ao conjunto e paralelos, em vez de planos de execução seriais ineficientes e iterativos. Esse recurso é habilitado por padrão no nível de compatibilidade do banco de dados 150.

Para saber mais, confira [Scalar UDF Inlining](../relational-databases/user-defined-functions/scalar-udf-inlining.md) (Embutimento de UDF escalar).

#### <a name="a-nametruncation-truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a><a name="truncation" />Mensagem de erro de truncamento aprimorada para incluir nomes de tabela e coluna e o valor truncado (CTP 2.1)

A mensagem de erro com ID 8152 `String or binary data would be truncated` é familiar para muitos desenvolvedores e administradores do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que desenvolvem ou mantêm cargas de trabalho de movimentação de dados. O erro é gerado durante transferências de dados entre uma origem e um destino com esquemas diferentes quando os dados de origem são muito grandes para caber no tipo de dados de destino. Essa mensagem de erro pode ter resolução demorada. O [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] apresenta uma mensagem de erro nova e mais específica (2628) para esse cenário:  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

A nova mensagem de erro 2628 fornece mais contexto para o problema de truncamento de dados, simplificando o processo de solução de problemas. 

**CTP 2.1 e CTP 2.2** Essa é uma mensagem de erro para aceitação e requer que o [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 esteja habilitado.

**CTP 2.4** A mensagem de erro 2628 torna-se a mensagem de truncamento padrão e substitui a mensagem de erro 8152 no nível de compatibilidade do banco de dados 150. Uma nova configuração no escopo do banco de dados `VERBOSE_TRUNCATION_WARNINGS` é introduzida para alternar entre a mensagem de erro 2628 e a 8152 quando o nível de compatibilidade do banco de dados é 150. Para obter mais informações, veja [ALTERAR A CONFIGURAÇÃO NO ESCOPO DO BANCO DE DADOS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
Para o nível de compatibilidade do banco de dados 140 ou inferior, a mensagem de erro 2628 permanece uma mensagem de erro de aceitação que exige a habilitação do [sinalizador de rastreamento](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460.

#### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Dados de diagnóstico aprimorados para estatísticas de bloqueio (CTP 2.1)

A [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fornece dados de diagnóstico aprimorados para consultas de longa execução que esperam operações de atualização de estatísticas síncronas. O modo de exibição de gerenciamento dinâmico `sys.dm_exec_requests` de coluna `command` mostra `SELECT (STATMAN)` se um `SELECT` está aguardando até que uma operação de atualização de estatísticas síncronas seja concluída antes de continuar a execução da consulta. Além disso, o novo tipo de espera `WAIT_ON_SYNC_STATISTICS_REFRESH` será exposto no modo de exibição de gerenciamento dinâmico `sys.dm_os_wait_stats`. Ele mostra o tempo de nível de instância acumulado gasto em operações de atualização de estatísticas síncronas.

#### <a name="hybrid-buffer-pool-ctp-21"></a>Pool de buffers híbrido (CTP 2.1)

O pool de buffers híbrido é um novo recurso do mecanismo de banco de dados do SQL Server em que páginas de banco de dados em arquivos de banco de dados são colocadas em um dispositivo de PMEM (memória persistente) que será acessado diretamente quando necessário. Como dispositivos PMEM fornecem uma latência muito baixa para o acesso a dados, o mecanismo pode não fazer uma cópia dos dados em uma área de "páginas limpas" do pool de buffers e simplesmente acessar a página diretamente no PMEM. O acesso é realizado usando E/S de memória mapeada, como ocorre com a capacitação. Isso oferece benefícios de desempenho, por evitar uma cópia da página para a DRAM e evitar a pilha de E/S do sistema operacional para acessar a página no armazenamento persistente. Esse recurso está disponível no SQL Server no Windows e no SQL Server no Linux.

Para obter mais informações, confira [Pool de buffers híbrido](../database-engine/configure-windows/hybrid-buffer-pool.md)

#### <a name="static-data-masking-ctp-21"></a>Mascaramento de dados estáticos (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduz o mascaramento de dados estáticos. Você pode usar o de mascaramento dados estáticos para limpar dados confidenciais em cópias de bancos de dados do SQL Server. O mascaramento de dados estáticos ajuda a criar uma cópia limpa de bancos de dados em que todas as informações confidenciais são alteradas de forma a tornar a cópia compartilhável com usuários de não produção. O mascaramento de dados estáticos pode ser usado para desenvolvimento, teste, análise e relatórios de negócios, conformidade, solução de problemas e qualquer outro cenário em que dados específicos não possam ser copiados para ambientes diferentes.

O mascaramento de dados estáticos opera no nível de coluna. Selecione quais colunas mascarar e, para cada coluna selecionada, especifique uma função de mascaramento. O mascaramento de dados estáticos copia o banco de dados e, em seguida, aplica as funções de mascaramento especificadas às colunas.

##### <a name="static-data-masking-vs-dynamic-data-masking"></a>Mascaramento de dados estáticos versus mascaramento de dados dinâmicos

O mascaramento de dados é o processo de aplicação de uma máscara a um banco de dados para ocultar informações confidenciais e substituí-la por dados novos ou dados limpos. A Microsoft oferece duas opções de mascaramento: o mascaramento de dados estáticos e o mascaramento de dados dinâmicos. A Máscara de Dados Dinâmicos foi introduzida no [!INCLUDE[ssSQL16](../includes/sssql16-md.md)]. A seguinte tabela compara essas duas soluções:

|Mascaramento de dados estáticos |Mascaramento de dados dinâmicos|
|:----|:----|
|Ocorre em uma cópia do banco de dados <br/><br/>Dados originais não recuperáveis<br/><br/>O mascaramento ocorre no nível de armazenamento<br/><br/>Todos os usuários têm acesso aos mesmos dados mascarados<br/><br/>Voltado para o acesso contínuo de toda a equipe|Ocorre no banco de dados original<br/><br/>Dados originais intactos<br/><br/>O mascaramento ocorre dinamicamente no momento da consulta<br/><br/>O mascaramento varia com base na permissão do usuário <br/><br/>Voltado para o acesso específico de usuário pontual|

#### <a name="database-compatibility-level-ctp-20"></a>Nível de compatibilidade de banco de dados (CTP 2.0)

**COMPATIBILITY_LEVEL 150** do banco de dados adicionado. Para habilitar um banco de dados de usuário específico, execute:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

#### <a name="resumable-online-index-create-ctp-20"></a>Criação de índice online retomável (CTP 2.0)

A **criação de índice online retomável** permite que uma operação de criação de índice fique em pausa e seja retomada posteriormente do ponto em que a operação parou ou falhou, em vez de reiniciar desde o início.

A criação de índice online retomável dá suporte aos cenários a seguir:
- retomar uma operação de criação de índice após uma falha na criação do índice, por exemplo, após um failover do banco de dados ou após faltar espaço em disco.
- pausar uma operação de criação de índice em andamento e retomá-la mais tarde permitindo a liberação temporária de recursos, conforme necessário.
- criar índices grandes sem usar muito espaço de log e uma transação de execução longa que bloqueia outras atividades de manutenção e permite o truncamento de log.

No caso de falha na criação de um índice, sem esse recurso, uma operação de criação de índice online deve ser executada novamente e a operação deve ser reiniciada desde o início.

Com esta versão, estendemos a funcionalidade retomável adicionando o recurso à [recompilação de índice online retomável](https://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/).

Além disso, esse recurso pode ser definido como padrão para um banco de dados específico usando a [configuração padrão de escopo do banco de dados para operações de DDL online e retomáveis](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Para obter mais informações, consulte [Criação de índice online retomável](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

#### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Compilar e recompilar índices de columnstore em cluster online (CTP 2.0)

Converta tabelas de repositório de linha no formato columnstore. A criação de CCIs (índices columnstore clusterizados) era um processo offline nas versões anteriores do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] – exigindo que todas as alterações parassem enquanto o CCI era criado. Com o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] e o [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)], você pode criar ou recriar CCI online. A carga de trabalho não será bloqueada e todas as alterações feitas nos dados subjacentes serão adicionadas de maneira transparente à tabela de destino de columnstore. Exemplos de novas instruções [!INCLUDE[tsql](../includes/tsql-md.md)] que podem ser usadas são:

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

#### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted com enclaves seguros (CTP 2.0)

Expande o Always Encrypted com criptografia no local e cálculos avançados. As expansões são decorrentes da habilitação de cálculos em dados de texto sem formatação, dentro de um enclave seguro no lado do servidor.

Operações de criptografia incluem a criptografia de colunas e a rotação de chaves de criptografia de coluna. Agora, essas operações podem ser emitidas usando [!INCLUDE[tsql](../includes/tsql-md.md)] e não exigem que os dados sejam movidos para fora do banco de dados. Enclaves seguros fornecem o Always Encrypted para um conjunto mais amplo de cenários que têm os dois requisitos a seguir:  

- a demanda que dados confidenciais sejam protegidos contra usuários de alto privilégio, porém não autorizados, incluindo administradores de banco de dados, administradores do sistema, operadores de nuvem ou malware.
- o requisito de que cálculos avançados em dados protegidos tenham suporte dentro do sistema de banco de dados.

Para conhecer detalhes, consulte [Always Encrypted com enclaves seguros](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> O Always Encrypted com enclaves seguros está disponível apenas no SO Windows.

#### <a name="intelligent-query-processing-ctp-20"></a>Processamento de consulta inteligente (CTP 2.0)

- **Feedback de concessão de memória no modo de linha** expande o recurso de feedback de concessão de memória introduzido no [!INCLUDE[ssSQL17](../includes/sssql17-md.md)], ajustando os tamanhos da concessão de memória para os operadores de modo de lote e de linha. Para uma condição de concessão excessiva, se a memória concedida tiver mais de duas vezes o tamanho da memória real usada, o feedback de concessão de memória recalculará a concessão de memória. As execuções consecutivas, em seguida, solicitarão menos memória. Para uma concessão de memória de tamanho insuficiente que resulta em um despejo no disco, o feedback de concessão de memória acionará o recálculo da concessão de memória. As execuções consecutivas, em seguida, solicitarão mais memória. Esse recurso é habilitado por padrão no nível de compatibilidade do banco de dados 150.

- **COUNT DISTINCT aproximado** retorna o número aproximado de valores não nulos exclusivos em um grupo. Essa função foi criada para uso em cenários de Big Data. Essa função é otimizada para consultas em que todas as seguintes condições forem verdadeiras:
   - acesso a conjuntos de dados com pelo menos milhões de linhas.
   - agregação de uma coluna ou colunas com grande número de valores distintos.
   - a capacidade de resposta é mais crítica que a precisão absoluta.
      - `APPROX_COUNT_DISTINCT` retorna resultados que normalmente estão dentro de 2% da resposta precisa.
      - E retorna a resposta aproximada em uma pequena fração do tempo necessário para a resposta precisa.

- **O modo de lote em rowstore** não requer mais um índice columnstore para processar uma consulta no modo de lote. O modo de lote permite que operadores de consulta funcionem em um conjunto de linhas, em vez de apenas uma linha por vez. Esse recurso é habilitado por padrão no nível de compatibilidade do banco de dados 150. O modo de lote aumenta a velocidade de consultas que acessam tabelas de rowstore quando todos os itens a seguir são verdadeiras:
   - a consulta usa operadores analíticos como junções ou operadores de agregação.
   - a consulta envolve 100.000 linhas ou mais.
   - a consulta é limitada pela CPU, em vez de ser limitada por dados de entrada/saída.
   - a criação e uso de um índice columnstore teria uma das seguintes desvantagens:
      - adicionaria muita sobrecarga à consulta.
      - ou não é viável porque seu aplicativo depende de um recurso que ainda não tem suporte de índices columnstore.

- **A compilação adiada de variável da tabela** melhora a qualidade do plano e o desempenho geral para consultas que fazem referência a variáveis de tabela. Durante a otimização e compilação inicial, esse recurso propagará estimativas de cardinalidade com base nas contagens reais de linha de variável de tabela. Essas informações de contagem de linha precisas serão ser usadas para otimizar operações de plano de downstream. Esse recurso é habilitado por padrão no nível de compatibilidade do banco de dados 150.

Para usar recursos de processamento de consulta inteligente, defina o banco de dados `COMPATIBILITY_LEVEL = 150`.

#### <a id="programmability"></a> Extensões de programação de linguagem Java (CTP 2.0)

- **Extensão da linguagem Java (versão prévia)** : Use a extensão da linguagem Java para executar o código Java em [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. No [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], esta extensão é instalada quando você adiciona o recurso 'Serviços do Machine Learning (No Banco de Dados)' à instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

#### <a id="sqlgraph"></a> Recursos do SQL Graph (CTP 2.3)

- **Usar aliases de tabela derivada ou exibição na consulta de correspondência de gráfico (CTP 2.1)** Consultas do Graph na versão prévia [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] dão suporte ao uso de aliases de tabela derivada e exibição na sintaxe `MATCH`. Para usar esses aliases no `MATCH`, as exibições e as tabelas derivadas devem ser criadas em um conjunto de nós ou em um conjunto de tabelas de borda, usando o operador `UNION ALL`. As tabelas de nós ou de borda podem ou não ter filtros nelas. A capacidade de usar aliases de tabela derivada e exibição em consultas `MATCH` pode ser muito útil em cenários em que você deseja consultar entidades heterogêneas ou conexões heterogêneas entre duas ou mais entidades no gráfico.

- **O suporte a correspondência em `MERGE` DML (CTP 2.0)** permite que você especifique relações de gráfico em uma única instrução, em vez de instruções `INSERT`, `UPDATE` ou `DELETE` separadas. Mescle seus dados de gráfico atuais de tabelas de nó ou de borda com novos dados usando os predicados `MATCH` na instrução `MERGE`. Esse recurso permite cenários de `UPSERT` nas tabelas de borda. Agora, os usuários podem usar uma única instrução merge para inserir uma nova borda ou atualizar uma existente entre dois nós.

- **Restrições de borda (CTP 2.0)** são introduzidas para tabelas de borda no SQL Graph. Tabelas de borda podem conectar qualquer nó a qualquer outro nó no banco de dados. Com a introdução das restrições de borda, agora você pode aplicar algumas restrições a esse comportamento. A nova restrição `CONNECTION` pode ser usada para especificar o tipo de nós a que uma determinada tabela de borda terá permissão para se conectar no esquema. 

  **(CTP 2.3)** Estendendo ainda mais esse recurso, você pode definir as ações de exclusão em cascata em uma restrição de borda. Você pode definir as ações que o mecanismo de banco de dados usa quando um usuário exclui os nós que uma determinada borda conecta.

#### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations-ctp-20"></a>Configuração padrão com escopo de banco de dados para operações de DDL online e retomáveis (CTP 2.0)

- **A configuração padrão com escopo de banco de dados para operações de DDL online e retomáveis** permite a configuração de um comportamento padrão para operações de índice `ONLINE` e `RESUMABLE` no nível do banco de dados, em vez de definir essas opções para cada instrução DDL de índice individual, como criar ou recompilar o índice.

- Defina esses padrões usando as opções de configuração de escopo do banco de dados `ELEVATE_ONLINE` e `ELEVATE_RESUMABLE`. Ambas as opções farão com que o mecanismo eleve automaticamente as operações com suporte para execução online ou retomável. Você pode habilitar os seguintes comportamentos usando essas opções:

  - a opção `FAIL_UNSUPPORTED` permite todas as operações de índice online ou operações de índice retomáveis e com falha que não têm suporte para a opção online ou retomável.
  - a opção `WHEN_SUPPPORTED` permite operações com suporte online ou operações sem suporte de retomáveis e de execução de índice offline ou não retomáveis.
  - a opção `OFF` permite o comportamento atual de executar todas as operações de índice offline e não retomáveis a menos que explicitamente especificado na instrução DDL.

Para substituir a configuração padrão, inclua a opção `ONLINE` ou `RESUMABLE` nos comandos de criação e recompilação do índice. 

Sem esse recurso, você precisa especificar as opções online e retomáveis diretamente na instrução DDL do índice, assim como criar e recompilar o índice.

Para obter mais informações sobre operações retomáveis de índice, consulte [Criação de índice online retomável](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

#### <a id="ha"></a>Grupos de Disponibilidade Always On – mais réplicas síncronas (CTP 2.0)

- **Até cinco réplicas síncronas**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] aumenta o número máximo de réplicas síncronas para 5, de até de 3 no [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Você pode configurar esse grupo de cinco réplicas para ter failover automático dentro do grupo. Há uma réplica primária, além de quatro réplicas secundárias síncronas.

- **Redirecionamento de conexão de réplica secundária para primária**: Permite que conexões do aplicativo cliente sejam direcionadas para a réplica primária, independentemente do servidor de destino especificado na cadeia de conexão. Esse recurso permite o redirecionamento de conexão sem um ouvinte. Use o redirecionamento de conexão de réplica secundária para primária nos seguintes casos:

  - a tecnologia de cluster não oferece um recurso de ouvinte.
  - uma configuração de várias sub-redes em que o redirecionamento se torna complexo.
  - cenários de expansão de leitura ou de recuperação de desastre em que o tipo de cluster é `NONE`.

Para conhecer os detalhes, consulte [Secondary to primary replica read/write connection redirection (Always On Availability Groups)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) (Redirecionamento de conexão de leitura/gravação de réplica secundária para primária [Grupos de Disponibilidade Always On]).

#### <a name="data-discovery-and-classification-ctp-20"></a>Descoberta e classificação de dados (CTP 2.0)

A descoberta e classificação de dados fornece recursos avançados que são internos e nativos no [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Classificar e rotular seus dados mais confidenciais fornece os seguintes benefícios:
- ajuda a atender a padrões de privacidade de dados e requisitos de conformidade regulamentar.
- dá suporte a cenários de segurança, como monitoramento (auditoria) e alertas sobre acesso anômalo a dados confidenciais.
- torna mais fácil identificar onde os dados confidenciais residem na empresa, para que os administradores possam adotar as etapas corretas para proteger o banco de dados.

Para obter mais informações, consulte [Descoberta e classificação de dados SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

A [auditoria](../relational-databases/security/auditing/sql-server-audit-database-engine.md) também foi aprimorada para incluir um novo campo no log de auditoria chamado `data_sensitivity_information`, que registra a classificações (rótulos) de confidencialidade dos dados reais que foram retornados pela consulta. Para obter detalhes e exemplos, consulte [Adicionar classificação de confidencialidade](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Não há nenhuma alteração em termos de como a auditoria é habilitada. Foi adicionado um novo campo aos registros de auditoria, `data_sensitivity_information`, que registra a classificações (rótulos) de confidencialidade dos dados reais que foram retornados pela consulta. Consulte [Auditoria de acesso a dados confidenciais](/azure/sql-database/sql-database-data-discovery-and-classification/#subheading-3).

#### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Suporte estendido para dispositivos de memória persistentes (CTP 2.0)

Agora, qualquer arquivo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] colocado em um dispositivo de memória persistente pode funcionar no modo *capacitado*. O [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acessa o dispositivo diretamente, ignorando a pilha de armazenamento do sistema operacional usando operações de memória eficientes. Esse modo melhora o desempenho porque permite entrada/saída de baixa latência em relação a esses dispositivos.
    - Exemplos de arquivos [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] incluem:
        - Arquivos de banco de dados
        - Arquivos de log de transações
        - Arquivos de ponto de verificação de OLTP in-memory
    - A memória persistente também é conhecida como memória de classe de armazenamento.
    - Ocasionalmente, a memória persistente é chamada informalmente de *pmem* em alguns sites que não são da Microsoft.

> [!NOTE]
> Para esta versão prévia, a capacitação de arquivos em dispositivos de memória persistente só está disponível no Linux. O [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no Windows dá suporte a dispositivos de memória persistente começando com o [!INCLUDE[ssSQL15](../includes/sssql15-md.md)].

#### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Suporte para estatísticas de columnstore em DBCC CLONEDATABASE (CTP 2.0)

O `DBCC CLONEDATABASE` cria uma cópia somente de esquema de um banco de dados que inclui todos os elementos necessários para solucionar problemas de desempenho de consulta sem copiar os dados. Em versões anteriores do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], o comando não copiava as estatísticas necessárias para solucionar problemas com precisão em consultas de índice de columnstore, e etapas manuais eram necessárias para capturar essas informações. Agora, no [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], o `DBCC CLONEDATABASE` captura automaticamente os blobs de estatísticas para índices columnstore, de modo que nenhuma etapa manual é necessária.

#### <a name="new-options-added-to-sp_estimate_data_compression_savings-ctp-20"></a>Novas opções adicionadas a sp_estimate_data_compression_savings (CTP 2.0)

`sp_estimate_data_compression_savings` retorna o tamanho atual do objeto solicitado e faz a estimativa do tamanho do objeto para o estado de compactação solicitado. Atualmente, esse procedimento dá suporte a três opções: `NONE`, `ROW` e `PAGE`. O [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduz duas novas opções: `COLUMNSTORE` e `COLUMNSTORE_ARCHIVE`. Essas novas opções permitirão que você estime a economia de espaço se um índice columnstore for criado na tabela usando a compactação de columnstore padrão ou de arquivos.

#### <a id="ml"></a> Modelagem baseada em partição e clusters de failover dos Serviços do Machine Learning do SQL Server (CTP 2.0)

- **Modelagem baseada em partição**: Processe scripts externos por partição de seus dados usando os novos parâmetros adicionados ao `sp_execute_external_script`. Essa funcionalidade dá suporte ao treinamento de muitos modelos pequenos (um modelo para cada partição de dados) em vez de um modelo grande.

- **Cluster de failover do Windows Server**: Configure alta disponibilidade para Serviços do Machine Learning em um Cluster de failover do Windows Server.

Para obter informações detalhadas, consulte [Novidades dos Serviços do Machine Learning do SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

#### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Infraestrutura de perfil de consulta leve habilitada por padrão (CTP 2.0)

A infraestrutura de criação de perfil com consulta leve (LWP) fornece dados de desempenho de consulta de maneira mais eficiente do que os mecanismos de criação de perfil padrão. A criação de perfil leve agora está habilitada por padrão. Ela foi introduzida no [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. A criação de perfil leve oferece um mecanismo de coleção de estatísticas de execução de consulta com uma sobrecarga esperada de 2% da CPU, em comparação com uma sobrecarga de até 75% da CPU para o mecanismo de criação de perfil com consulta padrão. Em versões anteriores, ela ficava DESATIVADA por padrão. Os administradores de banco de dados podiam habilitá-la com o [sinalizador de rastreamento 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Para obter mais informações sobre essa criação de perfil leve, confira [Infraestrutura de criação de perfil de consulta](../relational-databases/performance/query-profiling-infrastructure.md).

**CTP 2.3** Uma nova configuração com escopo de banco de dados `LIGHTWEIGHT_QUERY_PROFILING` é introduzida para habilitar ou desabilitar a infraestrutura de criação de perfil de consulta leve.

#### <a id="polybase"></a>Novos conectores de PolyBase

- **Novos conectores para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata e MongoDB**: o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduz novos conectores para dados externos para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata e MongoDB.

#### <a name="new-sysdm_db_page_info-system-function-returns-page-information-ctp-20"></a>A nova função de sistema sys.dm_db_page_info retorna informações da página (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` retorna informações sobre uma página em um banco de dados. A função retorna uma linha que contém as informações de cabeçalho da página, incluindo `object_id`, `index_id` e `partition_id`. Essa função substitui a necessidade de usar `DBCC PAGE` na maioria dos casos. 

Para facilitar a solução de problemas de esperas relacionadas à página, uma nova coluna chamada page_resource também foi adicionada a `sys.dm_exec_requests` e `sys.sysprocesses`. Essa nova coluna permite unir `sys.dm_db_page_info` a essas exibições por meio de uma nova função de sistema – `sys.fn_PageResCracker`. Consulte o seguinte script como exemplo:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

### <a id="sqllinux"></a> SQL Server no Linux

- **Grupos de Disponibilidade Always On em contêineres do Docker com Kubernetes (CTP 2.2)** : O Kubernetes pode orquestrar contêineres que executam instâncias de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para fornecer um conjunto altamente disponível de bancos de dados com os Grupos de Disponibilidade Always On do SQL Server. Um operador de Kubernetes implanta um StatefulSet incluindo um contêiner com **contêiner mssql-server** e um monitor de integridade.

- **Novo registro de contêiner (CTP 2.1)** : Todas as imagens de contêiner para [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], bem como [!INCLUDE[ssSQL17](../includes/sssql17-md.md)], agora estão localizadas no Registro de Contêiner da Microsoft. O Registro de Contêiner da Microsoft é o registro de contêiner oficial para distribuição de contêineres de produtos da Microsoft. Além disso, imagens certificadas baseadas em RHEL agora foram publicadas.

  - Registro de Contêiner da Microsoft: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Imagens de contêiner baseadas em RHEL certificadas: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

- **Suporte de replicação (CTP 2.0)** : o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] dá suporte à Replicação do SQL Server no Linux. Uma máquina de virtual do Linux com SQL Agent pode ser um publicador, distribuidor ou assinante. 

  Crie os tipos seguintes de publicações:
  - Transacional.
  - Instantâneo
  - Mesclagem

  Configure a replicação [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou use [procedimentos armazenados de replicação](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Suporte para o MSDTC (Coordenador de Transações Distribuídas da Microsoft) (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] no Linux dá suporte ao MSDTC (Coordenador de Transações Distribuídas da Microsoft). Para obter detalhes, consulte [Como configurar o MSDTC no Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Suporte de OpenLDAP para provedores terceirizados do AD (CTP 2.0)** : o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] no Linux dá suporte a OpenLDAP, que permite que provedores terceirizados ingressem no Active Directory.

- **Machine Learning no Linux (CTP 2.0)** : Os Serviços do Machine Learning do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (no banco de dados) agora são compatíveis com o Linux. O suporte inclui o procedimento armazenado `sp_execute_external_script`. Para obter instruções de como instalar os Serviços do Machine Learning no Linux, consulte [Instalar o suporte dos Serviços do Machine Learning do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] para R e Python no Linux](../linux/sql-server-linux-setup-machine-learning.md).

### <a id="mds"></a> Master Data Services 

- **Controles do Silverlight substituídos por HTML (CTP 2.0)** : O portal do MDS (Master Data Services) não depende mais do Silverlight. Todos os componentes do Silverlight anteriores foram substituídos por controles HTML.

### <a id="security"></a>Segurança

- **Gerenciamento de certificados no SQL Server Configuration Manager (CTP 2.0)** : Certificados SSL/TLS são amplamente usados para proteger o acesso a instâncias do SQL Server. O gerenciamento de certificados agora está integrado ao SQL Server Configuration Manager, simplificando tarefas comuns como:

  - exibir e validar certificados instalados em uma instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  - exibindo certificados prestes a expirar.
  - implantar certificados em computadores que participam de Grupos de Disponibilidade Always On (começando no nó que contém a réplica primária).
  - implantar certificados em computadores que participam de uma instância de cluster de failover (começando no nó ativo).

  > [!NOTE]
  > O usuário precisa ter permissões de administrador em todos os nós de cluster.

### <a id="tools"></a>Ferramentas

- [**Azure Data Studio**](../azure-data-studio/what-is.md): Lançado anteriormente com nome de versão prévia SQL Operations Studio, o Azure Data Studio é uma ferramenta de área de trabalho leve, moderna, de software livre e multiplataforma comuns usada para as tarefas mais comuns no desenvolvimento e administração de dados. Com o Azure Data Studio e a [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]extensão da Versão prévia do](../azure-data-studio/sql-server-2019-extension.md), você pode se conectar ao SQL Server local e na nuvem do Windows, macOS e Linux. O Azure Data Studio permite:

<a name = "tools-ctp23"></a>

  - Agora há suporte para o AAD. (CTP 2.3)
  - A interface do usuário da exibição do notebook foi movida para o núcleo do Azure Data Studio. (CTP 2.3)
  - Um novo assistente foi adicionado para criar fontes de dados externas do HDFS (sistema de arquivos distribuído do Hadoop) para o cluster de Big Data do SQL Server. (CTP 2.3)
  - Interface do visualizador do notebook aprimorada. (CTP 2.3)
  - Novas APIs do notebook foram adicionadas. (CTP 2.3)
  - Adicionado o comando "Reinstalar dependências do notebook" para ajudá-lo com as atualizações de pacote do Python. (CTP 2.3)
  - Conecte-se e gerencie clusters de Big Data do [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. (CTP 2.1)
  - editar e executar consultas em um ambiente de desenvolvimento moderno com Intellisense extremamente rápido, trechos de código e integração de controle do código-fonte. (CTP 2.0) 
  - visualizar rapidamente dados com gráficos internos de seus conjuntos de resultados. (CTP 2.0)
  - criar painéis personalizados para seus servidores e bancos de dados usando widgets personalizáveis. (CTP 2.0)  
  - gerenciar facilmente seu ambiente mais abrangente com o terminal interno. (CTP 2.0)
  - analisar dados em uma experiência de notebook integrada baseado em Jupyter. (CTP 2.0)
  - Aprimorar sua experiência com extensões e temas personalizados. (CTP 2.0)
  - e explorar seus recursos do Azure com um navegador de recursos e assinatura interno. (CTP 2.0)
  - Dá suporte a cenários que usam um cluster de Big Data do SQL Server. (CTP 2.0)
  
  > [!TIP]
  > Para os aprimoramentos mais recentes do Azure Data Studio, consulte as [notas sobre a versão do Azure Data Studio](../azure-data-studio/release-notes-azure-data-studio.md).

- [**SSMS (SQL Server Management Studio) 18.0 (versão prévia)** ](../ssms/sql-server-management-studio-ssms.md): Dá suporte a [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

  - Iniciar o Azure Data Studio do SSMS. (CTP 2.3)
  - Suporte para Always Encrypted com enclaves seguros. (CTP 2.0)
  - Menor tamanho de download. (CTP 2.0)
  - Agora baseado no Shell Isolado do Visual Studio 2017. (CTP 2.0)
  - Para obter uma lista completa, consulte o [Log de mudanças do SSMS](../ssms/release-notes-ssms.md). (CTP 2.0)

- [**Módulo do SQL Server PowerShell**](http://www.powershellgallery.com/packages/SqlServer/21.1.18080): O módulo do SQL Server PowerShell permite que os administradores, desenvolvedores do SQL Server e profissionais de BI automatizem a administração de servidores e a implantação de bancos de dados.

  - Atualização de 21.0 para 21.1 para dar suporte ao SMO v150.
  - Provedor atualizado do SQL Server (SQLRegistration) para exibir os grupos AS/IS/RS.
  - Corrigido um problema no cmdlet `New-SqlAvailabilityGroup` ao direcionar para o SQL Server 2014.
  - Adicionado o parâmetro `–LoadBalancedReadOnlyRoutingList` a `Set-SqlAvailabilityReplica` e `New-SqlAvailabilityReplica`.
  - Atualizado o cmdlet `AnalysisService` para usar o token de logon armazenado em cache de `Login-AzureAsAccount` para o Azure Analysis Services.

### <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

#### <a name="online-attach-ctp32"></a>Anexação online (CTP 3.2)

O CTP 3.2 introduz a capacidade de anexar um modelo de tabela como uma operação online. A anexação online pode ser usada para sincronização de réplicas somente leitura em ambientes de expansão de consulta local. Para executar uma operação de anexação online, use a opção **AllowOverwrite** do comando Attach XMLA. 

```xmla
<Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine"> 
  <Folder>C:\Program Files\Microsoft SQL Server\MSAS15\OLAP\Data\AdventureWorks.0.db\</Folder> 
  <AllowOverwrite>True</AllowOverwrite> 
</Attach> 
```

Esta operação pode exigir *o dobro da memória do modelo* para manter a versão antiga online ao carregar a nova versão. 

Um padrão de uso típico poderia ser o seguinte: 

1. O DB1 (versão 1) já está anexado ao servidor somente leitura B. 

2. O DB1 (versão 2) é processado no servidor de gravação A. 

3. O DB1 (versão 2) é desanexado e colocado em um local acessível ao servidor B (seja por meio de um local compartilhado ou usando o robocopy, etc.). 

4. O comando <Attach> com AllowOverwrite=True é executado no servidor B com o novo local de DB1 (versão 2). 

Sem esse recurso, os administradores precisam primeiro desanexar o banco de dados e, em seguida, anexar a nova versão do banco de dados. Isso leva a tempo de inatividade quando o banco de dados não está disponível para os usuários e as consultas feitas a ele falharão. 

Quando esse novo sinalizador é especificado, a versão 1 do banco de dados é excluída atomicamente dentro da mesma transação, sem tempo de inatividade. No entanto, ele vem com o ônus de ter ambos os bancos de dados carregados na memória simultaneamente. 


#### <a name="many-to-many-ctp24"></a>Relações muitos para muitos em modelos tabulares (CTP 2.4)

Esse recurso permite relações muitos para muitos entre tabelas em que ambas as colunas não são exclusivas. Uma relação pode ser definida entre uma tabela de dimensões e uma de fatos com uma granularidade maior do que a coluna de chave da dimensão. Isso evita a necessidade de normalizar as tabelas de dimensões e pode melhorar a experiência do usuário, já que o modelo resultante tem um número menor de tabelas com colunas agrupadas logicamente. Para esta versão CTP 2.4, relações muitos para muitos são recursos somente de mecanismo. 

Relações muitos para muitos exigem que os modelos estejam no nível de compatibilidade 1470, que atualmente é compatível apenas com o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 e posterior. Para essa versão CTP 2.4, relações muitos para muitos podem ser criadas usando a API de TOM (objeto de modelo tabular), a TMSL (linguagem de script de modelo tabular) e a ferramenta de Editor de Tabelas de software livre. O suporte no SSDT (SQL Server Data Tools) será incluído em uma versão futura, bem como a documentação. Informações adicionais para esse e outros recursos lançados no CTP serão fornecidas no blog do Analysis Services.

#### <a name="property-ctp24"></a>Configurações de memória para governança de recursos (CTP 2.4)

As configurações de memória descritas aqui já estão disponíveis no Azure Analysis Services. Começando com o CTP 2.4, elas agora também são compatíveis com o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Analysis Services. 

- **Memory\QueryMemoryLimit** – essa propriedade de memória pode ser usada para limitar spools memória criados por consultas DAX enviadas para o modelo. 
- **DbpropMsmdRequestMemoryLimit** – essa propriedade XMLA pode ser usada para substituir o valor da propriedade de servidor Memory\QueryMemoryLimit para uma conexão.
- **OLAP\Query\RowsetSerializationLimit** – essa propriedade de servidor limita o número de linhas retornadas em um conjunto de linhas, protegendo os recursos do servidor uso extensivo da exportação de dados. Essa propriedade se aplica a ambas as consultas DAX e MDX.

Essas propriedades podem ser definidas usando a versão mais recente do SSMS (SQL Server Management Studio). Informações adicionais para esse recurso serão fornecidas no blog do Analysis Services.

#### <a name="calc-ctp24"></a>Grupos de cálculos em modelos de tabela (CTP 2.3) 

Grupos de cálculos resolvem um problema comum em modelos complexos nos quais pode haver uma proliferação de medidas usando os mesmos cálculos, assim como em inteligência temporal. Grupos de cálculos são mostrados em clientes de relatório como uma tabela com uma única coluna. Cada valor na coluna representa um cálculo reutilizável ou um item de cálculo que pode ser aplicado a qualquer uma das medidas.  

Um grupo de cálculos pode ter qualquer número de itens de cálculo. Cada item de cálculo é definido por uma expressão DAX. Três novas funções DAX foram introduzidas para trabalhar com grupos de cálculos: 

- `SELECTEDMEASURE()` – retorna uma referência para a medida atualmente no contexto.  

- `SELECTEDMEASURENAME()` – retorna uma cadeia de caracteres que contém o nome da medida atualmente no contexto.  

- `ISSELECTEDMEASURE(M1, M2, …)` – retorna um valor booliano que indica se a medida atualmente no contexto é uma daquelas especificadas como um argumento.

Além das novas funções DAX, duas novas exibições de gerenciamento dinâmico foram introduzidas:

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

##### <a name="limitations-in-this-release"></a>Limitações nesta versão:

- A função `ALLSELECTED DAX` ainda não é compatível.
- A Segurança em Nível de Linha definida na tabela de grupo de cálculo ainda não é compatível.
- A segurança em nível de objeto definida na tabela de grupo de cálculo ainda não é compatível.
- Expressões de DetailsRows que fazem referência a itens de cálculo ainda não são compatíveis.
- MDX ainda não é compatível.

##### <a name="known-issues-in-this-release"></a>Problemas conhecidos nesta versão:

- A presença de grupos de cálculo em um modelo pode fazer com que medidas retornem tipos de dados variantes, o que pode causar falhas de atualização em tabelas e colunas calculadas que fazem referência a essas medidas.

##### <a name="compatibility-level"></a>Nível de Compatibilidade

Grupos de cálculos exigem que os modelos estejam no nível de compatibilidade 1470, que atualmente é compatível apenas com o [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 e posterior. Neste momento, os grupos de cálculo podem ser criados usando a API de TOM (objeto de modelo tabular), a TMSL (linguagem de script de modelo tabular) e a ferramenta de Editor de Tabelas de software livre. O suporte no SSDT (SQL Server Data Tools) será incluído em uma versão futura, bem como a documentação. Informações adicionais para esse e outros recursos lançados no CTP serão fornecidas no blog do Analysis Services.

## <a name="see-also"></a>Confira também

- [`SqlServer` Módulo do PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Documentação do SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Próximas etapas

- [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]Notas sobre a versão](sql-server-ver15-release-notes.md).

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: White paper técnico](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Publicado em setembro de 2018. Aplica-se ao Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 para contêineres do Windows, Linux e Docker.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
