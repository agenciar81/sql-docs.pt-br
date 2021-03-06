---
title: Usando repositórios de teste (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: da99b63c986029a1791793fbbd33910bb95d4b7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086799"
---
# <a name="using-test-repositories-oracletosql"></a>Uso de repositórios de teste (OracleToSQL)
O repositório de teste do SSMA armazena casos de teste e resultados de teste do SSMA Tester para uso posterior. Os dados do repositório são salvos nas tabelas de SQL Server **TestCaseRepository** e **RunTestCaseResultRepository** no esquema **ssma_oracle_utilities** do banco de dados **ssmatesterdb** .  
  
Os botões a seguir estão disponíveis na caixa de diálogo repositório de casos de teste:  
  
-   Clique no botão **Atualizar** para atualizar os casos de teste ou resultados de teste lista.  
  
-   Clique no botão **fechar** para fechar o repositório da caixa de diálogo casos de teste.  
  
## <a name="test-cases-repository"></a>Repositório de casos de teste  
Você pode exibir o repositório de casos de teste clicando em **casos de teste...** no menu **testador** . Em seguida, o SSMA exibe a janela de caixa de diálogo **repositório de casos de** teste com uma lista de casos de teste salvos na página **casos de teste** .  
  
A grade mostra as seguintes informações sobre cada caso de teste:  
  
-   Nome: o nome do caso de teste.  
  
-   Criado: a data de criação do caso de teste.  
  
-   Modificado: a data da última modificação do caso de teste.  
  
-   Descrição: as descrições do caso de teste.  
  
Os botões a seguir estão disponíveis na página casos de teste:  
  
-   Clique no botão **Adicionar** para executar o assistente de caso de teste e criar um novo teste.  
  
-   Clique no botão **remover** para excluir o teste selecionado do repositório. Quando um caso de teste é excluído, todos os Resultados de Teste relacionados também são excluídos.  
  
-   Clique no botão **Editar** para executar o assistente de caso de teste e alterar o teste selecionado.  
  
-   Clique no botão **executar** para abrir a caixa de diálogo [executando casos de teste (OracleToSQL)](https://msdn.microsoft.com/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) e execute o teste selecionado.  
  
## <a name="test-results-repository"></a>Repositório de Resultados de Teste  
Você pode exibir o repositório Resultados de Teste na página **resultados de teste** do **repositório da janela casos de teste** . Abra-o clicando em **resultados de teste...** no menu do **testador** .  
  
Você pode usar dois filtros na página **resultados de teste** :  
  
-   O filtro de nome de caso de teste: permite escolher resultados de teste por nome de caso de teste. O valor de **todos os casos de teste** do filtro permite exibir resultados de teste para todos os casos de teste.  
  
-   O filtro de data de execução do caso de teste: filtra os resultados do teste pela data de salvamento. O valor de **todos os períodos** do filtro permite exibir resultados de teste para qualquer data de salvamento.  
  
As informações a seguir sobre os resultados de teste são exibidas na grade.  
  
-   Nome: nome do caso de teste.  
  
-   Salvo: data do caso de teste de salvamento.  
  
-   Resultados: um breve resumo da execução de teste (a dica de ferramenta dessa célula exibe um resumo completo da execução do teste).  
  
Os botões a seguir estão disponíveis na página resultado do teste:  
  
-   Clique no botão **Exibir** para abrir a [exibição de relatórios de caso de teste &#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) do resultado do caso de teste atual.  
  
-   Clique no botão **excluir** para excluir o resultado do teste selecionado  
  
## <a name="see-also"></a>Consulte Também  
[Executando casos de teste &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testando objetos de banco de dados migrados &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
