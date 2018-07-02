---
title: Destino de arquivo simples | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 624815a71ccd642cda1ee11db39ca08994cb6dff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36011183"
---
# <a name="flat-file-destination"></a>Destino de arquivo simples
  O destino de Arquivo Simples grava dados em um arquivo de texto. O arquivo de texto pode ser em formato delimitado, de largura fixa, largura fixa com delimitador de linha ou com imperfeição à direita.  
  
 Você pode configurar o destino de arquivo simples das seguintes formas:  
  
-   Forneça um bloco de texto que é inserido no arquivo antes de qualquer dado ser escrito. O texto pode fornecer informações como cabeçalhos de coluna.  
  
-   Especifique se os dados devem ser substituídos em um arquivo de destino que tenha o mesmo nome.  
  
 Esse destino utiliza um gerente de conexões de arquivo simples para acessar o arquivo de texto. Ao definir propriedades no gerenciador de conexões de arquivo simples que o arquivo simples usa, você pode especificar como o destino do arquivo simples formata e escreve o arquivo de texto. Quando você configura o gerenciador de conexões de arquivo simples, você especifica informações sobre o arquivo e sobre cada coluna do arquivo. Por exemplo, pode-se especificar os caracteres que delimitam colunas e linhas no arquivo e especificar o tipo de dados e o comprimento de cada coluna. Para obter mais informações, consulte [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 O destino de arquivo simples inclui a propriedade personalizada Header. Essa propriedade pode ser atualizada por uma expressão de propriedade quando o pacote é carregado. Para obter mais informações, consulte [Expressões do Integration Services &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md), [Usar expressões de propriedade em pacotes](../expressions/use-property-expressions-in-packages.md) e [Propriedades personalizadas de arquivo simples](flat-file-custom-properties.md).  
  
 Esse destino tem uma saída. Não dá suporte a uma saída de erro.  
  
## <a name="configuration-of-the-flat-file-destination"></a>Configuração do destino de Arquivo Simples  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou programaticamente.  
  
 Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor de Fonte de Arquivo Simples**, clique em um dos seguintes tópicos:  
  
-   [Editor de destino do arquivo simples &#40;página Gerenciador de Conexão&#41;](../flat-file-destination-editor-connection-manager-page.md)  
  
-   [Editor de destino do arquivo simples &#40;página mapeamentos&#41;](../flat-file-destination-editor-mappings-page.md)  
  
 A caixa de diálogo **Editor Avançado** reflete as propriedades que podem ser definidas programaticamente. Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor Avançado** ou programaticamente, clique em um dos seguintes tópicos:  
  
-   [Propriedades comuns](../common-properties.md)  
  
-   [Propriedades personalizadas de arquivo simples](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Para obter informações sobre como definir as propriedades do componente de fluxo de dados, consulte [Definir as propriedades de um componente de fluxo de dados](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Consulte também  
 [Fonte de arquivo simples](flat-file-source.md)   
 [Fluxo de Dados](data-flow.md)  
  
  