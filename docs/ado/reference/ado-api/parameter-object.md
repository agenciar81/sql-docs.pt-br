---
title: Objeto de parâmetro | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15df27e3dc48decf743a78dd4d147a22dc7cf276
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931662"
---
# <a name="parameter-object"></a>Objeto Parameter
Representa um parâmetro ou argumento associado a um objeto de [comando](../../../ado/reference/ado-api/command-object-ado.md) com base em uma consulta parametrizada ou em um procedimento armazenado.  
  
## <a name="remarks"></a>Comentários  
 Muitos provedores oferecem suporte a comandos com parâmetros. Esses são comandos nos quais a ação desejada é definida uma vez, mas variáveis (ou parâmetros) são usadas para alterar alguns detalhes do comando. Por exemplo, uma instrução SQL SELECT poderia usar um parâmetro para definir os critérios de correspondência de uma cláusula WHERE e outra para definir o nome da coluna para uma cláusula SORT BY.  
  
 Os objetos de **parâmetro** representam parâmetros associados a consultas parametrizadas ou os argumentos in/out e os valores de retorno de procedimentos armazenados. Dependendo da funcionalidade do provedor, algumas coleções, métodos ou propriedades de um objeto de **parâmetro** podem não estar disponíveis.  
  
 Com as coleções, métodos e propriedades de um objeto de **parâmetro** , você pode fazer o seguinte:  
  
-   Defina ou retorne o nome de um parâmetro com a propriedade [Name](../../../ado/reference/ado-api/name-property-ado.md) .  
  
-   Defina ou retorne o valor de um parâmetro com a propriedade [Value](../../../ado/reference/ado-api/value-property-ado.md) . **Value** é a propriedade padrão do objeto **Parameter** .  
  
-   Defina ou retorne características de parâmetro com os [atributos](../../../ado/reference/ado-api/attributes-property-ado.md), [direção](../../../ado/reference/ado-api/direction-property.md), [precisão](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [tamanho](../../../ado/reference/ado-api/size-property-ado-parameter.md)e propriedades de [tipo](../../../ado/reference/ado-api/type-property-ado.md) .  
  
-   Passe dados binários longos ou de caractere para um parâmetro com o método [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) .  
  
-   Acesse atributos específicos do provedor usando a coleção de [Propriedades](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
 Se você souber os nomes e as propriedades dos parâmetros associados ao procedimento armazenado ou à consulta parametrizada que deseja chamar, poderá usar o método [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) para criar objetos de **parâmetro** com as configurações de propriedade apropriadas e usar o método [Append](../../../ado/reference/ado-api/append-method-ado.md) para adicioná-los à coleção de [parâmetros](../../../ado/reference/ado-api/parameters-collection-ado.md) . Isso permite que você defina e retorne valores de parâmetro sem precisar chamar o método de [atualização](../../../ado/reference/ado-api/refresh-method-ado.md) na coleção de **parâmetros** para recuperar as informações de parâmetro do provedor, uma operação potencialmente intensiva de recursos.  
  
 O objeto de **parâmetro** não é seguro para scripts.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, métodos e eventos do objeto Parameter](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Objeto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Método CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Coleção Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Coleção Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
