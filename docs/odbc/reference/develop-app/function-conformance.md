---
title: Conformidade da função | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45eb427b660496430334633b5d43ee8989211c0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069749"
---
# <a name="function-conformance"></a>Conformidade de função
A tabela a seguir indica o nível de conformidade de cada função ODBC, em que isso é bem definido.  
  
|Função|Compatibilidade com nível|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Núcleo|  
|**SQLBindCol**|Núcleo|  
|**SQLBindParameter**|Núcleo [1]|  
|**SQLBrowseConnect**|Nível 1|  
|**SQLBulkOperations**|Nível 1|  
|**SQLCancel**|Núcleo [1]|  
|**SQLCloseCursor**|Núcleo|  
|**SQLColAttribute**|Núcleo [1]|  
|**SQLColumnPrivileges**|Nível 2|  
|**SQLColumns**|Núcleo|  
|**SQLConnect**|Núcleo|  
|**SQLCopyDesc**|Núcleo|  
|**SQLDataSources**|Núcleo|  
|**SQLDescribeCol**|Núcleo [1]|  
|**SQLDescribeParam**|Nível 2|  
|**SQLDisconnect**|Núcleo|  
|**SQLDriverConnect**|Núcleo|  
|**SQLDrivers**|Núcleo|  
|**SQLEndTran**|Núcleo [1]|  
|**SQLExecDirect**|Núcleo|  
|**SQLExecute**|Núcleo|  
|**SQLFetch**|Núcleo|  
|**SQLFetchScroll**|Núcleo [1]|  
|**SQLForeignKeys**|Nível 2|  
|**SQLFreeHandle**|Núcleo|  
|**SQLFreeStmt**|Núcleo|  
|**SQLGetConnectAttr**|Núcleo|  
|**SQLGetCursorName**|Núcleo|  
|**SQLGetData**|Núcleo|  
|**SQLGetDescField**|Núcleo|  
|**SQLGetDescRec**|Núcleo|  
|**SQLGetDiagField**|Núcleo|  
|**SQLGetDiagRec**|Núcleo|  
|**SQLGetEnvAttr**|Núcleo|  
|**SQLGetFunctions**|Núcleo|  
|**SQLGetInfo**|Núcleo|  
|**SQLGetStmtAttr**|Núcleo|  
|**SQLGetTypeInfo**|Núcleo|  
|**SQLMoreResults**|Nível 1|  
|**SQLNativeSql**|Núcleo|  
|**SQLNumParams**|Núcleo|  
|**SQLNumResultCols**|Núcleo|  
|**SQLParamData**|Núcleo|  
|**SQLPrepare**|Núcleo|  
|**SQLPrimaryKeys**|Nível 1|  
|**SQLProcedureColumns**|Nível 1|  
|**SQLProcedures**|Nível 1|  
|**SQLPutData**|Núcleo|  
|**SQLRowCount**|Núcleo|  
|**SQLSetConnectAttr**|Núcleo [2]|  
|**SQLSetCursorName**|Núcleo|  
|**SQLSetDescField**|Núcleo [1]|  
|**SQLSetDescRec**|Núcleo|  
|**SQLSetEnvAttr**|Núcleo [2]|  
|**SQLSetPos**|Nível 1 [1]|  
|**SQLSetStmtAttr**|Núcleo [2]|  
|**SQLSpecialColumns**|Núcleo [1]|  
|**SQLStatistics**|Núcleo|  
|**SQLTablePrivileges**|Nível 2|  
|**SQLTables**|Núcleo|  
  
 [1] recursos significativos dessa função estão disponíveis apenas em níveis de conformidade mais altos.  
  
 [2] a configuração de determinados atributos para valores não padrão depende do nível de conformidade. Para obter mais informações, consulte a próxima seção, [conformidade do atributo](../../../odbc/reference/develop-app/attribute-conformance.md).
