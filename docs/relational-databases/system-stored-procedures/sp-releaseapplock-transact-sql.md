---
title: sp_releaseapplock (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7b75962019d9b39728ceff0b151e770dd0f51a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68075629"
---
# <a name="sp_releaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Libera um bloqueio em um recurso de aplicativo.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @Resource= ] '*resource_name*'  
 É um nome de recurso de bloqueio especificado pelo aplicativo cliente. O aplicativo deve garantir que o recurso seja exclusivo. O nome especificado é internamente transformado em hash para um valor que pode ser armazenado no gerenciador de bloqueio do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* é **nvarchar (255)** sem padrão. *resource_name* é uma comparação binária, portanto diferencia maiúsculas de minúsculas, independentemente das configurações de agrupamento do banco de dados atual.  
  
 [ @LockOwner= ] '*lock_owner*'  
 É o proprietário do bloqueio, que é o valor de *lock_owner* quando o bloqueio foi solicitado. *lock_owner* é **nvarchar (32)**. O valor pode ser **Transaction** (o padrão) ou **Session**. Quando o valor de *lock_owner* é **transação**, por padrão ou especificado explicitamente, sp_getapplock deve ser executado de dentro de uma transação.  
  
 [ @DbPrincipal= ] '*database_principal*'  
 É o usuário, função ou função de aplicativo que tem permissões para um objeto em um banco de dados. O chamador da função deve ser membro da função de banco de dados fixa *database_principal*, dbo ou db_owner para chamar a função com êxito. O padrão é público.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 \>= 0 (êxito) ou < 0 (falha)  
  
|Valor|Result|  
|-----------|------------|  
|0|O bloqueio foi liberado com êxito.|  
|-999|Indica validação de parâmetro ou outro erro de chamada.|  
  
## <a name="remarks"></a>Comentários  
 Quando um aplicativo chama sp_getapplock várias vezes para o mesmo recurso de bloqueio, sp_releaseapplock deve ser chamado o mesmo número de vezes para liberar o bloqueio.  
  
 Quando o servidor é desligado por algum motivo, os bloqueios são liberados.  
  
## <a name="permissions"></a>Permissões  
 Requer associação à função public.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir libera o bloqueio associado à transação atual no recurso `Form1` do banco de dados `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [&#41;&#40;Transact-SQL de APPLOCK_MODE](../../t-sql/functions/applock-mode-transact-sql.md)   
 [&#41;&#40;Transact-SQL de APPLOCK_TEST](../../t-sql/functions/applock-test-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_getapplock](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
