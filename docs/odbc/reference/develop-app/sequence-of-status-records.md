---
title: Sequência de registros de status | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67eac22a630305f32f141ea18861e5638445f19b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094355"
---
# <a name="sequence-of-status-records"></a>Sequência de registros de status
Se dois ou mais registros de status forem retornados, o Gerenciador de driver e o driver os classificarão de acordo com as regras a seguir. O registro com a classificação mais alta é o primeiro registro. A origem de um registro (Gerenciador de driver, Driver, gateway e assim por diante) não é considerada durante a classificação de registros.  
  
-   **Erros** do Os registros de status que descrevem erros têm a classificação mais alta. Entre registros de erro, registros que indicam uma falha de transação ou possível falha de transação outrank todos os outros registros. Se dois ou mais registros descreverem a mesma condição de erro, sqlstates definidos pela especificação da CLI do grupo aberto (classes 03 a HZ) outrank definidos pelo ODBC e sqlstates definidos pelo driver.  
  
-   **Implementação-nenhum valor de dados definido** Os registros de status que descrevem os valores de dados definidos pelo driver (classe 02) têm a segunda classificação mais alta.  
  
-   **Avisos** Os registros de status que descrevem avisos (classe 01) têm a classificação mais baixa. Se dois ou mais registros descreverem a mesma condição de aviso, o aviso sqlestado definido pela especificação da CLI do grupo aberto outranká os sqlstates definidos pelo ODBC e definidos pelo driver.  
  
 Se houver dois ou mais registros com a classificação mais alta, será indefinido qual registro é o primeiro registro. A ordem de todos os outros registros é indefinida. Em particular, como os avisos podem aparecer antes dos erros, os aplicativos devem verificar todos os registros de status quando uma função retorna um valor diferente de SQL_SUCCESS.
