---
title: Selecionar um pacote | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 561495eaad4dbe41a0af05e80d3c2ba35d91cb74
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71293960"
---
# <a name="select-a-package"></a>Selecionar um Pacote

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Use a caixa de diálogo **Selecionar um Pacote** para especificar o pacote do qual a tarefa Fila de Mensagens pode receber mensagens.  
  
## <a name="static-options"></a>Opções estáticas  
 **Local**  
 Especifique o local do pacote. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Defina o local como uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ao selecionar esse valor, as opções dinâmicas **Servidor**, **Usar Autenticação do Windows**, **Usar Autenticação do SQL Server**, **Nome de usuário**e **Senha**são exibidas.|  
|Arquivo DTSX|Defina o local para um arquivo DTSX. Ao selecionar este valor,a opção dinâmica **Nome do arquivo**será exibida.|  
  
## <a name="location-dynamic-options"></a>Opções Dinâmicas de Local  
  
### <a name="location--sql-server"></a>Local = SQL Server  
 **Nome do pacote**  
 Selecione um pacote que esteja armazenado no servidor especificado.  
  
 **Servidor**  
 Forneça um nome de servidor ou selecione um servidor na lista.  
  
 **Usar Autenticação do Windows**  
 Clique para usar Autenticação do Windows.  
  
 **Usar Autenticação do SQL Server**  
 Clique para usar Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **User name**  
 Se usar Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , forneça um nome de usuário a ser usado no logon no servidor.  
  
 **Senha**  
 Se estiver usando a Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , forneça uma senha.  
  
### <a name="location--dtsx-file"></a>Local = arquivo DTSX  
 **Nome do arquivo**  
 Forneça o caminho de um pacote ou clique no botão Procurar **(…)** e localize o pacote.  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefa Fila de Mensagens](../../integration-services/control-flow/message-queue-task.md)  
  
  
