---
title: Uso de palavras-chave de cadeia de conexão com o Driver do OLE DB para SQL Server | Microsoft Docs
description: Uso de palavras-chave de cadeia de conexão com o Driver do OLE DB para SQL Server
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
ms.openlocfilehash: cf754729c99d8826072b6b97acfc99a9986a9abc
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381883"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Uso de palavras-chave de cadeia de conexão com o Driver do OLE DB para SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Alguns OLE DB driver para APIs de SQL Server usam cadeias de conexão para especificar atributos de conexão. Cadeias de conexão são listas de palavras-chave e valores associados; cada palavra-chave identifica um atributo de conexão específico.  
  
> [!NOTE]
> O Driver do OLE DB para SQL Server permite ambiguidade em cadeias de conexão a fim de manter a compatibilidade com versões anteriores (por exemplo, algumas palavras-chave podem ser especificadas mais de uma vez e outras, conflitantes, permitidas tendo a resolução baseada na posição ou na precedência). Versões futuras do driver OLE DB para SQL Server podem não permitir ambigüidade em cadeias de conexão. Trata-se de uma boa prática, ao modificar aplicativos, usar o Driver do OLE DB para SQL Server para eliminar todas as dependências relacionadas à ambiguidade da cadeia de conexão.  
  
 As seções a seguir descrevem as palavras-chave que podem ser usadas com o driver de OLE DB para SQL Server e o ActiveX Data Objects (ADO) ao usar o driver OLE DB para SQL Server como o provedor de dados.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Palavras-chave da cadeia de conexão do Driver do OLE DB para SQL Server  
 Os aplicativos OLE DB podem inicializar objetos de fonte de dados de duas formas:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 No primeiro caso, uma cadeia de caracteres do provedor pode ser usada para inicializar as propriedades da conexão, definindo a propriedade DBPROP_INIT_PROVIDERSTRING no conjunto de propriedades DBPROPSET_DBINIT. No segundo, uma cadeia de caracteres de inicialização pode ser passada para o método **IDataInitialize::GetDataSource** a fim de inicializar as propriedades da conexão. Ambos os métodos inicializam as mesmas propriedades de conexão OLE DB, embora sejam usados conjuntos diferentes de palavras-chave. O conjunto de palavras-chave usado por **IDataInitialize::GetDataSource** é, no mínimo, a descrição das propriedades dentro do grupo de propriedades de inicialização.  
  
 Qualquer configuração da cadeia de caracteres do provedor tem uma propriedade OLE DB correspondente definida com um valor padrão ou explicitamente definida com um valor; o valor de propriedade OLE DB substituirá a configuração na cadeia de caracteres do provedor.  
  
 As propriedades boolianas definidas nas cadeias de caracteres do provedor por meio dos valores DBPROP_INIT_PROVIDERSTRING são definidas usando os valores "sim" e "não". As propriedades boolianas definidas nas cadeias de caracteres de inicialização que usam **IDataInitialize::GetDataSource** são definidas usando os valores "verdadeiro" e "falso".  
  
 Os aplicativos que usam **IDataInitialize::GetDataSource** também podem usar as palavras-chave usadas por **IDBInitialize::Initialize**, mas só para propriedades que não tenham um valor padrão. Caso um aplicativo use ambas as palavras-chave **IDataInitialize::GetDataSource** e **IDBInitialize::Initialize** na cadeia de caracteres de inicialização, é usada a definição da palavra-chave **IDataInitialize::GetDataSource**. É altamente recomendável que os aplicativos não usem palavras-chave **IDBInitialize::Initialize** em cadeias de conexão **IDataInitialize:GetDataSource**, uma vez que esse comportamento talvez não seja mantido em versões futuras.  
  
