---
title: Como tratar metadados com o JDBC Driver | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0176e1da9a64e4ed32ba6989496178f5f9741193
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028021"
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Tratando metadados com o JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  O [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pode ser usado para trabalhar com metadados em um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de diversas formas. O driver JDBC pode ser usado para obter metadados sobre o banco de dados, um conjunto de resultados ou parâmetros.  
  
 O driver JDBC fornece três classes para recuperar metadados de um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), que é usado para retornar informações sobre o banco de dados que está conectado atualmente.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), que é usado para retornar informações sobre o conjunto de resultados.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), que é usado para retornar informações sobre os parâmetros de instruções preparadas e chamáveis.  
  
 Os tópicos nesta seção descrevem como você pode usar cada uma das três classes de metadados para trabalhar com metadados em um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Os métodos de metadados discutidos nesta seção são geralmente caros em termos de desempenho de aplicativo; portanto, tome cuidado com o seu uso.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Como usar metadados de banco de dados](../../connect/jdbc/using-database-metadata.md)|Descreve como recuperar informações de metadados sobre o banco de dados conectado atualmente.|  
|[Como usar metadados do conjunto de resultados](../../connect/jdbc/using-result-set-metadata.md)|Descreve como recuperar informações de metadados sobre o conjunto de resultados atual.|  
|[Como usar metadados de parâmetro](../../connect/jdbc/using-parameter-metadata.md)|Descreve como recuperar informações de metadados sobre os parâmetros de instruções preparadas e chamáveis.|  
  
## <a name="see-also"></a>Confira também  
 [Visão geral do JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
