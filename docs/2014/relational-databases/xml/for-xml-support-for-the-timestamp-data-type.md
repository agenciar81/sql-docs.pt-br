---
title: Suporte de FOR XML para o tipo de dados de carimbo de data/hora | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 094cd2859c9973c2d91145de5960d4752800ce1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63287674"
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a>Suporte de FOR XML para o tipo de dados timestamp
  Na transformação FOR XML, valores de tipo **timestamp** são tratados como dados **varbinary(8)** e sempre serão codificados na base 64. O esquema XSD ou XDR, se solicitado, reflete esse tipo.  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 Este é o resultado:  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Suporte a FOR XML para vários tipos de dados de SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