> [!NOTE]  
>  Uma cadeia de conexão passada por meio de **IDataInitialize::GetDataSource** é convertida em propriedades e aplicada por meio de **IDBProperties::SetProperties**. Se os serviços de componente encontraram a descrição da propriedade em **IDBProperties::GetPropertyInfo**, essa propriedade será aplicada como uma propriedade autônoma. Caso contrário, ela será aplicada por meio da propriedade DBPROP_PROVIDERSTRING. Por exemplo, se você especificar fonte de dados de cadeia de conexão **= Server1; Server = Server2**, a **fonte de dados** será definida como uma propriedade, mas o servidor entrará em uma cadeia de caracteres **do** provedor.  
  
 Se você especificar várias instâncias da mesma propriedade específica do provedor, o primeiro valor da primeira propriedade será usado.  
  
 As cadeias de conexão usadas por aplicativos OLE DB que usam DBPROP_INIT_PROVIDERSTRING com **IDBInitialize::Initialize** têm a seguinte sintaxe:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Os valores de atributo podem ser colocados entre chaves, sendo uma boa prática fazer isso. Isso evita problemas quando os valores de atributo contêm caracteres não alfanuméricos. Como a primeira chave de fechamento é usada para encerrar o valor, os valores não podem conter caracteres de chave de fechamento.  
  
 Um caractere de espaço após o sinal de igual (=) de uma palavra-chave de cadeia de conexão será interpretado como um literal, mesmo que o valor seja colocado entre aspas.  
  
 A tabela a seguir descreve as palavras-chave que podem ser usadas com DBPROP_INIT_PROVIDERSTRING.  
  
