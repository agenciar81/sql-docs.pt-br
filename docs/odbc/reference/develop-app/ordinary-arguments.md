---
title: Argumentos comuns | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 997604b4376656d36d2bc4bc31f1959aa6c8a229
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987822"
---
# <a name="ordinary-arguments"></a>Argumentos comuns
Quando um argumento de cadeia de caracteres de função de catálogo é um argumento comum, ele é tratado como uma cadeia de caracteres literal. Um argumento comum não aceita nenhum padrão de pesquisa de cadeia de caracteres nem uma lista de valores. O caso de um argumento comum é significativo e os caracteres de aspas na cadeia de caracteres são usados literalmente. Esses argumentos serão tratados como argumentos comuns se o atributo de instrução SQL_ATTR_METADATA_ID for definido como SQL_FALSE; Eles são tratados como argumentos de identificador, em vez disso, se esse atributo for definido como SQL_TRUE.  
  
 Se um argumento comum for definido como um ponteiro NULL e o argumento for um argumento necessário, a função retornará SQL_ERROR e SQLSTATE HY009 (uso inválido de ponteiro NULL). Se um argumento comum for definido como um ponteiro nulo e o argumento não for um argumento necessário, o comportamento do argumento será dependente de driver. Os argumentos necessários são listados na tabela a seguir.  
  
|Função|Argumentos necessários|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
