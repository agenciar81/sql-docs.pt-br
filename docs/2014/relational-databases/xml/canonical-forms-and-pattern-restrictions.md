---
title: Formas canônicas e restrições de padrões | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 731fce4f107240da52dbba01d95ce50b88fea5e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36120321"
---
# <a name="canonical-forms-and-pattern-restrictions"></a>Formas canônicas e restrições de padrões
  A faceta de padrão XSD permite restringir o espaço léxico de tipos simples. Quando uma restrição de padrão é colocada em um tipo para o qual há mais de uma representação léxica possível, alguns valores podem provocar comportamento inesperado na validação.  
  
 Esse comportamento ocorre porque representações léxicas desses valores não são armazenados no banco de dados. Portanto os valores são convertidos em suas representações canônicas quando serializados como saída. Se um documento contiver um valor cuja forma canônica não está em conformidade com a restrição de padrão de seu tipo, o documento será rejeitado se um usuário tentar reinseri-lo.  
  
 Para evitar isso, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejeita qualquer documento XML que contenha valores que não podem ser reinseridos, por causa da violação de restrições de padrão por suas formas canônicas. Por exemplo, o valor "33.000" não é validado em relação a um tipo derivado de **xs:decimal** com uma restrição de padrão de "33\\.0+". Embora "33.000" obedeça a esse padrão, a forma canônica, "33", não obedece.  
  
 Portanto, você deve ter cuidado ao aplicar facetas de padrão a tipos derivados dos seguintes tipos primitivos: `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary` , e `base64Binary`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emite um aviso quando qualquer componente desse tipo é adicionado a um coleção de esquemas.  
  
 A serialização imprecisa de valores de ponto flutuante tem um problema semelhante. Por causa do algoritmo de serialização de ponto flutuante usado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], é possível que valores semelhantes compartilhem a mesma forma canônica. Quando um valor de ponto flutuante é serializado e reinserido, seu valor pode ser ligeiramente alterado. Em casos raros, isso pode resultar em um valor que viola qualquer uma das facetas de seu tipo na reinserção: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**ou **maxExclusive**. Para evitar isso, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejeita todos os valores de tipos derivados de `xs:float` ou `xs:double` que não podem ser serializados e reinseridos.  
  
## <a name="see-also"></a>Consulte também  
 [Requisitos e limitações para o uso de Coleções de Esquemas XML no servidor](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  