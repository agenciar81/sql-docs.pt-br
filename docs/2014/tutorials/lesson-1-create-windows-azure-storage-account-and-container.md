---
title: 'Lição 1: Criar uma conta de armazenamento e um contêiner do Windows Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9047c517fe4766ab5c3792d2fa2bf92eb7197965
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028501"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>Lição 1: Criar conta e contêiner de Armazenamento do Microsoft Azure
  Para que possa iniciar o armazenamento de arquivos de dados do SQL Server no Armazenamento do Windows Azure, você deve primeiro criar uma conta de Armazenamento do Windows Azure e um contêiner de blob e uma assinatura de acesso compartilhado. A lição 1 conduzirá você pelas etapas do registro em log no Portal de Gerenciamento do Windows Azure, criando uma conta de armazenamento, um contêiner de blob e uma assinatura de acesso compartilhado.  
  
 Por padrão, somente o proprietário da conta de armazenamento pode acessar blobs, tabelas e filas nessa conta. Para acessar esses recursos usando esse novo aprimoramento do SQL Server sem compartilhar a chave de acesso da conta de armazenamento, será necessário fazer o seguinte:  
  
-   Defina as permissões do contêiner como privadas.  
  
-   Crie uma assinatura de acesso compartilhado. Ela permitirá que você delegue acesso restrito a um contêiner, um blob, uma tabela ou um recurso de fila, especificando o intervalo no qual os recursos estarão disponíveis e as permissões que um cliente terá nesse intervalo.  
  
-   Use uma política de acesso armazenado para gerenciar assinaturas de acesso compartilhado para um contêiner ou seus blobs. A política de acesso armazenado oferece a você uma medida adicional de controle sobre suas assinaturas de acesso compartilhado, além de fornecer um meio simples de revogá-los.  
  
 Para obter mais informações, consulte [gerenciar o acesso aos recursos de armazenamento do Windows Azure](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Criar uma conta de armazenamento  
 Para criar uma conta de armazenamento no Portal de Gerenciamento do Windows Azure, execute estas etapas:  
  
1.  Faça logon no [portal de gerenciamento do Windows Azure](https://manage.windowsazure.com) usando sua conta. Se você não tiver uma conta do Windows Azure, visite [avaliação gratuita do Windows Azure](http://www.windowsazure.com/pricing/free-trial/).  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Use as instruções passo a passo para [criar uma conta de armazenamento](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Observe que, ao criar uma conta de armazenamento a ser usada para o recurso de arquivos de dados do SQL Server no Windows Azure, você deve desmarcar ou desabilitar a replicação geográfica. Isso acontece porque a ordem de gravação não é garantida para vários blobs que participam da replicação geográfica. Se uma conta de armazenamento for replicada geograficamente e a recuperação for necessária, ocorrerá um dano.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Criar um contêiner de blob  
 No Windows Azure, um contêiner fornece um agrupamento de um conjunto de blobs. Todos os blobs devem estar em um contêiner. Uma conta de armazenamento pode conter um número ilimitado de contêineres, mas deve ter pelo menos um contêiner. Um contêiner pode armazenar um número ilimitado de blobs. Para obter informações mais atualizadas sobre os limites de tamanho de armazenamento, consulte [como usar o serviço de armazenamento de blob do Windows Azure no .net](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Para criar um contêiner no Windows Azure, siga estas etapas:  
  
1.  Faça logon no [portal de gerenciamento do Windows Azure](https://manage.windowsazure.com).  
  
2.  Selecione a conta de armazenamento, clique na guia contêineres e clique em **Adicionar contêiner** na parte inferior da tela, que abre uma nova caixa de diálogo.  
  
3.  Insira um nome do contêiner.  
  
4.  Selecione **privado** para **tipo de acesso**. Quando você definir o acesso para privado, o contêiner e os dados de blob poderão ser lidos somente pelo proprietário da conta do Windows Azure.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Para criar uma contêiner de modo programático, você também poderá usar as APIs REST. Para obter mais informações, consulte [criar contêiner](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) e também [referência da API REST dos serviços de armazenamento do Windows Azure](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Próxima lição:**  
  
 [Lição 2. Criar uma política no contêiner e gerar uma chave SAS &#40;&#41; de assinatura de acesso compartilhado](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  
