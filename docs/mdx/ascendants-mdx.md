---
title: Ascendentes (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 16c6f812d1d7cae5a81a8e64fb425f4d33f4cb5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017064"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  Retorna o conjunto dos ascendentes de um membro especificado, inclusive o próprio membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
## <a name="remarks"></a>Comentários  
 A função **ascendentes** retorna todos os ancestrais de um membro do próprio membro até a parte superior da hierarquia do membro; mais especificamente, ele executa uma passagem de ordem posterior da hierarquia para o membro especificado e, em seguida, retorna todos os membros de ascendentes relacionados ao membro, inclusive em um conjunto. Isso é diferente da função [ancestral](../mdx/ancestor-mdx.md) , que retorna um membro ascendentes específico, ou ancestral, em um nível específico.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna a contagem de pedidos de revendedor para o `[Sales Territory].[Northwest]` membro e todos os ascendentes do membro do cubo **Adventure Works** . A função **ascendentes** constrói o conjunto que inclui o `[Sales Territory].[Northwest]` membro e seu ascendentes para o eixo de linhas.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de função MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
