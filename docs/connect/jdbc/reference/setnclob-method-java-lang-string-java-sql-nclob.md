---
title: Método setNClob (java.lang.String, java.sql.NClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4e30d242-0c1b-45db-b75f-41b041692f31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cafa1124f193be1f747ad63e2024ea24d8fd5137
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973686"
---
# <a name="setnclob-method-javalangstring-javasqlnclob"></a>Método setNClob (java.lang.String, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o parâmetro designado como o objeto NClob especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>parâmetros  
 *parameterName*  
  
 Uma **String** que contém o nome do parâmetro.  
  
 *value*  
  
 Um objeto NClob.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método deve ser usado para tipos de dados de parâmetros **NCHAR**, **NVARCHAR**, **NTEXT** e **XML**.  
  
 Esse método setNClob é especificado pelo método setNClob na interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Método setNClob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
