---
title: Configurar o Always Encrypted usando o PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6ad4a50d8aeca225ae0d00574a62cc428593ebb2
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72903013"
---
# <a name="configure-always-encrypted-using-powershell"></a>Configurar Always Encrypted usando o PowerShell
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

O módulo do SqlServer PowerShell fornece cmdlets para configurar o [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) no Banco de Dados SQL do Azure e no SQL Server 2016.

Always Encrypted cmdlets no módulo SqlServer trabalhar com chaves ou dados confidenciais, portanto, é importante que você execute os cmdlets em um computador seguro. Ao gerenciar o Always Encrypted, execute os cmdlets de um computador diferente do computador que hospeda a instância do SQL Server.

Como a meta principal do Always Encrypted é garantir que os dados confidenciais criptografados estejam seguros mesmo se o sistema do banco de dados for comprometido, executar um script do PowerShell que processa chaves ou dados confidenciais no computador do SQL Server pode reduzir ou anular os benefícios do recurso. Para obter recomendações adicionais relacionadas à segurança, consulte [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Considerações de segurança para o Gerenciamento de Chaves).

Links para os artigos individuais de cmdlet estão na parte [inferior dessa página](#aecmdletreference).

## <a name="prerequisites"></a>Prerequisites

Instalar o [módulo do SqlServer](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/sqlserver) em um computador seguro que NÃO seja um computador que hospeda a instância do SQL Server. O módulo pode ser instalado diretamente da Galeria do PowerShell.  Consulte as instruções de [download](../../../ssms/download-sql-server-ps-module.md) para ver mais detalhes.


## <a name="importsqlservermodule"></a> Importando o módulo SqlServer 

Para carregar o módulo SqlServer:

1.  Use o cmdlet **Set-ExecutionPolicy** para definir a política de execução de script adequada.
2.  Use o cmdlet **Import-Module** para importar o módulo SqlServer.

Este exemplo carrega o módulo SqlServer.

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> Conectando a um banco de dados

Alguns dos cmdlets do Always Encrypted trabalham com dados ou metadados no banco de dados e requerem que você se conecte ao banco de dados primeiro. Há dois métodos recomendados para se conectar a um banco de dados ao configurar o Always Encrypted usando o módulo SqlServer: 
1. Conectar-se usando o SQL Server PowerShell.
2. Conectar-se usando o SMO (SQL Server Management Objects).

### <a name="using-sql-server-powershell"></a>Usando o SQL Server PowerShell

Esse método funciona apenas para o SQL Server (não há suporte no Banco de Dados SQL do Azure).

Com o SQL Server PowerShell, você pode navegar nos caminhos usando aliases do Windows PowerShell semelhantes aos comandos normalmente usados para navegar em caminhos do sistema de arquivos. Depois de navegar para a instância de destino e para o banco de dados, os cmdlets subsequentes terão como destino esse banco de dados, como mostrado no exemplo a seguir:

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
Como alternativa, você pode especificar um caminho de banco de dados usando o parâmetro **Path** genérico, em vez de navegar até o banco de dados.


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
### <a name="using-smo"></a>Usando o SMO

Este método funciona para o Banco de Dados SQL do Azure e para o SQL Server.
Com o SMO, você pode criar um objeto da [Classe Database](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.database.aspx), e, em seguida, passar o objeto usando o parâmetro **InputObject** de um cmdlet que se conecta ao banco de dados.


```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```


Como alternativa, você pode usar a barra vertical:


```
$database | Get-SqlColumnMasterKey
```

## <a name="always-encrypted-tasks-using-powershell"></a>Tarefas do Always Encrypted usando o PowerShell

- [Configurar chaves do Always Encrypted usando o PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [Girar chaves Always Encrypted usando o PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Configurar a criptografia de coluna usando o PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Referência de cmdlet do Always Encrypted

Os cmdlets do PowerShell a seguir estão disponíveis para o Always Encrypted:

|CMDLET |Descrição
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)**   |Executa a autenticação no Azure e adquire um token de autenticação.
|**[Add-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlcolumnencryptionkeyvalue)**   |Adiciona um novo valor criptografado para um objeto de chave de criptografia da coluna existente no banco de dados.
|**[Complete-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/complete-sqlcolumnmasterkeyrotation)**   |Conclui a rotação de uma chave mestra de coluna
|**[Get-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnencryptionkey)** |Retorna todos os objetos de chave de criptografia de coluna no banco de dados ou retorna um objeto de chave de criptografia da coluna com o nome especificado.
|**[Get-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnmasterkey)** |Retorna os objetos de chave mestra da coluna definidos no banco de dados ou retorna um objeto de chave mestra da coluna com o nome especificado.
|**[Invoke-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/invoke-sqlcolumnmasterkeyrotation)**   |Inicia a rotação de uma chave mestra de coluna.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)**   |Cria um objeto SqlColumnMasterKeySettings descrevendo uma chave assimétrica armazenada no Cofre de Chaves do Azure.
|**[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)**   |Cria um objeto SqlColumnMasterKeySettings descrevendo uma chave assimétrica armazenada em um repositório de chaves com suporte à API de CNG (Cryptography Next Generation).
|**[New-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkey)** |Cria um objeto de chave de criptografia de coluna no banco de dados.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkeyencryptedvalue)** |Produz um valor criptografado de uma chave de criptografia da coluna.
|**[New-SqlColumnEncryptionSettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionsettings)**   |Cria um objeto SqlColumnEncryptionSettings que encapsula informações sobre a criptografia de uma única coluna, incluindo o tipo de criptografia e CEK.
|**[New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)** |Cria um objeto de chave mestra de coluna no banco de dados.
|**[New-SqlColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkeysettings)**|Cria um objeto SqlColumnMasterKeySettings para uma chave mestra de coluna com o provedor especificado e o caminho principal.
|**[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)**   |Cria um objeto SqlColumnMasterKeySettings descrevendo uma chave assimétrica armazenada em um repositório de chaves com um CSP (Provedor de Serviços de Criptografia) dando suporte à CAPI (Cryptography API).
|**[Remove-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkey)**   |Remove o objeto de chave de criptografia da coluna do banco de dados.
|**[Remove-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkeyvalue)** |Remove um valor criptografado de um objeto de chave de criptografia da coluna no banco de dados.
|**[Remove-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnmasterkey)**   |Remove o objeto de chave mestra da coluna do banco de dados.
|**[Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption)**   |Criptografa, descriptografa ou criptografa novamente as colunas especificadas no banco de dados.



## <a name="additional-resources"></a>Recursos adicionais

- [Always Encrypted (mecanismo de banco de dados)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Visão geral do gerenciamento de chaves do Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Usando o Always Encrypted com o Provedor de Dados .NET Framework para SQL Server](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Configurar o Always Encrypted usando o SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)


