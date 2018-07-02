---
title: Script de log suplementar Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 04e2c152da025473f049159a8e9eff4f4d28c3c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36010283"
---
# <a name="oracle-supplemental-logging-script"></a>Script de log suplementar Oracle
  Essa caixa de diálogo mostra o script suplementar de registro em log do Oracle.  
  
 Quando você prepara uma Instância CDC para uso, o Designer de CDC cria um script Oracle SQL que configura o registro em log suplementar para as tabelas a serem capturadas. O script suplementar de registro em log diz ao Oracle que, quando uma tabela específica é atualizada, os registros de alteração que ele grava no log de transação deve conter os dados de todas as colunas de interesse, não apenas as colunas que foram alteradas.  
  
 Dependendo das políticas do DBA Oracle em sua organização, executar o script suplementar de registro em log pode exigir revisão e aprovação de um DBA da Oracle.  
  
## <a name="options"></a>Opções  
 Veja a seguir as opções disponíveis sobre como executar o script.  
  
 **Executar o script**  
 Executa o script suplementar de registro em log nas tabelas definidas para a instância CDC. Para executar este script, o usuário Oracle deve ter permissão ALTER TABLE para todas as tabelas a serem capturadas e permissão SELECT na exibição DBA_LOG_GROUPS. Além disso, o usuário Oracle deve ter as credenciais para um uso de banco de dados Oracle com as permissões obrigatórias. Você pode deixar o programa solicitar que você insira as credenciais do Oracle e, em seguida, executar o script.  
  
 **Salvar como**  
 Salva o script em um arquivo de texto. Isto é usado se um administrador de banco de dados Oracle (DBA) precisar examinar e executar o script suplementar de registro em log. O programa deixa salvar o script em um arquivo de texto que você pode enviar posteriormente para o DBA da Oracle por email ou por outros meios para ser executa posteriormente (usando o utilitário SQL*Plus Oracle ou outra ferramenta para executar scripts em um banco de dados Oracle).  
  
 **Copiar**  
 Copiar o script para a área de transferência. Quando você estiver pronto, poderá colar o script em qualquer local necessário no caso de um administrador de banco de dados Oracle (DBA) precisa examinar e executar o script suplementar de registro em log.  
  
## <a name="see-also"></a>Consulte também  
 [Como gerenciar uma instância CDC](manage-a-cdc-instance.md)   
 [Gerenciar uma instância CDC](manage-a-cdc-instance.md)  
  
  