---
title: Método wasNull (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.wasNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a27b2fe-ae12-46a9-9bca-2c5ca66b9eb3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 03e2ba3f7721c0322e54686cef0a53d93a9bf79c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68001548"
---
# <a name="wasnull-method-sqlservercallablestatement"></a>Método wasNull (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera se o último parâmetro OUT lido teve o valor de SQL NULL.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean wasNull()  
```  
  
## <a name="return-value"></a>Valor retornado  
 **true** se a leitura do último parâmetro era nula. Caso contrário, **false**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método wasNull é especificado pelo método wasNull na interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
