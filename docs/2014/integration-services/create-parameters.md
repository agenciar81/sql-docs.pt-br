---
title: Criar parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 639e31d8ec9282a948a7eda9050cc1a2025ac65e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060137"
---
# <a name="create-parameters"></a>Create Parameters
  Use o [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para criar parâmetros de projeto e parâmetros de pacote. Os procedimentos a seguir fornecem instruções passo a passo para criar parâmetros de pacote/projeto.  
  
> [!NOTE]  
>  Se você estiver convertendo um projeto criado com o uso de uma versão anterior do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] no modelo de implantação de projeto, use o **Assistente de Conversão de Projeto do Integration Services** para criar parâmetros com base em configurações. Para obter mais informações, consulte [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
### <a name="to-create-package-parameters"></a>Para criar parâmetros de pacote  
  
1.  Abra o pacote no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]e clique na guia **Parâmetros** no SSIS Designer.  
  
     ![Guia Parâmetro de Pacote](media/denali-package-parameters.gif "Guia Parâmetro de Pacote")  
  
2.  Clique no botão **Adicionar Parâmetro** na barra de ferramentas.  
  
     ![Adicionar botão da barra de ferramentas](media/denali-parameter-add.gif "Botão Adicionar Barra de Ferramentas")  
  
3.  Insira valores para as propriedades **Nome**, **Tipo de Dados**, **Valor**, **Diferencia**e **Obrigatório** na própria lista ou na janela **Propriedades** . A tabela a seguir descreve essas propriedades.  
  
    |Propriedade|DESCRIÇÃO|  
    |--------------|-----------------|  
    |Nome|O nome do parâmetro.|  
    |Tipo de dados|O tipo de dados do parâmetro.|  
    |Valor padrão|O valor padrão do parâmetro atribuído em tempo de design. Também conhecido como o padrão de design.|  
    |Sigiloso|Valores de parâmetros confidenciais são criptografados no catálogo e aparecem como um valor NULL quando exibidos com o Transact-SQL ou o SQL Server Management Studio.|  
    |Obrigatório|Exige que um valor diferente do padrão de design seja especificado para que o pacote possa ser executado.|  
    |DESCRIÇÃO|Para fins de manutenção, a descrição do parâmetro. No [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], defina a descrição do parâmetro na janela Propriedades do Visual Studio quando o parâmetro for selecionado na janela de parâmetros aplicável.|  
  
    > [!NOTE]  
    >  Quando você implanta um projeto no catálogo, várias propriedades adicionais são associadas ao projeto. Para ver todas as propriedades de todos os parâmetros no catálogo, use a exibição [catalog.object_parameters &#40;Banco de Dados SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
4.  Salve o projeto para salvar as alterações nos parâmetros. Valores de parâmetros são armazenados no arquivo de projeto.  
  
    > [!WARNING]  
    >  Você pode editar no local na lista ou usar a janela **Propriedades** para modificar os valores de propriedades de parâmetro. Você pode excluir um parâmetro usando o botão da barra de ferramentas **Excluir (X)** . Usando o último botão da barra de ferramentas, você pode especificar um valor para um parâmetro que só seja usado quando você executar o pacote no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
    > [!NOTE]  
    >  Se você reabrir o arquivo de pacote sem abrir o projeto no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], a guia **Parâmetros** estará vazia e desabilitada.  
  
### <a name="to-create-project-parameters"></a>Para criar os parâmetros do projeto  
  
1.  Abra o projeto no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
2.  Clique com o botão direito em **Project.params** no Gerenciador de Soluções e clique em **Abrir** (OU) clique duas vezes em **Project.params** para abri-lo.  
  
     ![Janela Parâmetros do Projeto](media/denali-project-parameters.gif "Janela Parâmetros do Projeto")  
  
3.  Clique no botão **Adicionar Parâmetro** na barra de ferramentas.  
  
     ![Adicionar botão da barra de ferramentas](media/denali-parameter-add.gif "Botão Adicionar Barra de Ferramentas")  
  
4.  Insira valores para as propriedades **Nome**, **Tipo de Dados**, **Valor**, **Diferencia**e **Obrigatório** .  
  
    |Propriedade|DESCRIÇÃO|  
    |--------------|-----------------|  
    |Nome|O nome do parâmetro.|  
    |Tipo de dados|O tipo de dados do parâmetro.|  
    |Valor padrão|O valor padrão do parâmetro atribuído em tempo de design. Também conhecido como o padrão de design.|  
    |Sigiloso|Valores de parâmetros confidenciais são criptografados no catálogo e aparecem como um valor NULL quando exibidos com o Transact-SQL ou o SQL Server Management Studio.|  
    |Obrigatório|Exige que um valor diferente do padrão de design seja especificado para que o pacote possa ser executado.|  
    |DESCRIÇÃO|Para fins de manutenção, a descrição do parâmetro. No [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], defina a descrição do parâmetro na janela Propriedades do Visual Studio quando o parâmetro for selecionado na janela de parâmetros aplicável.|  
  
5.  Salve o projeto para salvar as alterações nos parâmetros. O valores de parâmetros são armazenados em configurações no arquivo de projeto. Salve o arquivo de projeto para confirmar em disco as alterações nos valores de parâmetros.  
  
    > [!WARNING]  
    >  Você pode editar no local na lista ou usar a janela **Propriedades** para modificar os valores de propriedades de parâmetro. Você pode excluir um parâmetro usando o botão da barra de ferramentas **Excluir (X)** . Usando o último botão da barra de ferramentas para abrir **Gerenciar Valores de Parâmetro** , você pode especificar um valor para um parâmetro que só seja usado quando você executar o pacote no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
## <a name="see-also"></a>Consulte Também  
 [Integration Services parâmetros&#41; &#40;SSIS](integration-services-ssis-package-and-project-parameters.md)  
  
  
