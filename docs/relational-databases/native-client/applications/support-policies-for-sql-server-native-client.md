---
title: Políticas de suporte para SQL Server Native Client | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 09c80cf4-23e6-4027-a24f-cdb9c87af811
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 400589fa583a9c75dcde2208622cff4c62e11ab9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761540"
---
# <a name="support-policies-for-sql-server-native-client"></a>Políticas de suporte do SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Este tópico aborda como vários componentes de acesso a dados podem ser usados com o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="server-support"></a>Suporte de servidor  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]O Native Client 11,0 dá suporte a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]conexões [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]com [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]o [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],, [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)],, e.  
  
## <a name="supported-operating-system-versions"></a>Versões de sistemas operacionais com suporte  
 A tabela a seguir lista os sistemas operacionais que oferecem suporte ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
|Versão do SQL Server Native Client|Sistemas operacionais com suporte|  
|--------------------------------------|---------------------------------|  
|SQL Server Native Client (SQL Server 2005)|Microsoft Windows 2000 Service Pack 4 ou posterior<br /><br /> Microsoft Windows Server 2003 ou posterior<br /><br /> Microsoft Windows XP Service Pack 1 ou posterior<br /><br /> Microsoft Windows Vista (exige o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 ou posterior)<br /><br /> Microsoft Windows Server 2008 R2 (requer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 ou posterior)|  
|SQL Server Native Client 10,0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)])|Microsoft Windows Server 2003 Service Pack 2 ou posterior<br /><br /> Microsoft Windows XP Service Pack 2 ou posterior<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2|  
|SQL Server Native Client 10,5 ([!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)])|Microsoft Windows Server 2003 Service Pack 2 ou posterior<br /><br /> Microsoft Windows XP Service Pack 2 ou posterior<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7|  
|SQL Server Native Client 11.0 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)])|Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7<br /><br /> Microsoft Windows 8<br /><br /> Microsoft Windows Server 2012|  
  
## <a name="ado-support-policies"></a>Políticas de suporte para ADO  
 Os aplicativos ADO podem usar o provedor OLE DB SQLOLEDB incluído no Windows caso não precisem dos recursos do [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou posterior.  
  
 Os aplicativos ADO podem usar a versão [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] do Native Client incluída [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]no. Os aplicativos ADO também podem usar o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 (incluído no [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]), mas caso façam isso, eles devem especificar `DataTypeCompatibility=80` nas cadeias de conexão. Apenas os recursos do [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] estão disponíveis quando `DataTypeCompatibility=80` está presente nas cadeias de conexão.  
  
## <a name="bcp-support-policies"></a>Políticas de suporte do BCP  
 A partir do [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], bcp.exe dá suporte a arquivos de dados que não sejam de mais de três versões do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anteriores em relação à versão do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no qual o bcp.exe é fornecido.  
  
## <a name="odbc-support-policies"></a>Políticas de suporte do ODBC  
 Os aplicativos devem usar o driver ODBC do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluído no sistema operacional Windows. É possível usar o driver ODBC do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client caso o aplicativo seja certificado para ser usado com uma versão específica do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="ole-db-support-policies"></a>Políticas de suporte do OLE DB  
 Os aplicativos devem usar o provedor de dados OLE DB do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluído no sistema operacional Windows. É possível usar o provedor de dados OLE DB do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client caso o aplicativo seja certificado para ser usado com uma versão específica do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 Os aplicativos OLE DB sem-certificação para serem usados com o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client podem usar o cliente do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native caso especifiquem `DataTypeCompatibility=80` nas cadeias de conexão.  
  
 Os aplicativos OLE DB que usam Componentes de Serviço do OLE DB só podem usar o cliente do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Nativo caso especifiquem `DataTypeCompatibility=80` nas cadeias de conexão. No entanto, nenhum recurso [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] adicionado após estará disponível nesse caso.  
  
## <a name="see-also"></a>Consulte Também  
 [Criando aplicativos com o SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
