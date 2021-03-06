---
title: Acessando linhas em um conjunto de registros hierárquico | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e73b2ca96cc5e7eb7683b72aa19fd59a318b8596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926352"
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Acessando linhas em um conjunto de registros hierárquico (exemplo)
O exemplo a seguir mostra as etapas necessárias para acessar linhas em um [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md)hierárquico:

1.  Os objetos **Recordset** das tabelas **Authors** e **titleauthor** são relacionados por ID de autor.

2.  O loop externo exibe o nome e o sobrenome de cada autor, o estado e a identificação.

3.  O conjunto de **registros** anexado para cada linha é recuperado da coleção [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) e atribuído a *rstTitleAuthor*.

4.  O loop interno exibe quatro campos de cada linha no **conjunto de registros**anexado.

 A propriedade [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) é definida como **false** para fins de ilustração, para que você possa ver o capítulo ser alterado explicitamente em cada iteração do loop externo. Para tornar o exemplo de código mais eficiente, você pode mover a atribuição na etapa 3 antes da primeira linha na etapa 2, para que a atribuição seja executada apenas uma vez. Em seguida, defina a propriedade [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) como **true**para que o *rstTitleAuthor* seja alterado implicitamente e automaticamente para o capítulo correspondente sempre que *RST* se mover para uma nova linha.

## <a name="example"></a>Exemplo

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>Consulte Também
 Definição de campos de [objeto de campo](../../../ado/reference/ado-api/field-object.md) de [visão geral de data Shaping](../../../ado/guide/data/data-shaping-overview.md) [(ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [gramática forma formal](../../../ado/guide/data/formal-shape-grammar.md) [Microsoft Data Shaping Service for OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) (ADO) [requerido Providers for Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md) [Shape Append](../../../ado/guide/data/shape-append-clause.md) function [Commands na](../../../ado/guide/data/shape-commands-in-general.md) [cláusula COMPUTE de forma](../../../ado/guide/data/shape-compute-clause.md) geral [Visual Basic for Applications funções](../../../ado/guide/data/visual-basic-for-applications-functions.md)