|Palavra-chave|Propriedade de inicialização|Descrição|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Sinônimo de "Endereço".|  
|**Endereço**|SSPROP_INIT_NETWORKADDRESS|O endereço de rede do servidor executando uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** é normalmente o nome da rede do servidor, mas pode ter outros nomes como, um pipe, um endereço IP ou uma porta TCP/IP e endereço de soquete.<br /><br /> Se você especificar um endereço IP, verifique se os protocolos de pipes nomeados ou TCP/IP estão habilitados no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> O valor do **endereço** tem precedência sobre o valor passado para o **servidor** em cadeias de conexão ao usar o driver OLE DB para SQL Server. Observe também que `Address=;` conecta-se com o servidor especificado na palavra-chave **Server**, enquanto que `Address= ;, Address=.;`, `Address=localhost;` e `Address=(local);` estabelecem uma conexão com o servidor local.<br /><br /> A sintaxe completa para a palavra-chave **Address** é a seguinte:<br /><br /> [_protocolo_ **:** ] _Endereço_[ **,** _porta &#124;\pipe\pipename_]<br /><br /> O_protocolo_ pode ser **tcp** (TCP/IP), **lpc** (memória compartilhada) ou **np** (pipes nomeados). Para obter mais informações sobre protocolos, consulte [Configurar protocolos de cliente](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Se nenhuma das palavras-chave de _protocolo_ nem de **rede** for especificada, OLE DB driver para SQL Server usará a ordem de protocolo especificada em [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* é a porta à qual se conectar, no servidor especificado. Por padrão, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usa a porta 1433.|   
|**APP**|SSPROP_INIT_APPNAME|A cadeia de caracteres que identifica o aplicativo.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Declara o tipo de carga de trabalho de aplicativo ao conectar-se a um servidor. Os valores possíveis são **ReadOnly** e **ReadWrite**.<br /><br /> O padrão é **ReadWrite**. Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|O nome do arquivo primário (com o nome do caminho completo incluído) de um banco de dados anexável. Para usar **AttachDBFileName**, você também deve especificar o nome do banco de dados com a palavra-chave Database da cadeia de caracteres do provedor. Caso o banco de dados já tenha sido anexado, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não o anexa novamente (ele usa o banco de dados anexado como sendo o padrão da conexão).|  
|**Autenticação**<a href="#table1_1"><sup id="table1_authmode">**1**</sup></a>|SSPROP_AUTH_MODE|Especifica a autenticação SQL ou Active Directory usada. Os valores válidos são:<br/><ul><li>`(not set)`: modo de autenticação determinado por outras palavras-chave.</li><li>ID de `ActiveDirectoryPassword:`User e autenticação de senha com uma identidade de Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` autenticação integrada com uma identidade de Azure Active Directory.</li><br/>**Observação:** A palavra-chave `ActiveDirectoryIntegrated` também pode ser usada para a autenticação do Windows para SQL Server. Ele substitui as palavras-chave de autenticação `Integrated Security` (ou `Trusted_Connection`). É **recomendável** que os aplicativos que usam palavras-chave `Integrated Security` (ou `Trusted_Connection`) ou suas propriedades correspondentes definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `ActiveDirectoryIntegrated` para habilitar o novo comportamento de criptografia e validação de certificado .<br/><br/><li>`ActiveDirectoryInteractive:` a autenticação interativa com uma identidade de Azure Active Directory. Esse método dá suporte à MFA (autenticação multifator) do Azure. </li><li>autenticação [do `ActiveDirectoryMSI:` identidade de serviço gerenciada (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) . Para uma identidade atribuída pelo usuário, a ID de usuário deve ser definida como a ID de objeto da identidade do usuário.</li><li>`SqlPassword:` autenticação usando a ID de usuário e a senha.</li><br/>**Observação:** É **recomendável** que os aplicativos que usam `SQL Server` autenticação definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `SqlPassword` para habilitar o [novo comportamento de criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Tradução automática**|SSPROP_INIT_AUTOTRANSLATE|Sinônimo de "Tradução automática".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura a conversão de caracteres OEM/ANSI. Os valores reconhecidos são "sim" e "não".|  
|**Backup de banco de dados**|DBPROP_INIT_CATALOG|Nome do banco de dados.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Especifica o modo de manipulação do tipo de dados a ser usado. Os valores reconhecidos são "0" para tipos de dados do provedor e "80" para tipos de dados do SQL Server 2000.|  
|**Criptografar**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Especifica se os dados devem ser criptografados antes de serem enviados pela rede. Os valores possíveis são "sim" e "não". O valor padrão é "não".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|O nome do servidor de failover usado no espelhamento de banco de dados.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|O SPN do parceiro de failover. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Idioma**|SSPROPT_INIT_CURRENTLANGUAGE|O idioma do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Habilita ou desabilita MARS na conexão caso o servidor seja [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou posterior. Os valores possíveis são "sim" e "não". O valor padrão é "não".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Sempre especifique **MultiSubnetFailover=Yes** ao se conectar ao ouvinte de um grupo de disponibilidade do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou a uma instância de cluster de failover do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=Yes** configura o driver do OLE DB para SQL Server para fornecer mais rapidez na detecção do servidor ativo (atualmente) e na conexão a ele. Os valores possíveis são **Sim** e **Não**. O padrão é **No**. Por exemplo:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Sinônimo de "Rede".|  
|**Rede**|SSPROP_INIT_NETWORKLIBRARY|A biblioteca de rede usada para estabelecer uma conexão com uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.|  
|**Biblioteca de rede**|SSPROP_INIT_NETWORKLIBRARY|Sinônimo de "Rede".|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Tamanho do pacote de rede. O padrão é 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Aceita as cadeias de caracteres "sim" e "não" como valores. Em caso de "não", o objeto de fonte de dados não tem permissão para manter informações confidenciais de autenticação|  
|**PWD**|DBPROP_AUTH_PASSWORD|A senha de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Servidor**|DBPROP_INIT_DATASOURCE|O nome de uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. O valor deve ser o nome de um servidor na rede, um endereço IP ou o nome de um alias do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> Quando não especificado, uma conexão é estabelecida com a instância padrão no computador local.<br /><br /> A palavra-chave **Address** substitui a palavra-chave **Server** .<br /><br /> É possível se conectar à instância padrão no servidor local especificando uma das seguintes opções:<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *nomedainstância* **;**<br /><br /> Para obter mais informações sobre o suporte a LocalDB, consulte [OLE DB driver for SQL Server Support for LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Para especificar uma instância nomeada do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], acrescente **\\** _InstanceName_.<br /><br /> Quando nenhum servidor está especificado, uma conexão é estabelecida com a instância padrão no computador local.<br /><br /> Se você especificar um endereço IP, verifique se os protocolos de pipes nomeados ou TCP/IP estão habilitados no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> A sintaxe completa para a palavra-chave **Server** é a seguinte:<br /><br /> **Server=** [_protocolo_ **:** ]*Server*[ **,** _porta_]<br /><br /> O_protocolo_ pode ser **tcp** (TCP/IP), **lpc** (memória compartilhada) ou **np** (pipes nomeados).<br /><br /> O seguinte é um exemplo de como especificar um pipe nomeado:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Esta linha especifica o protocolo de pipe nomeado, um pipe nomeado na máquina local (`\\.\pipe`), o nome da instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) e o nome padrão do pipe nomeado (`sql/query`).<br /><br /> Se nem uma palavra-chave de *protocolo* nem de **rede** for especificada, OLE DB driver para SQL Server usará a ordem de protocolo especificada em [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* é a porta à qual se conectar, no servidor especificado. Por padrão, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usa a porta 1433.<br /><br /> Os espaços são ignorados no início do valor passado para o **servidor** em cadeias de conexão ao usar o driver OLE DB para SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|O SPN do servidor. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Tempo Limite**|DBPROP_INIT_TIMEOUT|O tempo (em segundos) para aguardar a conclusão da inicialização da fonte de dados.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Quando "Sim", o instrui o driver de OLE DB para SQL Server usar o modo de autenticação do Windows para validação de logon. Do contrário, instrui o driver OLE DB para SQL Server a usar um nome de usuário e uma senha do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na validação do logon, e as palavras-chave UID e PWD devem ser especificadas.|  
|**TrustServerCertificate**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Aceita as cadeias de caracteres "sim" e "não" como valores. O valor padrão é "não", o que significa que o certificado do servidor será validado.|  
|**UID**|DBPROP_AUTH_USERID|O nome de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|Controla como os metadados são recuperados ao se conectar ao [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e mais recente. Os valores possíveis são "sim" e "não". O valor padrão é "não".<br /><br />Por padrão, o driver OLE DB para SQL Server usa procedimentos armazenados [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) e [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) para recuperar metadados. Esses procedimentos armazenados têm algumas limitações (por exemplo, eles falharão ao operar em tabelas temporárias). Definir **UseFMTONLY** como "Sim" instrui o driver a usar [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) para recuperação de metadados em vez disso.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Essa palavra-chave é preterida e sua configuração é ignorada pelo driver de OLE DB para SQL Server.|  
|**WSID**|SSPROP_INIT_WSID|O identificador da estação de trabalho.|  
  
<b id="table1_1">[1]:</b> Para melhorar a segurança, a criptografia e o comportamento de validação de certificado são modificados ao usar as propriedades de inicialização do token de acesso/autenticação ou suas palavras-chave de cadeia de conexão correspondentes. Para obter detalhes, consulte [criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 As cadeias de conexão usadas por aplicativos OLE DB que usam **IDataInitialize::GetDataSource** têm a seguinte sintaxe:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 O uso de propriedades deve estar em conformidade com a sintaxe permitida em seu escopo.  Por exemplo, **WSID** usa caracteres de chaves ( **{}** ) e **Application Name** usa caracteres de aspas simples ( **'** ) ou de aspas duplas ( **"** ). Apenas propriedades de cadeia de caracteres podem ser colocadas entre aspas. A tentativa de colocar um número inteiro ou propriedade enumerada entre aspas resultará no erro: "A Cadeia de Conexão não está de acordo com a especificação OLE DB".  
  
 Opcionalmente, os valores de atributos podem ser colocados entre aspas simples ou duplas, o que é uma boa prática. Isso evita problemas quando os valores contêm caracteres não alfanuméricos. O caractere de aspas usado também pode ser exibido em valores, desde que seja dobrado.  
  
 Um caractere de espaço após o sinal de igual (=) de uma palavra-chave de cadeia de conexão será interpretado como um literal, mesmo que o valor seja colocado entre aspas.  
  
 Se uma cadeia de conexão tiver mais de uma das propriedades listadas na tabela a seguir, o valor da última propriedade será usado.  
  
 A tabela a seguir descreve as palavras-chave que podem ser usadas com **IDataInitialize::GetDataSource**:  
  
|Palavra-chave|Propriedade de inicialização|Descrição|  
|-------------|-----------------------------|-----------------|  
|**Token de acesso**<a href="#table2_1"><sup id="table2_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|O token de acesso usado para autenticar para Azure Active Directory. <br/><br/>**Observação:** É um erro especificar essa palavra-chave e também `UID`, `PWD`, `Trusted_Connection` ou `Authentication` palavras-chave da cadeia de conexão ou suas propriedades/palavras-chave correspondentes.|
|**Nome do Aplicativo**|SSPROP_INIT_APPNAME|A cadeia de caracteres que identifica o aplicativo.|  
|**Intenção do aplicativo**|SSPROP_INIT_APPLICATIONINTENT|Declara o tipo de carga de trabalho de aplicativo ao conectar-se a um servidor. Os valores possíveis são **ReadOnly** e **ReadWrite**.<br /><br /> O padrão é **ReadWrite**. Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Autenticação**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Especifica a autenticação SQL ou Active Directory usada. Os valores válidos são:<br/><ul><li>`(not set)`: modo de autenticação determinado por outras palavras-chave.</li><li>ID de `ActiveDirectoryPassword:`User e autenticação de senha com uma identidade de Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` autenticação integrada com uma identidade de Azure Active Directory.</li><br/>**Observação:** A palavra-chave `ActiveDirectoryIntegrated` também pode ser usada para a autenticação do Windows para SQL Server. Ele substitui as palavras-chave de autenticação `Integrated Security` (ou `Trusted_Connection`). É **recomendável** que os aplicativos que usam palavras-chave `Integrated Security` (ou `Trusted_Connection`) ou suas propriedades correspondentes definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `ActiveDirectoryIntegrated` para habilitar o novo comportamento de criptografia e validação de certificado .<br/><br/><li>`ActiveDirectoryInteractive:` a autenticação interativa com uma identidade de Azure Active Directory. Esse método dá suporte à MFA (autenticação multifator) do Azure. </li><li>autenticação [do `ActiveDirectoryMSI:` identidade de serviço gerenciada (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) . Para uma identidade atribuída pelo usuário, a ID de usuário deve ser definida como a ID de objeto da identidade do usuário.</li><li>`SqlPassword:` autenticação usando a ID de usuário e a senha.</li><br/>**Observação:** É **recomendável** que os aplicativos que usam `SQL Server` autenticação definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `SqlPassword` para habilitar o [novo comportamento de criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Tradução automática**|SSPROP_INIT_AUTOTRANSLATE|Sinônimo de "Tradução automática".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura a conversão de caracteres OEM/ANSI. Os valores reconhecidos são "verdadeiro" e "falso".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|O tempo (em segundos) para aguardar a conclusão da inicialização da fonte de dados.|  
|**Idioma Atual**|SSPROPT_INIT_CURRENTLANGUAGE|O nome do idioma do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Fonte de dados**|DBPROP_INIT_DATASOURCE|O nome de uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.<br /><br /> Quando não especificado, uma conexão é estabelecida com a instância padrão no computador local.<br /><br /> Para obter mais informações sobre sintaxe de endereço válida, consulte a descrição da palavra-chave **Server** neste tópico.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Especifica o modo de manipulação do tipo de dados a ser usado. Os valores reconhecidos são "0" para tipos de dados de provedor e "80" para tipos de dados do [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|O nome do servidor de failover usado no espelhamento de banco de dados.|  
|**SPN do parceiro de failover**|SSPROP_INIT_FAILOVERPARTNERSPN|O SPN do parceiro de failover. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Catálogo Inicial**|DBPROP_INIT_CATALOG|Nome do banco de dados.|  
|**Nome do Arquivo Inicial**|SSPROP_INIT_FILENAME|O nome do arquivo primário (com o nome do caminho completo incluído) de um banco de dados anexável. Para usar **AttachDBFileName**, você também deve especificar o nome do banco de dados com a palavra-chave DATABASE da cadeia de caracteres do provedor. Caso o banco de dados já tenha sido anexado, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não o anexa novamente (ele usa o banco de dados anexado como sendo o padrão da conexão).|  
|**Segurança Integrada**|DBPROP_AUTH_INTEGRATED|Aceita o valor o "SSPI" para a Autenticação do Windows.|  
|**Conexão MARS**|SSPROP_INIT_MARSCONNECTION|Habilita ou desabilita MARS (Multiple Active Result Sets) na conexão. Os valores reconhecidos são "verdadeiro" e "falso". O padrão é "falso".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Sempre especifique **MultiSubnetFailover=True** ao se conectar ao ouvinte de um grupo de disponibilidade do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou a uma instância de cluster de failover do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configura o OLE DB Driver for SQL Server para fornecer mais rapidez na detecção do servidor ativo (atualmente) e na conexão a ele. Os valores possíveis são **True** e **False**. O padrão é **False**. Por exemplo:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Endereço de rede**|SSPROP_INIT_NETWORKADDRESS|O endereço de rede de uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.<br /><br /> Para obter mais informações sobre sintaxe de endereço válida, consulte a descrição da palavra-chave **Address** neste tópico.|  
|**Biblioteca de rede**|SSPROP_INIT_NETWORKLIBRARY|A biblioteca de rede usada para estabelecer uma conexão com uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Tamanho do pacote de rede. O padrão é 4096.|  
|**Senha**|DBPROP_AUTH_PASSWORD|A senha de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Aceita as cadeias de caracteres "verdadeiro" e "falso" como valores. Em caso de "falso", o objeto de fonte de dados não tem permissão para manter informações confidenciais de autenticação|  
|**Provedor**||Para OLE DB driver para SQL Server, isso deve ser "MSOLEDBSQL".|  
|**SPN do servidor**|SSPROP_INIT_SERVERSPN|O SPN do servidor. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Confiar em certificado do servidor**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Aceita as cadeias de caracteres "verdadeiro" e "falso" como valores. O valor padrão é "falso", o que significa que o certificado do servidor será validado.|  
|**Usar criptografia para dados**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Especifica se os dados devem ser criptografados antes de serem enviados pela rede. Os valores possíveis são "verdadeiro" e "falso". O valor padrão é "falso".|  
|**Usar FMTONLY**|SSPROP_INIT_USEFMTONLY|Controla como os metadados são recuperados ao se conectar ao [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e mais recente. Os valores possíveis são "verdadeiro" e "falso". O valor padrão é "falso".<br /><br />Por padrão, o driver OLE DB para SQL Server usa procedimentos armazenados [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) e [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) para recuperar metadados. Esses procedimentos armazenados têm algumas limitações (por exemplo, eles falharão ao operar em tabelas temporárias). A configuração **usar FMTONLY** como "true" instrui o driver a usar [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) para recuperação de metadados em vez disso.|  
|**ID de usuário**|DBPROP_AUTH_USERID|O nome de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID da estação de trabalho**|SSPROP_INIT_WSID|O identificador da estação de trabalho.|  
  
<b id="table2_1">[1]:</b> Para melhorar a segurança, a criptografia e o comportamento de validação de certificado são modificados ao usar as propriedades de inicialização do token de acesso/autenticação ou suas palavras-chave de cadeia de conexão correspondentes. Para obter detalhes, consulte [criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Observação** Na cadeia de conexão, a propriedade "Old Password" define SSPROP_AUTH_OLD_PASSWORD, que é a senha atual (provavelmente expirada) que não está disponível por meio de uma propriedade de cadeia de caracteres do provedor.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Palavras-chave da cadeia de conexão do ADO (ActiveX Data Objects)  
 Os aplicativos ADO definem a propriedade **ConnectionString** dos objetos **ADODBConnection** ou fornecem uma cadeia de conexão como um parâmetro ao método **Open** de objetos **ADODBConnection**.  
  
 Os aplicativos ADO também podem usar as palavras-chave usadas pelo método **IDBInitialize::Initialize** do OLE DB, mas só para propriedades que não tenham um valor padrão. Se um aplicativo usar as palavras-chave do ADO e **IDBInitialize::Initialize** na cadeia de caracteres de inicialização, a configuração da palavra-chave do ADO será usada. É altamente recomendável que os aplicativos só usem palavras-chave da cadeia de conexão do ADO.  
  
 As cadeias de conexão usadas pelo ADO têm a seguinte sintaxe:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Os valores de atributo podem ser colocados entre aspas duplas, sendo uma boa prática fazer isso. Isso evita problemas quando os valores contêm caracteres não alfanuméricos. Os valores de atributo não podem conter aspas duplas.  
  
 A seguinte tabela descreve as palavras-chave que podem ser usadas com uma cadeia de conexão do ADO:  
  
|Palavra-chave|Propriedade de inicialização|Descrição|  
|-------------|-----------------------------|-----------------|  
|**Token de acesso**<a href="#table3_1"><sup id="table3_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|O token de acesso usado para autenticar para Azure Active Directory.<br/><br/>**Observação:** É um erro especificar essa palavra-chave e também `UID`, `PWD`, `Trusted_Connection` ou `Authentication` palavras-chave da cadeia de conexão ou suas propriedades/palavras-chave correspondentes.|
|**Intenção do aplicativo**|SSPROP_INIT_APPLICATIONINTENT|Declara o tipo de carga de trabalho de aplicativo ao conectar-se a um servidor. Os valores possíveis são **ReadOnly** e **ReadWrite**.<br /><br /> O padrão é **ReadWrite**. Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Nome do Aplicativo**|SSPROP_INIT_APPNAME|A cadeia de caracteres que identifica o aplicativo.|  
|**Autenticação**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Especifica a autenticação SQL ou Active Directory usada. Os valores válidos são:<br/><ul><li>`(not set)`: modo de autenticação determinado por outras palavras-chave.</li><li>ID de `ActiveDirectoryPassword:`User e autenticação de senha com uma identidade de Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` autenticação integrada com uma identidade de Azure Active Directory.</li><br/>**Observação:** A palavra-chave `ActiveDirectoryIntegrated` também pode ser usada para a autenticação do Windows para SQL Server. Ele substitui as palavras-chave de autenticação `Integrated Security` (ou `Trusted_Connection`). É **recomendável** que os aplicativos que usam palavras-chave `Integrated Security` (ou `Trusted_Connection`) ou suas propriedades correspondentes definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `ActiveDirectoryIntegrated` para habilitar o novo comportamento de criptografia e validação de certificado .<br/><br/><li>`ActiveDirectoryInteractive:` a autenticação interativa com uma identidade de Azure Active Directory. Esse método dá suporte à MFA (autenticação multifator) do Azure. </li><li>autenticação [do `ActiveDirectoryMSI:` identidade de serviço gerenciada (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) . Para uma identidade atribuída pelo usuário, a ID de usuário deve ser definida como a ID de objeto da identidade do usuário.</li><li>`SqlPassword:` autenticação usando a ID de usuário e a senha.</li><br/>**Observação:** É **recomendável** que os aplicativos que usam `SQL Server` autenticação definam o valor da palavra-chave `Authentication` (ou sua propriedade correspondente) como `SqlPassword` para habilitar o [novo comportamento de criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Tradução automática**|SSPROP_INIT_AUTOTRANSLATE|Sinônimo de "Tradução automática".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura a conversão de caracteres OEM/ANSI. Os valores reconhecidos são "verdadeiro" e "falso".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|O tempo (em segundos) para aguardar a conclusão da inicialização da fonte de dados.|  
|**Idioma Atual**|SSPROPT_INIT_CURRENTLANGUAGE|O nome do idioma do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Fonte de dados**|DBPROP_INIT_DATASOURCE|O nome de uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.<br /><br /> Quando não especificado, uma conexão é estabelecida com a instância padrão no computador local.<br /><br /> Para obter mais informações sobre sintaxe de endereço válida, consulte a descrição da palavra-chave **Server** neste tópico.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Especifica o modo de manuseio do tipo de dados a ser usado. Os valores reconhecidos são "0" para tipos de dados do provedor e "80" para tipos de dados do SQL Server 2000.|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|O nome do servidor de failover usado no espelhamento de banco de dados.|  
|**SPN do parceiro de failover**|SSPROP_INIT_FAILOVERPARTNERSPN|O SPN do parceiro de failover. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Catálogo Inicial**|DBPROP_INIT_CATALOG|Nome do banco de dados.|  
|**Nome do Arquivo Inicial**|SSPROP_INIT_FILENAME|O nome do arquivo primário (com o nome do caminho completo incluído) de um banco de dados anexável. Para usar **AttachDBFileName**, você também deve especificar o nome do banco de dados com a palavra-chave DATABASE da cadeia de caracteres do provedor. Caso o banco de dados já tenha sido anexado, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não o anexa novamente (ele usa o banco de dados anexado como sendo o padrão da conexão).|  
|**Segurança Integrada**|DBPROP_AUTH_INTEGRATED|Aceita o valor o "SSPI" para a Autenticação do Windows.|  
|**Conexão MARS**|SSPROP_INIT_MARSCONNECTION|Habilita ou desabilita MARS na conexão caso o servidor seja [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou posterior. Os valores reconhecidos são "verdadeiro" e "falso".O padrão é "falso".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Sempre especifique **MultiSubnetFailover=True** ao se conectar ao ouvinte de um grupo de disponibilidade do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou a uma instância de cluster de failover do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configura o OLE DB Driver for SQL Server para fornecer mais rapidez na detecção do servidor ativo (atualmente) e na conexão a ele. Os valores possíveis são **True** e **False**. O padrão é **False**. Por exemplo:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Para obter mais informações sobre o driver de OLE DB para suporte de SQL Server para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [OLE DB driver para suporte de SQL Server para alta disponibilidade e recuperação de desastre](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Endereço de rede**|SSPROP_INIT_NETWORKADDRESS|O endereço de rede de uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.<br /><br /> Para obter mais informações sobre sintaxe de endereço válida, consulte a descrição da palavra-chave **Address** neste tópico.|  
|**Biblioteca de rede**|SSPROP_INIT_NETWORKLIBRARY|A biblioteca de rede usada para estabelecer uma conexão com uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] na organização.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Tamanho do pacote de rede. O padrão é 4096.|  
|**Senha**|DBPROP_AUTH_PASSWORD|A senha de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Aceita as cadeias de caracteres "verdadeiro" e "falso" como valores. Quando "falso", o objeto de fonte de dados não tem permissão para manter informações confidenciais de autenticação.|  
|**Provedor**||Para OLE DB driver para SQL Server, isso deve ser "MSOLEDBSQL".|  
|**SPN do servidor**|SSPROP_INIT_SERVERSPN|O SPN do servidor. O valor padrão é uma cadeia de caracteres vazia. Uma cadeia de caracteres vazia faz com que OLE DB driver para SQL Server use o SPN gerado pelo provedor padrão.|  
|**Confiar em certificado do servidor**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Aceita as cadeias de caracteres "verdadeiro" e "falso" como valores. O valor padrão é "falso", o que significa que o certificado do servidor será validado.|  
|**Usar criptografia para dados**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Especifica se os dados devem ser criptografados antes de serem enviados pela rede. Os valores possíveis são "verdadeiro" e "falso". O valor padrão é "falso".|  
|**Usar FMTONLY**|SSPROP_INIT_USEFMTONLY|Controla como os metadados são recuperados ao se conectar ao [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e mais recente. Os valores possíveis são "verdadeiro" e "falso". O valor padrão é "falso".<br /><br />Por padrão, o driver OLE DB para SQL Server usa procedimentos armazenados [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) e [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) para recuperar metadados. Esses procedimentos armazenados têm algumas limitações (por exemplo, eles falharão ao operar em tabelas temporárias). A configuração **usar FMTONLY** como "true" instrui o driver a usar [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) para recuperação de metadados em vez disso.|  
|**ID de usuário**|DBPROP_AUTH_USERID|O nome de logon do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID da estação de trabalho**|SSPROP_INIT_WSID|O identificador da estação de trabalho.|  
  
<b id="table3_1">[1]:</b> Para melhorar a segurança, a criptografia e o comportamento de validação de certificado são modificados ao usar as propriedades de inicialização do token de acesso/autenticação ou suas palavras-chave de cadeia de conexão correspondentes. Para obter detalhes, consulte [criptografia e validação de certificado](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Observação** Na cadeia de conexão, a propriedade "Old Password" define SSPROP_AUTH_OLD_PASSWORD, que é a senha atual (provavelmente expirada) que não está disponível por meio de uma propriedade de cadeia de caracteres do provedor.  
  
## <a name="see-also"></a>Confira também  
 [Criação de aplicativos com o Driver do OLE DB para SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
