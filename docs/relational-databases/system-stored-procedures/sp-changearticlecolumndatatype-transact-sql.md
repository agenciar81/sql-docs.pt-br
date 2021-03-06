---
title: sp_changearticlecolumndatatype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f101d9081c7eb898d43c461a3bd64eca0c043b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995520"
---
# <a name="sp_changearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Altera o mapeamento de tipo de dados da coluna de artigo para uma publicação Oracle. Esse procedimento armazenado é executado no Distribuidor em qualquer banco de dados.  
  
> [!NOTE]  
>  Os mapeamentos de tipo de dados entre os tipos de Editor com suporte são fornecidos por padrão. Use **sp_changearticlecolumndatatype** somente ao substituir essas configurações padrão.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'`É o nome da publicação Oracle. a *publicação* é **sysname**, sem padrão.  
  
`[ @article = ] 'article'`É o nome do artigo. o *artigo* é **sysname**, sem padrão.  
  
`[ @column = ] 'column'`É o nome da coluna para a qual alterar o mapeamento de tipo de dados. a *coluna* é **sysname**, sem padrão.  
  
`[ @type = ] 'type'`É o nome do tipo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de dados na coluna de destino. o *tipo* é **sysname**, com um padrão de NULL.  
  
`[ @length = ] length`É o comprimento do tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de dados na coluna de destino. *Length* é **bigint**, com um padrão de NULL.  
  
`[ @precision = ] precision`É a precisão do tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de dados na coluna de destino. a *precisão* é **bigint**, com um padrão de NULL.  
  
`[ @publisher = ] 'publisher'`Especifica um não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publicador. o *Publicador* é **sysname**, com um padrão de NULL.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **Sp_changearticlecolumndatatype** é usado para substituir os mapeamentos de tipo de dados padrão entre os tipos de Publicador com suporte (Oracle e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Para exibir esses mapeamentos de tipo de dados padrão, execute [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 Só há suporte para **sp_changearticlecolumndatatype** para Publicadores Oracle. A execução desse procedimento armazenado em uma publicação [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resulta em um erro.  
  
 **sp_changearticlecolumndatatype** deve ser executado para cada mapeamento de coluna de artigo que deve ser alterado.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros da função de servidor fixa **sysadmin** ou **db_owner** função de banco de dados fixa podem ser executados **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>Consulte Também  
 [Alterar propriedades da publicação e do artigo](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Procedimentos armazenados de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
