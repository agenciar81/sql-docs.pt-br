---
title: Unir tabelas automaticamente (Visual Database Tools) | Microsoft Docs
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
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 373264e421362d29ee00909707abc2be41ce1956
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36120252"
---
# <a name="join-tables-automatically-visual-database-tools"></a>Unir tabelas automaticamente (Visual Database Tools)
  Quando você adiciona duas ou mais tabelas a uma consulta, o [Designer de Consulta e Exibição](visual-database-tools.md) tenta determinar se elas estão relacionadas. Se estiverem, o Designer de Consulta e Exibição unirá automaticamente linhas de junção entre os retângulos que representam as tabelas ou objetos estruturados por tabela.  
  
 O Designer de Consulta e Exibição reconhecerá tabelas como unidas se:  
  
-   O banco de dados contiver informações que especifica que as tabelas estão relacionadas.  
  
-   Se duas colunas, uma em cada tabela, tiverem o mesmo nome e tipo de dados. A coluna deve ser uma chave primária em pelo menos uma das tabelas. Por exemplo, se você adicionar as tabelas `employee` e `jobs` , se a coluna `job_id` for a chave primária na tabela `jobs` , e se cada tabela tiver uma coluna chamada `job_id` com o mesmo tipo de dados, o Designer de Consulta e Exibição unirá as tabelas automaticamente.  
  
    > [!NOTE]  
    >  O Designer de Consulta e Exibição criará somente uma junção com base nas colunas com o mesmo nome e tipo de dados. Se for possível mais de uma união, o Designer de Consulta e Exibição será interrompido depois de criar uma união com base no primeiro conjunto de colunas coincidentes que encontrar.  
  
-   O Designer de Consulta e Exibição detecta que um critério de pesquisa (uma cláusula WHERE) é, de fato, uma condição de junção. Por exemplo, você pode adicionar as tabelas `employee` e `jobs`e, depois criar um critério de pesquisa que procure o mesmo valor na coluna `job_id` das duas tabelas. Quando você fizer isso, o Designer de Consulta e Exibição detecta que o critério de pesquisa resulta em uma junção e, depois, cria uma condição de junção baseado no critério de pesquisa.  
  
 Se o Designer de Consulta e Exibição criou uma junção não adequada à sua consulta, você poderá modificar a junção ou removê-la. Para obter detalhes, consulte [Modificar operadores de junção &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) e [Remover junções &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).  
  
 Se o Designer de Consulta e Exibição não unir automaticamente as tabelas em sua consulta, você poderá criar uma junção. Para obter detalhes, consulte [Unir tabelas manualmente &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como o Designer de consulta e exibição representa junções &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)   
 [Tópicos de instruções de consultas e modos de exibição de design &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Consultar com junções &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  