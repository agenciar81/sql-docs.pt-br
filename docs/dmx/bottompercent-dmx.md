---
title: BottomPercent (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9d8b1665c6e6978af7dc673f7dd51a363da5c48d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892875"
---
# <a name="bottompercent-dmx"></a>BottomPercent (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retorna, em ordem crescente de classificação, as linhas mais baixas de uma tabela, cujo total cumulativo é, no mínimo, uma porcentagem especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
BottomPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="arguments"></a>Argumentos  
 *\<> De expressão de tabela*  
 O nome de uma coluna de tabela aninhada ou expressão com valor de tabela.  
  
 *\<expressão de classificação >*  
 Uma coluna na tabela aninhada ou expressão avaliada para uma coluna.  
  
 *\<percentual de >*  
 Um duplo que indica a porcentagem de destino total.  
  
## <a name="result-type"></a>Tipo de Resultado  
 Uma tabela.  
  
## <a name="remarks"></a>Comentários  
 A função **BottomPercent** retorna as linhas inferiores em ordem crescente de classificação. A classificação é baseada no valor avaliado da expressão de \<classificação > argumento para cada linha, de modo que a soma \<da expressão de classificação > valores seja pelo menos a porcentagem especificada pelo \<percentual de > argumento. **BottomPercent** retorna o menor número de elementos possíveis ao mesmo tempo em que atende ao valor percentual especificado.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma consulta de previsão em relação ao modelo de associação que você criou no [tutorial de mineração de dados básico](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Para entender como o BottomPercent funciona, pode ser útil primeiro executar uma consulta de previsão que retorna apenas a tabela aninhada.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  Neste exemplo, o valor fornecido como entrada contém uma única aspa e, portanto, deve ser precedido por outra aspa. Se você não tiver certeza da sintaxe para inserção de um caractere de escape, use o Construtor de Consultas de Previsão para criar a consulta. Quando você seleciona o valor da lista suspensa, o caractere de escape exigido é inserido. Para obter mais informações, consulte [criar uma consulta singleton no designer de mineração de dados](https://docs.microsoft.com/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Resultados do exemplo:  
  
|Modelo|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patch kit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Tubo de pneu de estrada|1588|0.106727603|0.101229538|  
|Capacete para Ciclismo|1473|0.098998589|0.094256014|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 A função BottomPercent usa os resultados dessa consulta e retorna as linhas com valores menores que somam ao percentual especificado.  
  
```  
SELECT   
BottomPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 O primeiro argumento para a função BottomPercent é o nome de uma coluna de tabela. Neste exemplo, a tabela aninhada é retornada chamando a função Predict e usando o argumento INCLUDE_STATISTICS.  
  
 O segundo argumento para a função BottomPercent é a coluna na tabela aninhada que você usa para ordenar os resultados. Neste exemplo, a opção INCLUDE_STATISTICS retorna as colunas $SUPPORT, $PROBABILTY e $ADJUSTED PROBABILITY. Este exemplo usa $SUPPORT porque os valores de suporte não são fracionários e, portanto, são mais fáceis de verificar.  
  
 O terceiro argumento para a função BottomPercent especifica a porcentagem, como um Double. Para obter as linhas que representam os 50% inferiores do suporte, digite 50.  
  
 Resultados do exemplo:  
  
|Modelo|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Capacete para Ciclismo|1473|0.098998589|0.094256014|  
|Tubo de pneu de estrada|1588|0.106727603|0.101229538|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
  
 **Observação** Este exemplo é fornecido apenas para ilustrar o uso de BottomPercent. Dependendo do tamanho do conjunto de dados, esta consulta pode demorar muito para ser executada.  
  
> [!WARNING]  
>  As funções MDX para TOPPERCENT e BOTTOMPERCENT podem gerar resultados inesperados quando os valores usados para calcular o percentual incluem números negativos. Esse comportamento não afeta as funções DMX. Para obter mais informações, [consulte &#40;MDX&#41;do BottomPercent](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência da função &#40;DMX&#41; das extensões de mineração de dados](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funções &#40;DMX&#41;](../dmx/functions-dmx.md)  
  
  
