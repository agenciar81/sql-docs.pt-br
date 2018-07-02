---
title: Excluindo dados usando diagramas de atualização XML (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32134713be17a0770eb58d69529cc34691c181a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36020883"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Excluindo dados usando diagramas de atualização XML (SQLXML 4.0)
  Um diagrama de atualização indica uma operação de exclusão quando uma instância de registro aparece no  **\<antes >** blocos sem registros correspondentes no  **\<depois >** bloco. Nesse caso, o diagrama exclui o registro de  **\<antes >** blocos do banco de dados.  
  
 Este é o formato do diagrama de atualização em uma operação de exclusão:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 Você pode omitir o  **\<depois >** marca se o diagrama estiver executando uma operação de exclusão. Se você não especificar opcional `mapping-schema` atributo, o  **\<ElementName >** especificado no diagrama de atualização mapeará para uma tabela de banco de dados e o mapa de atributos ou elementos filho para colunas na tabela.  
  
 Se um elemento especificado no diagrama corresponde a mais de uma linha na tabela ou não corresponde a nenhuma linha, o diagrama de atualização retornará um erro e cancelará todo o  **\<sincronização >** bloco. Só um registro de cada vez pode ser excluído por um elemento no diagrama.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos desta seção usam o mapeamento padrão (ou seja, nenhum esquema de mapeamento é especificado no diagrama de atualização). Para obter mais exemplos de diagramas de atualização que usam esquemas de mapeamento, consulte [especificando um esquema de mapeamento anotado em um diagrama de atualização &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Para criar exemplos de funcionamento usando os exemplos a seguir, você deve atender aos requisitos especificados em [requisitos para executar exemplos do SQLXML](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Excluindo um registro usando um diagrama de atualização  
 Os diagramas a seguir excluem dois registros da tabela HumanResources.Shift.  
  
 Nestes exemplos, o diagrama não especifica um esquema de mapeamento. Portanto, o diagrama usa o mapeamento padrão no qual o nome de elemento é mapeado para o nome de tabela e os atributos ou subelementos para as colunas.  
  
 Este primeiro diagrama é centrado em atributo e identifica dois turnos (dia-tarde e tarde-noite) no  **\<antes >** bloco. Porque não há nenhum registro correspondente a  **\<depois >** bloco, essa é uma operação de exclusão.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Para testar o diagrama de atualização  
  
1.  Conclua o exemplo B ("Inserindo vários registros usando um diagrama de atualização") em [inserindo dados usando diagramas de atualização XML &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Copie o diagrama acima para o bloco de notas e salve-o como updategram-removeshifts.XML na mesma pasta que foi usada para concluir ("Inserindo vários registros usando um diagrama de atualização") em [inserindo dados usando diagramas de atualização XML &#40;SQLXML 4.0&#41; ](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Crie e use o Script de teste SQLXML 4.0 (Sqlxml4test.vbs) para executar o diagrama de atualização.  
  
     Para obter mais informações, consulte [usando o ADO para executar consultas do SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Consulte também  
 [Considerações de segurança do diagrama de atualização &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  