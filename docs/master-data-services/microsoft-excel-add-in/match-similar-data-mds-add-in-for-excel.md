---
title: Corresponder dados semelhantes (Suplemento MDS para Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 34a8e6ac8d40e23e1ccf99eacff9d391e79a48a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074580"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Corresponder dados semelhantes (Suplemento do MDS para Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  No [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use a funcionalidade do DQS (Data Quality Services) para localizar semelhanças em seus dados.  
  
 Para executar esse procedimento, você pode:  
  
-   Usar a base de dados de conhecimento do Data Quality Services ou  
  
-   Criar sua própria base de dados de conhecimento do DQS personalizada e a política correspondente. Para obter mais informações, consulte [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   Você deve ter uma planilha que contenha dados gerenciados no MDS. Para obter mais informações, consulte [Exportar dados para o Excel do Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
-   Opcional. Você pode combinar outros dados com os dados gerenciados no MDS antes de verificar semelhanças. Para obter mais informações, consulte [Combinar dados &#40;Suplemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>Para localizar semelhanças usando a base de dados de conhecimento padrão  
  
1.  Na planilha que contém dados gerenciados no MDS, no grupo **Qualidade de Dados** , clique em **Corresponder Dados**.  
  
2.  Na caixa de diálogo **Corresponder Dados** , na lista **Base de Dados de Conhecimento do DQS** , selecione **Dados do DQS (padrão)** .  
  
3.  Para cada coluna que contém dados que você queira corresponder, adicione uma linha na caixa de diálogo. Para obter informações sobre os campos desta caixa de diálogo, consulte [Como definir parâmetros de regra de correspondência](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Quando o total de todos os valores de peso for igual a 100%, clique em **OK**.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>Para localizar semelhanças usando a base de dados de conhecimento personalizada  
  
1.  Na planilha que contém dados gerenciados no MDS, no grupo **Qualidade de Dados** , clique em **Corresponder Dados**.  
  
2.  Na lista **Base de Dados de Conhecimento do DQS** , selecione o nome da base de dados de conhecimento personalizada.  
  
3.  Para cada coluna na planilha, selecione um domínio do DQS.  
  
4.  Quando todos os domínios do DQS estiverem mapeados para colunas na planilha, clique em **OK**.  
  
## <a name="next-steps"></a>Próximas etapas  
  
-   Exiba informações adicionais para determinar quais dados são semelhantes. Para obter mais informações, consulte [Colunas de correspondência de qualidade de dados &#40;Suplemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Consulte também  
 [Correspondência de qualidade de dados no Suplemento do MDS para Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Correspondência de dados](../../data-quality-services/data-matching.md)  
  
  
