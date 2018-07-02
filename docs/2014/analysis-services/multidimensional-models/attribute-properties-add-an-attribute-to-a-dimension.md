---
title: Adicionar um atributo a uma dimensão | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b3f94d20f7f39efffd435793bf3dff808e115df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36122748"
---
# <a name="add-an--attribute-to-a-dimension"></a>Adicionar um atributo a uma dimensão
  Você pode adicionar um atributo a uma dimensão automática ou manualmente no [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Para criar um atributo automaticamente, na guia **Estrutura da Dimensão** , do Designer de Dimensão do [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], selecione a coluna que você deseja mapear para um atributo e a arraste do painel **Exibição da Fonte de Dados** para o painel **Atributos** . Essa ação criará um atributo mapeado para a coluna e atribuirá a ele o mesmo nome da coluna. Se já houver um atributo com esse nome, o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adicionará um número ordinal como sufixo, começando com "1" para o primeiro nome duplicado.  
  
 Para criar um atributo manualmente, configure o painel **Atributos** para exibição de grade. Na coluna Nome da última linha na grade, clique o  **\<novo atributo >** item. Digite um nome para o novo atributo. Será criado um atributo que não será mapeado para uma coluna e que manterá as configurações padrão para todas as suas propriedades. É possível definir o mapeamento na janela **Propriedades** do [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] configurando a propriedade **KeyColumns** do novo atributo.  
  
 Para obter mais informações, consulte [Definir um novo atributo automaticamente](attribute-properties-define-a-new-attribute-automatically.md), [Definir um novo atributo manualmente](../define-a-new-attribute-manually.md), [Associar um atributo a uma coluna de nome](attribute-properties-bind-an-attribute-to-a-name-column.md)e [Modificar a propriedade KeyColumn de um atributo](attribute-properties-modify-the-keycolumn-property.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência de propriedades de atributo de dimensão](dimension-attribute-properties-reference.md)  
  
  