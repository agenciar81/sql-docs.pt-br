---
title: Mapeamento SQLTransact | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2082a97b24284afcc879048bb08e86a7b2bb3ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070107"
---
# <a name="sqltransact-mapping"></a>Mapeamento SQLTransact
**SQLTransact** agora é substituído por **SQLEndTran**. A principal diferença entre as duas funções é que **SQLEndTran** contém um *identificador*de argumento, que especifica o escopo do trabalho a ser feito. O argumento *HandleType* pode especificar o ambiente ou o identificador de conexão. A seguinte chamada para **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 está mapeado para  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* não for igual a SQL_NULL_HDBC. O argumento *ConnectionHandle* é definido como o valor de *HDBC*.  
  
 **SQL_Transact** está mapeado para  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* for igual a SQL_NULL_HDBC. O argumento *EnvironmentHandle* é definido como o valor de *HENV*.  
  
 Em ambos os casos anteriores, o argumento *complettype* é definido com o mesmo valor de *ftype*.
