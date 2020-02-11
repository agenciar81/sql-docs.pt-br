---
title: Funções de cadeia de caracteres (driver ODBC do Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db1fbaffbee0f74625f4a11cad3b961f194e3829
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948773"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Funções de cadeia de caracteres (Driver ODBC do Visual FoxPro)
A tabela a seguir lista as funções de manipulação de cadeia de caracteres ODBC com suporte no driver ODBC do Visual FoxPro; Quando a gramática do Visual FoxPro para a mesma função difere da sintaxe ODBC, o equivalente do Visual FoxPro é listado.  
  
|Gramática ODBC|Gramática do Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(código)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|DIFERENÇA *(string_exp1, string_exp2)*||  
|INSERIR *(string_exp1, iniciar, comprimento, string_exp2)*|ITENS *(string_exp1, início, comprimento, string_exp2)*|  
|LCASE *(string_exp)*|INFERIOR *(string_exp)*|  
|ESQUERDA *(string_exp, contagem)*||  
|COMPRIMENTO *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|REPETIR *(string_exp, contagem)*|REPLICAte *(string_exp, Count)*|  
|REPLACE *(string_exp1, string_exp2, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|DIREITA *(string_exp, contagem)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|ESPAÇO *(contagem)*||  
|Subcadeia *de caracteres (string_exp, início, comprimento)*|SUBST *(string_exp, início, comprimento)*|  
|UCASE *(string_exp)*|UPPER *(string_exp)*|
