---
title: sys. database_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2521d9543c71d9dee298fbb58518163fd45fbfdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67999532"
---
# <a name="sysdatabase_credentials-transact-sql"></a>sys. database_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Retorna uma linha para cada credencial no escopo do banco de dados no banco de dados.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Em vez disso, use [Sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) .    
  
|Nome da coluna|Tipo de dados|DESCRIÇÃO|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID da credencial no escopo do banco de dados. É exclusivo no banco de dados.|  
|name|**sysname**|Nome da credencial no escopo do banco de dados. É exclusivo no banco de dados.|  
|credential_identity|**nvarchar(4000)**|Nome da identidade a ser usada. Geralmente é um usuário do Windows. Não precisa ser exclusivo.|  
|create_date|**datetime**|Hora em que a credencial no escopo do banco de dados foi criada.|  
|modify_date|**datetime**|Hora em que a credencial no escopo do banco de dados foi modificada pela última vez.|  
|target_type|**nvarchar (100)**|Tipo de credencial no escopo do banco de dados. Retorna NULL para credenciais no escopo do banco de dados.|  
|target_id|**int**|ID do objeto ao qual a credencial no escopo do banco de dados está mapeada. Retorna 0 para credenciais no escopo do banco de dados|  
  
## <a name="permissions"></a>Permissões  
 Requer a permissão `CONTROL` no banco de dados.  
  
## <a name="see-also"></a>Consulte Também  
 [&#41;de credenciais &#40;Mecanismo de Banco de Dados](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CRIAR CREDENCIAl no escopo do banco de dados &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTERAÇÃO de CREDENCIAl no escopo do banco de dados &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [Descartar CREDENCIAl no escopo do banco de dados &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
