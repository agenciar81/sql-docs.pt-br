---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3b8e4690b0e0c501fee26648cd9632fdcf28b1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913682"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
    
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do Produto|MSSQLSERVER|  
|ID do evento|5554|  
|Origem do Evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|FS_MINIVER_OVERFLOW|  
|Texto da mensagem|O número total de versões para um único arquivo atingiu o limite máximo definido pelo sistema de arquivos.|  
  
## <a name="explanation"></a>Explicação  
 No MARS (conjunto de resultados ativos múltiplos) ou em cenários de gatilho, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa a miniversão especificada pelo sistema operacional.  
  
## <a name="user-action"></a>Ação do usuário  
 Tente evitar atualizações repetidas nos dados da mesma transação.  
  
  
