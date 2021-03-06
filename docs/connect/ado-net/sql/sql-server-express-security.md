---
title: Segurança do SQL Server Express
description: Descreve considerações de segurança para o SQL Server Express.
ms.date: 09/26/2019
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: f704511abd15c6bc4eb96afc633b4cfb46f45e1f
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896297"
---
# <a name="sql-server-express-security"></a>Segurança do SQL Server Express

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

O SQL Server Express (Microsoft SQL Server Express Edition) é baseado no Microsoft SQL Server e dá suporte à maioria dos recursos do mecanismo de banco de dados. Ele foi criado para que recursos não essenciais e a conectividade de rede estejam desativados por padrão. Isso reduz a área de superfície disponível para ataque por um usuário mal-intencionado.  
  
Normalmente o SQL Server Express é instalado como uma instância nomeada. O nome padrão da instância é `SQLExpress`. Uma instância nomeada é identificada pelo nome de rede do computador mais o nome da instância especificado durante a instalação.  
  
## <a name="network-access"></a>Acesso de rede  
Por razões de segurança, os protocolos de rede se encontram desabilitados por padrão no SQL Server Express. Isso impede ataques de usuários externos que podem comprometer o computador que hospeda a instância do SQL Server Express. Você deve habilitar explicitamente a conectividade de rede e iniciar o serviço SQL Server Browser para se conectar a uma instância do SQL Server Express em outro computador.  
  
Depois que a conectividade de rede for habilitada, uma instância do SQL Server Express terá os mesmos requisitos de segurança que as outras edições do SQL Server.  
  
## <a name="user-instances"></a>Instâncias de usuário  
Uma instância de usuário é uma instância separada do mecanismo de banco de dados do SQL Server Express gerada por uma instância pai do SQL Server Express. A meta principal de uma instância de usuário é permitir que usuários que estão executando o Windows em uma conta de usuário com privilégios mínimos tenham privilégios de administrador do sistema (`sysadmin`) na instância do SQL Server Express no computador local deles. As instâncias de usuário não são destinadas a usuários que são administradores de sistema nos próprios computadores deles.  
  
Uma instância de usuário é gerada com base em uma instância primária do SQL Server ou do SQL Server Express em nome de um usuário. Ela é executada como um processo de usuário no contexto de segurança do usuário do Windows, não como um serviço. Os logons do SQL Server não são permitidos; há suporte somente para logons do Windows. Isso impede que o software em execução em uma instância de usuário faça alterações em todo o sistema que o usuário não teria permissões para fazer. Uma instância de usuário também é conhecida como uma instância filho ou de cliente e, às vezes, é denominada usando o acrônimo RANU ("executar como usuário normal").  
  
Cada instância de usuário é isolada de sua instância pai e de outra instância de usuário que esteja em execução no mesmo computador. Os bancos de dados instalados em instâncias de usuário são abertos somente no modo de usuário único; vários usuários não podem se conectar a eles. A replicação, consultas distribuídas e conexões remotas estão desabilitadas para instâncias de usuário. Quando conectados a uma instância de usuário, os usuários não têm nenhum privilégio especial na instância pai do SQL Server Express.  
  
## <a name="external-resources"></a>Recursos externos  
Para obter mais informações sobre o SQL Server Express, confira os recursos a seguir.  
  
|||  
|-|-|  
|[Manuais online do Microsoft SQL Server 2005 Express Edition](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Conclua a documentação do SQL Server 2005 Express Edition.|  
|[Instância de usuário para não administradores](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) nos Manuais Online do SQL Server|Descreve como criar e implantar instâncias de usuário.|  
|[Instâncias de usuário do SQL Server Express](sql-server-express-user-instances.md)|Descreve as capacidades de instância de usuário em um aplicativo ADO.NET. Fornece informações sobre como habilitar uma instância de usuário e conectar-se a uma instância de usuário usando um <xref:Microsoft.Data.SqlClient.SqlConnection>, o tempo de vida da instância do usuário e cenários de instância do usuário.|  
  
## <a name="next-steps"></a>Próximas etapas
- [Segurança do SQL Server](sql-server-security.md)
- [Instâncias de usuário do SQL Server Express](sql-server-express-user-instances.md)
