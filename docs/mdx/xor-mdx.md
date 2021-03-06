---
title: XOR (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1657d9e58a0ae729a67e179602cd9a886ae923b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125785"
---
# <a name="xor-mdx"></a>XOR (MDX)


  Executa uma exclusão lógica em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>parâmetros  
 *Expression1*  
 Uma linguagem MDX válida que retorna um valor numérico.  
  
 *Expression2*  
 Uma expressão MDX válida que retorna um valor numérico.  
  
## <a name="return-value"></a>Valor retornado  
 Um valor booliano que retornará **true** se um e apenas um argumento for avaliado como **true**; caso contrário, **false**.  
  
## <a name="remarks"></a>Comentários  
 O operador **XOR** trata os parâmetros como valores Boolianos (zero, 0, como **false**; caso contrário, **true**) antes que o operador execute a exclusão lógica. A tabela a seguir ilustra como o operador **XOR** executa a exclusão lógica.  
  
|*Expression1*|*Expression2*|Valor retornado|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**for**|  
|**true**|**for**|**true**|  
|**for**|**true**|**true**|  
|**for**|**for**|**for**|  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de operador MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
