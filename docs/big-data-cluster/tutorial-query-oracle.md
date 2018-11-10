---
title: Como a consulta Oracle a partir de um cluster de big data do SQL Server | Microsoft Docs
description: Este tutorial demonstra como consultar dados do Oracle de um cluster de big data do SQL Server 2019 (visualização). Você cria uma tabela externa sobre os dados no Oracle e, em seguida, executa uma consulta.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/12/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 7f5383a6faf13f0454439a42efb7524eaeda7c76
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644084"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>Tutorial: Consultar o Oracle de um cluster de big data do SQL Server

Este tutorial demonstra como consultar dados do Oracle de um cluster de big data do SQL Server de 2019. Para executar este tutorial, você precisará ter acesso a um servidor Oracle. Se você não tiver acesso, este tutorial pode dar uma ideia de como funciona a virtualização de dados para fontes de dados externas no cluster de big data do SQL Server.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Crie uma tabela externa para dados em um banco de dados externo do Oracle.
> * Junte-se esses dados com dados de alto valor na instância do mestre.

> [!TIP]
> Se você preferir, você pode baixar e executar um script para os comandos neste tutorial. Para obter instruções, consulte a [exemplos de virtualização de dados](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) no GitHub.

## <a id="prereqs"></a> Pré-requisitos

* [Implantar um cluster de big data no Kubernetes](deployment-guidance.md).
* [Instalar o Studio de dados do Azure e a extensão do SQL Server 2019](deploy-big-data-tools.md).
* [Carregar dados de exemplo no cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-oracle-table"></a>Criar uma tabela do Oracle

As seguintes etapas criam uma tabela de exemplo chamada `INVENTORY` no Oracle.

1. Conecte-se para uma instância do Oracle e o banco de dados que você deseja usar para este tutorial.

1. Execute a seguinte instrução para criar o `INVENTORY` tabela:

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Importar o conteúdo do **inventory.csv** arquivo nessa tabela. Este arquivo foi criado pelos scripts de criação do exemplo na [pré-requisitos](#prereqs) seção.

## <a name="create-an-external-data-source"></a>Criar uma fonte de dados externa

A primeira etapa é criar uma fonte de dados externa que pode acessar o servidor Oracle.

1. No estúdio de dados do Azure, conecte-se à instância mestre do SQL Server do seu cluster de big data. Para obter mais informações, consulte [conectar-se a instância mestre do SQL Server](deploy-big-data-tools.md#master).

1. Clique duas vezes em que a conexão na **servidores** janela para mostrar o painel do servidor para a instância mestre do SQL Server. Selecione **nova consulta**.

   ![Consulta de instância mestre do SQL Server](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Execute o seguinte comando Transact-SQL para alterar o contexto para o **vendas** banco de dados na instância do mestre.

   ```sql
   USE Sales
   GO
   ```

1. Crie uma credencial no escopo do banco de dados para se conectar ao servidor Oracle. Forneça as credenciais apropriadas ao servidor Oracle na instrução a seguir.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Crie uma fonte de dados externa que aponta para o servidor Oracle.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>Criar uma tabela externa

Em seguida, crie uma tabela externa chamada **iventory_ora** sobre o `INVENTORY` tabela no servidor Oracle.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Nomes de tabela e nomes de coluna usará ANSI SQL identificador entre aspas durante a consulta em Oracle. Como resultado, os nomes diferenciam maiusculas de minúsculas. É importante especificar o nome na definição de tabela externa que corresponda exatamente da forma dos nomes de tabela e coluna nos metadados do Oracle.

## <a name="query-the-data"></a>Consultar os dados

Execute a seguinte consulta para unir os dados `iventory_ora` tabela externa com as tabelas no local `Sales` banco de dados.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Limpar

Use o seguinte comando para remover os objetos de banco de dados criados neste tutorial.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Próximas etapas

Aprenda a ingestão de dados para o pool de dados:
> [!div class="nextstepaction"]
> [Carregar dados no pool de dados](tutorial-data-pool-ingest-sql.md)