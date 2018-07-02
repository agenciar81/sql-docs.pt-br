---
title: Resumir ou agregar valores utilizando expressões personalizadas (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7d1619f794ee3bdec67ec24a46dec81645b6b6fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36120255"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Resumir ou agregar valores usando expressões personalizadas (Visual Database Tools)
  Além de utilizar funções de agregação para agregar dados, você pode criar expressões personalizadas para produzir valores de agregação. É possível utilizar expressões personalizadas ao invés de funções de agregação em qualquer lugar de uma consulta de agregação.  
  
 Por exemplo, na tabela `titles` você poderia querer criar uma consulta que exibisse não só o preço médio, mas qual seria o preço médio se houvesse um desconto.  
  
 Você não pode incluir uma expressão baseada em cálculos que envolvem apenas linhas individuais na tabela; a expressão deve se basear em um valor de agregação, pois somente os valores de agregação estão disponíveis no momento em que a expressão é calculada.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>Para especificar uma expressão personalizada para um valor resumido  
  
1.  Especifique os grupos para a sua consulta. Para obter detalhes, veja [Agrupar linhas em resultados da consulta &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
2.  Vá para uma linha em branco do painel Critérios e digite a expressão na coluna **Colunas**.  
  
     O [Designer de Consulta e Exibição](query-and-view-designer-tools-visual-database-tools.md) atribui automaticamente um alias de coluna à expressão para criar um título da coluna útil na saída da consulta. Para obter mais detalhes, veja [Criar aliases de coluna &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
3.  Na coluna **Agrupar por** da expressão, selecione **Expressão**.  
  
4.  Executa a consulta.  
  
## <a name="see-also"></a>Consulte também  
 [Classificar e agrupar os resultados de consulta &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Resumir resultados da consulta &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  