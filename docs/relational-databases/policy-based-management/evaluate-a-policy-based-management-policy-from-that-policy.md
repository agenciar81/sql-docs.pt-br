---
title: Avaliar uma política do gerenciamento baseado em políticas dessa política | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c68042c58aed428bafaa38f6c468a759b4b55e47
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907635"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a>Avaliar uma política do Gerenciamento Baseado em Políticas dessa política
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Este tópico descreve como avaliar uma política usando essa política no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para avaliar uma política, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Requer a associação à função PolicyAdministratorRole no banco de dados msdb.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy"></a>Para avaliar uma política  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor que contém a política que você deseja avaliar.  
  
2.  Clique no sinal de adição para expandir a pasta **Gerenciamento** .  
  
3.  Clique no sinal de adição para expandir a pasta **Gerenciamento de Política**.  
  
4.  Clique no sinal de adição para expandir a pasta **Políticas** .  
  
5.  Clique com o botão direito do mouse na política a ser avaliada e selecione **Avaliar**.  
  
6.  Na caixa de diálogo **Avaliar Resultados**  , você pode ver os resultados da avaliação de política. Para destinos que não obedecem à política e têm propriedades que podem ser reconfiguradas pelo Gerenciamento de Política, é possível impor a conformidade com a política clicando em **Aplicar**. Para obter mais informações sobre as opções disponíveis contidas na caixa de diálogo **Avaliar Políticas** , consulte [Evaluate Policies Dialog Box, Policy Selection Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-policy-selection-page.md) e [Evaluate Policies Dialog Box, Evaluation Results Page](../../relational-databases/policy-based-management/evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  Quando terminar, clique em **Fechar**.  

