---
title: Método isWrapperFor (SQLServerXADataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d612461d-4c3f-46db-b968-ff4c80b2aa7c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e32cbf975d156aae723dfbff105fe51e039dc1b5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977025"
---
# <a name="iswrapperfor-method-sqlserverxadatasource"></a>Método isWrapperFor (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se o objeto em questão é um wrapper para a interface especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>parâmetros  
 *iface*  
  
 Uma **classe** que define uma interface.  
  
## <a name="return-value"></a>Valor retornado  
 **true** se esse objeto implementar a interface ou encapsular um objeto que implementa a interface. Caso contrário, **false**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 O método [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md) e o método [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) são definidos pela interface java.sql.Wrapper introduzida no JDBC 4.0 Spec.  
  
 Se esse método retornar true, a chamada de [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) com o mesmo argumento será bem-sucedida.  
  
 Para obter mais informações, confira [Wrappers e interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Método unwrap &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)   
 [Métodos SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Membros SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Classe SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
