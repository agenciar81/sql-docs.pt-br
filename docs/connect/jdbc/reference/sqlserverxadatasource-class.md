---
title: Classe SQLServerXADataSource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c456336170cd7d4ad7cf37a0eebc52637f0a070
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67970226"
---
# <a name="sqlserverxadatasource-class"></a>Classe SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa um alocador para objetos [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) que é usado internamente.  
  
 **Pacote:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Implementa:** javax.sql.XADataSource  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Comentários  
 Um objeto que implementa a interface SQLServerXADataSource normalmente é registrado com um serviço de nomeação que usa a JNDI (Java Naming and Directory Interface).  
  
 A classe SQLServerXADataSource fornece conexões de banco de dados para uso em transações distribuídas (XA). A classe SQLServerXADataSource também dá suporte ao pool de conexões físicas. As interfaces SQLServerXADataSource e SQLServerXAConnection, definidas no pacote javax.sql, são implementadas por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Um objeto SQLServerXAConnection é uma conexão em pool que pode participar de uma transação distribuída. Mais precisamente, SQLServerXAConnection estende a interface SQLServerPooledConnection adicionando o método [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Esse método gera um objeto [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) que pode ser usado por um gerenciador de transação para coordenar o trabalho feito nessa conexão com os outros participantes na transação distribuída. Como elas estendem a interface SQLServerPooledConnection, os objetos SQLServerXAConnection dão suporte a todos os métodos de objetos SQLServerPooledConnection. Eles são conexões físicas reutilizáveis com uma fonte de dados subjacente e geram identificadores de conexão lógica que podem ser transmitidos de volta a um aplicativo JDBC.  
  
 Os objetos SQLServerXAConnection são produzidos por um objeto SQLServerXADataSource. Os objetos SQLServerConnectionPoolDataSource e SQLServerXADataSource são semelhantes porque ambos são implementados abaixo de uma camada de fonte de dados que é visível ao aplicativo JDBC. Essa arquitetura permite que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] seja compatível com as transações distribuídas de maneira transparente para o aplicativo. O SQLServerXADataSource pode ser configurado para se integrar ao DTC (Coordenador de Transações Distribuídas) do [!INCLUDE[msCoName](../../../includes/msconame_md.md)] para fornecer processamento de transações distribuído verdadeiro.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Referência de API do JDBC Driver](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
