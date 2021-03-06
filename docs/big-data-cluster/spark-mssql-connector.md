---
title: Conectar o Spark ao SQL Server
titleSuffix: SQL Server big data clusters
description: Saiba como usar o Conector do Spark MSSQL no Spark para ler e gravar no SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 105fa47ecaa560eace9d798a39950639ecbcb5c0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831182"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Como ler e gravar no SQL Server do Spark usando o Conector do Spark MSSQL

Um padrão importante de uso de Big Data é o processamento de dados de alto volume no Spark, seguido pela gravação dos dados no SQL Server para acesso a aplicativos de linha de negócios. Esses padrões de uso se beneficiam de um conector que utiliza otimizações de SQL importantes e fornecem um mecanismo de gravação eficiente.

Este artigo fornece um exemplo de como usar o conector do Spark MSSQL para ler e gravar nos seguintes locais em um cluster de Big Data:

1. Na instância mestre do SQL Server
1. No pool de dados SQL Server

   ![No diagrama do conector do Spark MSSQL](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

O exemplo executa as seguintes tarefas:

- Leia um arquivo do HDFS e faça alguns processamentos básicos.
- Grave o dataframe em uma instância mestre do SQL Server como uma tabela SQL e, em seguida, leia a tabela em um dataframe.
- Grave o dataframe em um pool de dados do SQL Server como uma tabela SQL externa e, em seguida, leia a tabela externa em um dataframe.

## <a name="mssql-spark-connector-interface"></a>Interface do Conector do Spark MSSQL

O SQL Server 2019 fornece o **conector do Spark MSSQL** para clusters de Big Data que usam APIs de gravação em massa do SQL Server para gravações do Spark para SQL. O conector do Spark MSSQL é baseado em APIs de fonte de dados do Spark e fornece uma interface de conector JDBC do Spark familiar. Para parâmetros de interface, confira a [documentação do Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). O conector do Spark MSSQL é referenciado pelo nome **com.microsoft.sqlserver.jdbc.spark**.

A tabela a seguir descreve os parâmetros de interface que foram alterados ou são novos:

| Nome da propriedade | Opcional | Descrição |
|---|---|---|
| **isolationLevel** | Sim | Isso descreve o nível de isolamento da conexão. O padrão para o conector do Spark MSSQL é **READ_COMMITTED** |

O conector usa APIs de gravação em massa do SQL Server. Os parâmetros de gravação em massa podem ser passados como parâmetros opcionais pelo usuário e passados no estado em que se encontram pelo conector para a API subjacente. Para obter mais informações sobre operações de gravação em massa, confira [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>Prerequisites

- Um [cluster de Big Data do SQL Server](deploy-get-started.md).

- [Azure Data Studio](https://aka.ms/getazuredatastudio).

## <a name="create-the-target-database"></a>Criar o banco de dados de destino

1. Abra o Azure Data Studio e [conecte-se à instância mestre do SQL Server do cluster de Big Data](connect-to-big-data-cluster.md).

1. Crie uma nova consulta e execute o comando a seguir para criar um banco de dados de exemplo chamado **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Carregar dados de exemplo no HDFS

1. Baixe [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) em seu computador local.

1. Inicie o Azure Data Studio e [conecte-se ao cluster de Big Data](connect-to-big-data-cluster.md).

1. Clique com o botão direito do mouse na pasta HDFS no cluster de Big Data e selecione **Novo diretório**. Nomeie o diretório **spark_data**.

1. Clique com o botão direito do mouse no diretório **spark_data** e selecione **Fazer upload de arquivos**. Faça upload do arquivo **AdultCensusIncome.csv**.

   ![Arquivo CSV AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Executar um notebook de exemplo

Para demonstrar o uso do conector do Spark MSSQL com esses dados, você pode baixar um notebook de exemplo, abri-lo no Azure Data Studio e executar cada bloco de código. Para obter mais informações sobre como trabalhar com notebooks, confira [Como usar notebooks no SQL Server](notebooks-guidance.md).

1. Em uma linha de comando do PowerShell ou Bash, execute o seguinte comando para baixar o notebook de exemplo **mssql_spark_connector_non_ad_pyspark.ipynb**:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector_non_ad_pyspark.ipynb"
   ```

1. No Azure Data Studio, abra o arquivo de notebook de exemplo. Verifique se ele está conectado ao seu gateway HDFS/Spark para o cluster de Big Data.

1. Execute cada célula de código no exemplo para ver o uso do conector do Spark MSSQL.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre clusters de Big Data, confira [Como implantar [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] no Kubernetes](deployment-guidance.md)
