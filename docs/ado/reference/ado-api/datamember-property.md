---
title: Propriedade DataMember | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 623f9b1f1e8873ddc4819bb8500c11edf09f5f76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919226"
---
# <a name="datamember-property"></a>Propriedade DataMember
Indica o nome do membro de dados que será recuperado do conjunto de [registros](../../../ado/reference/ado-api/recordset-object-ado.md) referenciado pela propriedade [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) .  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um valor de **cadeia de caracteres** . O nome não diferencia maiúsculas de minúsculas.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade é usada para criar controles ligados a dados com o ambiente de dados. O ambiente de dados mantém coleções de dados (fontes de dados) que contêm objetos nomeados (membros de dados) que serão representados como um objeto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 As propriedades **DataMember** e **DataSource** devem ser usadas juntas.  
  
 A propriedade **DataMember** determina qual objeto especificado pela propriedade **DataSource** será representado como um objeto **Recordset** . O objeto **Recordset** deve ser fechado antes que essa propriedade seja definida. Um erro será gerado se a propriedade **DataMember** não estiver definida antes da propriedade **DataSource** ou se o nome de **DataMember** não for reconhecido pelo objeto especificado na propriedade **DataSource** .  
  
## <a name="usage"></a>Uso  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Aplica-se A  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedade DataSource (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
