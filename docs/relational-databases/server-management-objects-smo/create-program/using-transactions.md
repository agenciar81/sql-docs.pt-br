---
title: Usando transações | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eaa6406e04eddbba012cfb61d6ae82a73b7f30bb
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148677"
---
# <a name="using-transactions"></a>Usando transações
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  No SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), o processamento de transações é feito por meio da conexão com a instância de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando o objeto <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. O <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objeto é referenciado <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> pela propriedade do <xref:Microsoft.SqlServer.Management.Smo.Server> objeto quando a conexão é estabelecida. Métodos como <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>e <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> pertencem à propriedade de objeto <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Criando programas SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
