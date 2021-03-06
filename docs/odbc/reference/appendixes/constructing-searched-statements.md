---
title: Construindo instruções pesquisadas | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8f24fe59da1377ea42900a8f1f0b89eb97125f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019173"
---
# <a name="constructing-searched-statements"></a>Construir instruções pesquisadas
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em novos trabalhos de desenvolvimento e planeje modificar os aplicativos que atualmente usam esse recurso. A Microsoft recomenda usar a funcionalidade de cursor do driver.  
  
 Para dar suporte a instruções UPDATE e DELETE posicionadas, a biblioteca de cursores constrói uma instrução **Update** ou **delete** pesquisada da instrução posicionada. Para dar suporte a chamadas para **SQLGetData** em um bloco de dados, a biblioteca de cursores constrói uma instrução **Select** pesquisada para criar um conjunto de resultados contendo a linha atual de dados. Em cada uma dessas instruções, a cláusula **Where** enumera os valores armazenados no cache para cada coluna associada que retorna SQL_PRED_SEARCHABLE ou SQL_PRED_BASIC para o identificador de campo de SQL_DESC_SEARCHABLE em **SQLColAttribute**.  
  
> [!CAUTION]  
>  A cláusula **Where** construída pela biblioteca de cursores para identificar a linha atual pode falhar ao identificar quaisquer linhas, identificar uma linha diferente ou identificar mais de uma linha.  
  
 Se uma instrução UPDATE ou DELETE posicionada afetar mais de uma linha, a biblioteca de cursores atualizará a matriz de status de linha somente para a linha na qual o cursor está posicionado e retornará SQL_SUCCESS_WITH_INFO e SQLSTATE 01001 (conflito de operação do cursor). Se a instrução não identificar nenhuma linha, a biblioteca de cursores não atualizará a matriz de status de linha e retornará SQL_SUCCESS_WITH_INFO e SQLSTATE 01001 (conflito de operação do cursor). Um aplicativo pode chamar **SQLRowCount** para determinar o número de linhas que foram atualizadas ou excluídas.  
  
 Se a cláusula **Select** usada para posicionar o cursor de uma chamada para **SQLGetData** identificar mais de uma linha, a **SQLGetData** não será garantida para retornar os dados corretos. Se não identificar nenhuma linha, **SQLGetData** retornará SQL_NO_DATA.  
  
 Se um aplicativo estiver em conformidade com as diretrizes a seguir, a cláusula **Where** construída pela biblioteca de cursores deverá identificar exclusivamente a linha atual, exceto quando isso for impossível, por exemplo, quando a fonte de dados contiver linhas duplicadas.  
  
-   **Associe colunas que identificam exclusivamente a linha.** Se as colunas associadas não identificarem exclusivamente a linha, a cláusula **Where** construída pela biblioteca de cursores poderá identificar mais de uma linha. Em uma instrução UPDATE ou DELETE posicionada, essa cláusula pode fazer com que mais de uma linha seja atualizada ou excluída. Em uma chamada para **SQLGetData**, essa cláusula pode fazer com que o driver retorne dados para a linha errada. A associação de todas as colunas em uma chave exclusiva garante que cada linha seja identificada exclusivamente.  
  
-   **Aloque buffers de dados grandes o suficiente para que nenhum truncamento ocorra.** O cache da biblioteca de cursores é uma cópia dos valores nos buffers de conjunto de linhas associados ao conjunto de resultados com **SQLBindCol**. Se os dados forem truncados quando forem colocados nesses buffers, eles também serão truncados no cache. Uma cláusula **Where** construída com valores truncados pode não identificar corretamente a linha subjacente na fonte de dados.  
  
-   **Especifique buffers de comprimento não nulo para dados binários C.** A biblioteca de cursores aloca buffers de comprimento em seu cache somente se o argumento de *StrLen_or_IndPtr* em **SQLBindCol** for não nulo. Quando o argumento *TargetType* é SQL_C_BINARY, a biblioteca de cursores requer o comprimento dos dados binários para construir uma cláusula **Where** a partir dos dados. Se não houver buffer de comprimento para uma coluna de SQL_C_BINARY e o aplicativo chamar **SQLGetData** ou tentar executar uma instrução UPDATE ou DELETE posicionada, a biblioteca de cursores retornará SQL_ERROR e SQLSTATE SL014 (uma solicitação posicionada foi emitida e nem todos os campos de contagem de coluna foram armazenados em buffer).  
  
-   **Especifique buffers de comprimento não nulo para colunas anuláveis.** A biblioteca de cursores aloca buffers de comprimento em seu cache somente se o argumento de *StrLen_or_IndPtr* em **SQLBindCol** for não nulo. Como SQL_NULL_DATA é armazenado no buffer de comprimento, a biblioteca de cursores supõe que qualquer coluna para a qual nenhum buffer de comprimento seja especificado seja não anulável. Se nenhuma coluna de comprimento for especificada para uma coluna anulável, a biblioteca de cursores construirá uma cláusula **Where** que usa o valor de dados para a coluna. Essa cláusula não identificará corretamente a linha.
