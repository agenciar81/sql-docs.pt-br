---
title: Descrevendo parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d32e5212ba1ba28262d871498f2974485d38233
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040022"
---
# <a name="describing-parameters"></a>Descrever parâmetros
**SQLBindParameter** tem argumentos que descrevem o parâmetro: seu tipo, precisão e escala SQL. O driver usa essas informações, ou *metadados,* para converter o valor do parâmetro para o tipo necessário para a fonte de dados. À primeira vista, pode parecer que o driver está em uma posição melhor para saber os metadados do parâmetro do que o aplicativo; Afinal, o driver pode facilmente descobrir os metadados de uma coluna de conjunto de resultados. Acontece que esse não é o caso. Primeiro, a maioria das fontes de dados não fornece uma maneira para o driver descobrir os metadados do parâmetro. Segundo, a maioria dos aplicativos já conhecem os metadados.  
  
 Se uma instrução SQL for embutida em código no aplicativo, o gravador de aplicativos já saberá o tipo de cada parâmetro. Se uma instrução SQL for construída pelo aplicativo em tempo de execução, o aplicativo poderá determinar os metadados à medida que criar a instrução. Por exemplo, quando o aplicativo constrói a cláusula  
  
```  
WHERE OrderID = ?  
```  
  
 Ele pode chamar **SQLColumns** para a coluna OrderID.  
  
 A única situação na qual o aplicativo não pode determinar facilmente os metadados do parâmetro é quando o usuário insere uma instrução parametrizada. Nesse caso, o aplicativo chama **SQLPrepare** para preparar a instrução, **SQLNumParams** para determinar o número de parâmetros e **SQLDescribeParam** para descrever cada parâmetro. No entanto, como foi observado anteriormente, a maioria das fontes de dados não fornece uma maneira para o driver descobrir os metadados do parâmetro; portanto, não há suporte amplo para **SQLDescribeParam** .
