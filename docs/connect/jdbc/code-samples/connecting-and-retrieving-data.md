---
title: Como conectar-se e recuperar dados | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11378d51cb6d88858ebba069dba161dbbb494f27
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028399"
---
# <a name="connecting-and-retrieving-data"></a>Conectando e recuperando dados

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Quando você trabalha com o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], há dois métodos principais para estabelecer uma conexão com um banco de dados do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Um é definir as propriedades de conexão na URL de conexão e, em seguida, chamar o método getConnection da classe DriverManager para retornar um objeto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
> [!NOTE]  
> Para obter uma lista das propriedades de conexão compatíveis com o driver JDBC, confira [Configuração das propriedades de conexão](../../../connect/jdbc/setting-the-connection-properties.md).  
  
O segundo método envolve definir as propriedades de conexão usando métodos setter da classe [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) e, em seguida, chamar o método [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) para retornar um objeto SQLServerConnection.  
  
Os tópicos nesta seção descrevem os modos diferentes nos quais você pode se conectar a um banco de dados do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e também demonstram técnicas diferentes para recuperar dados.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Exemplo de URL de conexão](../../../connect/jdbc/code-samples/connection-url-sample.md)|Descreve como usar uma URL de conexão para se conectar ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e usar uma instrução SQL para recuperar dados.|  
|[Exemplo de fonte de dados](../../../connect/jdbc/code-samples/data-source-sample.md)|Descreve como usar uma fonte de dados para se conectar ao SQL Server e, em seguida, usar um procedimento armazenado para recuperar dados.|  
  
## <a name="see-also"></a>Confira também

[Aplicativos de exemplo do JDBC Driver](../../jdbc/code-samples/sample-jdbc-driver-applications.md)
  
