---
title: Totais visuais e totais não visuais | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f110b54d1a8a057f16b5e5682adc3beb04c54f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073729"
---
# <a name="visual-totals-and-non-visual-totals"></a>Totais visuais e totais não visuais
  Totais visuais são totais no final de uma coluna ou linha que somam todos os itens visíveis na coluna ou linha. Esse é o comportamento padrão da maioria das tabelas ao serem exibidas. Porém, ocasionalmente o usuário desejará exibir somente certas colunas em uma tabela, mas manter os totais da linha inteira, inclusive das colunas que não são exibidas. Esses são chamados de `Non Visual Totals`, porque o total provém de valores tanto visíveis como não visíveis.  
  
 O cenário a seguir demonstra o comportamento dos totais Não Visuais. A primeira etapa mostra o comportamento padrão dos Totais Visuais.  
  
 O exemplo a seguir é uma consulta da [Adventure Works] para obter números de [Valor das Vendas do Revendedor] em uma tabela em que as categorias de produto são as colunas e os tipos de negócios dos revendedores são as linhas. Observe que são fornecidos totais para produtos e revendedores quando a seguinte instrução SELECT é emitida:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Gera os seguintes resultados:  
  
|||||||  
|-|-|-|-|-|-|  
||**Todos os produtos**|**Acessórios**|**Bicicletas**|**Vestuário**|**Componentes**|  
|**Todos os revendedores**|**$80450596.98**|**$571297.93**|**$66302381.56**|**$1777840.84**|**$11799076.66**|  
|**Loja de bicicletas Specialty**|**$6756166.18**|**$65125.48**|**$6080117.73**|**$252933.91**|**$357989.07**|  
|**Revendedor de valor agregado**|**$34,967,517.33**|**$175002.81**|**$30892354.33**|**$592385.71**|**$3307774.48**|  
|**Armazén**|**$38,726,913.48**|**$331169.64**|**$29329909.50**|**$932521.23**|**$8133313.11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>Não visual em linhas e colunas  
 Para produzir uma tabela somente com dados dos produtos Accessories e Clothing, revendedores Value Added Reseller e Warehouse, mas mantendo os totais gerais, o seguinte poderia ser escrito usando NON VISUAL:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Gera os seguintes resultados:  
  
|||||  
|-|-|-|-|  
||**Todos os produtos**|**Acessórios**|**Vestuário**|  
|**Todos os revendedores**|**$80450596.98**|**$571297.93**|**$1777840.84**|  
|**Revendedor de valor agregado**|**$34,967,517.33**|**$175002.81**|**$592385.71**|  
|**Armazén**|**$38,726,913.48**|**$331169.64**|**$932521.23**|  
  
## <a name="non-visual-on-rows"></a>Não visual em linhas  
 Para criar uma tabela que totalize visualmente as colunas, mas nos totais de linhas exiba o total verdadeiro de todos os itens em [Category], a seguinte consulta deve ser emitida:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Observe como NON VISUAL é aplicado somente a [Category].  
  
 A consulta anterior gera os seguintes resultados:  
  
|||||  
|-|-|-|-|  
||Todos os Produtos|Acessórios|Clothing|  
|Todos os Revendedores|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Revendedor de Valor Agregado|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 Quando comparados aos resultados anteriores, você poderá observar que a linha [Todos os Revendedores] agora soma os valores exibidos para [Revendedor de Valor Agregado] e [Warehouse], mas a coluna [Todos os Produtos] mostra o valor total para todos os produtos, inclusive aqueles não exibidos.  
  
## <a name="see-also"></a>Consulte Também  
 [Conceitos principais em MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Autoexists](autoexists.md)   
 [Trabalhando com membros, tuplas e conjuntos &#40;&#41;MDX](working-with-members-tuples-and-sets-mdx.md)   
 [Conceitos básicos de consulta MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [A consulta MDX básica &#40;&#41;MDX](mdx-query-the-basic-query.md)   
 [Restringindo a consulta com eixos de consulta e de segmentação &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)   
 [Estabelecendo o contexto de cubo em uma consulta &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)  
  
  
