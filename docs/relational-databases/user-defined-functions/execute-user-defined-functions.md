---
title: Executar funções definidas pelo usuário | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b028b6ab4da678444427682a635f679acce576ab
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68123579"
---
# <a name="execute-user-defined-functions"></a>Executar funções definidas pelo usuário
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  Execute uma função definida pelo usuário usando o Transact-SQL.
  

> **Observação:** visite  [função definida pelo usuário](user-defined-functions.md) e [Criar função (Transact SQL](../../t-sql/statements/create-function-transact-sql.md) para saber mais sobre funções definidas pelo usuário. 
  
 
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
 No Transact-SQL, os parâmetros podem ser fornecidos usando *valor* ou usando @*parameter_name*=*valor.* . Um parâmetro não faz parte de uma transação; portanto, se um parâmetro for alterado em uma transação que for posteriormente revertida, o parâmetro não será revertido para seu valor anterior. O valor retornado ao chamador será sempre o valor no momento do retorno do módulo.  
  
###  <a name="Security"></a> Segurança  
  
 Não são solicitadas permissões para executar a instrução [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) . Porém, permissões **são necessárias** nos protegíveis mencionados na cadeia de caracteres EXECUTE. Por exemplo, se a cadeia de caracteres tiver uma instrução [INSERT](../../t-sql/statements/insert-transact-sql.md) , o chamador da instrução EXECUTE deverá ter a permissão INSERT na tabela de destino. As permissões são verificadas quando a instrução EXECUTE for encontrada, mesmo se ela estiver incluída em um módulo. Para obter mais informações, veja [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
### <a name="example"></a>Exemplo 
  
Este exemplo usa a função de valor escalar `ufnGetSalesOrderStatusText` que está disponível na maioria das edições do `AdventureWorks`.  A finalidade da função é retornar um valor de texto para o status de vendas de um determinado inteiro.  Varie o exemplo passando números inteiros de 1 a 7 para o parâmetro **\@Status** .
  
~~~tsql
USE [AdventureWorks2016CTP3]
GO  

-- Declare a variable to return the results of the function. 
DECLARE @ret nvarchar(15);   

-- Execute the function while passing a value to the @status parameter
EXEC @ret = dbo.ufnGetSalesOrderStatusText 
    @Status = 5; 

-- View the returned value.  The Execute and Select statements must be executed at the same time.  
SELECT N'Order Status: ' + @ret; 

-- Result:
-- Order Status: Shipped
~~~
  
  
  
