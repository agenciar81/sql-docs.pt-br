---
title: Processar resultados (ODBC) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 99704433862dc92f2f677ba767b932ff8650f768
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="processing-results---process-results"></a>Resultados do processamento - resultados do processo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

Processamento de resultados em um aplicativo ODBC envolve primeiro determinar as características do conjunto de resultados e recuperar os dados em variáveis de programa usando o [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) ou [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md).  
  
### <a name="to-process-results"></a>Para processar resultados  
  
1.  Recupere informações do conjunto de resultados.  
  
2.  Se forem usadas colunas associadas, para cada coluna à qual deseja associar, chame [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) para associar um buffer de programa à coluna.  
  
3.  Para cada linha no conjunto de resultados:  
  
    -   Chame [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) para acessar a próxima linha.  
  
    -   Se forem usadas colunas associadas, use os dados disponíveis agora nos buffers de coluna associados.  
  
    -   Se forem usadas colunas desassociadas, chame [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) uma ou mais vezes para obter os dados dessas colunas depois da última coluna associada. As chamadas para **SQLGetData** devem estar em ordem crescente de número de coluna.  
  
    -   Chame **SQLGetData** várias vezes para obter dados de uma coluna de textos ou imagens.  
  
4.  Quando [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) sinalizar o término do conjunto de resultados retornando SQL_NO_DATA, chame [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) para determinar se há outro conjunto de resultados disponível.  
  
    -   Se SQL_SUCCESS for retornado, outro conjunto de resultados estará disponível.  
  
    -   Se SQL_NO_DATA for retornado, nenhum outro conjunto de resultados estará disponível.  
  
    -   Se SQL_SUCCESS_WITH_INFO ou SQL_ERROR for retornado, chame [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) para determinar se a saída de uma instrução PRINT ou RAISERROR estará disponível.  
  
         Se parâmetros de instrução associados forem usados para parâmetros de saída ou o valor retornado de um procedimento armazenado, use os dados disponíveis agora nos buffers de parâmetro associados. Além disso, quando são usados parâmetros associados, cada chamada para [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) ou [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) terá executado a instrução SQL por *S* vezes, em que *S* é o número de elementos na matriz de parâmetros associados. Isso significa que haverá *S* conjuntos de resultados a serem processados, em que cada conjunto consiste em todos os conjuntos de resultados, parâmetros de saída e códigos de retorno normalmente retornados por uma única execução da instrução SQL.  
  
    > [!NOTE]  
    >  Quando um conjunto de resultados contém linhas computadas, cada linha computada é disponibilizada como um conjunto de resultados separado. Esses conjuntos de resultados computados são intercalados nas linhas normais e dividem as linhas normais em vários conjuntos de resultados.  
  
5.  Outra opção é chamar [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) com SQL_UNBIND para liberar qualquer buffer de coluna associado.  
  
6.  Se outro conjunto de resultados estiver disponível, vá para a Etapa 1.  
  
> [!NOTE]  
>  Para cancelar o processamento de um conjunto de resultados antes que [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) retorne SQL_NO_DATA, chame [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>Consulte também  
[Recuperar informações do conjunto de resultados &#40; ODBC &#41;](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
  